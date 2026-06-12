---
title: "Strange Apache Behaviour - need advice"
date: 2007-07-22
forum: Server Platforms
---

### Post by heitjer on 2007-07-22
I installed the entire LAMP server today from scratch by following everything to the dot - see links at bottom.

I then placed my web sites in the /var/www folder. These are different websites within different subfolders with one index.htm file in the top folder (/var/www). Some of these subfolders are also directly linked from an external hosted website. 

From home when I go to the external website I can access all sites & pages in the subfolders. It seems that I can access all of them because I am on the local network. 

When I try from work _I can only see the top level index.htm page_. It displays it very quickly but when I click on a link which should take me into one of the subfolder it stalls on me and after a while it tells me that it can not display these pages. 

My /var/www was mounted on a second harddrive to separate the files from the rest of the server.

a) I don't think this is a router issue because I can assess the top level index page 
b) I tried access with and without router firewall
c) I tried the files 'mounted' and also 'unmounted' (/var/www direct on the main harddrive) - no change
d) access rights for the top and all subfolders in /var/www folder is 0755 

With all the above I strongly assume it has something to do with Apache. Somewhere there is probably a Deny or Allow All somewhere wrong. Please advise!


System - PPC G3 with Ubuntu 6.10
Standard install according to:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10")
[http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10_p4]("http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10_p4")

[COLOR="Red"]READ TO THE LAST POST FROM ME - THIS IS NOT AN APACHE ISSUE - IT HAS TO DO WITH MY CORPORATE IT FIREWALL OR SOMETHING. [/COLOR]

---

### Post by Mr. C. on 2007-07-23
Your logs are your friends.  Examine and post the access and error log entries relevant to your remote requests.

MrC

---

### Post by conjur3r on 2007-07-23
> **heitjer said:**
> 
I then placed my web sites in the /var/www folder. These are different websites within different subfolders with one index.htm file in the top folder (/var/www). Some of these subfolders are also directly linked from an external hosted website. 

From home when I go to the external website I can access all sites & pages in the subfolders. It seems that I can access all of them because I am on the local network. 

When I try from work _I can only see the top level index.htm page_. It displays it very quickly but when I click on a link which should take me into one of the subfolder it stalls on me and after a while it tells me that it can not display these pages. 


I'm guessing you used some sort of internal ip address in your linking?  What is an example link that you've used that doesn't work from your work.

---

### Post by heitjer on 2007-07-23
Thanks for your fast responses.

But - I still can't get to my web pages. I found out the following:

A) created a subfolder on the Apache Server and placed a simple index.html in there. 
B) created a link to this from my internet site
=> everything worked - opens the index.html from anywhere in cyberspace

C) placed the original (photo website) index.html in the same folder
D) called it from the outside 
=> nothing

ACCESS LOG:
xxx.xxx.xxx.xxx - - [23/Jul/2007:21:35:39 -0500] "GET /subfolder/index.html HTTP/1.1" 200 370 "http://xxx.external_website.com" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; H010818; .NET CLR 1.1.4322)"
xxx.xxx.xxx.xxx - - [23/Jul/2007:21:35:39 -0500] "GET /favicon.ico HTTP/1.1" 404 1069 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; H010818; .NET CLR 1.1.4322)"

NOTE the xxx.xxx.xxx.xxx is my WAN IP that I link from the external website with the following command to my home server: href="http://xxx.xxx.xxx.xxx/subfolder/index.html"

ERROR LOG keeps reporting this line:
[Mon Jul 23 21:35:39 2007] [error] [client xxx.xxx.xxx.xxx] File does not exist: /var/www/favicon.ico

There is no mentioning in the photo webpage for this file. I have no clue where this file is called from. 

E) found the file somewhere on my harddrive and placed it in the/var/www folder
=> still nothing

---

### Post by Mr. C. on 2007-07-23
If there is no mention in your apache logs for those reqeuests, then they did not make it to apache.  All requests are logged.  The log shows one successful get of a 370 byte index.html file.  Nothing more.

Ignore /var/www/favicon.ico - the browser asks for that file to place a little custom icon in the URL address bar for a website.

Show command output from :

```
ls -l /var/www
ls -l /var/www/*
cat /var/www/index.html

```

MrC

---

### Post by heitjer on 2007-07-24
ls -l /var/www gives me:
```

drwxr-xr-x  2 root root  4096 2007-07-23 21:33 apache2-default
-rw-r--r--  1 root root    98 2007-02-13 21:47 Desktop.ini
-rw-r--r--  1 root root 13270 2004-07-20 08:36 favicon.ico
-rw-r--r--  1 root root   370 2007-07-23 20:28 index.html
drwxr-xr-x  2 root root  4096 2007-07-22 21:04 _notes
drwxr-xr-x  2 root root  4096 2007-07-22 14:36 sharedip
drwxr-xr-x  2 root root  4096 2007-07-23 21:28 testfolder
drwxr-xr-x 16 root root  4096 2007-07-23 21:36 txspmain
drwxr-xr-x  2 root root  4096 2007-07-22 14:17 webalizer

```
ls -l /var/www/*  gives me:
```

drwxr-xr-x 8 root root  4096 2007-07-22 20:57 ASPMaker
drwxr-xr-x 2 root root  4096 2007-07-22 21:04 _download
drwxr-xr-x 2 root root  4096 2007-07-22 21:04 _images
-rw-r--r-- 1 root root 11387 2007-06-22 23:44 index.html
-rw-r--r-- 1 root root   370 2007-07-23 20:28 index.html.mo
drwxr-xr-x 2 root root  4096 2007-07-22 21:04 _notes
-rw-r--r-- 1 root root  6608 2006-07-24 20:20 TMP7evkt2xt6h.asp
-rw-r--r-- 1 root root  6608 2006-07-24 20:21 TMP7g7fh2xt87.asp
drwxr-xr-x 5 root root  4096 2007-07-22 20:57 TxSP_blanco
drwxr-xr-x 5 root root  4096 2007-07-22 20:57 TxSP_brazos
drwxr-xr-x 5 root root  4096 2007-07-22 20:58 TxSP_dinosaur
drwxr-xr-x 5 root root  4096 2007-07-22 20:58 TxSP_galveston
drwxr-xr-x 5 root root  4096 2007-07-22 20:58 TxSP_galveston2
drwxr-xr-x 5 root root  4096 2007-07-22 20:58 TxSP_huntsville
drwxr-xr-x 5 root root  4096 2007-07-22 20:58 TxSP_livingston
drwxr-xr-x 5 root root  4096 2007-07-22 20:59 TxSP_rusk
drwxr-xr-x 5 root root  4096 2007-07-22 20:59 TxSP_tyler
drwxr-xr-x 5 root root  4096 2007-07-22 21:04 TxSP_whitney

```
cat /var/www/index.html gives m the following. 

```

<html>
<head>
<title>Untitled Document</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>

<body bgcolor="#FFFFFF" text="#000000">
<p><a href="http://xxx.external_website.com" target="_self"><font size="+2" face="Arial, Helvetica, sans-serif">Click
  Here</font></a> </p>
<p>&nbsp;</p>
<p><font size="6">html</font></p>
</body>
</html>

```

But this is a website that is possible to access from the outside. I have problems when I replace this with the one inside one of the folders.

I can pm you the content of that one plus some actual links to the site. I don't want to post all this stuff here.

---

### Post by Mr. C. on 2007-07-24
There is too much miscommunication and confusion here. Let's clarify some things.

Correct me where I"m wrong.

From your remote location (work?), your index.html (which lives in /var/www) appears in your browser correctly.  This presents a link, which says "Click Here".  You click on that link, and it directs your browser to another site.

However, you have a different index.html, which fails in some way when you click on one of its links.  Any URLs in that file are interpreted by your browser.  If the link refers to a site not serviced by your server, of course there will be no apache log entires (which is what we see).  However, if link refers to a site hosted by your apache server, and your apache logs show no entires, a firewall has blocked the request, and in this case too your apache server posts no logs.  Both of these cases fit the data.

If this is correct, there is no reason to see any more files - the reason is clear.

This problem boils down to determining if your URL request reaches your firewall/router, and if so, why is it being blocked.

MrC

---

### Post by heitjer on 2007-08-04
Apologies for the inital confusing posts. It was extremly confusing for me too as I had to deal with browser cache as well. This confused the $%#* out of me. 

Alright - I finally found some time to close in on the problem. Here is what it boils down to:

1) created a simple HTM weppage (mytest.htm) with one link (to [www.yahoo.com](www.yahoo.com)) and two pictures (greg2.jpg & bug.gif)

```

<html>
<head>
<title>Untitled Document</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>

<body bgcolor="#FFFFFF" text="#000000">
<p><a href="www.yahoo.com">testing</a></p>
<p><img src="greg2.jpg" width="115" height="140"></p>
<p>&nbsp;</p>
<p><img src="bug.gif" width="100" height="75"></p>
</body>
</html>

```

2) placed page and pictures on the root directory of the webserver (/var/www)

3) try access file from home computers on network - no problem - page displays nicely with everything at the right place. 

4) try access file from work (or anywhere on the internet) - apache serves the page and displays the link 'testing' on the page and then stalls ("2 items remaining...") while retrieving the pictures. 

ERROR LOG 
nothing - no entry - empty

ACCESS LOG 
```

xxx.xxx.xxx.126 - - [04/Aug/2007:18:58:00 -0500] "GET /mytest.htm HTTP/1.1" 304 - "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; H010818; .NET CLR 1.1.4322)"
xxx.xxx.xxx.126 - - [04/Aug/2007:18:58:00 -0500] "GET /greg2.jpg HTTP/1.1" 200 9390 "http://yyy.yyy.yyy.137/mytest.htm" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; H010818; .NET CLR 1.1.4322)"
xxx.xxx.xxx.126 - - [04/Aug/2007:18:58:00 -0500] "GET /bug.gif HTTP/1.1" 200 2666 "http://yyy.yyy.yyy.137/mytest.htm" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; H010818; .NET CLR 1.1.4322)"

```

Checking user group:
After some search I found[ this link ]("http://ubuntuforums.org/showthread.php?t=499777&highlight=apache+image")on the forum. I thought I found a solution and I changed my user to www-data and the group to www-data. 

> 
/var/www# ls -ld

gives me 
> 
drwxrwxr-x 26 www-data www-data 4096 2007-08-04 17:59


All files in question do have 0755 permission set. I also had shared the /var/www directory from Samba but took this out as Samba handles different access control. So no interference from Samba and still not access to pictures. 

I also read something about MIME extension and added in Webmin the type "image/jpeg" and extension".jpg" in hope to produce the jpg image. No success. 

I am clueless.......


Some thoughts from ya'lls side are extremly welcome!

---

### Post by Mr. C. on 2007-08-04
See my post #14 here:

[http://ubuntuforums.org/showthread.php?t=477659&highlight=mrc+tcp&page=2](http://ubuntuforums.org/showthread.php?t=477659&highlight=mrc+tcp&page=2)

Since there are no errors in your error log, and because the web pages work internally, this is not a permissions issue.
MrC

---

### Post by heitjer on 2007-08-04
I disabled the IPv6 - no success.

---

### Post by heitjer on 2007-08-05
does this look normal to you guys....? Especially the part 

deny from all and allow from 127.0.0.0 - does this mean its allowed from the insite but not fromoutsite?


```

AliasMatch ^/apache2-default/manual(?:/(?:de|en|es|fr|ja|ko|ru))?(/.*)?$ "/usr/share/doc/apache2-doc/manual/$1"
AliasMatch ^/manual(?:/(?:de|en|es|fr|ja|ko|ru))?(/.*)?$ "/usr/share/doc/apache2-doc/manual/$1"
<Directory "/usr/share/doc/apache2-doc/manual/">
    Options Indexes
    AllowOverride None
    Order deny,allow
    deny from all
    Allow from  127.0.0.0/255.0.0.0 ::1/128

    <Files *.html>
	SetHandler type-map
    </Files>
									
    SetEnvIf Request_URI ^/manual/(de|en|es|fr|ja|ko|ru)/ prefer-language=$1
    RedirectMatch 301 ^/manual(?:/(de|en|es|fr|ja|ko|ru)){2,}(/.*)?$ /manual/$1$2
</Directory>

```

---

### Post by koenn on 2007-08-05
that just means, i think,  that the apache documentation in /usr/share/doc/apache2-doc/manual/ can only be viewed from (a browser on) the local machine, i.e the computer the documentation lives on.

---

### Post by gene02 on 2007-08-07
```
xxx.xxx.xxx.126 - - [04/Aug/2007:18:58:00 -0500] "GET /greg2.jpg HTTP/1.1" 200 9390 "http://yyy.yyy.yyy.137/mytest.htm" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; H010818; .NET CLR 1.1.4322)"

```

This line says that your server successfully (response code 200) delivered 9390 bytes worth of file.  I think your apache setup is fine, the problem is someplace else.  

What happens if you try looking directly at the jpg:

[http://your.server.ip/greg2.jpg](http://your.server.ip/greg2.jpg)

---

### Post by heitjer on 2007-08-07
Thanks for the tip - great idea...

Sorry - but no display of the jpg this way!

---

### Post by gene02 on 2007-08-09
What do you see in your error and access logs when you try this?  What happens if you try to view this url from a different computer?

---

### Post by heitjer on 2007-08-09
Access Log:

```

xxx.xxx.xxx.126 - - [07/Aug/2007:20:24:53 -0500] "GET /greg2.jpg HTTP/1.1" 200 9390 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; H010818; .NET CLR 1.1.4322)"

```

The only error close (+/- 5 minutes) to this time stamp is:

```

[Tue Aug 07 20:24:46 2007] [error] [client xxx.xxx.xxx.126] File does not exist: /var/www/favicon.ico

```

---

### Post by gene02 on 2007-08-10
heitjer, it still looks like the file is getting sent.  Can you send me a private message with the ip address of your server?  I can see if I can access the file.

---

### Post by heitjer on 2007-08-10
I have only my work computer to try this from the outside so I always had to wait another day to test it and this is driving me nuts.

...I just tried to access my page from my Blackberry. Guess what...! It worked. 

I am completely puzzled now....

So you guys have been telling me that the logs indicate that it serves the pages right but my work browser does not display it. It works on every other page on the internet that I access from work. So any ideas on this strange behaviour.

Gene - thanks for the offer - I send you a link to my page.

---

### Post by heitjer on 2007-08-10
All,
Gene02 tested my site and it displays just fine! So I need to close this topic - after all the struggle on my side to narrow in on the issue and all ya'lls help it comes down to a problem on my corporate IT side. :confused:

I appreciate all your input and your suggestions! That's what I like about the internet community!

---

