---
title: "How to get CGI script to run instead of index.html?"
date: 2010-01-04
forum: Server Platforms
---

### Post by UbuKunubi on 2010-01-04
Hello and happy new year!

I have a ubuntu 8.04 server running apache2 and would like to allow a CGI script to be executed when visitors come to my site.

The purpose of this is to determine which browser the visitor is using and redirect them to the relevant version of the site.

How is this done?

Thanks in advance,
Ubu

---

### Post by HighCommander540 on 2010-01-04
> **UbuKunubi said:**
> Hello and happy new year!

I have a ubuntu 8.04 server running apache2 and would like to allow a CGI script to be executed when visitors come to my site.

The purpose of this is to determine which browser the visitor is using and redirect them to the relevant version of the site.

How is this done?

Thanks in advance,
Ubu

Well you could do it in PHP. You just make a PHP script and name it index.php. Then you would just read the user's headers that were sent along with the request for the page. And determine what browser it is with PHP and then use links to redirect. Its actually very simple and part of the PHP.net tutorial.

---

### Post by UbuKunubi on 2010-01-04
Thanks HighCommander540,

But i need to use CGI.
 PHP is not installed (I have PHP in my 'to learn' list, but its not a priority right now).

---

### Post by HighCommander540 on 2010-01-04
> **UbuKunubi said:**
> Thanks HighCommander540,

But i need to use CGI.
 PHP is not installed (I have PHP in my 'to learn' list, but its not a priority right now).

You don't understand what CGI means do you? All it means Common Gateway interface. CGI is not a language by itself. It is just a way to use common languages (like Perl, PHP, C++, Java) with apache as the scripting language. There is no CGI language. 

So you have to learn one those to do what you want. PHP is the easiest/fastest to learn if you want to do this.

*edit: Also, if you installed the default Apache install...It would have been LAMP and would have auto grabbed and installed PHP...

---

### Post by UbuKunubi on 2010-01-04
> **HighCommander540 said:**
> You don't understand what CGI means do you? All it means Common Gateway interface. CGI is not a language by itself. It is just a way to use common languages (like Perl, PHP, C++, Java) with apache as the scripting language. There is no CGI language. 

So you have to learn one those to do what you want. PHP is the easiest/fastest to learn if you want to do this.

*edit: Also, if you installed the default Apache install...It would have been LAMP and would have auto grabbed and installed PHP...

The CGI scripts that I use are written in perl.

---

### Post by BkkBonanza on 2010-01-04
The easiest way to redirect based on browser type is with a .htaccess file. You can match the user agent value and rewrite the url. This requires no additional scripting but does require having mod_rewrite in apache. 

Here's an example syntax from the Apache docs,
```
RewriteCond %{HTTP_USER_AGENT}  ^Mozilla/3.*
RewriteRule ^foo\.html$         foo.NS.html          [L]

RewriteCond %{HTTP_USER_AGENT}  ^Lynx/.*         [OR]
RewriteCond %{HTTP_USER_AGENT}  ^Mozilla/[12].*
RewriteRule ^foo\.html$         foo.20.html          [L]

RewriteRule ^foo\.html$         foo.32.html          [L]

```
You adjust this and put it either in your apache config file or in a .htaccess file in the doc root for your site.

More information at,
[http://httpd.apache.org/docs/2.0/misc/rewriteguide.html](http://httpd.apache.org/docs/2.0/misc/rewriteguide.html)

---

### Post by UbuKunubi on 2010-01-04
> **BkkBonaza said:**
> The easiest way to redirect based on browser type is with a .htaccess file. You can match the user agent value and rewrite the url. This requires no additional scripting but does require having mod_rewrite in apache. 

Here's an example syntax from the Apache docs,
```
RewriteCond %{HTTP_USER_AGENT}  ^Mozilla/3.*
RewriteRule ^foo\.html$         foo.NS.html          [L]

RewriteCond %{HTTP_USER_AGENT}  ^Lynx/.*         [OR]
RewriteCond %{HTTP_USER_AGENT}  ^Mozilla/[12].*
RewriteRule ^foo\.html$         foo.20.html          [L]

RewriteRule ^foo\.html$         foo.32.html          [L]

```
You adjust this and put it either in your apache config file or in a .htaccess file in the doc root for your site.

More information at,
[http://httpd.apache.org/docs/2.0/misc/rewriteguide.html](http://httpd.apache.org/docs/2.0/misc/rewriteguide.html)

EXCELLENT!

Many thanks,
Ubu

---

### Post by UbuKunubi on 2010-01-05
> **BkkBonaza said:**
> The easiest way to redirect based on browser type is with a .htaccess file. You can match the user agent value and rewrite the url. This requires no additional scripting but does require having mod_rewrite in apache. 

Here's an example syntax from the Apache docs,
```
RewriteCond %{HTTP_USER_AGENT}  ^Mozilla/3.*
RewriteRule ^foo\.html$         foo.NS.html          [L]

RewriteCond %{HTTP_USER_AGENT}  ^Lynx/.*         [OR]
RewriteCond %{HTTP_USER_AGENT}  ^Mozilla/[12].*
RewriteRule ^foo\.html$         foo.20.html          [L]

RewriteRule ^foo\.html$         foo.32.html          [L]

```
You adjust this and put it either in your apache config file or in a .htaccess file in the doc root for your site.

More information at,
[http://httpd.apache.org/docs/2.0/misc/rewriteguide.html](http://httpd.apache.org/docs/2.0/misc/rewriteguide.html)

I think i'm going crazy: I've searched and searched the entire file system but cannot find any .htaccess files!

Id prefer to be thought an idiot and ask a stupid question, than live in ignorance, but:
 can anyone please either point me in the direction of where I can find a template of a .htaccess file, or provide one here please?

I ask because I dont want to plough away blindly and get myself into problems.

Many thanks,
Ubu

---

### Post by jokke91 on 2010-01-05
I've got very little experience with web servers, but as far as I remember, the .htaccess file is a hidden file in the wwwroot or the folder above. Correct me if I'm wrong.

---

### Post by BkkBonanza on 2010-01-05
You'll have to create the file. It won't be there unless you decide you want one. Also you don't have to use .htaccess - you can put the same directives in your apache conf file inside the VirtualHost directive for your site. I find it easier to do that but on systems, when you don't have full admin access to the conf, then using the separate file is the only option. 

If you do create a the file then it only has effect for requests to the directory or sub-directories that it's in. 

Before doing this I'd suggest reading the docs and getting familiar with it.

I can help with writing one if you tell me what you want to match on and redirect to.

---

### Post by UbuKunubi on 2010-01-05
> **BkkBonaza said:**
> You'll have to create the file. It won't be there unless you decide you want one. Also you don't have to use .htaccess - you can put the same directives in your apache conf file inside the VirtualHost directive for your site. I find it easier to do that but on systems, when you don't have full admin access to the conf, then using the separate file is the only option. 

If you do create a the file then it only has effect for requests to the directory or sub-directories that it's in. 

Before doing this I'd suggest reading the docs and getting familiar with it.

I can help with writing one if you tell me what you want to match on and redirect to.

Thanks for the input - its appreciated.
Im still digesting the docs you refered to in your post, but they seem to not provide an example of a 'basic' .htaccess file, whence my quesion.

I'll keep at it, and hope to post back with my solution so i can mark this post as solved soon.

Cheers,
Ubu

---

