---
title: "Nginx returns 404 on Laravel POST API's routes"
date: 2020-12-17
forum: Server Platforms
---

### Post by nasserahmed96 on 2020-12-17
I have a running a Laravel project on Nginx, every thing works fine except when I want to send a POST  API, I use Passport for authentication, but when I try to sign up
(or doing any POST request) it returns with 404 and a message "The GET method is not supported for this route. Supported methods: POST.", although it works fine via
 ```
php artisan serve
```

Here is my request:
URL: [http://my_droplet_ip/api/v1/sign-up](http://my_droplet_ip/api/v1/sign-up)
Body: 
```

[COLOR=#d4d4d4][FONT=Droid Sans Mono][COLOR=#dcdcdc]{[/COLOR][COLOR=#d4d4d4] [/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#9cdcfe]"first_name"[/COLOR][COLOR=#dcdcdc]:[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"Nasser_Test"[/COLOR][COLOR=#dcdcdc],[/COLOR][COLOR=#d4d4d4] [/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#9cdcfe]"last_name"[/COLOR][COLOR=#dcdcdc]:[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"Ismaiel"[/COLOR][COLOR=#dcdcdc],[/COLOR][COLOR=#d4d4d4] [/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#9cdcfe]"password"[/COLOR][COLOR=#dcdcdc]:[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"password"[/COLOR][COLOR=#dcdcdc],[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#9cdcfe]"email"[/COLOR][COLOR=#dcdcdc]:[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"abdelnasser.test@gmail.com"[/COLOR][COLOR=#dcdcdc],[/COLOR][COLOR=#d4d4d4] [/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#9cdcfe]"scode"[/COLOR][COLOR=#dcdcdc]:[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"School_URL"[/COLOR][COLOR=#dcdcdc],[/COLOR]

[COLOR=#d4d4d4]    [/COLOR][COLOR=#9cdcfe]"phone"[/COLOR][COLOR=#dcdcdc]:[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"231564987"[/COLOR][COLOR=#d4d4d4] [/COLOR]

[COLOR=#dcdcdc]}[/COLOR]

[/FONT][/COLOR]

```

The response :
```

Symfony\Component\HttpKernel\Exception\MethodNotAllowedHttpException: The GET method is not supported for this route. Supported methods: POST. in file /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Routing/AbstractRouteCollection.php on line 117

#0 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Routing/AbstractRouteCollection.php(103): Illuminate\Routing\AbstractRouteCollection->methodNotAllowed()
#1 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Routing/AbstractRouteCollection.php(40): Illuminate\Routing\AbstractRouteCollection->getRouteForMethods()
#2 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Routing/RouteCollection.php(162): Illuminate\Routing\AbstractRouteCollection->handleMatchedRoute()
#3 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Routing/Router.php(639): Illuminate\Routing\RouteCollection->match()
#4 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Routing/Router.php(628): Illuminate\Routing\Router->findRoute()
#5 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Routing/Router.php(617): Illuminate\Routing\Router->dispatchToRoute()
#6 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Foundation/Http/Kernel.php(165): Illuminate\Routing\Router->dispatch()
#7 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Pipeline/Pipeline.php(128): Illuminate\Foundation\Http\Kernel->Illuminate\Foundation\Http\{closure}()
#8 /home/nginx/my_project/vendor/barryvdh/laravel-debugbar/src/Middleware/InjectDebugbar.php(60): Illuminate\Pipeline\Pipeline->Illuminate\Pipeline\{closure}()
#9 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Pipeline/Pipeline.php(167): Barryvdh\Debugbar\Middleware\InjectDebugbar->handle()
#10 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/View/Middleware/ShareErrorsFromSession.php(49): Illuminate\Pipeline\Pipeline->Illuminate\Pipeline\{closure}()
#11 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Pipeline/Pipeline.php(167): Illuminate\View\Middleware\ShareErrorsFromSession->handle()
#12 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Session/Middleware/StartSession.php(116): Illuminate\Pipeline\Pipeline->Illuminate\Pipeline\{closure}()
#13 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Session/Middleware/StartSession.php(62): Illuminate\Session\Middleware\StartSession->handleStatefulRequest()
#14 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Pipeline/Pipeline.php(167): Illuminate\Session\Middleware\StartSession->handle()
#15 /home/nginx/my_project/vendor/fideloper/proxy/src/TrustProxies.php(57): Illuminate\Pipeline\Pipeline->Illuminate\Pipeline\{closure}()
#16 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Pipeline/Pipeline.php(167): Fideloper\Proxy\TrustProxies->handle()
#17 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Foundation/Http/Middleware/TransformsRequest.php(21): Illuminate\Pipeline\Pipeline->Illuminate\Pipeline\{closure}()
#18 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Pipeline/Pipeline.php(167): Illuminate\Foundation\Http\Middleware\TransformsRequest->handle()
#19 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Foundation/Http/Middleware/TransformsRequest.php(21): Illuminate\Pipeline\Pipeline->Illuminate\Pipeline\{closure}()
#20 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Pipeline/Pipeline.php(167): Illuminate\Foundation\Http\Middleware\TransformsRequest->handle()
#21 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Foundation/Http/Middleware/ValidatePostSize.php(27): Illuminate\Pipeline\Pipeline->Illuminate\Pipeline\{closure}()
#22 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Pipeline/Pipeline.php(167): Illuminate\Foundation\Http\Middleware\ValidatePostSize->handle()
#23 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Foundation/Http/Middleware/CheckForMaintenanceMode.php(63): Illuminate\Pipeline\Pipeline->Illuminate\Pipeline\{closure}()
#24 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Pipeline/Pipeline.php(167): Illuminate\Foundation\Http\Middleware\CheckForMaintenanceMode->handle()
#25 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Pipeline/Pipeline.php(103): Illuminate\Pipeline\Pipeline->Illuminate\Pipeline\{closure}()
#26 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Foundation/Http/Kernel.php(140): Illuminate\Pipeline\Pipeline->then()
#27 /home/nginx/my_project/vendor/laravel/framework/src/Illuminate/Foundation/Http/Kernel.php(109): Illuminate\Foundation\Http\Kernel->sendRequestThroughRouter()
#28 /home/nginx/my_project/public/index.php(53): Illuminate\Foundation\Http\Kernel->handle()
#29 {main}

```

My nginx site-available configuration

```

server {
    listen 80 default_server;
    listen [::]:80;

    root /home/nginx/my_project/public;

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-XSS-Protection "1; mode=block";
    add_header X-Content-Type-Options "nosniff";
    add_header 'Access-Control-Allow-Origin' '*';
    add_header 'Add-Control-Allow-Methods' 'GET, POST, PUT, PATCH, DELETE, OPTIONS';    
    
    index index.php index.html index.htm;
    charset utf-8;
    
    server_name 134.122.100.243;

    access_log /home/nginx/logs/my_project_logs/access.log;
    error_log /home/nginx/logs/my_project_logs/error.log;
    
    
    location / {
        try_files $uri $uri/ $uri/index2.php =404;

        if ($request_method = 'OPTIONS') {
            add_header 'Access-Control-Allow-Origin' '*';
            add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS';
            add_header 'Access-Control-Allow-Headers' 'DNT, User-Agent, X-Requested-With, If-Modified-Since, Cache-Control, Content-Type, Range';
            add_header 'Access-Control-Max-Age' 1728000;
            add_header 'Content-Type' 'text/plain; charset=utf-8';
            add_header 'Content-Length' 0;
            return 204;
        }
        if ($request_method = 'POST') {
                add_header 'Access-Control-Allow-Origin' '*';
                add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS';
                add_header 'Access-Control-Allow-Headers' 'DNT, User-Agent, X-Requested-With, If-Modified-Since, Cache-Control, Content-Type, Range';
                add_header 'Access-Control-Expose-Headers' 'Content-Length, Content-Range';
            } 
        if ($request_method = 'GET') {
                add_header 'Access-Control-Allow-Origin' '*';
                add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS';
                add_header 'Access-Control-Allow-Headers' 'DNT, User-Agent, X-Requested-With, If-Modified-Since, Cache-Control, Control-Type, Range';
                add_header 'Access-Control-Expose-Headers' 'Content-Length, Content-Range';
        }

            

    }

    location /oauth/token {
        try_files $uri $uri/ = 404;
    }
    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt { access_log off; log_not_found off; }
    location ~ /\.ht { deny all; }
    error_page 404 /index.php;

    location ~ \.php$ {        
        # With php-fpm (or other unix sockets):
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }

}

```

My last line from access.log 
```

my_device_ip - - [16/Dec/2020:17:53:46 +0000] "request: "POST /api/v1/auth/signup-save" 404 195971 "-" "PostmanRuntime/7.26.5"

```
Note:
It works fine when using ```
 php artisan serve 
```

---

