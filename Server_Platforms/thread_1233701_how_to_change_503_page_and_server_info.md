---
title: "how to change 503 page and server info"
date: 2009-08-07
forum: Server Platforms
---

### Post by 007casper on 2009-08-07
How do you change the default 503 page on the server?

I want to get rid of this message down below and put a different page.
```

Service Temporarily Unavailable

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.
--------------------------------
Apache/2.2.11 (Ubuntu)
```

also, I would like to get rid of the server info that prints on the browser

---

### Post by amac777 on 2009-08-07
One way is edit /etc/apache2/apache2.conf and setup custom ErrorDocument's for the particular error message(s) you want.

```
sudo nano /etc/apache2/apache2.conf
```

and then search for "ErrorDocument" to see some examples.

---

### Post by 007casper on 2009-08-07
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#   Alias /error/include/ "/your/include/path/"

it is not really clear to me... am I suppose to uncomment the alias line and give my own path.  I figured I would just change the default HTTP_<error>.html.var file... 

I really appreciate any suggestions you have...  

# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.

---

### Post by amac777 on 2009-08-07
I was looking around to see how I shut off the ServerTokens on my apache configuration because I did it a long time ago and couldn't remember. Anyway, I found it:

To get rid of the signature line at the bottom of the standard error messages showing Ubuntu and the version number:

```
sudo nano /etc/apache2/conf.d/security
```

and change the "ServerSignature" to "Off".

Then restart apache2 by running:

```
sudo /etc/init.d/apache2 restart
```

I'll play around with the custom error messages now to see if I can figure that out (I have not done that before myself.)

---

### Post by amac777 on 2009-08-07
Ok, custom error messages are very easy too:

```
sudo nano /etc/apache2/apache2.conf
```

Then add this line to the bottom:

```
ErrorDocument 503 /my_custom_error_message_503.html
```

Then create your my_custom_error_message_503.html in the root file of your websever (for example in /var/www)

Then restart apache2:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by 007casper on 2009-08-07
Thank you. I tried that... there is a bit of a problem.  I got mod_proxy on... because of that it doesnt pick up /var/www/.  I tried to use mod_jk but I was getting problems, so switch to mod_proxy.  I dont know how to block proxy for certain instances.

Trying your example I got... 
```

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.

Additionally, a 503 Service Temporarily Unavailable error was encountered while trying to use an ErrorDocument to handle the request.
```

---

### Post by amac777 on 2009-08-07
I've never used mod_proxy so not really sure how that effects things. 

Where do you want to put your custom error message .html file on your filesystem? I am just experiementing here, but assuming you wanted to put it in /var/www/my_errors, does it work if you change apache2.conf to:

```
Alias /my_errors/ "/var/www/my_errors/"
ErrorDocument 503 /my_errors/my_custom_error_message_503.html
```

---

### Post by 007casper on 2013-02-27
Thank you.  I found out that you can do it also...
[http://askubuntu.com/questions/53199/custom-apache-404-page]("http://askubuntu.com/questions/53199/custom-apache-404-page")

---

### Post by cariboo on 2013-02-28
Another 4 year old, without anything new added, thread closed.

---

