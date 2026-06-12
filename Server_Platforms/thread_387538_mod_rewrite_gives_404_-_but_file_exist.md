---
title: "mod_rewrite gives 404 - but file exist"
date: 2007-03-18
forum: Server Platforms
---

### Post by tomjen on 2007-03-18
Hej,
I am playing around with PHPCake (a MVC framework for php) that uses mod_rewrite to rewrite URLs - mod_rewrite works but if I request [http://127.0.0.1/~user/index.php](http://127.0.0.1/~user/index.php) I get a 404 error - claiming that [http://127.0.0.1/~user/webroot/index.php](http://127.0.0.1/~user/webroot/index.php) (the place it was supposed to redirect to) doesnt exist. It does and if i type it in the address bar Apache2 loads it.

Does anyone know what I can do about this?

P.S I use Edgy

---

### Post by scoon on 2007-03-18
Hey there, 

Start by turning up the verbosity of logging that apache can do.  Then check the log files.  That should help to point you in your problem.  Remember, anytime you make a change to the apache conf files, you need to restart apache.

-scoon

---

### Post by tomjen on 2007-03-18
thanks setting the log level to debug turned up something I think might be interesting, but Ido not know why:

 [Sun Mar 18 18:42:38 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Sun Mar 18 18:42:55 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/mappers/mod_rewrite.c(1788): [clie
nt 127.0.0.1] mod_rewrite's internal redirect status: 0/10.
[Sun Mar 18 18:42:55 2007] [error] [client 127.0.0.1] File does not exist: /var/www/home

---

### Post by scoon on 2007-03-18
Hey there, 

Can you share what your rewrite rule is?

-scoon

---

### Post by tomjen on 2007-03-18
This is the contents of .htaccess - but it comes directly from phpcake and works one my online host - so I dont think the problem is here

<IfModule mod_rewrite.c>
        RewriteEngine on
        RewriteRule     ^$      webroot/
        RewriteRule     (.*) webroot/$1
</IfModule>

---

### Post by scoon on 2007-03-18
Is your online host serving content out of your home directory, like it appears you are trying to do here?  Also, check the permissions of the direcotry that you are trying to serve out of.  For kicks, set them to 0777 to test that the permissions are ok.

-scoon

---

### Post by tomjen on 2007-03-19
No it is not  - I am trying to setup a development enviroment on my computer (1s latency over ssh sucks when you are trying to edit files, but so does copying back and forth everytime you chance something)

I have pretty liberal right settings already but I did a recursive 777 - still doesnt work with mod_rewrite (still the silly 404) but works if I type in the adress it claims it cannot find.

---

### Post by scoon on 2007-03-19
Hey there, 

I still think there is a problem with your rewrite rule, all though I am not totally sure what.  It appears that the rule is capturing the url correctly but it is putting what was captured and appending that to what your DocumentRoot is in apache.  You may try changing the rule so that it is working on the complete url and not just the last part.  Read this for some other suggestions: [http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html]("http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html")

-scoon

---

### Post by tomjen on 2007-03-19
No webroot is a directory created by phpcake - it not the **real** webroot

---

### Post by tomjen on 2007-03-19
It keeps trying to read the file /var/www/home - so i created that directory. Then it attempts to load /var/www/home/username. Apparently it thinks it is supposed to load /var/www/home/username/ as opposed to /home/username/public_html/appname/webroot.

I case it was because of webroot being mistaken for the real webroot. I rename that dir to qqq. It did not help

---

### Post by scoon on 2007-03-19
Hey there, 

Did you read over that link I sent?  I have used mod_rewrite in the past and that link was super helpful.

-scoon

---

### Post by tomjen on 2007-03-19
Solved - I needed to add 
RewriteBase	/~username/appname
To the .htaccess file - so that mod_rewrite know how to get the new file

---

### Post by scoon on 2007-03-19
Excellent........

---

