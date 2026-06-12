---
title: "Apache 1.3 &amp; PHP4 (localhost works but not from another machine on my LAN)(revised)"
date: 2006-09-21
forum: Server Platforms
---

### Post by Nap_BlownApart on 2006-09-21
Hi,

I am very new to Linux, but not to computers and programming, so pardon my fau paux with regards to terminologies and departure from the straight and narrow road.

I know that Apache2 is what everyone here seems to want to use, but I have a specific need for the older versions (due to my web hosting provider).

I've installed Apache 1.3.34 (though 1.3.37 is what I actually need but can't find in the repositry), PHP4.4.4.2, mod-php4, MySQL 4.1.15 (though 4.1.21 is what I actually need but can't find in the repositry), phpMyAdmin 4.2.8.1-1 (though 2.8.0.2 is what I actually need but can't find in the repositry), and ODBC for PHP4.
Synaptic also installed a variety of packages that are required for the above applications.

I have my basic Apache working ok with localhost and from another machine on my lan (on port 80) for normal html pages, so I am now trying to get PHP working. (MySQL is next, followed by phpMyAdmin.) 

I am having problems getting PHP to work properly though. I have searched the forums and read a number of articles, all to no avail.

I have edited my httpd.conf file and have the following lines in it:
[list][*]AddModule mod_php4.c
[*]AddType application/x-httpd-php .php
[*]AddType application/x-httpd-php-source .phps
[*]LoadModule php4_module /usr/lib/apache/1.3/libphp4.so (At the bottom of the httpd.conf I've added this line even though it is already in my module.conf.)[/list]
A line "include /etc/apache/conf.d" was automatically added to the bottom of httpd.conf by one of the packages that were installed, which duplicates the AddType entries I un-commented in it's main body above.

The modules.conf file has a number of Loadmodule entries, all automatically generated.

In my public_html folder, I have a PHP script that returns the server date/time and connects to a database.

Test #1
When I browse this script through localhost, it returns the server time (which is good) and I get a call to undefined function mysql_connect() error, which is ok since I haven't configured MySQL and ODBC yet, nor have I setup the database this script is connecting to.)

Test #2
When I browse the same script from another machine, I get a window popup asking me to save the PHP file on my computer. It would seem like a mime problem, but I don't think it is because of the result I get in Test #1.

For some reason I have Apache2 installed (which must have happened while I was installing one of the other applications, since I chose NOT to install it during setup, and did not mark it in Synaptic) and running (which I've stopped with the command [b/]/etc/init.d/apache2 stop[/b]).
(Note that Test #1 went ok despite the fact that Apache2 was running.  It wasn't until I started debugging Test #2 that I noticed Apache2 running.)



QUESTIONS:
(1)Can someone please diagnose what I've done wrong or haven't yet done and/or point me to a link that explains how to integrate the older versions of  Apache etc. and works?
(2)Can anyone help me with a reference doc/link that will explain how to setup everything else related to having a LAMP server running? (Every step seems to be a major battle for no apparent reason, I'm really looking for a smooth final stretch.)


Cheers,
Nap

---

### Post by spp on 2006-09-22
Usuall when another computer prompts you to download a file instead of running it, the MIME type being sent. I am not 100% sure of a permanent solution for your system but try adding the following code to the top of the PHP file to see if it is the problem:


```
header ("Content-type: text/html");
```

If the other computer now displays rather than prompts for download, the mime type being sent by apache is the problem.

SP

---

### Post by Nap_BlownApart on 2006-09-22
Spp,
  Thnx m8, but I'm certain it's not the script.  The script works fine on my web host's server.  I was just saying the problem looked like a MIME type issue.
  The real problem is that my Apache isn't cooperating with PHP properly when requests come from external sources, but I'm not sure why.

Cheers,
Nap

---

### Post by spp on 2006-09-22
I am certain it is not the script too ;) I just mentioned it because it will bypass whatever apache is sending as the mimetype. Just a quick way to check to see if my hunch was right. 

I had a similar issue to this issue before and it was IE blowing up due to the mime type sent. Is the local browser the same as the remote (as opposed to IE vs Firefox)? What does a wget from a remote machine display as the mime type? I haven't heard of any issue like this before (localhost works, remote doesn't) when it comes to PHP scripts. If the localhost works, obviously apache can process the PHP scripts as PHP. It seems the remote host does not like what it is being fed.

SP

---

### Post by VinylPusher on 2006-11-05
I just had a similar problem.

I've finished installing Apache 1.3.37 and PHP4.4.4 after downloading from the relevant official websites. It took about 10 attempts to get this right!

I have FF2.0 and Opera installed. I encountered the "download file" problem in FF but not Opera. This was when I realised I needed to flush FF's cache.

All was then well!

*EDIT* having just gone through that most tedious process, I have /now/ found the BitRock LAMPStack distribution which automates the entire process and installs (via a GUI, I might add!): -

Apache 1.3.37
MySQL 4.1.21
PHP 4.4.4 (which would serve your purposes, as I believe the differences from 4.4.2 are mainly bugfixes and security patches).
Python 2.3.5
mod_python 2.7.11
phpMyAdmin 2.9.0-beta1 (which I have not read the changelog for, but surely cannot be far removed from 2.8.0.2?).

They also offer different stacks, some featuring apache2. You can find them here: [http://bitrock.com/download_webstacks_download.html](http://bitrock.com/download_webstacks_download.html)

---

