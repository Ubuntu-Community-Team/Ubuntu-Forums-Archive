---
title: "install hangs at Booting Linux ..."
date: 2007-08-17
forum: Sun Sparc Users
---

### Post by afinley on 2007-08-17
Hi I'm trying to install ubuntu-7.04-server-sparc on a sun ultra 80 expert 3D.  I load the disk  then stop+a, then choose the Boot install option. The process then hangs on Booting Linux ...

Any ideas? 

Thanks-
Andy

P.S. sorry about my last message (it was lame).

---

### Post by afinley on 2007-08-17
Hi again, I installed Ubuntu 6.06  without a problem. Perhaps I'll try downloading and burning 7.04 again.

---

### Post by lungdart on 2007-08-18
You boot the linux CD and then press stop+a and choose boot install?

Stop+a is generally a bad idea. It is an emergency drop to OBP. The better way to do this would be to boot the system with the CD in the drive, and press stop+n, this will halt the system at the okay prompt at which point you can use the boot cdrom command (or what ever alias your cdrom is) to put the linux disk.

---

### Post by Lord_Vader on 2007-08-21
Not sure if it would help or not, but I had to do ide=nodma at the install prompt before any of them would work. (I never got 7.04 to go so I just stayed with 6.01 )

---

### Post by slemmy on 2007-08-22
i had the same problems with a SUN Ultra 10 with creator 3d gfx. 

solved the problem by removing the gfx card and used the gfx chip on the motherboard instead.

---

### Post by qrwe on 2007-08-23
> **afinley said:**
> Hi again, I installed Ubuntu 6.06  without a problem. Perhaps I'll try downloading and burning 7.04 again.
If this was the simplest solution so far, maybe it's just an Ubuntu 6.06 installation + distribution upgrade that will do the trick?

---

### Post by qrwe on 2007-08-29
[SIZE="3"][FONT="Garamond"]Hmm.. My turn now:
After successfully booting the kernel with 6.06 on a SunFire V100 (7.04 didn't work as mentioned above), this error message pops out:[/FONT][/SIZE]

[FONT="Courier New"][    2.850787] PCI: Address space collision on region 6 [000001ff00080000:000001ff000bffff] of device 0000:00:05.0[/FONT]

[SIZE="3"][FONT="Garamond"]This doesn't tell me much unfortunatly.. Any suggestions what to try?[/FONT][/SIZE]

---

### Post by sys64738 on 2007-11-10
[ 2.850787] PCI: Address space collision on region 6 [000001ff00080000:000001ff000bffff] of device 0000:00:05.0

that is Davicom and it wont work on kernel 2.6.17 and newer.. dunno why

---

### Post by qrwe on 2008-01-08
*Sigh* So Linux failed me on this one.. Well, the first time has to come sooner or later.

---

### Post by switlikbob on 2008-01-08
If you search, this topic has been covered extensively.  I have a Sunblade 100 that exhibited all of the same problems.  WHen you get the memory errors, you need to cold boot the machine, as in, pull the power plug.  Then, do a stop + a.  At the OK prompt, issue this command: boot cdrom
The box will reboot to teh cdrom.  At the boot prompt for SILO, issue this command:
install ide=nodma

That should get your install going.  Things to consider are:

Is your OBP at the latest revision.  Is your video card / adapter and monitor compatible?

---

