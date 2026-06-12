---
title: "Porting a Guest to Host"
date: 2009-04-15
forum: Virtualisation
---

### Post by BobLand on 2009-04-15
I was wondering if I installed an OS in VB, got it tuned up then decided I'd like to use it in the host system, if it would be possible to port it bit for bit into the host as a "regular" OS.

Is this possible?

Thanks,
bobland

---

### Post by Cybie257 on 2009-04-16
It all depends. What are you trying to move over? Windows? Linux?

I have successfully restored a VM of windows with Acronis True Image Home V11 back to the Physical machine at work. 

The Story: I imported a physical machine with VMWare Workstation to do some testing. About 2 months later, the hard drive on the physical machine fried itself. Since it had an old program that runs software for our an archaic phone system, finding the software to re-install it to a fresh install of Windows (on the new hard drive), I attempted to Back up the OS within the VM with True Image. I them restored the backup from the VM into the new hard drive/physical machine. To my surprise, it worked. After a bit of driver reconfiguration (one of MS's best parts of XP), the only thing that was needed was re-activation due to the extreme hardware changes. It worked! :) 

For Linux, you can likely do it up with this method:

 [http://ubuntuforums.org/showthread.php?t=35087&highlight=bare+metal+backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=bare+metal+backup)

Haven't tried it, but don't see why it wouldn't work. Yeah, most would say just start from a fresh install, but if you are like me and have installed all sorts of software(s), then going through and re-installing it all would take forever. 

This method would require a fresh install of the OS, but when restoring the data as the 'howto' explains, everything would be restored to where you had it. 

Hope this helps...

-Cybie

---

### Post by BobLand on 2009-04-17
That link helped alot.  I was thinking of trying Arch and if I liked it I'd like to port it over to a hard disk. I have XP running in VirtualBox so I can watch Netflix but have no intention of moving it.


Thanks,
bobland

---

