---
title: "illegal instruction, ultra 2"
date: 2007-02-14
forum: Sun Sparc Users
---

### Post by virtualtoaster on 2007-02-14
hey everyone.. im not very proficient with *nix, but i know my way around a little, and im not a total idiot.. anyhow..

i recently got 2 sun ultra enterprise 2 servers, both with 296mhz processors and a lot of ram. i installed many versions of solaris and i didnt like them very much.. way too many hoops to jump through and not a lot of benefits...

so i dled ubuntu for sparc, 6.10 and 6.06.1 server version.. i burned the iso on my mac mini, both versions.. when i ok boot cdrom on either, it gives me the standard install or rescue, no matter which i choose, it goes thru a few motions, allocates 8 megs of ram to the kernel, and then it freaks out, gives me an illegal instruction, and returns to the ok prompt...

help!  i dont know what could be causing this, or what to do about it.. im sitting in class now typing this, but i can get you specific information on what happens when it gives the illegal instruction message..

THANKS
-merritt

---

### Post by adza on 2007-03-11
i was hoping for an answer here... my ultra 60 is doing the same thing.... i have installed solaris 10 on it no probs.. do i have to format that disk before installing ubuntu? or would the ubuntu install hose this for me?

---

### Post by todd_p_3 on 2007-04-10
> **virtualtoaster said:**
> hey everyone.. im not very proficient with *nix, but i know my way around a little, and im not a total idiot.. anyhow..

i recently got 2 sun ultra enterprise 2 servers, both with 296mhz processors and a lot of ram. i installed many versions of solaris and i didnt like them very much.. way too many hoops to jump through and not a lot of benefits...

so i dled ubuntu for sparc, 6.10 and 6.06.1 server version.. i burned the iso on my mac mini, both versions.. when i ok boot cdrom on either, it gives me the standard install or rescue, no matter which i choose, it goes thru a few motions, allocates 8 megs of ram to the kernel, and then it freaks out, gives me an illegal instruction, and returns to the ok prompt...

help!  i dont know what could be causing this, or what to do about it.. im sitting in class now typing this, but i can get you specific information on what happens when it gives the illegal instruction message..

THANKS
-merritt

I may be an idiot, but I have the same problem.  same system dual 296 mhz ultra2 384Mb Ram, creator graphics, cd drive, floppy...same error message....but I gave up and put Solaris 10 on it and stowed it in my garage until I gather enough info to try again.

---

### Post by RJARRRPCGP on 2007-04-10
> **virtualtoaster said:**
> hey everyone.. im not very proficient with *nix, but i know my way around a little, and im not a total idiot.. anyhow..

i recently got 2 sun ultra enterprise 2 servers, both with 296mhz processors and a lot of ram. i installed many versions of solaris and i didnt like them very much.. way too many hoops to jump through and not a lot of benefits...

so i dled ubuntu for sparc, 6.10 and 6.06.1 server version.. i burned the iso on my mac mini, both versions.. when i ok boot cdrom on either, it gives me the standard install or rescue, no matter which i choose, it goes thru a few motions, allocates 8 megs of ram to the kernel, and then it freaks out, gives me an illegal instruction, and returns to the ok prompt...

help!  i dont know what could be causing this, or what to do about it.. im sitting in class now typing this, but i can get you specific information on what happens when it gives the illegal instruction message..

THANKS
-merritt

The processor being overclocked too much or not enough Vcore is a likely cause. Can you even overclock those at all? 
I dunno about non-x86 processors.

If you are, lower the frequency and/or increase the Vcore and try again.

---

### Post by adza on 2007-04-14
hi everyone, i'm back from a holiday and have finally had time to check this out some more... i resolved this issue by performing a cold boot (turn off box, disconnect power supply for 30 secs), then when rebooting issue the stop command (with my setup it was CTRL + Break) as soon as possible on restart. Then at the ok> prompt, type boot cdrom.. all went well... I'm using 6.10 SPARC server, on a sun ultra 60 machine, dual 360Mhz, 2GB ram and 1 * 9GB SCSI HDD.... hope this helps!

---

### Post by virtualtoaster on 2007-04-27
the solution for me was to install it on my other machine then swap drives.. however this wasnt good enough.. i found that setting the extended diagnostics switch to false (diag-switch) did it for me. somehow i turned it on  on one machine when i first got the servers, and it caused boots to take about 20 minutes before id get the ok prompt.. this was ONLY on hard restarts, not soft restarts...

ymmv

anyone got gnome or another desktop running on an ultra2 yet? my web server is happily running on the server edition with good uptime, and i do have webmin installed. i would like to get a desktop on the machine i want to use as a router to ease configuration (hey, im not THAT great).. now if only i had a better upstream connection.. sigh

---

### Post by wsanders1 on 2007-06-06
Meh, 7.04 broken with illegal instruction on ramdisk load for me too. Ultra 60 with 2xUltrasparc II, Creator3D Series 3 FFB2+.

Same with 6.06.

Could this be an Ultrasparc III only build?

---

### Post by westfall@computer.org on 2007-09-07
I had this same problem.  By accident I discovered that it was my floppy drive cuasing the issue.  I disconnected the floppy drive in my Ultra 60 and the CD  booted with out issue.

---

### Post by CK0y0TE on 2007-12-20
Well I had some problems booting off CD's gentoo/ubuntu for sparc. It may be a different problem then yout all having... 

however I once red, and it did work for me, that you have to power-off first, then power-on again an boot from CD. 

I forgot the exact reason, but if i find it i'll post it back here. Obvisously my problem was the Ultra 10 did'nt boot after "ok reset" or anny forced break to OK prompt and boot from CD afterwards.

One more tip, if you happen to have a scsi DVD-rom (I ripped it from an obsolete 4500 and put it in a spare Sun disk unit) upgrade your DVDRom firmware to version f <something, just get the latest by googling around with whatever markings is on the ROM drive > , upgrade to latest openboot release and you can boot from DVD. This worked for me on Ultra Spark  5,10,60,250,450.

I just hope this is relevant, it took me some time to find out myself so I am eager to share.

cheers

---

### Post by Fink on 2007-12-20
> **virtualtoaster said:**
> the solution for me was to install it on my other machine then swap drives.. however this wasnt good enough.. i found that setting the extended diagnostics switch to false (diag-switch) did it for me. somehow i turned it on  on one machine when i first got the servers, and it caused boots to take about 20 minutes before id get the ok prompt.. this was ONLY on hard restarts, not soft restarts...

ymmv

anyone got gnome or another desktop running on an ultra2 yet? my web server is happily running on the server edition with good uptime, and i do have webmin installed. i would like to get a desktop on the machine i want to use as a router to ease configuration (hey, im not THAT great).. now if only i had a better upstream connection.. sigh

I konw my connection is rather poor and doesn't work really well

---

