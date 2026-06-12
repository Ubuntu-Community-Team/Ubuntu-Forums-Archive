---
title: "Mono for aspx webpages"
date: 2008-11-14
forum: Server Platforms
---

### Post by lang79james on 2008-11-14
Just like to start off I am a newb at Linux I can install it and install programs but not always get them to work 

task to get aspx files to load using hardy apache2 mono-2.0.1 with out using the command xsp2 or xsp 

I have mono installed and apache2 install 
I have tried to edit a few config files but either apache2 will load and the files want to save to disk and not load in the web browser or apache2 wont reload because it does not like the *.conf files when it comes to mono lines 

what I need is help on what files to edit and what to put in there 
I am using the mono ASP.net sample pages because they should work with out editing them.... if I can get them to work I am going to try them with my website files that are on a windows server running IIS 

the dir where the files are located at are /var/www

so can anyone please tell me what files I need to edit and how to edit them to get this to work 

I think I seen about 2 to 3 ways of doing this but they are for earlier version of mono and does not seem to work with mono-2.0.1

even tried an earlier version mono-1.1.18.7 but the mod_mono-1.1.18.5 would not install

---

### Post by directhex on 2008-11-14
Ubuntu does not contain Mono 2.0.1

And XSP runs independently of Apache

---

### Post by Vegan on 2008-11-14
To be able to use ASP and ASP.NET you should be using Server 8.10 as older versions have issues.

If you don't you will have some problems like I did.

look for mono killed php

:guitar:

---

### Post by directhex on 2008-11-14
> **Vegan said:**
> To be able to use ASP and ASP.NET you should be using Server 8.10 as older versions have issues.

If you don't you will have some problems like I did.

look for mono killed php

:guitar:

He seems to be compiling his own Mono anyway, which is unsupportable, so he's pretty much on his own

---

### Post by lang79james on 2008-11-14
> **directhex said:**
> He seems to be compiling his own Mono anyway, which is unsupportable, so he's pretty much on his own

Hey I dont care if you tell me to download ubuntu 8.10 and tell my to use the built in installer and Yes I did read mono killed my php5 I have tried the installer and compiled and I have edit the *.conf files that this forum has said and nothing works and yes i know the xsp and xsp2 are a stand alone and those work I just dont want to type those commands every time I have to restart

also as an update I did upgrade to 8.10 shortly after reading mono killed php5 

From what I can tell you just need to edit a few config files 
I just need to know which ones and what to put in there

---

### Post by directhex on 2008-11-14
> **lang79james said:**
> Hey I dont care if you tell me to download ubuntu 8.10 and tell my to use the built in installer and Yes I did read mono killed my php5 I have tried the installer and compiled and I have edit the *.conf files that this forum has said and nothing works and yes i know the xsp and xsp2 are a stand alone and those work I just dont want to type those commands every time I have to restart

also as an update I did upgrade to 8.10 shortly after reading mono killed php5 

From what I can tell you just need to edit a few config files 
I just need to know which ones and what to put in there

Do you even have mod_mono installed?

---

### Post by lang79james on 2008-11-14
> **directhex said:**
> Do you even have mod_mono installed?

From what I can tell yes at the time but now I dont because I just reloaded 8.4 and now is upgrading to 8.10 to start fresh I am willing to take step by step instructions on how to set it up.

---

### Post by directhex on 2008-11-14
> **lang79james said:**
> From what I can tell yes at the time but now I dont because I just reloaded 8.4 and now is upgrading to 8.10 to start fresh I am willing to take step by step instructions on how to set it up.

install mono-apache-server2

install libapache2-mod-mono

a2dismod mod_mono

ln -s /usr/bin/mono-apache-server2 /usr/bin/mono-apache-server

a2enmod mod_mono_auto

restart apache

---

### Post by lang79james on 2008-11-14
Ok did that now so what files do I need to edit to have the files to be read in the browser

---

### Post by directhex on 2008-11-14
> **lang79james said:**
> Ok did that now so what files do I need to edit to have the files to be read in the browser

That's it. Just shove .aspx files in /var/www/

If it isn't working, paste the last few lines from the Apache error log.

---

### Post by lang79james on 2008-11-14
Ok it works on the local host but not from anther computer 
When I try it on anther computer the file wants to be downloaded how do it set it up to where the page will not be downloaded

---

### Post by directhex on 2008-11-14
So [http://localhost/helloworld.aspx](http://localhost/helloworld.aspx) works, but [http://yourserver/helloworld.aspx](http://yourserver/helloworld.aspx) from a different machine does not?

Do other formats, e.g. html, behave as expected?

Have you messed about with your Apache config before - e.g. changing things in sites-enabled or httpd.conf?

---

### Post by lang79james on 2008-11-14
Nope well it is working now i guess it just takes time for things to change
and yes i know for the linux box itself i was using [http://localhost/index.aspx](http://localhost/index.aspx) and for the second computer [http://ipaddress/index.aspx](http://ipaddress/index.aspx) 

much thanks btw

---

### Post by nquinnathome1 on 2008-11-18
I'd like to reopen this thread as it followed the same problem I'm now having; I've set up a fresh install of 8.10 server w/LAMP and followed the instructions for ModMono on Ubuntu [here]("https://help.ubuntu.com/community/ModMono"), but all I get when I try to access the web server remotely is a downloaded aspx file. PHP and ordinary html files parse just fine. I have no errors in my Apache error log that suggest there was any problem starting mod_mono.

Anyone have any ideas why the code is downloading? I've Googled and not found much that has helped.

---

### Post by directhex on 2008-11-18
> **nquinnathome1 said:**
> I'd like to reopen this thread as it followed the same problem I'm now having; I've set up a fresh install of 8.10 server w/LAMP and followed the instructions for ModMono on Ubuntu [here]("https://help.ubuntu.com/community/ModMono"), but all I get when I try to access the web server remotely is a downloaded aspx file. PHP and ordinary html files parse just fine. I have no errors in my Apache error log that suggest there was any problem starting mod_mono.

Anyone have any ideas why the code is downloading? I've Googled and not found much that has helped.

Because mod_mono is not being asked to parse your site. Your apache config must be wrong somehow. Setting up .webapp files is a pain (I'm considering packaging a major ASP.NET package to teach myself the ins and outs)

[http://ubuntuforums.org/showpost.php?p=6178123&postcount=8](http://ubuntuforums.org/showpost.php?p=6178123&postcount=8) is the "easy" solution

---

### Post by paulm on 2009-01-06
For anyone struggling with this issue, when testing whether your changes have fixed the issue be sure to do something like:

curl -I [http://example.com/Test.aspx](http://example.com/Test.aspx)

rather than use your browser. Your browser may tend to cache the result when the server was sending you the aspx source and keep giving you that even if the server has been fixed and would send out the correct content with the right mime type.

I've been working on this for about an hour and have probably fixed (and rebroken) my server configuration multiple time before realising my browser was lying to me.

---

