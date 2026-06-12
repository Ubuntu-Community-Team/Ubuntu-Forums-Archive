---
title: "[SOLVED] Apache is not displaying images nor css."
date: 2008-02-18
forum: Server Platforms
---

### Post by Joh739 on 2008-02-18
Hello,

First I want to say that I'm new to Ubuntu and I am also using openSuSE for a few months. I've been using Ubuntu mainly on a USB pen drive, I installed Ubuntu on it with the help of this guide: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/"). 
Here and there I run into minor problems that where easily fixable, but when I tried installing apache I run into a major one, the images and the ccs styles aren't displaying... I fought this was caused by some corrupted files so I formated the 4GB USB drive and installed Ubuntu on it again, then I installed apache with the following command: ```
apt-get install mysql-server mysql-client libmysqlclient15-dev apache2 apache2-doc php5 php5-common php5-curl php5-dev php5-gd
``` And still apache refuses the display the images nor any css styles, however things like phpMyAdmin and Drupal are working but without any images and css stuff :(. However I also installed Webmin on the pen drive and the web server where in runs on works flawlessly.

I got here some entry's form my /var/log/apache2/access.log:
```
127.0.0.1 - - [18/Feb/2008:18:38:09 +0000] "GET / HTTP/1.0" 200 743 "-" "Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 (internal dummy connection)"
127.0.0.1 - - [18/Feb/2008:18:39:53 +0000] "GET / HTTP/1.1" 200 743 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:18:39:55 +0000] "GET /apache2-default/ HTTP/1.1" 304 - "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:18:39:55 +0000] "GET /apache2-default/apache_pb22.png HTTP/1.1" 206 1502 "http://localhost/apache2-default/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:18:39:57 +0000] "GET /apache2-default/ HTTP/1.1" 304 - "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:18:39:57 +0000] "GET /apache2-default/apache_pb22.png HTTP/1.1" 206 1502 "http://localhost/apache2-default/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
```

I'm at a loss of this glitch or whatever this is, so could somebody help me out here please?

---

### Post by faulkes on 2008-02-18
Check that your css and image files are world readable.  That is the likely culprit.

```

ls -l /path/to/apache/image.png

```

If you don't see something like -rw-r--r-- then that is what the problem is.

Although I'm not very familiar with webmin, I do recall it runs under a different set of privileges
which would likely explain why it could see the files and apache could not.

Faulkes

---

### Post by Joh739 on 2008-02-18
Oke thanks for the replay, I looked at the permissions with ls -l and it says: ```
-rw-r--r-- 1 root root 1502 2005-12-14 16:25 /var/www/apache2-default/apache_pb22.png
``` This doesn't explain much... any suggestions?

---

### Post by faulkes on 2008-02-18
Well, from the log you posted, I see a 304 status code being generated.

```

304 - Not Modified
The 304 status code is sent in response to a request (for a document) that asked for the
document only if it was newer than the one the client already had. Normally, when a 
document is cached, the date it was cached is stored. The next time the document is viewed, 
the client asks the server if the document has changed. If not, the client just reloads 
the document from the cache.

```

So, first I would clear your firefox cache, second I would create an additional
image and link it in to the page.  Then see what happens.

Faulkes

---

### Post by Joh739 on 2008-02-18
I cleared the cache on both the notebook where the pen drive is loaded on and my desktop where I post messages from. I created a link on top of a images to the same page and I still get the same result. Also when I go to directly to an image I see the path to it(the same thing I type in the URL bar) instead of the image.

---

### Post by faulkes on 2008-02-18
> **Joh739 said:**
> I cleared the cache on both the notebook where the pen drive is loaded on and my desktop where I post messages from. I created a link on top of a images to the same page and I still get the same result. Also when I go to directly to an image I see the path to it(the same thing I type in the URL bar) instead of the image.

Another thing being that I don't see the css file being called at all in the log
snippet you posted.

I would check the html source for any possible errors.

Faulkes

---

### Post by Joh739 on 2008-02-18
The css problem was before I reinstalled Ubuntu on the pen drive, Drupal didn't display colors and it looked more like some text with simple things like <h1> and so on...

I downloaded a template with css and images on it form a website.
And I put it in the /var/www/ folder and when I go to it, it's blank(even the html)!

This is my access log now:
```
192.168.2.8 - - [18/Feb/2008:20:30:33 +0000] "GET /icons/blank.gif HTTP/1.1" 304 - "http://192.168.2.6/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.1.12) Gecko/20080203 SUSE/2.0.0.12-0.1 Firefox/2.0.0.12"
192.168.2.8 - - [18/Feb/2008:20:30:33 +0000] "GET /icons/text.gif HTTP/1.1" 200 229 "http://192.168.2.6/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.1.12) Gecko/20080203 SUSE/2.0.0.12-0.1 Firefox/2.0.0.12"
192.168.2.8 - - [18/Feb/2008:20:30:33 +0000] "GET /icons/folder.gif HTTP/1.1" 304 - "http://192.168.2.6/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.1.12) Gecko/20080203 SUSE/2.0.0.12-0.1 Firefox/2.0.0.12"
192.168.2.8 - - [18/Feb/2008:20:30:33 +0000] "GET /icons/unknown.gif HTTP/1.1" 200 245 "http://192.168.2.6/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.1.12) Gecko/20080203 SUSE/2.0.0.12-0.1 Firefox/2.0.0.12"
192.168.2.8 - - [18/Feb/2008:20:30:37 +0000] "GET /index2.html HTTP/1.1" 200 7361 "http://192.168.2.6/" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.1.12) Gecko/20080203 SUSE/2.0.0.12-0.1 Firefox/2.0.0.12"
127.0.0.1 - - [18/Feb/2008:20:32:01 +0000] "GET / HTTP/1.1" 200 1474 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:20:32:01 +0000] "GET /icons/blank.gif HTTP/1.1" 200 148 "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:20:32:01 +0000] "GET /icons/folder.gif HTTP/1.1" 200 225 "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:20:32:01 +0000] "GET /icons/unknown.gif HTTP/1.1" 200 245 "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:20:32:01 +0000] "GET /icons/text.gif HTTP/1.1" 200 229 "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:20:32:03 +0000] "GET /index2.html HTTP/1.1" 200 7361 "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:20:32:04 +0000] "GET /index2.html HTTP/1.1" 206 7361 "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:20:32:04 +0000] "GET /index2.html HTTP/1.1" 206 7361 "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
127.0.0.1 - - [18/Feb/2008:20:32:08 +0000] "GET /index2.html HTTP/1.1" 206 7361 "http://localhost/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6"
```

And this is the template I used: [http://www.oswd.org/design/preview/id/3693]("http://www.oswd.org/design/preview/id/3693")

It's just getting stranger with the moment....

---

### Post by faulkes on 2008-02-18
IIRC doesn't drupal have a specific method for adding themes / styles via it's admin panel functions?

Faulkes

---

### Post by Joh739 on 2008-02-18
Drupal does have a style manager but that isn't the problem here, apache not displaying images and that sort is. I have Drupal installed on my openSUSE desktop and the installation is graphical and on the pen drive it was not...

---

### Post by Joh739 on 2008-02-18
I found a work around for my problem, simply uninstall every apache packages and install XAMPP for Linux and It worked like a charm :D. However of somebody got the answer to my previous problem I would like to know.

Thanks for the help.

---

### Post by geodog on 2008-03-12
I have the exact same problem, and I am hoping not to have to reinstall Apache etc to get it fixed.

I installed LAMP via Tasksel, and the first application I tried to install, lilina, I ran into this problem where the stylesheets were not displayed.

Driving me crazy.

---

### Post by geodog on 2008-03-12
I actually found a solution, on another forum [http://www.usenet-forums.com/apache-web-server/41101-apache-2-2-0-not-serving-js-css-image-files.html](http://www.usenet-forums.com/apache-web-server/41101-apache-2-2-0-not-serving-js-css-image-files.html)

The solution:

[INDENT]To fix this problem, simply use the EnableSendfile directive to disable sendfile for all or part of your server.... After setting "EnableSendfile off" in httpd.conf and restarting httpd
it works as it should.[/INDENT]

In my case, I made the change to apache2.conf, and it worked.

---

