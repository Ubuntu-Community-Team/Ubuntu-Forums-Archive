---
title: "Apache server problem after 9.04 upgrade"
date: 2009-04-25
forum: Server Platforms
---

### Post by pmulgaonkar on 2009-04-25
[SOLVED] Folks: I upgraded my 8.10 machine to 9.04 today and (as far as I know) I answered "keep existing" to every request to upgrade configuration files. But now my apache web server has a strange behavior that I cannot seem to fix.

The web server's index.html file is in /var/www and it loads fine.

In index.html, is a hyperlink to ~prasanna/files
This was working fine under 8.10 until the upgrade

As far as I can tell, I have User Directories enabled, and pointing to the public_html folder. There is a folder called files in public_html. Apache2 is running as www-data. public_html and files are owned by www-data (and to debug, permissions set to 777). 

However, clicking on the link produces a "you do not have permission to access ..." message. The error.log says 
"permission denied: access to /~prasanna/files denied referrer http://localhost/"

I don't know why this broke with the upgrade. Pointers much appreciated since this has broken my web server.

--prasanna

---

### Post by minsik on 2009-04-25
I am new and know nothing! but try turning apparmor off maybe and see if that lets it run. It fixed my nagios service stopping after a short time but itself.

good luck

---

### Post by pmulgaonkar on 2009-04-25
Thanks minsik. But that isn't it.

Another data point. If I try to connect to some user that does not have a public_html file (i.e., by saying [http://localhost/~xyz](http://localhost/~xyz), then the error log message is "File does not exist". So obviously in the case where it should work, it knows that the file exists. So it cannot be that apache is looking in the wrong place.

--p

---

### Post by pmulgaonkar on 2009-04-25
[SOLVED]

My home directory itself (/home/prasanna) had changed permissions from 755 to 700. That was the issue. Found it and fixed it.

--prasanna

---

