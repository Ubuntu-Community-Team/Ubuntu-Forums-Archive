---
title: "Can anyone offer some advice on downloading an entire website for admin offline?"
date: 2009-11-29
forum: Server Platforms
---

### Post by bobnutfield on 2009-11-29
Hello Everyone,

I started a new job a couple of months ago and I am the only one in this small company with any computer knowledge.  I certainly not an expert, especially with maintaining the content of our website, but that is exactly what I have been asked to do.

The website was created and is hosted by a separate company, but they are useless.  No help at all.  Anyway, what I need to do is download the entire website and make changes to it offline, then make the changes to the live website.  The site was built by this company using Joomla and I can use this program while it is online using administrator privileges, but this is all new to me and it takes the site offline for a long time while I bumble around trying to do things.

I have found that I can get the website downloaded with wget, but it does not let me administer it offline.  I need to experiment with adding new pages and photographs of products, which of course I need administrator privileges to do.

I would be most appreciative if someone knowledgeable with this could offer some advice to get me going.  The boss is counting on me to come up with something.

Many thanks in advance

---

### Post by BkkBonanza on 2009-11-29
I would suggest creating a virtual machine on your system that is similar to the real server. This is fairly easy to do by installing VirtualBox and then a suitable server os as guest. For example, if your real web site is served on Linux then you can install Ubuntu server as a guest in VirtualBox. Then install web server packages needed (apache, mysql, php) and your web site software into that guest. 

This allows you to run a fully function test copy of your server inside your development system - no additional costs. You can admin this system and do any tests/change you need locally. When you have what you want working then use rsync to copy the changes up to your real server (probably without going offline at all).

It will work best if the guest os is as setup close as possible to mimic the real server. ie. same versions of apache, joomla, mysql etc. Then rsync will do the work for you as it copies any differences up to the real server. For Joomla based sites most of the update will be in the database and you may have to work out what needs to update and if user entered data (comments) is present it will need to be excluded by rsync.

Even if you don't do it this way you definitely should maintain a backup copy of the website for safety. Wherever the site is hosted you cannot be sure that one day it won't end up inaccessible or wiped out. Always have a backup so you can start fresh on another host if need be.

If running a test server like this is too much work then another method would be to run a duplicate site in joomla on the real server (a second database) and make updates to it. Then rsync the data from one database to the other to update the real site almost instantly.

---

### Post by bobnutfield on 2009-11-29
Thank you for your reply.  I understand about half of this, but you kindly provided enough information/instructions for me to study it and do it.  I will have to eventually talk to the company that is hosting the site to find out what version of each of the programs you mentioned they are running.  They have not been helpful and hard to get in touch with, but the company owner likes them, so....

I did find an app in the Ubuntu repos that downloaded the site, but it did not include some content in the download (photos, gifs, etc.)  I also have attempted to install Joomla locally on my Ubuntu machine, but haven't figured out how to do it yet (it was a tar.gz app, but does not act like other source files I have installed before.)

Anyway, thanks for your reply.  It will get me started.

---

### Post by BkkBonanza on 2009-11-29
Doing all this without having background knowledge of server admin will be difficult but if you want to learn how to admin and run a server then it is a stuff you will need to know anyway. It is a lot more than just administering from the Joomla control panel. You may want to start in the Joomla forum looking for more info specific to Joomla and how to back it up from the control panel. I'm not a Joomla expert but I did install it once and use it briefly.

The Joomla tar.gz file will be an archive of the web site php code. So it needs to be installed into a working web server folder (where apache can use it). It doesn't run as an app by itself. You would need eg. LAMP installed (linux,apache,mysql,php) first and then Joomla installed. You would need to learn about Apache, Mysql and PHP to some extent.

You may find at the bottom of your web site the Joomla version info. This will help with what version of Joomla you would want to install on a test web server.

If the downloaded site copy you made was done using wget or similar tools then what you have is just a copy of the "served pages". What you really need to be able to take over admin fully is a copy of the actual server files. In Joomla all of the data that determines the site content is stored in mysql database files. So those files would be needed and cannot be accessed as a regular web user. You would need admin access to the server to get them, or a backup of the sql data given to you by the current admin or done through Joomla admin. If the current admin is not helpful (because you're taking over the job?) then you'll have a bit of a headache to take over the site.

---

### Post by bobnutfield on 2009-11-29
Thanks again, BkkBonza.  You are so right, there is a lot more to learn than just the Joomla control panel, which is all I have been shown how to do.  This, of course, takes the site down while I am making changes to it.  But you have set me on the right track.  I will take my studies first to the Joomla forums, then start reading tutorials on Apache and Mysql.  

Thanks again

---

### Post by blindmist on 2009-11-30
If you have Adobe Dreamweaver, this is very simple.

---

### Post by BkkBonanza on 2009-11-30
> **blindmist said:**
> If you have Adobe Dreamweaver, this is very simple.

Only if you have full access to the server...

---

### Post by Vegan on 2009-11-30
Depending on the site you want to copy it could come with a lot of components, so be careful.

---

