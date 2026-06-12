---
title: "Install Problem - udevd timeout killing..."
date: 2012-08-03
forum: Ubuntu Studio
---

### Post by AlexBW on 2012-08-03
I have tried googling for my problem and there seems to be hundreds of guys having the same problem as I am ! Ironically, none of them have been resolved and a few that have been resolved were to do with the HDDs. So, here is the synopsis.

Latest version of Ubuntustudio downloaded  (12.04-amd64 torrent version), burned to a DVD-RW and booting off. Past the boot menu and all I get is screen blanking which looks like fb or nouveau being initialized but failing. So, I wait for a few long seconds and then frantically hit Ctrl+Alt+Fn keys which doesn't help but, hitting Ctrl+C on the first console stops the flickering and I can seen some output now. Switching to console 7 works now and I can see the Ubuntu splash screen with that spinning wheel animation. Hitting Esc takes me to the text mode with all the boot messages. Then I see the following lines scrolling eternally.

> (Initramfs) udevd [94]: timeout '/sbin/blkid-o udev-p /dev/sda' 
#######Several Similar lines about /dev/sda# here####

udevd [94]: timeout: killing '/sbin/blkid-o udev-p /dev/sda' [144]

#######Several Similar lines about /dev/sda# here#### 
udevd [94]: '/sbin/blkid-o udev-p /dev/sda' [144] terminated by signal 9 (Killed)
There's nothing I can do once the above messages start scrolling. I don't even get a command prompt. 
I have tried waiting for as long as 15 minutes but no joy. The only way out is Ctrl+Alt+Del and sometime 
even that doesn't work forcing me to use Alt+SysRq shortcuts.

Thinking it might be a corrupt iso image, I downloaded another from the direct link which 
produced exact same results. Tried with 32 bits, even worser ! Stuck at the screen flickering, doesn't 
respond to the keyboard and a hard reset is the only way out !

Before someone tells me that it might be a problem with the hard disk, let me tell you
that SMART diags come out clean on all the HDDs (there's 3 of them). No corrupt partitions, boot sectors and such things.

I am long term linux user (since early 90's) and currently have BLFS, Exherbo, Funtoo   and OpenSuse installed. None exhibit such behaviour. I keep trying different linux distros and never 
faced such a problem. And unforuately do not have the time to troubleshoot this.

It is a pity that 100's have experienced this issue and there're no answers or work arounds. Said that, I'm gonna try 
some boot options to see if that makes it tick !

Hope someone is going to help with this pissy problem I'm having.

Cheers !

---

### Post by AlexBW on 2012-08-03
Haha ! Setting the nomodeselect did the trick or at least that's what I think !

Apparently the problem with the HDDs is a bit random as every second or third boot 
It picks a different drive to fight with. 

This time around it had problems with sdb and sdc. Took a long time though.
Seems like KMS and udevd were making the system non-responsive. Getting KMS out of the way seemed to
have made it work by cutting away the delay.

I intend to install it to the hard drive and upgrade the kernel or at least recompile it as 
I believe it must be the kernel config that is screwing up things for me. May be I should upgrade udev too.

I would come back and add to this thread but, it'll be a while before I'd have to time to install it to the HDD.

---

### Post by AlexBW on 2012-08-06
Duh ! The quickest way I could get it to installed was to take the two HDDs that were troubling me offline ! 

I have it installed now and I'm able to boot it with the two disks back online. So looks like the install system got some weird way of doing things or is broken... ?

---

