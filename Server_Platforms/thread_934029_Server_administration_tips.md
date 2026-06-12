---
title: "Server administration tips?"
date: 2008-09-30
forum: Server Platforms
---

### Post by bazookaaa on 2008-09-30
Hello!

I'm a long-time user of Ubuntu, but new to administering a server. Since my site is gaining in popularity, I'm wondering if anybody has any tips, links, etc. that can help; for instance, memory leaks. My server is Apache 2 with mod_rails, and I use MySQL. This is all on Ubuntu 8.04.

Thank you!

---

### Post by devonps on 2008-09-30
Try google! It usually works for me :D

---

### Post by DanNYGB on 2008-09-30
Hello, I too am after some tips. I am new to Linux (since spring 2007, not gained much experience due to old Windows habits which Ubuntu so thoughtfully accommodates through its excellent GUI, possibly even better than Windows) I am looking to set up a webserver, I have already had a try at it using Ubuntu 7.04 Desktop on a VirtualBox VM on an Acer laptop installing the LAMP package plus phpmyadmin and webmin. 

Since then I have started my own business and am looking to create a similar production installation (shared webhosting being a bit of a lottery and dedicated hosting being expensive), I'm in no hurry, any late suggestins welcome! I like the advantages of virtualisation, and am hoping there will be a stable release of Sun's Open xVM Server to install an Ubuntu OS on. At the moment I only have a small selection of Compaq ProLiant Pentium 3 servers to work with, but may need newer hardware if OpenxVM requires hardware assisted virtualisation. 

I am looking for any helpful information, particularly security information, such as any risks associated with the Webmin control panel, it seems very powerful and anyone hacking into it would gain quite a lot of control over the server, I see Ubuntu no longer lists it in their repositories, are they concerned? What are the best ways to secure the webserver on the internet, while allowing local network administration of it? How about running it through a security gateway such as the open source Untangle? 

Assuming I use virtualisation, would it be best to run both on the same server, or use separate servers for the gateway and webserver? Any suggestions regarding high availability? I have 2 APC UPS power supplies (although no servers with redundant PSU supplies yet) and RAID 1 with hot swappable drives. I only have one connection on one site at the moment. 

Please accept my apologies if you found that question mind numbingly boring, hope it will interest someone.

---

### Post by shizakapayou on 2008-09-30
I assume by gateway you mean the firewall.  I prefer to keep that as a separate machine with only that role, and a webserver in a DMZ off that.

I used Webmin for a bit starting out.  It's good for visualising what's going on as you work, and it does help coming from a Windows environment.  However, I found that more than once, it made a mess of things, which caused me some headaches.  When I do use Webmin, it's only to look, never to change.

---

### Post by cariboo on 2008-09-30
Have a look here:

[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

and here:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

Jim

---

### Post by MystaMax on 2008-09-30
Memory leaks are usually caused by application (in your case, Ruby on Rails) code. You may want to make sure your code is optimized to the best of  your abilities. 

I like the articles @ slicehost.com - [http://articles.slicehost.com](http://articles.slicehost.com). Good instructions on setting up ubuntu servers and some maintaining tips in there as well.

---

