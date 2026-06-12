---
title: "Setting up a website to download files from MU depending on the URL I use"
date: 2011-06-04
forum: Server Platforms
---

### Post by kenny2009 on 2011-06-04
Originally posted in [http://ubuntuforums.org/showthread.php?p=10887843#post10887843](http://ubuntuforums.org/showthread.php?p=10887843#post10887843)

The original thread was closed because "*Sounds as if you are trying to steal a service which you have not paid for. We do not support that kind of activity here on Ubuntu Forums.*" However, it's not stealing since I am only going to use this with accounts that I have legitimately paid for. 

This might not be the right place to post this... if that's the case, I apologize - please move it to the correct location.


I know a guy who has a website setup where he can download files from Megaupload with his premium account without signing in. He takes the MU link's ID, eg: [http://www.megaupload.com/?d=xxxxxxxxand](http://www.megaupload.com/?d=xxxxxxxxand) adds it to the end of the URL ([http://192.168.1.199/mu/?d=xxxxxxxx](http://192.168.1.199/mu/?d=xxxxxxxx)) and it downloads using _his_ premium account logged in on the computer he has his site hosted on. We don't get along well and I would rather not ask him how he does it.

How would I set this up on my own computer to use **_my_** premium account? I can see this being extremely useful for me if I need to download some of my artwork or projects from MU but I don't want to sign in because I'm on a *public computer* or something or because the computer has MU blocked. I want this to be a private site that only I have access to since it's my premium account and my money. I am not asking how to circumvent megauploads download limit at all (I've already paid for it... no need to circumvent it). 


I just need a nudge in the right direction. Thanks in advance for any help you can provide.


I already have everything installed on my computer to host a site. I have a simple "Hello World" page running on my webserver right now. I don't need help getting that part set up, just the rest of it. I assume this has something to do with setting up a proxy server - I just don't know how to do that and make it work like I need it to.

---

### Post by mmad on 2011-06-05
Check out rapidleech - [http://wiki.rapidleech.com/Main_Page](http://wiki.rapidleech.com/Main_Page).

Its a PHP script that uses your login credentials on your own server
and allows you to download files from loads of file hosts. I've never
set it up myself, but I've heard good things.

---

### Post by hakermania on 2011-06-05
In your server have a index.php
everything passed to your server (e.g. a megaupload link) could be written to a file or something, then, an external program would take this file and download it.

Sound logical but dunno if can practically work, i don't know php well and im not sure i did understand the problem well enough to propose a solution :)

---

### Post by BkkBonanza on 2011-06-06
You could make a simple php script that takes the id you give it and uses curl to access MU and do the download for you. It just needs to provide curl with the correct info / cookie etc to get the download to work. If you know php then reading up on curl would be helpful as you can use it to emulate anything you can do manually with a browser.

---

