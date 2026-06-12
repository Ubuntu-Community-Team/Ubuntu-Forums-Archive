---
title: "mod_rewrite breaks PHP post"
date: 2010-08-29
forum: Server Platforms
---

### Post by locosway on 2010-08-29
My .htaccess file looks like this:


```
Options -indexes

RewriteEngine on
RewriteBase /

# Redirect direct client request for old URL with .php extension
# to new extensionless URL if the .php file exists
RewriteCond %{THE_REQUEST} ^[A-Z]+\ /([^/\ ]+/)*[^.\ ]+\.php\ HTTP/
RewriteCond %{REQUEST_FILENAME} -f
RewriteRule ^(([^/]+/)*[^.]+)\.php$ http://dev.mysite.com/$1 [R=301,L]           

# Redirect any request for a URL with a trailing slash to extensionless URL
# without a trailing slash unless it is a request for an existing directory
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.+)/$ http://dev.mysite.com/$1 [R=301,L]

# Internally rewrite extensionless URL request
# to .php file if the .php file exists
RewriteCond %{REQUEST_FILENAME}.php -f
RewriteRule ^(([^/]+/)*[^./]+)$ /$1.php [L]
```

The rules seem to function perfectly. However, when I try to login to my website, I can't. There's no errors in the logs. I just get a login error. When I disable the rules everything works fine.

The login posts to login.php. Here is the form for the login:

```
<div id="login">
                        <form action="https://<?php echo $siteUrl ?>/login.php" method="post">
                                <fieldset>
                                        <legend>Login</legend>
                                        <p><label for="email">Email</label> <input type="email" id="email" name="email" placeholder="Email Address"  autofocus /></p>
                                        <p><label for="password">Password</label> <input type="password" id="password" name="password" placeholder="Password" /><br /></p>
                                        <label>&nbsp; </label><p><input class="submit"  type="submit" value="Login" />
                                        &nbsp;&nbsp;&nbsp;
                                        <a class="forgot" href="https://<?php echo $siteUrl ?>/forgot.php">Forgot Password?</a></p>
                                </fieldset>
                        </form>
                </div>
```

And here is the first part of login.php


```
<?php
        include "../includes/config.php";

        // if they're submitting information, we process it
        if(isset($_POST['email']) && isset($_POST['password'])) {

```

Any help or tips would be appreciated, thanks.

---

### Post by Ryan Dwyer on 2010-08-29
Your first RewriteRule issues a redirect header. Redirects use GET, so the POST data is not sent.

Change your form action so it logs in to the new URL. That way it won't have to redirect.

---

### Post by locosway on 2010-08-29
I ran across this thread, which is what's happening to me:

[http://www.bigresource.com/Tracker/Track-php-JtI8WA3v/](http://www.bigresource.com/Tracker/Track-php-JtI8WA3v/)

However there's no solution offered other than to have your forms use a url that's not being rewritten. Well, this defeats the whole purposes of using mod_rewrite.

Here's my PHP version, so I doubt it's because the version is too old.

PHP Version 5.2.14

---

### Post by locosway on 2010-08-29
Thanks Ryan. That does seem to correct the problem. However I was hoping to have a solution without changing a lot of code.

I guess that's how things work though.  :)

---

