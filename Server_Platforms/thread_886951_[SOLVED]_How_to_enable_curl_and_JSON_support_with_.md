---
title: "[SOLVED] How to enable curl and JSON support with PHP"
date: 2008-08-11
forum: Server Platforms
---

### Post by CrusaderAD on 2008-08-11
How do you enable curl and JSON support with PHP on a Hardy Ubuntu Server?

---

### Post by UzLA on 2008-08-11
> **raptormanad said:**
> How do you enable curl and JSON support with PHP on a Hardy Ubuntu Server?

There are several options:
- recompile PHP from the source with somehting similar to --with-curl=/usr/local/curl (depending on your system pathes). same applies to JSON or plug them as shared modules.

More on that:
[http://www.google.co.uk/search?hl=en&q=enable+curl+in+php&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&q=enable+curl+in+php&btnG=Search&meta=)

Or tutorial on "how to find out if PHP is compiled with CURL extension installed enabled"

[http://www.wallpaperama.com/forums/how-to-find-out-if-php-is-compiled-with-curl-extension-installed-enabled-t1576.html](http://www.wallpaperama.com/forums/how-to-find-out-if-php-is-compiled-with-curl-extension-installed-enabled-t1576.html)

and then just uncomment ";extension=php_curl.dll" adn restart apache.

---

### Post by cariboo on 2008-08-11
The standard php5 available from Ubuntu is already set up to use curl, just install it from the repositories. It also seems that it is ready to use JSON, there are packages also available from the repostiories.

A little searching in synaptic answered the questions.

Jim

---

### Post by CrusaderAD on 2008-08-12
Do I only need to install them? Is there any type of configuration?

---

### Post by CrusaderAD on 2008-08-13
I added the extensions to the php.ini file and restarted apache. I ran a php script to test curl, and it works. Is there anyway to test things like ffmpeg and json?

---

### Post by CrusaderAD on 2008-08-13
I think I got JSON and CURL under control. To see if CURL is working, open a text editor and make the following script:

<?php 
echo '<pre>'; 
var_dump(curl_version()); 
echo '</pre>'; 
?>

save it was testcurl.php and then run it from the browser, if all is well, there should be no errors. These's still one thing I can't get working... ffmpeg. I can't figure this guy out... I installed ffmpeg and php-ffmpeg... it won't work... help!

---

### Post by CrusaderAD on 2008-09-08
Here's a little tutorial on this subject. To install JSON and CURL, open synaptic with admin controls...

sudo synaptic

search for json and curl, install the packages. Then open up your php.ini file. *Only do this if you know what you're doing, make a backup*

sudo vi /etc/php5/apache2/php.ini

Add the following lines:

extension=php_curl.dll
extension=ffmpeg.so
extension=json.so

Save and restart Apache:

sudo /etc/init.d/apache2 restart

If all is well, these functions should now be operational.

---

### Post by Cliving on 2010-03-02
Hi

I am running civiCRM on my Ubuntu/joomla webserver.
My problem is "... dashboard is in a continual "Loading" state ..."

 See: [http://forum.civicrm.org/index.php/topic,11355.0.html](http://forum.civicrm.org/index.php/topic,11355.0.html)
The solution as per this forum, is to enable JSON support.

To do this I have:

1) I have installed php5-jsonsudo using aptitude. :~$ sudo aptitude install php5-jsonsudo

2) have added extension=json.so to /etc/php5/apache2/php.ini

;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;
;
; If you wish to have an extension loaded automatically, use the following
; syntax:
;
;   extension=modulename.extension
;
; For example, on Windows:
;
;   extension=msql.dll
;
; ... or under UNIX:
;
;   extension=msql.so
;
; Note that it should be the name of the module only; no directory information
; needs to go here.  Specify the location of the extension with the
; extension_dir directive above.

And 3)  restarted apache. sudo /etc/init.d/apache2 restart

However this problem persists.

Any suggestions will be greatly appreciated.

Dick

---

### Post by CrusaderAD on 2010-03-05
I've never used Joomla before, so I don't think I can help you out there. You might get better responses if you post your issue into a new thread relating to Joomla.

---

### Post by xxilus on 2010-05-22
I did not have to modify php.ini, but I had to run this command
```
sudo apt-get install curl libcurl3 libcurl3-dev php5-curl
```

---

### Post by hdesousa on 2010-06-17
That worked for me. :KS

Thanks!

---

### Post by hoangnguyen on 2012-10-04
Thank you alot, i have just setup finished for my VPS.
Right now my VPS can run joomla 2.5 code. It is here *snip*

---

### Post by Toz on 2012-10-04
Old thread. Closed.

---

