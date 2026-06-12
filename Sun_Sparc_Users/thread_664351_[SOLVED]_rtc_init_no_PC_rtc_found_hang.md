---
title: "[SOLVED] rtc_init: no PC rtc found hang"
date: 2008-01-11
forum: Sun Sparc Users
---

### Post by adza on 2008-01-11
Hi there, i've just installed a new (secondary) HDD for my ultra60 server running 6.06. Now when i reboot it is hanging at rtc_init: no PC rtc found??? Has anyone experienced this sort of thing before, it never used to hang here... it's starting the boot process so i summise that it's still booting off the right disk.. why would this second disk be causing this now? any help would be appreciated :) **Edit** I'll try to elaborate further here, what i need to try to figure out is how to add this second drive properly i guess, i can remove this drive from the system and then restart the machine without incident, it comes right up (right past the no PC rtc found error message...)... my other scenario could be that the (new) drive is set to master, but there doesn't seem to be any markings on the drive to indicate what the slave settings are for the drive... do scsi drives have the same master/slave jumper configurations as IDE? anyway, hoping for a response here - cos i'm stuck...

---

### Post by netztier on 2008-01-11
> **adza said:**
> my other scenario could be that the (new) drive is set to master, but there doesn't seem to be any markings on the drive to indicate what the slave settings are for the drive... do scsi drives have the same master/slave jumper configurations as IDE? anyway, hoping for a response here - cos i'm stuck...

Master/Slave concepts don't exist fo SCSI. Each SCSI device on the bus needs to have a unique ID from 0 to 6 or 8 to 15, where ID7 is the SCSI controller in most setups. Normally, you would set the SCSI ID with a DIP switch or jumpers before attaching the device to the flat ribbon cable.

Sun Ultras of this generation however have disks with 80pin SCA connectors, and with these, it is the slot number that determines the SCSI ID; so the two slots you have inside your U60 are always ID 0 and ID1.

And you are certain that the Box actually hangs at this stage? I remember seeing the rtc message linger around for quite  a while before it would go away and the boot process would finish normally.

regards

Marc

---

### Post by adza on 2008-01-11
Hi Marc, perhaps 'hang' is the wrong word, 'crash' is probably more appropriate. It will appear to stall for about 5 minutes or so before it drops out into the ash shell with the message 'can't open tty0'. I've attached the only thing that looks like a jumper diagram on the drive i got (ebay!), also attached the output of probe-scs-all from the <ok> prompt, it appears to be detecting the drive correctly... Is the 'target' number the id you've mentioned or the 'unit' number the id? Should they all be unit 0?. there doesn't seem to be too much documentation on this around, another joy of sun architecture i guess...   thanks for you help :)

---

### Post by adza on 2008-01-11
Finally - success!!! Thanks for your help Marc, you really got me pointed in the right direction, along with [this post]("http://forums.devshed.com/unix-help-35/need-assistance-with-sun-ultra-60t-160671.html") i figured out how to address the drive properly. I can safely say with experience now, the more these things frustrate you - the greater the satisfaction of figuring it out... thanks again man :)

---

