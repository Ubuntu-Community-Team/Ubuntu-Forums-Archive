---
title: "What are correct permissions for running a server?"
date: 2007-02-03
forum: Server Platforms
---

### Post by mickbuntu on 2007-02-03
Hello,

1. What are the correct group and username should be assigned to: /var/www?
2. What are the correct  group and username should be assigned to  /var/www/anything past this point?


Currently username is:  root
Currently Group is : www-data  


What would be correct thanks.

---

### Post by gombadi on 2007-02-03
Correct is a matter of opinion.

What the distribution has setup is generally fine.

Generally there are three things to remember -

1 - The web server process has to be able to read the files so readable by anyone.

2 - Directories readable and executable by anyone.

3 - The web server process must NOT have write permissions to the files or directories.


So files owned by root and group readable by www-data (as long as only readable) will work and should be fine. If you have a user that updates the files then you can make the files owned by that user to make it easy for them to update.

---

### Post by detectiveinspekta on 2007-02-04
I havn't done it to my server yet but what if rx permissions were removed to everyone apart from root? Wouldn't it be safer?

---

### Post by mickbuntu on 2007-02-04
Thanks   not  sure  myself.:confused:       :)

Here is sort of a lead:  [http://ubuntuforums.org/showthread.php?t=263064](http://ubuntuforums.org/showthread.php?t=263064)

---

### Post by Brazen on 2007-02-04
> **detectiveinspekta said:**
> I havn't done it to my server yet but what if rx permissions were removed to everyone apart from root? Wouldn't it be safer?

Mmm, maybe safer, but then the Apache daemon would not be able to read the files.  I believe the Apache daemon user and group are both named 'www-data' so your web directory (/var/www) must be readable by either the user or group 'www-data'.

---

### Post by mickbuntu on 2007-02-04
> **gombadi said:**
> Correct is a matter of opinion.

What the distribution has setup is generally fine.

Generally there are three things to remember -

1 - The web server process has to be able to read the files so readable by anyone.

2 - Directories readable and executable by anyone.

3 - The web server process must NOT have write permissions to the files or directories.


So files owned by root and group readable by www-data (as long as only readable) will work and should be fine. If you have a user that updates the files then you can make the files owned by that user to make it easy for them to update.

> **Brazen said:**
> Mmm, maybe safer, but then the Apache daemon would not be able to read the files.  I believe the Apache daemon user and group are both named 'www-data' so your web directory (/var/www) must be readable by either the user or group 'www-data'.


Thank You your post appeared out of nowhere we must have been all posting at the same 
time.


Have another problem some  sites  cause   an issue  with 127.0.0.1 reposted from another site. 
It appears no one hacked me but it can happen maybe.  My site is totally not  the site that is in the log.

**_It appears this:_**


```


 Few days ago was concerned someone hacked into my server after taking precautions. 
A fresh generic install of a linux  distribution yielded the same. It seems their is some
 issue that Can not resolve.  This is currently beyond my scope of comprehension.     

Found the root cause it seems some sites like:  http://forums.amd.com/index.php?showtopic=90367   

Cause my  access_logs to start filling up with external websites while apache is running.  What can it  
be  that while apache is on and certain  sites  cause this?      On another note It seems if  pages match 
some  pages on my server. That website below is not mine, mine is a totally different site.


Here is an excerpt from my  current   tests on access_log:

> 

Firefox/2.0.0.1 (Ubuntu-feisty)"
127.0.0.1 - - [04/Feb/2007:08:23:37 -0500] "GET /galerie/images/files/3/13/index.php?main_page=page_not_found HTTP/1.1" 301 - "http://forums.amd.com/index.php?showtopic=90367" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061201 Firefox/2.0.0.1 (Ubuntu-feisty)"
127.0.0.1 - - [04/Feb/2007:08:23:37 -0500] "GET /galerie/images/files/3/13/index.php?main_page=page_not_found HTTP/1.1" 301 - "http://forums.amd.com/index.php?showtopic=90367" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061201 Firefox/2.0.0.1 (Ubuntu-feisty)"
127.0.0.1 - - [04/Feb/2007:08:23:37 -0500] "GET /galerie/images/files/3/13/index.php?main_page=page_not_found HTTP/1.1" 301 - "http://forums.amd.com/index.php?showtopic=90367" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061201 Firefox/2.0.0.1 (Ubuntu-feisty)"
127.0.0.1 - - [04/Feb/2007:08:23:37 -0500] "GET /galerie/images/files/3/13/index.php?main_page=page_not_found HTTP/1.1" 301 - "http://forums.amd.com/index.php?showtopic=90367" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061201 Firefox/2.0.0.1 (Ubuntu-feisty)"
127.0.0.1 - - [04/Feb/2007:08:23:38 -0500] "GET /galerie/images/files/3/13/index.php?main_page=page_not_found HTTP/1.1" 301 - "http://forums.amd.com/index.php?showtopic=90367" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061201 Firefox/2.0.0.1 (Ubuntu-feisty)"
127.0.0.1 - - [04/Feb/2007:08:23:38 -0500] "GET /galerie/images/files/3/13/index.php?main_page=page_not_found HTTP/1.1" 301 - "http://forums.amd.com/index.php?showtopic=90367" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061201 Firefox/2.0.0.1 (Ubuntu-feisty)"
127.0.0.1 - - [04/Feb/2007:08:23:38 -0500] "GET /galerie/images/files/3/13/index.php?main_page=page_not_found HTTP/1.1" 301 - "http://forums.amd.com/index.php?showtopic=90367" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061201 Firefox/2.0.0.1 (Ubuntu-feisty)"
127.0.0.1 - - [04/Feb/2007:08:23:38 -0500] "GET /galerie/images/files/3/13/index.php?main_page=page_not_found HTTP/1.1" 301 - "http://forums.amd.com/index.php?showtopic=90367" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061201 Firefox/2.0.0.1 (Ubuntu-feisty)"
127.0.0.1 - - [04/Feb/2007:08:23:38 -0500] "GET /galerie/images/files/3/13/index.php?main_page=page_not_found HTTP/1.1" 301 - "http://forums.amd.com/index.php?showtopic=90367" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20061201 Firefox/2.0.0.1 (Ubuntu-feisty)"



As you see the external website  says it  came from my  computer the connection as if it 
originated.   Using my hardware router  filtered  all access to  the local   127.0.0.1  
connection.  Meaning at the router point to block any  spoofing  packets.    Yet  
now  websites register  on my  logs. Seems the trigger for that website was   
the not found error. Have a similar one on my apaches www  serving  dir. 



```

[B][U]
String that might be setting it off in access log:[/U][/B]
```
127.0.0.1 - - [04/Feb/2007:12:34:56 -0500] "GET /galerie/images/files/3/13/index.php?main_page=page_not_found HTTP/1.1" 301 
```
[B][U]
String in error log:[/U][/B]
```
  

[Sun Feb 04 11:59:32 2007] [error] [client 127.0.0.1] File does not exist: /var/www/catalog/galerie, referer: http://forums.amd.com/index.php?showtopic=90367


```
[B][U]
Cleared  the firefox's about:cache  to  start fresh here is the log:[/U][/B]
```


Disk cache device

Number of entries: 	39
Maximum storage size: 	50000 KiB
Storage in use: 	208 KiB
Cache Directory: 	/home/user/.mozilla/firefox/30bd2dpg.default/Cache

           Key: http://forums.amd.com/style_images/amdv214/p_offline.gif
     Data size: 788 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/style_images/amdv214/spacer.gif
     Data size: 43 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/style_images/amdv214/p_quote.gif
     Data size: 1507 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:55
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/jscripts/ipb_topic.js
     Data size: 11658 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-13 12:56:51

           Key: http://forums.amd.com/style_images/amdv214/p_online.gif
     Data size: 1224 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:55
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/jscripts/ips_xmlhttprequest.js
     Data size: 8288 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:53
       Expires: 2007-03-13 12:56:50

           Key: http://forums.amd.com/style_images/amdv214/p_up.gif
     Data size: 1397 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:55
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/style_images/amdv214/p_pm.gif
     Data size: 1219 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:55
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/style_images/amdv214/t_reply.gif
     Data size: 1960 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/jscripts/ipb_global_xmlenhanced.js
     Data size: 9755 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:53
       Expires: 2007-03-13 12:56:51

           Key: http://www.userbars.com/galerie/images/files/3/13/ASRock.png
     Data size: 0 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:56
       Expires: No expiration time

           Key: http://img404.imageshack.us/img404/4112/0000011800135951ld7.jpg
     Data size: 2836 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:56
       Expires: 2007-02-08 21:50:47

           Key: http://forums.amd.com/style_images/amdv214/amd_brand_logo.gif
     Data size: 1154 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:52
       Expires: 2007-03-04 21:31:58

           Key: http://forums.amd.com/style_images/amdv214/amd_brand_fill.gif
     Data size: 137 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:51
       Expires: 2007-03-13 12:56:04

           Key: http://forums.amd.com/style_images/amdv214/tile_dark.gif
     Data size: 517 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:55
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/style_images/amdv214/tile_back.gif
     Data size: 7251 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:55
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/style_images/amdv214/menu_item.gif
     Data size: 87 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:55
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/style_images/amdv214/amd_brand_forums.gif
     Data size: 1170 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:51
       Expires: 2007-03-13 12:56:04

           Key: http://forums.amd.com/style_images/amdv214/nav_m.gif
     Data size: 53 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/favicon.ico
     Data size: 1406 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:50
       Expires: 2007-03-13 12:56:47

           Key: http://forums.amd.com/style_images/amdv214/amd_sponsers.jpg
     Data size: 10203 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:55
       Expires: 2007-03-13 12:56:08

           Key: http://forums.amd.com/style_images/amdv214/folder_js_skin/ips_menu_html.js
     Data size: 2846 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:52
       Expires: 2007-03-13 12:56:05

           Key: http://forums.amd.com/index.php?showtopic=90367
     Data size: 15786 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:51
       Expires: 1969-12-31 19:00:00

           Key: http://img161.imageshack.us/img161/5931/gentoolinuxcj0.png
     Data size: 8941 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:56
       Expires: 2007-02-14 09:50:49

           Key: http://forums.amd.com/uploads/av-109.png
     Data size: 8265 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:55
       Expires: 2007-05-28 22:53:31

           Key: http://forums.amd.com/style_images/amdv214/to_post_off.gif
     Data size: 64 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/style_images/amdv214/menu_action_down.gif
     Data size: 100 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/style_images/amdv214/t_new.gif
     Data size: 1953 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-13 12:56:07

           Key: http://www.usersigs.com/site/data/media/11/hendrix.jpg
     Data size: 10244 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:56
       Expires: 2007-03-07 07:28:36

           Key: http://forums.amd.com/style_images/amdv214/pip.gif
     Data size: 91 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/uploads/av-67075.jpeg
     Data size: 1553 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-04 11:57:34

           Key: http://forums.amd.com/style_images/amdv214/nav.gif
     Data size: 1119 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:53
       Expires: 2007-03-13 12:56:06

           Key: http://forums.amd.com/style_images/amdv214/loading.gif
     Data size: 1827 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:53
       Expires: 2007-03-13 12:56:06

           Key: http://img224.imageshack.us/img224/2765/snap8ds4.jpg
     Data size: 3907 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:56
       Expires: 2007-02-22 07:04:13

           Key: http://forums.amd.com/jscripts/dom-drag.js
     Data size: 6333 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:53
       Expires: 2007-03-13 12:56:51

           Key: http://forums.amd.com/jscripts/ipb_global.js
     Data size: 19025 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:52
       Expires: 2007-03-13 12:56:49

           Key: http://forums.amd.com/style_images/amdv214/p_mq_add.gif
     Data size: 1612 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:55
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/style_images/amdv214/p_card.gif
     Data size: 1543 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:54
       Expires: 2007-03-13 12:56:07

           Key: http://forums.amd.com/jscripts/ips_menu.js
     Data size: 10350 bytes
   Fetch count: 1
 Last modified: 2007-02-04 12:34:52
       Expires: 2007-03-13 12:56:50



```


_**First thought was hacked:**_ 

Feel free to see post here:  [http://ubuntuforums.org/showthread.php?t=351643]("http://ubuntuforums.org/showthread.php?t=351643")

---

### Post by b0red on 2007-02-04
Directory perms should be chmod 751 but files should allow everyone read.
Trust me don't allow read (exec only) on directories as then the hacker must guess every filename ;)

Having all files in webroot owned by root is good , ensure there are *no* writeable files or dirs in there for the apache or www-data account.

---

