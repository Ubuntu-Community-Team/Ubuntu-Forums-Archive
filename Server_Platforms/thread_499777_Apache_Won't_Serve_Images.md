---
title: "Apache Won't Serve Images"
date: 2007-07-13
forum: Server Platforms
---

### Post by icarius on 2007-07-13
I am relatively new to configuring a LAMP server and I am having issues with a LAMP server I set up not serving picures from a few webpages I wrote using html. I have also tried using random webpages I have downloaded, and apache won't serrve any of those pictures either. I have installed apache on my feisty box and it serves pictures just fine. I can't find anything about this issue, any help?????:guitar:

---

### Post by SomethingUniqueHere on 2007-07-13
Sounds like a permissions issue.  Make sure the images have read and execute on them by running: chmod 755 *  which will change the entire directory or replace the * with filenames if you want to do it file by file.  Also, if you have images in a subdirectory make sure the directory has the appropriate permissions as well.

Cheers

ps, you might have to run chmod as root

---

### Post by icarius on 2007-07-13
All of the files within the directory, including the images, have the correct permissions, this is one of the first things I did. Any other suggestions?

---

### Post by koenn on 2007-07-13
maybe something with MIME-types not set correctly ?

This is from a lighttpd config, but I suspect apache needs something similar
```

mimetype.assign = (
        ".html"         =>       "text/html",
        ".txt"          =>      "text/plain",
        ".jpg"          =>      "image/jpeg",
        ".png"          =>      "image/png",
)

```

---

### Post by Mr. C. on 2007-07-13
What do your apache error and access logs show for those transactions?

MrC

---

### Post by icarius on 2007-07-14
I can't find a file with the following mime types listed, however Webmin says there are a number of mime types that are active, none of them read .png or .gif or any other image extension. 

There are a number of errors that are listed in access log. Here are the error lines

"GET" /images/fntc_sunset.gif HTTP/1.1 404 307 "http://192.168.0.3/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv1.8.1.3) Gecko/20070321 Firefox/2.0.0.3 (Swiftfox)"

"GET" /icon/back.gif HTTP/1.1" 304 - "http://192.168.0.3/fntc/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.3) Gecko/20070321 Firefox/2.0.0.3 (Swiftfox)"

........and theh error log says


(13)Permission denied: file permissions deny server access: /var/www/fntc/images/fntc_sunset.gif, referer: [http://192.168.0.3/](http://192.168.0.3/)

File Does no exist: /var/www/fntc/images/fntc_sunset.jpg, referer: [http://192.168.0.3/](http://192.168.0.3/)

Does this help????

---

### Post by Mr. C. on 2007-07-14
Well, there's your problem:

> (13)Permission denied: file permissions deny server access: /var/www/fntc/images/fntc_sunset.gif

The permissions on the gif file, and perhaps the entire directory tree under fntc are inaccessible to apache (www-data).

The apache user (www-data) or group (www-data) must have read access on the files, and examine access on the directories.

Change the permissions so that apache can read them.  Ask if you need help here.

MrC

---

### Post by icarius on 2007-07-14
I just changed all of the permissions to 755, is this correct? The images dont display after chaning the permissions. Help wtih creating the correct permissionos and user groups would be really helpful, thanks.

---

### Post by Mr. C. on 2007-07-14
If it does not work, show evidence from your error logs.  This is very important in problem solving.  Nobody here wants to play the guessing game.

755 permissions not technically correct for files that are not executable, but we'll ignore that.

Let's see output from your web directory in question:
```

ls -ld fntc fntc/images
ls -l fntc/images

```
MrC

---

### Post by icarius on 2007-07-14
the images directory (/var/www/fntc/images) output is 

-rwxr-xr-x 1 root root 1895681 2007-07-11 21:06 fntc_sunset_2.gif
-rwxr-xr-x 1 root root 1879175 2007-07-11 21:06 fntc_sunset.gif

/var/www/fntc

drwxr-xr-x 2 root root 4096 2007-07-11 21:06 images

/var/www

drwxr-xr-x 4 root root 4096 2007-07-11 21:30 fntc
lrwxrwxrwx 1 root root 26 2007-07-11 21:52 index.html -> fntc/fntc_vers1

The access log from toady shows

"GET" /images/fntc_sunset.gif HTTP/1.1" 404 307 "http://1921.68.0.3/" "Mozilla/5.0 (X11 U; Linux i686; en-US; rv:1.8.1.3) Gecko/2--70321 Firefox/2.0.0.3 (Swiftfox)

"GET" /favicon.ico HTTP/1.1" 404 296 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.3) Gecko/20070321 FIrefox/2.0.0.3 (Swiftfox)"

and the error log shows

[notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured --resuming normal operations
[error] [client 192.168.0.2 File does not exist: /var/www/images, refer: [http://192.168.0.3/](http://192.168.0.3/)
[error] [client 192.168.0.2] File does not exist: /var/www/apache2-default/apache_pb2.gif, refer:[http://192.168.0.3/](http://192.168.0.3/)
[error] [client 192.168.0.2] File does not exist: /var/www/favicon.ico


I have no idea what the /var/www/facicon.ico file is, it is not a link in any of my webpages

is this the information that you need?

Thanks,

---

### Post by Mr. C. on 2007-07-14
You are getting a 404 error, which means the file does not exist.

Your error logs tells you exactly what the problem is - the directory which contains your gif files:

```
file **does not exist**: /var/www/images
```

You have a path problem in your web site setup.  You are now looking in a different place than you were earlier:

```
/var/www/images
```
vs
```
/var/www/fntc/images
```

It serves no purpose to show the permissions of a directory and its files if you then use some other directory!

Ignore the favicon.ico - that's your browser asking for a common thumbnail file for a website to show in the URI address bar of the browser.

You have to learn to read and pay attention to these messages - they are your clues to what is wrong.

MrC

---

### Post by icarius on 2007-07-14
Thanks. I am quite new to this, I had no idea the log files were there, and now I will use them religously. You are right, it was a pathing issue. Thanks agan MrC.

---

### Post by Mr. C. on 2007-07-14
Excellent; glad to hear you have your issue resolved.

MrC

---

