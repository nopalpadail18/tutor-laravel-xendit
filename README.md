# tutor-laravel-xendit
TITLE: Removing Multiple Possible Suffixes in Laravel PHP
DESCRIPTION: The chopEnd method can also accept an array of values, removing the first one found at the end of the string.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_94

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$url = Str::of('http://laravel.com')->chopEnd(['.com', '.io']);

// 'http://laravel'
```

----------------------------------------

TITLE: Faking All Unmatched URLs (Fallback) - PHP
DESCRIPTION: This snippet shows how to provide a fallback fake response for any HTTP request URL that doesn't match other specific patterns defined in the `Http::fake()` array. Using the '*' wildcard as a key ensures that any unmatched request receives the specified default fake response. Requires the `Illuminate\Support\Facades\Http` facade.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_45

LANGUAGE: php
CODE:
```
Http::fake([
    \/\/ Stub a JSON response for GitHub endpoints...
    'github.com\/*' => Http::response(['foo' => 'bar'], 200, ['Headers']),

    \/\/ Stub a string response for all other endpoints...
    '*' => Http::response('Hello World', 200, ['Headers']),
]);
```

----------------------------------------

TITLE: Using Fluent Strings afterLast() Method in Laravel
DESCRIPTION: The afterLast method returns everything after the last occurrence of a given value in a string, useful for extracting file extensions or trailing segments.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_78

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$slice = Str::of('App\Http\Controllers\Controller')->afterLast('\\');

// 'Controller'
```

----------------------------------------

TITLE: Removing Suffix from String in Laravel PHP
DESCRIPTION: The chopEnd method removes the last occurrence of a given value only if it appears at the end of the string.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_93

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$url = Str::of('https://laravel.com')->chopEnd('.com');

// 'https://laravel'
```

----------------------------------------

TITLE: Using Str::chopEnd for String Suffix Removal in PHP
DESCRIPTION: The Str::chopEnd method removes the last occurrence of the given value only if it appears at the end of the string. It can also accept an array of values to check.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_15

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$url = Str::chopEnd('app/Models/Photograph.php', '.php');

// 'app/Models/Photograph'
```

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$url = Str::chopEnd('laravel.com/index.php', ['/index.html', '/index.php']);

// 'laravel.com'
```

----------------------------------------

TITLE: Conditionally Modifying a String Based on Ending Content in Laravel
DESCRIPTION: The whenEndsWith method invokes the given closure if the string ends with the given sub-string. The closure will receive the fluent string instance.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_162

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;
use Illuminate\Support\Stringable;

$string = Str::of('disney world')->whenEndsWith('world', function (Stringable $string) {
    return $string->title();
});

// 'Disney World'
```

----------------------------------------

TITLE: Implementing CSP Nonce Middleware in Laravel
DESCRIPTION: Creates a middleware class to handle Content Security Policy headers and nonce generation for script and style tags.
SOURCE: https://github.com/laravel/docs/blob/12.x/vite.md#2025-04-23_snippet_17

LANGUAGE: php
CODE:
```
<?php

namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Vite;
use Symfony\Component\HttpFoundation\Response;

class AddContentSecurityPolicyHeaders
{
    /**
     * Handle an incoming request.
     *
     * @param  \Closure(\Illuminate\Http\Request): (\Symfony\Component\HttpFoundation\Response)  $next
     */
    public function handle(Request $request, Closure $next): Response
    {
        Vite::useCspNonce();

        return $next($request)->withHeaders([
            'Content-Security-Policy' => "script-src 'nonce-".Vite::cspNonce()."'",
        ]);
    }
}
```

----------------------------------------

TITLE: Faking Specific URLs with Custom Responses - PHP
DESCRIPTION: This snippet demonstrates faking HTTP responses for specific URL patterns by passing an array to `Http::fake()`. Array keys are URL patterns (wildcards allowed), and values are fake responses created using `Http::response()`. Requests matching a pattern return the stubbed response; others execute normally. Requires the `Illuminate\Support\Facades\Http` facade.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_44

LANGUAGE: php
CODE:
```
Http::fake([
    \/\/ Stub a JSON response for GitHub endpoints...
    'github.com\/*' => Http::response(['foo' => 'bar'], 200, $headers),

    \/\/ Stub a string response for Google endpoints...
    'google.com\/*' => Http::response('Hello World', 200, $headers),
]);
```

----------------------------------------

TITLE: Ping URLs Before and After a Scheduled Task in Laravel PHP
DESCRIPTION: The `pingBefore` and `thenPing` methods allow automatically sending an HTTP GET request to a specified URL before the task begins and after it finishes. This is commonly used to notify monitoring services or external platforms like Envoyer about task execution start and end.
SOURCE: https://github.com/laravel/docs/blob/12.x/scheduling.md#_snippet_44

LANGUAGE: php
CODE:
```
Schedule::command('emails:send')
    ->daily()
    ->pingBefore($url)
    ->thenPing($url);
```

----------------------------------------

TITLE: Retrieve Generic Trial End Date
DESCRIPTION: Retrieves the end date of a user's generic trial period using the `trialEndsAt` method on the user instance. Returns a Carbon instance or null if not on a generic trial.
SOURCE: https://github.com/laravel/docs/blob/12.x/billing.md#_snippet_142

LANGUAGE: php
CODE:
```
if ($user->onTrial()) {
    $trialEndsAt = $user->trialEndsAt('main');
}
```

----------------------------------------

TITLE: Using Str::endsWith for String Suffix Checking in PHP
DESCRIPTION: The Str::endsWith method determines if the given string ends with the specified value. It can also check against multiple possible endings by passing an array of values.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_20

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$result = Str::endsWith('This is my name', 'name');

// true
```

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$result = Str::endsWith('This is my name', ['name', 'foo']);

// true

$result = Str::endsWith('This is my name', ['this', 'foo']);

// false
```

----------------------------------------

TITLE: Subscription Middleware in Laravel
DESCRIPTION: A middleware implementation that ensures routes are only accessible to subscribed users, redirecting non-subscribers to a billing page.
SOURCE: https://github.com/laravel/docs/blob/12.x/cashier-paddle.md#2025-04-21_snippet_36

LANGUAGE: php
CODE:
```
<?php

namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;
use Symfony\Component\HttpFoundation\Response;

class EnsureUserIsSubscribed
{
    /**
     * Handle an incoming request.
     *
     * @param  \Closure(\Illuminate\Http\Request): (\Symfony\Component\HttpFoundation\Response)  $next
     */
    public function handle(Request $request, Closure $next): Response
    {
        if ($request->user() && ! $request->user()->subscribed()) {
            // This user is not a paying customer...
            return redirect('/billing');
        }

        return $next($request);
    }
}
```

----------------------------------------

TITLE: Using Str::afterLast for String Extraction in PHP
DESCRIPTION: The Str::afterLast method returns everything after the last occurrence of the given value in a string. The entire string is returned if the value doesn't exist.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_5

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$slice = Str::afterLast('App\Http\Controllers\Controller', '\\');

// 'Controller'
```

----------------------------------------

TITLE: Installing UV Extension for Event Loop
DESCRIPTION: Command to install the UV extension via PECL to handle more than 1,000 concurrent connections
SOURCE: https://github.com/laravel/docs/blob/12.x/reverb.md#2025-04-21_snippet_8

LANGUAGE: shell
CODE:
```
pecl install uv
```

----------------------------------------

TITLE: Faking Response Sequence with Empty Fallback - PHP
DESCRIPTION: This snippet demonstrates faking a sequence of responses for a URL pattern and providing a default response using `whenEmpty()`. If the sequence defined by `Http::sequence()` is consumed, subsequent requests to the same URL pattern will return the response specified in `whenEmpty()`. Requires the `Illuminate\Support\Facades\Http` facade.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_50

LANGUAGE: php
CODE:
```
Http::fake([
    \/\/ Stub a series of responses for GitHub endpoints...
    'github.com\/*' => Http::sequence()
        ->push('Hello World', 200)
        ->push(['foo' => 'bar'], 200)
        ->whenEmpty(Http::response()),
]);
```

----------------------------------------

TITLE: Example: Preventing Stray Requests Effect - PHP
DESCRIPTION: This snippet provides an example demonstrating the behavior of `Http::preventStrayRequests()`. It shows that a request to a faked URL (`github.com`) succeeds, while a request to a non-faked URL (`laravel.com`) throws an exception because stray requests are prevented. Requires `Http::preventStrayRequests()` to be called beforehand. Requires the `Illuminate\Support\Facades\Http` facade.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_54

LANGUAGE: php
CODE:
```
Http::fake([
    'github.com\/*' => Http::response('ok'),
]);

\/\/ An "ok" response is returned...
Http::get('https:\/\/github.com\/laravel\/framework');

\/\/ An exception is thrown...
Http::get('https:\/\/laravel.com');
```

----------------------------------------

TITLE: Checking if String Ends With Value in Laravel PHP
DESCRIPTION: The endsWith method determines if a string ends with a given value, useful for validating file extensions or string formats.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_104

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$result = Str::of('This is my name')->endsWith('name');

// true
```

----------------------------------------

TITLE: Registering Global HTTP Request Middleware (PHP)
DESCRIPTION: Demonstrates registering a Guzzle request middleware that will apply to all outgoing HTTP client requests. This is typically done in the `boot` method of a service provider.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_34

LANGUAGE: php
CODE:
```
use Illuminate\Support\Facades\Http;

Http::globalRequestMiddleware(fn ($request) => $request->withHeader(
    'User-Agent', 'Example Application/1.0'
));
```

----------------------------------------

TITLE: Securing Markdown Conversion in PHP
DESCRIPTION: Shows how to use the 'markdown' method with security options to prevent XSS vulnerabilities when converting Markdown to HTML.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_128

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

Str::of('Inject: <script>alert("Hello XSS!");</script>')->markdown([
    'html_input' => 'strip',
    'allow_unsafe_links' => false,
]);

// <p>Inject: alert(&quot;Hello XSS!&quot;);</p>
```

----------------------------------------

TITLE: Expanding Dot Notation in Laravel Collection (PHP)
DESCRIPTION: The `undot` method converts a single-dimensional collection using dot notation keys (e.g., 'address.line_1') into a nested, multi-dimensional collection. This is useful for processing flat data structures into hierarchical ones.
SOURCE: https://github.com/laravel/docs/blob/12.x/collections.md#_snippet_179

LANGUAGE: php
CODE:
```
$person = collect([
    'name.first_name' => 'Marie',
    'name.last_name' => 'Valentine',
    'address.line_1' => '2992 Eagle Drive',
    'address.line_2' => '',
    'address.suburb' => 'Detroit',
    'address.state' => 'MI',
    'address.postcode' => '48219'
]);

$person = $person->undot();

$person->toArray();

/*
    [
        "name" => [
            "first_name" => "Marie",
            "last_name" => "Valentine",
        ],
        "address" => [
            "line_1" => "2992 Eagle Drive",
            "line_2" => "",
            "suburb" => "Detroit",
            "state" => "MI",
            "postcode" => "48219",
        ],
    ]
*/
```

----------------------------------------

TITLE: Securing Markdown with HTML Stripping in PHP
DESCRIPTION: Demonstrates how to use the inlineMarkdown method to strip HTML from Markdown input for security purposes. It uses options to control HTML handling and unsafe links.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_113

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

Str::of('Inject: <script>alert("Hello XSS!");</script>')->inlineMarkdown([
    'html_input' => 'strip',
    'allow_unsafe_links' => false,
]);

// Inject: alert(&quot;Hello XSS!&quot;);
```

----------------------------------------

TITLE: Restoring Normal ULID Generation in Laravel
DESCRIPTION: The createUlidsNormally method restores normal ULID generation after it has been mocked, typically used in test teardown phases.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_62

LANGUAGE: php
CODE:
```
Str::createUlidsNormally();
```

----------------------------------------

TITLE: Managing Quantities for Multi-Product Subscriptions in Laravel Paddle
DESCRIPTION: Method to increment quantities for specific products within a multi-product subscription by specifying the price ID as the second argument.
SOURCE: https://github.com/laravel/docs/blob/12.x/cashier-paddle.md#2025-04-21_snippet_57

LANGUAGE: php
CODE:
```
$user->subscription()->incrementQuantity(1, 'price_chat');
```

----------------------------------------

TITLE: Mocking ULIDs for Testing in Laravel
DESCRIPTION: The createUlidsUsing method allows mocking ULID generation for testing purposes, ensuring predictable identifiers during tests.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_61

LANGUAGE: php
CODE:
```
use Symfony\Component\Uid\Ulid;

Str::createUlidsUsing(function () {
    return new Ulid('01HRDBNHHCKNW2AK4Z29SN82T9');
});
```

----------------------------------------

TITLE: Using Str::finish for String Suffix Enforcement in PHP
DESCRIPTION: The Str::finish method adds a single instance of the given value to a string if it does not already end with that value, ensuring strings have specific endings.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_22

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$adjusted = Str::finish('this/string', '/');

// this/string/

$adjusted = Str::finish('this/string/', '/');

// this/string/
```

----------------------------------------

TITLE: Sharing Sites with Ngrok/Expose
DESCRIPTION: Commands for sharing local Valet sites via ngrok or Expose.
SOURCE: https://github.com/laravel/docs/blob/12.x/valet.md#2025-04-23_snippet_10

LANGUAGE: shell
CODE:
```
valet share-tool ngrok

cd ~/Sites/laravel

valet share

valet set-ngrok-token YOUR_TOKEN_HERE
```

----------------------------------------

TITLE: End Subscription Trial Immediately
DESCRIPTION: Immediately ends the trial period for a specific subscription using the `endTrial` method on the subscription instance.
SOURCE: https://github.com/laravel/docs/blob/12.x/billing.md#_snippet_137

LANGUAGE: php
CODE:
```
$user->subscription('default')->endTrial();
```

----------------------------------------

TITLE: Truncating Strings in PHP
DESCRIPTION: Demonstrates various ways to use the 'limit' method for truncating strings, including custom endings and word preservation.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_125

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$truncated = Str::of('The quick brown fox jumps over the lazy dog')->limit(20);

// The quick brown fox...

$truncated = Str::of('The quick brown fox jumps over the lazy dog')->limit(20, ' (...)');

// The quick brown fox (...)

$truncated = Str::of('The quick brown fox')->limit(12, preserveWords: true);

// The quick...
```

----------------------------------------

TITLE: Faking Global Response Sequence - PHP
DESCRIPTION: This snippet shows how to define a global fake response sequence using `Http::fakeSequence()`. This sequence will be used for any HTTP requests that do not match other specific URL patterns faked with `Http::fake([])`. It allows defining a list of responses consumed in order for general test scenarios. Requires the `Illuminate\Support\Facades\Http` facade.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_51

LANGUAGE: php
CODE:
```
Http::fakeSequence()
    ->push('Hello World', 200)
    ->whenEmpty(Http::response());
```

----------------------------------------

TITLE: Linking Sites with Valet
DESCRIPTION: Commands to link individual sites and directories with custom hostnames in Valet.
SOURCE: https://github.com/laravel/docs/blob/12.x/valet.md#2025-04-23_snippet_7

LANGUAGE: shell
CODE:
```
cd ~/Sites/laravel

valet link

valet link application

valet link api.application

valet links

valet unlink
```

----------------------------------------

TITLE: Extending Cashier Default Models
DESCRIPTION: Example of extending Cashier's default models to customize functionality.
SOURCE: https://github.com/laravel/docs/blob/12.x/cashier-paddle.md#2025-04-21_snippet_9

LANGUAGE: php
CODE:
```
use Laravel\Paddle\Subscription as CashierSubscription;

class Subscription extends CashierSubscription
{
    // ...
}
```

----------------------------------------

TITLE: Specifying Product Quantities in Multi-Product Subscriptions
DESCRIPTION: Methods to specify quantities for individual products when creating a multi-product subscription, using an associative array with price IDs as keys and quantities as values.
SOURCE: https://github.com/laravel/docs/blob/12.x/cashier-paddle.md#2025-04-21_snippet_59

LANGUAGE: php
CODE:
```
$user = User::find(1);

$checkout = $user->subscribe('default', ['price_monthly', 'price_chat' => 5]);
```

----------------------------------------

TITLE: Extending Flash Data Persistence in Laravel
DESCRIPTION: Methods to extend the lifetime of flash data beyond a single request using reflash() and keep().
SOURCE: https://github.com/laravel/docs/blob/12.x/session.md#2025-04-21_snippet_12

LANGUAGE: php
CODE:
```
$request->session()->reflash();

$request->session()->keep(['username', 'email']);
```

----------------------------------------

TITLE: Faking Laravel Sleep in Pest Tests (Pest)
DESCRIPTION: Demonstrates how to use `Sleep::fake()` within a Pest test to prevent actual execution pauses, significantly speeding up the test suite when testing code that uses the `Sleep` class.
SOURCE: https://github.com/laravel/docs/blob/12.x/helpers.md#_snippet_201

LANGUAGE: Pest
CODE:
```
it('waits until ready', function () {
    Sleep::fake();

    // ...
});
```

----------------------------------------

TITLE: Conditional Process Waiting with waitUntil
DESCRIPTION: Demonstrates using waitUntil method to stop waiting for a process based on specific output conditions.
SOURCE: https://github.com/laravel/docs/blob/12.x/processes.md#2025-04-21_snippet_15

LANGUAGE: php
CODE:
```
$process = Process::start('bash import.sh');

$process->waitUntil(function (string $type, string $output) {
    return $output === 'Ready...';
});
```

----------------------------------------

TITLE: Slack Notification Integration
DESCRIPTION: Configuration for sending notifications to Slack after task execution
SOURCE: https://github.com/laravel/docs/blob/12.x/envoy.md#2025-04-21_snippet_7

LANGUAGE: blade
CODE:
```
@finished
    @slack('webhook-url', '#bots', 'Hello, Slack.')
@endfinished
```

----------------------------------------

TITLE: Faking Response Sequence for URL Pattern - PHP
DESCRIPTION: This snippet shows how to fake a sequence of responses for a specific URL pattern using `Http::sequence()` within `Http::fake()`. Each request to the specified URL pattern will receive the next response defined in the sequence (`push()`, `pushStatus()`, etc.) until the sequence is exhausted. Requires the `Illuminate\Support\Facades\Http` facade.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_49

LANGUAGE: php
CODE:
```
Http::fake([
    \/\/ Stub a series of responses for GitHub endpoints...
    'github.com\/*' => Http::sequence()
        ->push('Hello World', 200)
        ->push(['foo' => 'bar'], 200)
        ->pushStatus(404),
]);
```

----------------------------------------

TITLE: Registering Global HTTP Response Middleware (PHP)
DESCRIPTION: Demonstrates registering a Guzzle response middleware that will apply to all incoming HTTP client responses. This is typically done in the `boot` method of a service provider.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_35

LANGUAGE: php
CODE:
```
use Illuminate\Support\Facades\Http;

Http::globalResponseMiddleware(fn ($response) => $response->withHeader(
    'X-Finished-At', now()->toDateTimeString()
));
```

----------------------------------------

TITLE: Using Str::beforeLast for String Extraction in PHP
DESCRIPTION: The Str::beforeLast method returns everything before the last occurrence of the given value in a string, useful for extracting content before specific patterns.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_9

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$slice = Str::beforeLast('This is my name', 'is');

// 'This '
```

----------------------------------------

TITLE: Configuring Group Middleware with URL Patterns in Laravel Folio
DESCRIPTION: Shows how to apply middleware to multiple pages using URL patterns with wildcards. Demonstrates configuration for admin routes with authentication and verification.
SOURCE: https://github.com/laravel/docs/blob/12.x/folio.md#2025-04-21_snippet_9

LANGUAGE: php
CODE:
```
use Laravel\Folio\Folio;

Folio::path(resource_path('views/pages'))->middleware([
    'admin/*' => [
        'auth',
        'verified',

        // ...
    ],
]);
```

----------------------------------------

TITLE: Validating ULID Strings in PHP
DESCRIPTION: Demonstrates how to use the 'isUlid' method to check if a given string is a valid ULID (Universally Unique Lexicographically Sortable Identifier).
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_119

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$result = Str::of('01gd6r360bp37zj17nxb55yv40')->isUlid();

// true

$result = Str::of('Taylor')->isUlid();

// false
```

----------------------------------------

TITLE: Request ID Middleware with Log Context
DESCRIPTION: Middleware implementation showing how to add request ID context to all subsequent log entries.
SOURCE: https://github.com/laravel/docs/blob/12.x/logging.md#2025-04-21_snippet_8

LANGUAGE: php
CODE:
```
<?php

namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Log;
use Illuminate\Support\Str;
use Symfony\Component\HttpFoundation\Response;

class AssignRequestId
{
    public function handle(Request $request, Closure $next): Response
    {
        $requestId = (string) Str::uuid();

        Log::withContext([
            'request-id' => $requestId
        ]);

        $response = $next($request);

        $response->headers->set('Request-Id', $requestId);

        return $response;
    }
}
```

----------------------------------------

TITLE: Testing Exit Codes of Laravel Console Commands (Pest and PHPUnit)
DESCRIPTION: Demonstrates how to test Artisan command exit codes using the assertExitCode method in both Pest and PHPUnit. The code shows how to verify that a command completed with a specific exit code.
SOURCE: https://github.com/laravel/docs/blob/12.x/console-tests.md#2025-04-21_snippet_0

LANGUAGE: php
CODE:
```
test('console command', function () {
    $this->artisan('inspire')->assertExitCode(0);
});
```

LANGUAGE: php
CODE:
```
/**
 * Test a console command.
 */
public function test_console_command(): void
{
    $this->artisan('inspire')->assertExitCode(0);
}
```

----------------------------------------

TITLE: Checking if String Ends With Any Values in Laravel PHP
DESCRIPTION: The endsWith method can check if a string ends with any of the values in an array.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_105

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$result = Str::of('This is my name')->endsWith(['name', 'foo']);

// true

$result = Str::of('This is my name')->endsWith(['this', 'foo']);

// false
```

----------------------------------------

TITLE: Writing Markdown Mail Template (Blade)
DESCRIPTION: This Blade snippet shows how to write a Markdown mail notification template. It uses special `<x-mail::component>` tags like `<x-mail::message>` as the main wrapper and `<x-mail::button>` to render interactive elements. Standard Markdown syntax is used for headings (`#`), paragraphs, and other text elements. Variables like `$url` are available from the data passed in the notification's `toMail` method.
SOURCE: https://github.com/laravel/docs/blob/12.x/notifications.md#_snippet_42

LANGUAGE: blade
CODE:
```
<x-mail::message>
# Invoice Paid

Your invoice has been paid!

<x-mail::button :url="$url">
View Invoice
</x-mail::button>

Thanks,<br>
{{ config('app.name') }}
</x-mail::message>
```

----------------------------------------

TITLE: Securing Markdown with Str::inlineMarkdown in PHP
DESCRIPTION: Demonstrates how to use Str::inlineMarkdown to strip or escape HTML in Markdown for security purposes. It shows options for handling HTML input and unsafe links.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_25

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

Str::inlineMarkdown('Inject: <script>alert("Hello XSS!");</script>', [
    'html_input' => 'strip',
    'allow_unsafe_links' => false,
]);

// Inject: alert(&quot;Hello XSS!&quot;);
```

----------------------------------------

TITLE: Using Laravel Lottery for Probabilistic Execution
DESCRIPTION: Executes a winner or loser callback based on specified odds using the `Lottery` facade, useful for running code only for a percentage of requests.
SOURCE: https://github.com/laravel/docs/blob/12.x/helpers.md#_snippet_192

LANGUAGE: PHP
CODE:
```
use Illuminate\Support\Lottery;

Lottery::odds(1, 20)
    ->winner(fn () => $user->won())
    ->loser(fn () => $user->lost())
    ->choose();
```

----------------------------------------

TITLE: Using Database Truncation Trait in Pest Test
DESCRIPTION: Demonstrates how to use the DatabaseTruncation trait in a Pest test file to truncate database tables between tests for improved performance.
SOURCE: https://github.com/laravel/docs/blob/12.x/dusk.md#2025-04-21_snippet_7

LANGUAGE: php
CODE:
```
<?php

use Illuminate\Foundation\Testing\DatabaseTruncation;
use Laravel\Dusk\Browser;

uses(DatabaseTruncation::class);

//
```

----------------------------------------

TITLE: Preventing Stray HTTP Requests in Tests - PHP
DESCRIPTION: This snippet configures the HTTP client to throw an exception if any real HTTP request is attempted that has not been faked. After this call, any request without a corresponding fake response will fail, ensuring all external dependencies are properly mocked during testing. Requires the `Illuminate\Support\Facades\Http` facade.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_53

LANGUAGE: php
CODE:
```
use Illuminate\Support\Facades\Http;

Http::preventStrayRequests();
```

----------------------------------------

TITLE: Combining Lottery with DB Query Monitoring
DESCRIPTION: Integrates the `Lottery` class with `DB::whenQueryingForLongerThan` to probabilistically report slow queries, demonstrating how Lottery instances can be used as callables.
SOURCE: https://github.com/laravel/docs/blob/12.x/helpers.md#_snippet_193

LANGUAGE: PHP
CODE:
```
use Carbon\CarbonInterval;
use Illuminate\Support\Facades\DB;
use Illuminate\Support\Lottery;

DB::whenQueryingForLongerThan(
    CarbonInterval::seconds(2),
    Lottery::odds(1, 100)->winner(fn () => report('Querying > 2 seconds.')),
);
```

----------------------------------------

TITLE: Extracting Substring Before Last Occurrence in Laravel PHP
DESCRIPTION: The beforeLast method returns everything before the last occurrence of the given value in a string.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_85

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$slice = Str::of('This is my name')->beforeLast('is');

// 'This '
```

----------------------------------------

TITLE: Limiting Words in a String with Str::words in Laravel
DESCRIPTION: The Str::words method limits the number of words in a string and can append a suffix to the truncated text, useful for creating excerpts.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_71

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

return Str::words('Perfectly balanced, as all things should be.', 3, ' >>>');

// Perfectly balanced, as >>>
```

----------------------------------------

TITLE: String Truncation with Str::limit in PHP
DESCRIPTION: Demonstrates various ways to use Str::limit for truncating strings, including custom endings and word preservation.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_35

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$truncated = Str::limit('The quick brown fox jumps over the lazy dog', 20);

// The quick brown fox...
```

LANGUAGE: php
CODE:
```
$truncated = Str::limit('The quick brown fox jumps over the lazy dog', 20, ' (...)');

// The quick brown fox (...)
```

LANGUAGE: php
CODE:
```
$truncated = Str::limit('The quick brown fox', 12, preserveWords: true);

// The quick...
```

----------------------------------------

TITLE: Waiting for Text Removal
DESCRIPTION: Examples of waiting until text is removed from the page.
SOURCE: https://github.com/laravel/docs/blob/12.x/dusk.md#2025-04-21_snippet_40

LANGUAGE: php
CODE:
```
// Wait a maximum of five seconds for the text to be removed...
$browser->waitUntilMissingText('Hello World');

// Wait a maximum of one second for the text to be removed...
$browser->waitUntilMissingText('Hello World', 1);
```

----------------------------------------

TITLE: Configuring Allowed Origins in PHP
DESCRIPTION: PHP configuration for defining allowed origins in the Reverb config file.
SOURCE: https://github.com/laravel/docs/blob/12.x/reverb.md#2025-04-21_snippet_2

LANGUAGE: php
CODE:
```
'apps' => [
    [
        'app_id' => 'my-app-id',
        'allowed_origins' => ['laravel.com'],
        // ...
    ]
]
```

----------------------------------------

TITLE: Defining Global Shorthand Selectors in Laravel Dusk
DESCRIPTION: The `siteElements` method in the base Page class defines global shorthand selectors that are available on every page throughout the application.
SOURCE: https://github.com/laravel/docs/blob/12.x/dusk.md#2025-04-21_snippet_75

LANGUAGE: php
CODE:
```
/**
 * Get the global element shortcuts for the site.
 *
 * @return array<string, string>
 */
public static function siteElements(): array
{
    return [
        '@element' => '#selector',
    ];
}
```

----------------------------------------

TITLE: Managing Subscription Quantities in Laravel Paddle
DESCRIPTION: Methods to increment, decrement, or set specific quantities for a subscription. This is useful for per-seat or per-unit pricing models.
SOURCE: https://github.com/laravel/docs/blob/12.x/cashier-paddle.md#2025-04-21_snippet_54

LANGUAGE: php
CODE:
```
$user = User::find(1);

$user->subscription()->incrementQuantity();

// Add five to the subscription's current quantity...
$user->subscription()->incrementQuantity(5);

$user->subscription()->decrementQuantity();

// Subtract five from the subscription's current quantity...
$user->subscription()->decrementQuantity(5);
```

----------------------------------------

TITLE: Database Migration Test Setup - Pest
DESCRIPTION: Example of using DatabaseMigrations trait in a Pest-style Dusk test for database setup.
SOURCE: https://github.com/laravel/docs/blob/12.x/dusk.md#2025-04-21_snippet_5

LANGUAGE: php
CODE:
```
<?php

use Illuminate\Foundation\Testing\DatabaseMigrations;
use Laravel\Dusk\Browser;

uses(DatabaseMigrations::class);

//
```

----------------------------------------

TITLE: Create Subscription with Trial Until Date (Payment Up Front)
DESCRIPTION: Creates a new subscription, specifying the exact end date for the trial period using the `trialUntil` method, which accepts a `DateTime` instance like a Carbon object.
SOURCE: https://github.com/laravel/docs/blob/12.x/billing.md#_snippet_135

LANGUAGE: php
CODE:
```
use Carbon\Carbon;

$user->newSubscription('default', 'price_monthly')
    ->trialUntil(Carbon::now()->addDays(10))
    ->create($paymentMethod);
```

----------------------------------------

TITLE: Applying Subscription Middleware to Laravel Route
DESCRIPTION: Shows how to apply the subscription middleware to a Laravel route to restrict access to subscribed users only.
SOURCE: https://github.com/laravel/docs/blob/12.x/cashier-paddle.md#2025-04-21_snippet_18

LANGUAGE: php
CODE:
```
use App\Http\Middleware\Subscribed;

Route::get('/dashboard', function () {
    // ...
})->middleware([Subscribed::class]);
```

----------------------------------------

TITLE: Using Str::inlineMarkdown for Markdown to HTML Conversion in PHP
DESCRIPTION: The Str::inlineMarkdown method converts GitHub-flavored Markdown into inline HTML using CommonMark. Unlike the markdown method, it does not wrap the generated HTML in a block-level element.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_24

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$html = Str::inlineMarkdown('**Laravel**');

// <strong>Laravel</strong>
```

----------------------------------------

TITLE: Redirecting to External Domains in Laravel
DESCRIPTION: Shows how to redirect to an external domain using the away method, which creates a RedirectResponse without additional URL encoding or validation.
SOURCE: https://github.com/laravel/docs/blob/12.x/responses.md#2025-04-21_snippet_17

LANGUAGE: php
CODE:
```
return redirect()->away('https://www.google.com');
```

----------------------------------------

TITLE: Configuring Request Exception Truncation (PHP)
DESCRIPTION: Demonstrates how to configure the truncation length or disable truncation entirely for logged `RequestException` messages within the application's exception handler configuration.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_31

LANGUAGE: php
CODE:
```
->withExceptions(function (Exceptions $exceptions) {
    // Truncate request exception messages to 240 characters...
    $exceptions->truncateRequestExceptionsAt(240);

    // Disable request exception message truncation...
    $exceptions->dontTruncateRequestExceptions();
})
```

----------------------------------------

TITLE: Faking Request Exceptions for URLs - PHP
DESCRIPTION: This snippet demonstrates faking a request exception (`Illuminate\Http\Client\RequestException`) for specific URLs using `Http::fake()`. By associating `Http::failedRequest()` with a URL pattern, requests matching it will throw the exception with the provided response body and status code. Requires the `Illuminate\Support\Facades\Http` facade.
SOURCE: https://github.com/laravel/docs/blob/12.x/http-client.md#_snippet_48

LANGUAGE: php
CODE:
```
Http::fake([
    'github.com\/*' => Http::failedRequest(['code' => 'not_found'], 404),
]);
```

----------------------------------------

TITLE: Converting Markdown to Inline HTML in Laravel PHP
DESCRIPTION: The inlineMarkdown method converts GitHub flavored Markdown into inline HTML using CommonMark, without wrapping it in a block-level element.
SOURCE: https://github.com/laravel/docs/blob/12.x/strings.md#2025-04-21_snippet_112

LANGUAGE: php
CODE:
```
use Illuminate\Support\Str;

$html = Str::of('**Laravel**')->inlineMarkdown();

// <strong>Laravel</strong>
```

----------------------------------------

TITLE: Testing Interactive Console Commands in Laravel (Pest and PHPUnit)
DESCRIPTION: Demonstrates testing an interactive console command by mocking user input and verifying expected output using expectsQuestion and expectsOutput methods.
SOURCE: https://github.com/laravel/docs/blob/12.x/console-tests.md#2025-04-21_snippet_4

LANGUAGE: php
CODE:
```
test('console command', function () {
    $this->artisan('question')
        ->expectsQuestion('What is your name?', 'Taylor Otwell')
        ->expectsQuestion('Which language do you prefer?', 'PHP')
        ->expectsOutput('Your name is Taylor Otwell and you prefer PHP.')
        ->doesntExpectOutput('Your name is Taylor Otwell and you prefer Ruby.')
        ->assertExitCode(0);
});
```

LANGUAGE: php
CODE:
```
/**
 * Test a console command.
 */
public function test_console_command(): void
{
    $this->artisan('question')
        ->expectsQuestion('What is your name?', 'Taylor Otwell')
        ->expectsQuestion('Which language do you prefer?', 'PHP')
        ->expectsOutput('Your name is Taylor Otwell and you prefer PHP.')
        ->doesntExpectOutput('Your name is Taylor Otwell and you prefer Ruby.')
        ->assertExitCode(0);
}
```

----------------------------------------

TITLE: Conditionally Ping URLs for Scheduled Tasks in Laravel PHP
DESCRIPTION: The `pingBeforeIf`, `thenPingIf`, `pingOnSuccessIf`, and `pingOnFailureIf` methods enable conditional URL pinging. A ping is only sent if the provided boolean condition evaluates to true, offering more granular control over notifications based on application logic.
SOURCE: https://github.com/laravel/docs/blob/12.x/scheduling.md#_snippet_46

LANGUAGE: php
CODE:
```
Schedule::command('emails:send')
    ->daily()
    ->pingBeforeIf($condition, $url)
    ->thenPingIf($condition, $url);

Schedule::command('emails:send')
    ->daily()
    ->pingOnSuccessIf($condition, $successUrl)
    ->pingOnFailureIf($condition, $failureUrl);
```

----------------------------------------

TITLE: Preventing Stray Processes in Laravel Tests
DESCRIPTION: This code demonstrates how to use the preventStrayProcesses method to ensure all invoked processes have been faked, throwing an exception for any unfaked process executions.
SOURCE: https://github.com/laravel/docs/blob/12.x/processes.md#2025-04-21_snippet_23

LANGUAGE: php
CODE:
```
use Illuminate\Support\Facades\Process;

Process::preventStrayProcesses();

Process::fake([
    'ls *' => 'Test output...',
]);

// Fake response is returned...
Process::run('ls -la');

// An exception is thrown...
Process::run('bash import.sh');
```

----------------------------------------

TITLE: Applying Layout Component with Named Slot (Blade)
DESCRIPTION: Demonstrates how to use the `layout` component and provide content for both the default `$slot` and a named slot (`$title`) using the `<x-slot:slot-name>` syntax. Content within `<x-slot:title>` overrides the default title in the layout.
SOURCE: https://github.com/laravel/docs/blob/12.x/blade.md#_snippet_106

LANGUAGE: blade
CODE:
```
<!-- resources/views/tasks.blade.php -->

<x-layout>
    <x-slot:title>
        Custom Title
    </x-slot>

    @foreach ($tasks as $task)
        <div>{{ $task }}</div>
    @endforeach
</x-layout>
```
