---
title: "Add file download to my web page"
date: 2013-10-25
forum: Server Platforms
---

### Post by CR4NFdA on 2013-10-25
Hello all, 
I have a Ubuntu server at my home hosting just a few basic web pages. Just type my domain name in your browser and go there for some basic local astronomical info. Nothing complex. No login or passwords needed. No mail server. Using Ubuntu Server 12.04.2 with the basic LAMP install. No GUI. Computer is a very old Gateway with 1000Mhz AMD cpu and 640 ram. I would like to use it like a cloud. Example: Once or twice a month, I like to give a few friends some large files. To big for dropbox, Ubuntu one, ect. Without using FTP, (to complex for friends), can I make a directory to put the file(s) in so I can just tell them to go to my web site and hit a download button or open the directory and select the files they want? I need  to have a login ID and password for the download part so regular users can't access the files. Just one ID and password for all to keep it simple. If they can upload to me also that would be nice. Not good at PHP scripts but if needed I can learn . Tomorrow I'm going to look at OpenStack, but can that be run alongside my regular webpage? 

Many thanks all,
magpie

---

### Post by houstonbofh on 2013-10-26
If there is no index.htm(l) file, and you allow directory listing, they can see the entire directory.  As for login, look into htpasswd files.

---

### Post by CharlesA on 2013-10-26
Owncloud ftw!

---

### Post by CR4NFdA on 2013-10-26
Thanks all. But can I run Owncloud in a VM. I know how to setup Apache to load a different site, (different domain name), so I can have two sites on the same server. Anyways, I'll try it today. Must always learn right. :)

Thanks again all.
magpie

---

### Post by CharlesA on 2013-10-26
> **CR4NFdA said:**
> Thanks all. But can I run Owncloud in a VM. I know how to setup Apache to load a different site, (different domain name), so I can have two sites on the same server. Anyways, I'll try it today. Must always learn right. :)

Thanks again all.
magpie

Yes you can run it in a VM. :)

I run it on one of my VPSes.

Also, you can have Apache serving multiple sites from the same server, no problem.

[http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)

---

