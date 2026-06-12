---
title: "Ubuntu 8.04 LTS (hardy): Upgrade kernel to 2.6.32?"
date: 2010-09-22
forum: Server Platforms
---

### Post by Avada Kedavra on 2010-09-22
Hello,

due to  [[this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607167")] I need to update the kernel from 2.6.24 to 2.6.32 on my production servers. Can I do this without upgrading the distro from 8.04 LTS to 10.04 LTS? Preferably I would only like to download and install a new, precompiled, kernel. 

My current kernel is:
```
uname -a
Linux 2.6.24-24-server #1 SMP Tue Jul 7 19:39:36 UTC 2009 x86_64 GNU/Linux
```I need this upgrade to be *safe*. The servers are running mostly basic services such as apache, tomcat, mysql, munin, squid, mail. But its production and I cannot take any chances (I do have test servers to try everything on firstly).

---

### Post by CharlesA on 2010-09-22
You could try it, but I wouldn't suggest it, since Hardy is over two years old and Lucid just released.

I'd suggest trying to do a dist-upgrade after doing a full backup/image of the drive in case something doesn't work right.

Outside of that, I would recommend just backing up yer database/tomcat/apache config and doing a clean install of 10.04 then reinstall the db/other services and see if it'll have the same problem.

Would be a good idea to do it on a test machine.

---

### Post by Avada Kedavra on 2010-09-22
CharlesA,

thanks for your answer. I am worried to brake something while doing the upgrade, but your reasoning is logical. I guess that some things could potentially break by upgrading the kernel only, so maybe a full upgrade is the best alternative. I will experiment on the test server of course and hopefully move on to production if everything turns out smoothly. 
Just quite unfortunate that the filed bug hasn't received any attention (yet). 

If anyone else has tried what I ask above, please your input is welcomed. I have not yet started to upgrade the system :)

Cheers,
Avada

---

### Post by CharlesA on 2010-09-22
The reason I suggest a clean install, is because I've had problems when doing upgrades before, and sometimes upgrades can lead to problems down the road.

Are all the machines the same model? I'd run the install of the test server for a week or two to see if it's stable. I've only had one (semi major) problem with my server, in that I had problems with it booting after a kernel upgrade, but it turned out to be a problem with fstab. There are a few work arounds for that one too.

---

### Post by Avada Kedavra on 2010-09-23
Hi CharlesA,

Yes, all servers are Dell PowerEdge R710, so they all face the same incompability issue and sometimes, randomly freezes for a few minutes before jumping back into game.

I upgraded to Lucid on the testserver, and everything went really smooth. If it wasn't for the deprication of sun-java6 it would have been completely seamless with a downtime of approximately 15-20 minutes. Java is now in place and everything appears to be running as it should. Cudos to the Ubuntu development team!

Will run the test server for a while to see if the problems dissapears. If so, plan a stop in production while updating the rest of the setup. If not, try a clean install.


Thanks for your input on the subject!
Cheers
/Avada

---

### Post by CharlesA on 2010-09-23
Awesome. Glad it's working for you. 

The only other things I can suggest is that when you are ready to make the jump to Lucid, that you do it one machine at a time. Let the newly upgraded machine run for a week or so, just in case there are any conflicts or something.

It might be a bit of a pain, but that way you won't be putting all yer eggs in one basket.

---

