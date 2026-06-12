---
title: "I see the beauty of GNU/Linux now"
date: 2013-08-23
forum: The Cafe
---

### Post by Welly Wu on 2013-08-23
I just spend the last hour and fifteen minutes trying to solve a particular problem on a friend's HP desktop PC running Microsoft Windows 7 Home Premium Service Pack 1 64 bit and it still isn't solved. He's got an older Nvidia GeForce GT 220 GPU and I couldn't update to the latest 320.49 WHQL drivers so I mistakenly uninstalled the old drivers. Now, I can't get the old one to re-install correctly. I did a search and it seems like I have to remove a RAM module and boot into safe mode and uninstall all graphics drivers and boot back into regular mode to install the new graphics drivers and then test it if it works. Then, I have to put the RAM module back in to make sure everything works.

This is bs.

I don't get these problems with Ubuntu. Then again, I'm using the open source Intel drivers and everything works perfectly. Ubuntu works just fine as it did before. Ubuntu 12.04.3 LTS 64 bit is particularly stable.

I had another friend who has a retina MacBook Pro and she is having problems updating her Nvidia graphics drivers to the latest version. I finally figured it out where I had to remove the old one and install the new one, but it worked.

I think that given the difficulties with Microsoft Windows, I'm going to stay far away from it as much as possible. It's too painful to get software and device drivers to update correctly without going through major problems.

My first friend has a bunch of outdated device drivers that need to be updated, but nothing is working. I think he has to do a system recovery back to the factory default configuration which means that he'll lose everything because he doesn't backup his data.

My other friend can't re-install Super Anti-Spyware Professional. The installer won't work and his Windows 7 installation is partially corrupted. He has to do a system recovery again for the fourth time in less than 6 months.

These aren't techies that I'm talking about or else they would do it themselves. I thought Windows 7 was supposed to be the greatest operating system that Microsoft ever released, but I guess it isn't.

Ubuntu gives me none of this bs. It just works.

---

### Post by CharlesA on 2013-08-23
If you are having problems running with just the Windows driver (which should be included by default on Win7) and the Nvidia drivers don't want to install, you could have posted what error message you were getting and maybe someone could have helped you. :)

As far as "None of this BS with Ubuntu" - it depends on your hardware. I was trying to help someone who had their graphics majorly messed up after installing the proprietary Nvidia drivers. Everything is working now, but it was a real pain to get it working.

---

### Post by Welly Wu on 2013-08-23
I can't remember now why the Nvidia graphics drivers won't install on his HP desktop PC with the latest WHQL drivers.

When I had my ASUS N61JV-X2 notebook PC, installing Nvidia device drivers was simple. Getting Nvidia Optimus to work was another story, but the Nvidia graphics drivers weren't a problem for me back then.

GNU/Linux and Nvidia Optimus technology is going to get tepid support in Ubuntu 13.10 this October 2013. It should work with the latest Mesa, Nvidia, Linux kernel, and RandR software right out of the box with the XMir display server. I expect Ubuntu 14.04 LTS to support Nvidia Optimus technology very robustly as more work will be accomplished to get it to work smoothly and seamlessly like on Microsoft Windows 7 and 8 PCs right now. It took many years, but we're getting there for Ubuntu users.

I had a chance to play with the latest System76 Bonobo Extreme and the Nvidia graphics drivers installed flawlessly. Updating them to the latest WHQL drivers was a simple task and it worked perfectly. Of course, the Intel integrated GPU is disabled, but the Nvidia proprietary drivers do work right out of the box.

I think I may have overstated my case a bit, but the fact is that my friend Vincent's HP desktop PC don't work properly and I can't re-install any Nvidia graphics drivers now. I think he'll have to do a system recovery.

---

### Post by Mariane on 2013-08-24
When someone asks me for help with their windows computer, I always have a Ubuntu disk in my pocket :). 

Once even that didn't work: the hard disk was not detected. I asked permission to open the laptop. The hard disk had moved in it's casing and gently pressing upon it fixed the laptop. My friend told me the guy at the repair shop had told her it would be very expensive to fix this computer and had advised her to buy a new one, offering their services for data retrieval and data transfer to the new machine...

---

### Post by kevdog on 2013-08-24
I kind of laugh at this post.  Depending on your hardware, linux video drivers can be very easy or very much a pain install in Linux.  Nvidia and Catalyst drivers can be very easy or just a stinkin' pain in the butt.  I'd encourage you to go find a bunch a different computers with different hardware and then come back to me about graphic installs on Linux.  I'm not bashing Linux or waving the flag for windows -- hardware makes a big difference no matter what the OS is.

---

