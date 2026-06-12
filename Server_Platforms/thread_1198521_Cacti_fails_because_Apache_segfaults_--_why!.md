---
title: "Cacti fails because Apache segfaults -- why!?"
date: 2009-06-27
forum: Server Platforms
---

### Post by fogster on 2009-06-27
I'm running Jaunty (9.04) inside a virtual machine. I set it up with Cacti on LAMP (all installed by apt-get). It failed with errors because it's trying to connect as root, not debian-sys-maint, to create the database. No problem, I'll do it by hand.

I'm now able to hit /cacti on my server, which redirects to /cacti/install. But I get a blank page there, and looking through the logs reveals that this is all Apache is logging:
> 
root@ubuntu:~# tail -f /var/log/apache2/error.log 
[Sat Jun 27 01:40:23 2009] [notice] child pid 6220 exit signal Segmentation fault (11)
[Sat Jun 27 01:41:33 2009] [notice] child pid 6221 exit signal Segmentation fault (11)


I'm intuiting that it has something to do with Suhosin, but I can't for the life of me figure out where it's logging or how to go about fixing it. I toyed with hacking the install/index.php script to print text to the page so I can tell where it's failing, and it appears to get hung up on the first line:
> 
include("../include/global.php");


I tried changing permissions (775) on the file, and then the whole directory, but it makes no difference. Plus, the Apache logs aren't saying that permission is denied, they're saying that a segfault occurred.

This is a very basic install. 9.04 in a virtual machine using about 500MB of disk, and Apache2/PHP/MySQL installed through apt-get. Where should I look to fix this? I'm very confused.

---

### Post by v3xtra on 2009-06-27
...You could check the Cacti Forums!

[http://forums.cacti.net/about32460.html&highlight=seg+fault](http://forums.cacti.net/about32460.html&highlight=seg+fault)

I did it for you!

Here's another one:

[http://forums.cacti.net/viewtopic.php?t=25260&start=0&postdays=0&postorder=asc&highlight=Segmentation+fault+(11)](http://forums.cacti.net/viewtopic.php?t=25260&start=0&postdays=0&postorder=asc&highlight=Segmentation+fault+(11))

They both seem to be related to importing the cacti.sql file correctly, and I really would try and use what it wants normally first and see if it will work instead of fiddling with a program that won't even work in the first place!  It minimizes the things that ARE wrong, with just the ones that should be wrong.  Hope that helps you!

---

### Post by fogster on 2009-06-27
> **v3xtra said:**
> ...You could check the Cacti Forums!

Ha! I assumed it was related to Ubuntu/Suhosin, not Cacti itself. Seems I was quite wrong. Thanks!

> I really would try and use what it wants normally first and see if it will work instead of fiddling with a program that won't even work in the first place!

That's the problem. There seems to be a bug with the installer (see [https://bugs.launchpad.net/ubuntu/+source/cacti/+bug/374280](https://bugs.launchpad.net/ubuntu/+source/cacti/+bug/374280) ) and it was keeping it from working at all for me. I figured it would be pretty easy to pick up where the installer left off.

In any case, thanks to your help, it was a trivial fix. Just had to manually import the database that seems to have failed during install.

---

### Post by v3xtra on 2009-06-28
Glad you got everything working!  Hope you enjoy it!

---

