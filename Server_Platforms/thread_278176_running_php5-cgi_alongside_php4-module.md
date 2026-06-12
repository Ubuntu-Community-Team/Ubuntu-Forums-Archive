---
title: "running php5-cgi alongside php4-module"
date: 2006-10-15
forum: Server Platforms
---

### Post by MystaMax on 2006-10-15
Hello, I did search before posting, but was unable to find a clear solution and I'm hoping someone can point me in the right direction.
  
I'm trying to run php5-cgi on a box thats already running php4 apache module successfully. How do I control which folder gets parsed by my choice of php (4 or 5) via .htaccess. I want to avoid changing the extensions to the scripts to .php5 or changing port numbers in apache. I've read that its possible to specify a php.ini file via .htaccess. Is this true, if so how? Am i telling apache where php5-cgi is correctly via .htacces? I have installed php5-cgi and php4 as an apache module.
   
   I added a .htaccess file to a subdirectory where I want scripts to parsed w/ php5 with this text:
  
  ```

DirectoryIndex index.html index.cgi index.pl index.php index.xhtml 
AddHandler application/x-httpd-php5 .php
  
  Action php-script usr/lib/cgi-bin/php5 


```I'm sure there is something wrong w/ the code above, but I can't figure out what. I even tried the following .htaccess file which parses php5 files:

```
DirectoryIndex index.html index.cgi index.pl index.php5 index.xhtml


AddHandler php-script .php5
Action php-script usr/lib/cgi-bin/php5

```I placed a info.php file with the following code:

[php]
<?

phpinfo();

?>
[/php]in the same folder and tested it and just spits out the text of the file, and doesn't parse the script. I tried it with both .htacess files and changed the extension (to .php5) for the second .htaccess.

I'd really would like to get this work properly, and help would be appreciated, thanks.

---

### Post by MystaMax on 2006-10-17
I got some info from my web host, and he suggested replacing

[I]Action php-script usr/lib/cgi-bin/php5

[/I]**with**


[I] Action application/x-httpd-php5 /usr/lib/cgi-bin/php5

[/I]Is this pointing to the right path for php5-cgi? I tried it with 

[I]/usr/bin/php5
[/I][I]/usr/bin/php5-cgi

[/I]with no luck. Any thoughts?

---

### Post by MystaMax on 2006-10-19
Ok, I realized I was doing a lot of things wrong. someone from apache IRC recommended that I use FastCGI. I'm going to redo my install of php5. 

I found [a tutorial]("http://www.deanspot.org/%7Ealex/php5fcgi/index.html") that shows you how to run the two concurrently using FastCGI. In the tutorial, it says I can build from source or use binaries. So I went searching through aptitude and found, libapache2-mod-fcgid.** I guess there isn't a mod_fcgi package in the repositories, and I assume this is the recommended package, is that true?** For those that run this package for their cgi applications is it configured the same way as mod_fcgi? 

google search results look like more people suggest this package than I thought. what do anyone here recommend or suggest/tips. Thanks.

---

