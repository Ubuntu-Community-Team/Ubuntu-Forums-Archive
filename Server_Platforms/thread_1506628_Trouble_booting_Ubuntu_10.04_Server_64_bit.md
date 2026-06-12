---
title: "Trouble booting Ubuntu 10.04 Server 64 bit"
date: 2010-06-10
forum: Server Platforms
---

### Post by DanV2 on 2010-06-10
So, I've been having a rather strange problem trying to setup Ubuntu Server 10.04.  The research group I am in recently ordered a Dell Precision T7500 workstation.  The specs are 24 GB of ram, 2 Quad Core E5620, and 2 450 GB hard drives in a RAID 0 array.  The system came with Redhat enterprise but we would like to have Ubuntu on it instead.

Now, when I try to install Ubuntu 10.04 Server amd64, the installation works fine.  On rebooting afterwards, however, the system will hang before grub saying "Dell MPT boot rum installed successfully" or something similar.  I am able to install the 10.04 desktop 64 bit and it boots without a problem.  In fact, that is where I am writing this from.

So basically, is there some detail I missed or anything I can do to make this installation work?  Life would be much simpler if there was an easy way to install and boot the server edition.

If you need any more info just let me know.  I am fairly experienced with Ubuntu desktop and know my way around the terminal a bit but may need help with some of the finer details.

Thanks to anyone who can shed light on this conundrum!

Daniel

---

### Post by arrrghhh on 2010-06-10
Did you setup the partitioning/hard drive section the same?  The x64 version does use a different kernel (32-bit & desktop version use the 'generic' kernel, which the x64 server edition uses the 'server' kernel...) so perhaps there is something related to that... but somehow I doubt it.

---

### Post by sanderj on 2010-06-10
1) Can you boot and install an older Ubuntu Server version?

2) Reading [http://www.justlinux.com/forum/archive/index.php/t-109530.html](http://www.justlinux.com/forum/archive/index.php/t-109530.html) , I would try removing one disk to see if that helps.

---

### Post by DanV2 on 2010-06-11
Well, before I try any of the above suggestions, is there any particularly compelling reason for me to install the Server edition instead?  All the computer will really be used for is to SSH into it in order to run CPU intensive chemistry simulations.  I believe that the desktop 64 bit version should be able to accomplish this task for us just the same, shouldn't it?  Is there anything really important or crucial that I will be missing out on by not installing the server edition and instead configuring the desktop version ot suit our needs?

---

### Post by arrrghhh on 2010-06-11
The server version is just stripped.  No GUI, so less overhead.  If you've got the hardware, there's should be issue in running the desktop edition.

---

### Post by NullHead on 2010-06-11
If I recall, the server's kernel is better optimized for throughput and visualization tasks. There *are* differences, but I simply cannot remember them. 

The server version has no GUI, so you get much less overhead ram wise, but considering you've got 24gb of ram, I don't think you'll have much issues running the desktop version. 

I say, if your group runs into resource issues, try to install server edition again and work from there; otherwise the desktop version will be fine.

---

### Post by DanV2 on 2010-06-11
Alright, the network guy is coming buy today to set it up for SSH on the network.  I think desktop will work for now but if we need to change I'll go ahead and try one of the older versions of the server edition.

Thanks for the help guys!

Daniel

---

