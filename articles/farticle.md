---

title: Laravel__CSRF Protection
type: page
description: Click on me to see more content.
topic: php

---

Cross-site request forgeries are a type of malicious exploit whereby  unauthorized commands are performed on behalf of an authenticated user.

## [Preventing CSRF Requests](https://laravel.com/docs/10.x/csrf#preventing-csrf-requests)

Laravel automatically generates a CSRF "token" for each active [user session](https://laravel.com/docs/10.x/session) managed by the application.  CHANGE AND REGENERATE

```php
use Illuminate\Http\Request;
 
Route::get('/token', function (Request $request) {
    $token = $request->session()->token();
 
    $token = csrf_token();
 
    // ...
});
```

a hidden CSRF `_token` field in the form so that the CSRF protection middleware can validate the request. For convenience, you may use the `@csrf` Blade directive to generate the hidden token input field:

```php
<form method="POST" action="/profile">
    @csrf
 
    <!-- Equivalent to... -->
    <input type="hidden" name="_token" value="{{ csrf_token() }}" />
</form>
```


