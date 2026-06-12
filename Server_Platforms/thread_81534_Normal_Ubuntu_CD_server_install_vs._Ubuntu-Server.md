---
title: "Normal Ubuntu CD server install vs. Ubuntu-Server"
date: 2005-10-24
forum: Server Platforms
---

### Post by matthurne on 2005-10-24
Hey all, I was just wondering - is installing from the normal Ubuntu CD with the "server" option equivalent to installing directly from the Ubuntu-Server CD?  If not, what differences are there, and are they major?

Because of the i2o bug, I had to install Hoary "server" and am now using apt to upgrade to Breezy, so I can hack the modules to work around that problem.

So - should I bother downloading Ubuntu-Server and trying to hack an install (I think I could try switching to the second vc halfway through running the installer, move out the i2o modules and modprobe dpt_i2o, and in theory that would work - too bad I didn't think of that before) - or should everything end up the same as the way I have done it up to this point?

Thanks folks.

---

### Post by mcking on 2005-10-27
I would also like to know if there are any differences between the two.  I just finished an install off of  the "desktop" breezy cd using the "server" option at the boot prompt.  I didn't even realize that there was a separate "server" install cd until a while later.

---

### Post by hostile on 2005-10-31
:confused: 

I'm curious about this one myself before I waste the b/w on downloading two identical items...

---

### Post by TomB on 2005-11-01
The Ubuntu Server CD installs more server related packages than the server install in the normal cd

---

### Post by hostile on 2005-11-01
[QUOTE=TomB]The Ubuntu Server CD installs more server related packages than the server install in the normal cd[/QUOTE]


Do you know what sorts of packages? I have been unable to find any documentation on the differences...

---

### Post by steffen on 2005-11-01
At least Apache2, postfix, MySQL and PHP, if I remember correctly from the release announcement.

---

### Post by hostile on 2005-11-01
[quote=steffen]At least Apache2, postfix, MySQL and PHP, if I remember correctly from the release announcement.[/quote]

Ah. In other words, it just installs more daemons OOTB. 

So then, I'm guessing the "Server" install w/ the regular CD is a more lean install?

---

### Post by steffen on 2005-11-01
[QUOTE=hostile]Ah. In other words, it just installs more daemons OOTB. 

So then, I'm guessing the "Server" install w/ the regular CD is a more lean install?[/QUOTE]

Yep - no GUI, but an array of server specific software. Here's the announcement: [http://lwn.net/Articles/156309/](http://lwn.net/Articles/156309/)

---

### Post by Tails on 2005-11-01
[QUOTE=TomB]The Ubuntu Server CD installs more server related packages than the server install in the normal cd[/QUOTE]

well, they dun install by default still, but they do have server related packages **included** in the CD, so, when ur interenet and need to reinnstall, u can fetch those packages from the CD rather than internet like the normal CD...

---

### Post by Z3K3 on 2005-11-04
Regarding the i2o bug, I'm having similar issues with a Adaptec ZCR card, I've installed Hoary (2.6.10-386) and have been able to run the system with kernels (2.6.11-686-smp) for large memory and multi-processor.  Anything above that and I get an array of kernel panics.

I believe the panics are caused by the i2o bug you speak of, is there some reference to this "bug"?  From what I can tell the issue that I have is that somewhere from 2.6.11 to 2.6.12+ it either tries to load both dpt_i2o and i2o_block and this borks? or it just switches over to i2o_block, and as the device paths change, it borks on reboot (/dev/sda1 = /dev/i2o/hda1).

I'm currently compiling a 2.6.14 kernel with dpt_i2o disabled

"
Don't i need SCSI_DPT_I2O (dpt_i2o) driver?

The dpt_i2o driver is supported by Adaptec itself, and don't use the I2O subsystem in Linux. It uses the SCSI subsystem and "simulates" an SCSI host adapter. You can only use the I2O subsystem OR the dpt_i2o driver, not both at the same time.)
"

...and i2o (_block/_config/_etc) compiled in (not modules).  I'm going to change my fstab to point to the new device paths as per the i2o FAQ's:  

If this doesn't work, I guess I will try to do the following fix and try using dpt_i2o only?

Hack: Remove /lib/modules/2.6.12-9-686-smp/kernel/drivers/message/i2o out of the modules tree (recompile).

Will post results.

---

### Post by matthurne on 2005-11-04
The bug is documented on Ubuntu's Buzilla:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17897](http://bugzilla.ubuntu.com/show_bug.cgi?id=17897)
[http://bugzilla.ubuntu.com/show_bug.cgi?id=16011](http://bugzilla.ubuntu.com/show_bug.cgi?id=16011)

As far as I can tell from reading up in the above bugzilla pages, the problem is indeed that Breezy tries to load both i2o and dpt_i2o.

If you're going to recompile, I would do so with dpt_i2o and drop i2o - but that's just me and I only say so because the following workaround from one of the bugzilla pages worked for me (which doesn't require recompiling anything):

> 
OK - hotplug didn't exit under 2.6.12-9-686-smp, but booting into the
2.6.10-5-686-smp kernel from Hoary was fine.

I then completely removed the I2O subsystem by moving
/lib/modules/2.6.12-9-686-smp/kernel/drivers/message/i2o out of the modules tree
and reran depmod for that version.

Rebooting into 2.6.12-9-686-smp then finally worked!


I'm pretty sure there's a description of this same method somewhere here on the forums as well.  But it only works if you're willing to install Hoary, upgrade to Breezy - the Breezy installer chokes and there's no way around that.

I don't see why you'd really need to recompile - modules are the preferred way of using most device drivers anyway, and removing the modules from the modules tree has essentially the same effect as recompiling the kernel with the i2o subsystem not compiled.  Same difference, but extra work.

---

### Post by Z3K3 on 2005-11-06
well custom compiling removing dpt_i2o and strictly using i2o did not work, it kernel panic again.  Since im on day 3 of hacking this I've done the i2o remove hack as you suggested, and as suggested in the forums previously and it has worked flawlessly, its nice to be running a current kernel.

Thanks for all the help.

---

### Post by matthurne on 2005-11-07
[QUOTE=Z3K3]
Thanks for all the help.
[/QUOTE]

No problem - wish its something I could have figured out on my own.  But I'm glad someone figured it out and I was more than happy to pass it on.

---

