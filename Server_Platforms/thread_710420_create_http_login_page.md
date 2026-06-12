---
title: "create http login page"
date: 2008-02-28
forum: Server Platforms
---

### Post by reckless2k2 on 2008-02-28
I'm trying to figure out how to create a login for access to a HTML page of mine for security. I'm not sure how to go about this. If anyone can point me in the right direction or give me answers on how to accomplish this it would be appreciated. 

i'm looking to have a url that would show a login page. once the proper user and password is entered then it would redirect to another page or the page behind the login screen. or more simply, url would show a login box that would need to be entered before the page would show. 


thanks for any help.

---

### Post by farruinn on 2008-02-28
Sounds like you want to protect the directory with .htaccess and .htpasswd. Try [http://www.javascriptkit.com/howto/htaccess.shtml](http://www.javascriptkit.com/howto/htaccess.shtml) for a decent how-to or search for .htaccess.

---

### Post by astrotech226 on 2008-02-28
This isn't something that can be strictly in HTML.  You'll need PHP or something else (JSP, etc...) for the portion that does the authentication.  Here's the first link I came across that had examples:

[http://www.mtdev.com/2002/07/creating-a-secure-php-login-script]("http://www.mtdev.com/2002/07/creating-a-secure-php-login-script")

---

### Post by astrotech226 on 2008-02-28
> **farruinn said:**
> Sounds like you want to protect the directory with .htaccess and .htpasswd. Try [http://www.javascriptkit.com/howto/htaccess.shtml](http://www.javascriptkit.com/howto/htaccess.shtml) for a decent how-to or search for .htaccess.

Duh...  Look at me trying to make it really complicated for them and you have to go and make it easy and stuff!!  :)

---

### Post by Joeb454 on 2008-02-28
As suggested above, this can't be done in plain HTML, though it could be done in PHP/JavaScript etc. I guess :)

---

### Post by farruinn on 2008-02-28
> **Joeb454 said:**
> As suggested above, this can't be done in plain HTML, though it could be done in PHP/JavaScript etc. I guess :)

It *could* be done in javascript, however client-side authentication isn't nearly as secure as server-side.

OP: If you wanted a "Login screen" like you have for webmail you'd have to do it in PHP/perl/etc but .htaccess should be pretty simple. Just be sure your .htpasswd isn't in a directory accessible to the public.

---

### Post by Dr Small on 2008-02-28
[php]
<?php

$username = "admin";
$password = "safepass56";

$postusername = $_POST['username'];
$postpassword = $_POST['password'];


if($postusername == $username && $postpassword == $password)
   {
    echo 'This is what would display after having logged in...';
   }

else
    {
echo 'ERROR. Incorrect Username or Password.';
    }

?>[/php]

Now, have your login page point to:
```
<form action="login.php" method="post">
```

And have a login box:
```
Username: <input type="text" name="username">
Password: <input type="password" name="password">
```

If the username and password match, you will have your login page :)

Dr Small

---

### Post by whazooo on 2008-03-02
Create a directory

mkdir /var/www/secret
place your index.html file there IE,
/var/www/secret/index.html

open a terminal and 
touch /var/www/secret/.htaccess

Create a directory for your pass file out of the way
mkdir /var/private

nano /var/www/secret/.htaccess

add this:

AuthUserFile /var/private/.htpasswd
AuthName "Put what ever you want here"
AuthType Basic
Require valid-user


now create and add users to the .htpassword file:

cd /var/private

htpasswd -c .htpasswd username
you will be prompted for passwords

to add more users:
htpasswd .htpasswd newusername

now when users go to 
[http://localhost/secret](http://localhost/secret)

they will be presented with a login box
after they authenticate they will see the index.html page..

If you would rather send them to another page in a diffrent directory
you could use the rewrite module to accomplish this.

---

### Post by koenn on 2008-03-02
> **Dr Small said:**
> [php]
<?php

$username = "admin";
$password = "safepass56";

$postusername = $_POST['username'];
$postpassword = $_POST['password'];


if($postusername == $username && $postpassword == $password)
   {
    echo 'This is what would display after having logged in...';
   }

else
    {
echo 'ERROR. Incorrect Username or Password.';
    }

?>[/php]

Now, have your login page point to:
```
<form action="login.php" method="post">
```

And have a login box:
```
Username: <input type="text" name="username">
Password: <input type="password" name="password">
```

If the username and password match, you will have your login page :)

Dr Small
is this safe ? like, would it be possible to just wget login.php and read the username/password ? 
And how would this work with multiple users ?

---

### Post by astrotech226 on 2008-03-02
> **koenn said:**
> is this safe ? like, would it be possible to just wget login.php and read the username/password ? 
And how would this work with multiple users ?

Nothing inside the <? ?> tags will ever be visible to the end user if Apache is set up to parse php files.

---

### Post by koenn on 2008-03-02
> **astrotech226 said:**
> Nothing inside the <? ?> tags will ever be visible to the end user if Apache is set up to parse php files.
hm, yes, of course, because wget uses http, so the request will be handled through apache in any case. 
silly me.

---

### Post by BL00dFox on 2008-03-02
It seems like htaccess is the best solution... Google it

---

### Post by reckless2k2 on 2008-03-05
i appreciate the responses. i'm not sure why i didn't think of htaccess and htpasswd since i have used them before. i was thinking i had to make a crazy php login script similar to the one suggestion from koenn. i found the information provided by farruinn and whazooo to be very helpful. i had to tweak a setting in the config so it would read the htaccess file first though. i dropped in the follwing:

```
AllowOverride AuthConfig Indexes
```

i'm not sure if i should just be using the following though:

```

AllowOverride All
```

thanks for all the help guys.

---

### Post by sosimple on 2008-07-20
> **whazooo said:**
> Create a directory

mkdir /var/www/secret
place your index.html file there IE,
/var/www/secret/index.html

open a terminal and 
touch /var/www/secret/.htaccess

Create a directory for your pass file out of the way
mkdir /var/private

nano /var/www/secret/.htaccess

add this:

AuthUserFile /var/private/.htpasswd
AuthName "Put what ever you want here"
AuthType Basic
Require valid-user


now create and add users to the .htpassword file:

cd /var/private

htpasswd -c .htpasswd username
you will be prompted for passwords

to add more users:
htpasswd .htpasswd newusername

now when users go to 
[http://localhost/secret](http://localhost/secret)

they will be presented with a login box
after they authenticate they will see the index.html page..

If you would rather send them to another page in a diffrent directory
you could use the rewrite module to accomplish this.



AWESOME ANSWER - This works great ...

My understanding of this use of .htaccess/.htpasswd (please correct me if I'm wrong) is that once someone logs in, they can access all flles within the folder [example: '/www/secret/'] and subfolders that are not otherwise protected.

1) What is the mechanism used to cache the login/password ... Is Apache writing cookies, or storing the login info ?

2) Once logged in, if you return to /secret/ you are still authenticated and are not asked for login/password again. 

In the case of multiple accounts or for security reasons in case other users have access to the PC, what would need to be done to Log the person off (discard the cached info) ?

3) What I am looking for now is a way to put the login/password prompt on a webpage rather than the little popup login Windows Dialog box.

Kevin

---

