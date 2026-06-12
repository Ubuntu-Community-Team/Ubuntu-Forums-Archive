---
title: "Apache2 - 404 error when trying to &quot;save as&quot;"
date: 2006-06-26
forum: Server Platforms
---

### Post by b1gduk on 2006-06-26
Hi guys and gals :) 

I have recently installed the impressive Ubuntu distro and have not looked back however I have hit a hurdle and wonder if anyone could offer any help.

I have installed apache2 and have a perl script which I have placed in the /usr/lib/cgi-bin/cgiwrap/dwayne/script.pl and script.cgi

Basically the scripts allow my to upload files and place them in a directory in here called files ie /usr/lib/cgi-bin/cgiwrap/dwayne/files/uploaded.file

My problem is that the .cgi script lists the links to the files in this folder and I can see the files there when I look at the folder but when I click on one of the links or right click and "save as" from XP Explorer browser I get a 404 error and site is either unavailable or cannot be found message.

For example this is one of the URL links that does not work even though the files is physically there.

[http://10.10.10.4/usr/lib/cgi-bin/cgiwrap/dwayne/files/2006-06-bms_sleep_30sec.mpg](http://10.10.10.4/usr/lib/cgi-bin/cgiwrap/dwayne/files/2006-06-bms_sleep_30sec.mpg)

the script itself runs no problem from this URL
[http://10.10.10.4/usr/lib/cgi-bin/cgiwrap/dwayne/script.pl](http://10.10.10.4/usr/lib/cgi-bin/cgiwrap/dwayne/script.pl)

I have attempted to play with the sites-available and other config files with no joy. I have set the whole directory structure and all the files to 777 permission just in case.

I am fairly new to apache so I am guessing it is likely a configuration error.

Can anyone offer any help, I have tried looking on the web and plugging away but I feel a bit ](*,) at the moment 

Thanks in advance for any suggestions :)

---

### Post by scxtt on 2006-06-26
you'll want to use a path that's based off the "root directory"  (ServerRoot) of apache - not the path of the file on the box ...

this is generally /var/www (if you don't edit it in apache2.conf) ... so if a file is in /var/www (/var/www/file.mpg) the URL will be [http://192.168.1.100/file.mpg](http://192.168.1.100/file.mpg) ... the easiest thing to do would be create a /var/www/cgi-bin directory and put your scripts there ... some apache2.conf editing may be in order ...

---

### Post by b1gduk on 2006-06-27
Ah , thanks for that.

so I changed the /usr/lib/cgi-bin to /cgi-bin/ in the script so the path of the file includes the alias as described in the sites-available file.

The file path that I try to download is now

h t t p://10.10.10.4/cgi-bin/cgiwrap/dwayne/files/2006-06-bms_sleep_30sec.mpg

I now get a different error when I click on the file (see below).
Are there any option I have to make available to allow me to click or right click and save as ?

-=-=-=-=-=-=-=-=-=-

Internal Server Error
The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.


--------------------------------------------------------------------------------

Apache/2.0.55 (Ubuntu) Server at 10.10.10.4 Port 80

-=-=-=-=-=-=-=-=-

---

### Post by MJN on 2006-06-27
[quote=b1gduk]More information about this error may be available in the server error log.[/quote]
 
That's the key here - what's in your /var/log/apache2/access.log?
 
Mathew

---

### Post by b1gduk on 2006-06-27
:mrgreen: I moved the files to the /var/www/apache2-default/ folder and they are working fine now. Even though I gave the other folders the same options as this one ?

Thanks for the suggestions.

---

### Post by scxtt on 2006-06-27
you should be fine using /var/www to host everything ... the "apache2-default" folder just contains some generic apache2 files (maybe for use if you don't have an index.* file in /var/www, which might give you a "apache is installed on the box, but not configured" message) ...

---

### Post by b1gduk on 2006-06-28
Thanks for the advice scxtt , I have it working great now. ;)

---

