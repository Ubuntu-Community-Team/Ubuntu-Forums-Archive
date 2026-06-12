---
title: "If is there any file size restriction for ubuntu server?"
date: 2010-01-29
forum: Server Platforms
---

### Post by programming.name on 2010-01-29
Hi, 
I have a 2.4GB sized file on my ubuntu web hosting server (/var/www directory) and I created a web page that contains an anchor tag (<a href="blahblahblah.zip">) for someone else to download the file. But when someone outside of my network tried to download the file through the link, he got an odd file. What I mean by the odd file is that once someone have downloaded the file, the file name is, of course, the same but the file size is just like 3KB rather than its original size. So I thought the server might limit a big sized file and I replaced the 2.4GB file with a 100MB file and It surprisingly worked fine. What's going and what can I do to solve this troublesome?
Ah, downloading a big sized file within the same network(My laptop and the server desktop comptuer are in the same network) there's no problem at all. 
 
Thanks.

---

### Post by Vegan on 2010-01-29
ext3 is limited to 16GB in most configurations, ext4 is up in the range of 2^64.

---

### Post by Jekshadow on 2010-01-30
If you are using ext3/4, the limit could be a minimum of 16GiB (most likely higher), so nowhere near 2.4GB. It is more likely your ISP killed the transfer, than a problem with Ubuntu, as it does work over your local network, but not via the Internet.

---

### Post by smeerbartje on 2010-01-30
Incorrect; it has something to do with file size limitations from Apache. Please read [this]("http://www.issociate.de/board/post/226898/2_Gig_Apache_File_Size_Limit....html").

---

### Post by Lars Noodén on 2010-01-30
All three of the answers above point to potential bottlenecks.

Earlier versions of Apache [did not support files >2GB](http://httpd.apache.org/docs/2.2/new_features_2_2.html) prior to Apache 2.2

Other than that, it is the file system and how the file system is configured which determine maximum file size.

Make sure you have a recent version of Apache.  Failing that, the usual way around the limitation is to (carefully) set up Anonymous FTP to the same directory as the web server.  

You could also serve up the file as a torrent.  If there meant to be a lot of downloads, that might save bandwidth.

---

