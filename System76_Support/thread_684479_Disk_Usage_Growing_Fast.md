---
title: "Disk Usage Growing Fast"
date: 2008-02-01
forum: System76 Support
---

### Post by DomIncollingo on 2008-02-01
Hi,

I have a problem similar to one reported in another thread.  I have a desktop computer with a 220+ GB hard drive that is running Feisty Fawn.  (It's not a System 76, but I was hoping I could ask here anyway.)  Up until 2 weeks ago, Nautilus showed about 160 GB of free space.  A few hours ago, it was showing 100 GB of free space.  

I ran cd /, and then sudo du -h --max-depth=1.  The du command showed that only a  total of 26G was being used.  The commmand df showed that over 110GB was being used on /dev/sda1, and that /dev/sda1 was using 51% of the total available space.  There's quite a difference between the 26GB usage reported by du and the 110GB usage reported by the df command! 

As the last resort, I rebooted the computer.  After the reboot,  sudo du -h --max-depth=1 still shows 26G being used.  But the command df shows that /dev/sda1 is using only 43GB or 20% of available space on /dev/sda1!  Nautilus shows that there are 167GB of free space.

Any ideas on how rebooting freed up so much space?  I'm worried that something is rapidly eating up space while the system is running, and that the du command is not even reporting the files / directories that are consuming this space.

Thanks very much.

Dom

---

