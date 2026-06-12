---
title: "Install problems on HP DL380 G3"
date: 2008-11-15
forum: Server Platforms
---

### Post by fezzasus on 2008-11-15
Hello all

I've finally managed to install Ubuntu server edition (8.10) on my HP dl380 G3 and it simply wont boot, it gets through the install fine, gets to booting from the hard drive and just hangs.

I've read a few about a few other people with similar problems but haven't ever seen a clear solution - especially important as this is my first (proper) experience with ubuntu.

Any ideas?

---

### Post by elaar on 2008-11-15
I'm with you on this one, same hardware, same problem.
Mine stalls for about 5mins on boot and reports "Unable to set system clock to.." and then stalls indefinitely on "loop: module loaded".

I've tried various bios configurations without success.

I find it hard to believe that a server version of ubuntu fails to work properly on one of the most widespread and popular servers ever made.

elaar

---

### Post by Philio on 2008-11-15
Isn't the DL380 basically a 2U DL360?

I have several DL360's running Ubuntu with no issues... Very strange...

---

### Post by fezzasus on 2008-11-16
> **Philio said:**
> Isn't the DL380 basically a 2U DL360?

I have several DL360's running Ubuntu with no issues... Very strange...

That's right, they are essentially the same. The only difference is the backplane (for obvious hight reasons) but that shouldn't be the difference between working and being unable to boot.

---

### Post by Philio on 2008-11-16
> **fezzasus said:**
> That's right, they are essentially the same. The only difference is the backplane (for obvious hight reasons) but that shouldn't be the difference between working and being unable to boot.

Is the issue specific to 8.10?
My DL360's were originally running 8.04 and upgraded.

---

### Post by fezzasus on 2008-11-16
> **Philio said:**
> Is the issue specific to 8.10?
My DL360's were originally running 8.04 and upgraded.


I'm not sure, I haven't tried installing 8.04. I'll give it a go. However my feeling is that since it's hanging at attempting to boot from the HD, it's a much more fundamental problem than the small changes between 8.04 and 8.10

---

### Post by Philio on 2008-11-16
> **fezzasus said:**
> I'm not sure, I haven't tried installing 8.04. I'll give it a go. However my feeling is that since it's hanging at attempting to boot from the HD, it's a much more fundamental problem than the small changes between 8.04 and 8.10

Had a quick look at the specs of both they look identical, except for the obvious size difference.

Are you using the Smart Array controller?

---

### Post by fezzasus on 2008-11-16
> **Philio said:**
> Are you using the Smart Array controller?

Yes,

Haven't had a chance to try 8.04 yet - will do hopefully tonight or tomorrow morning.

---

### Post by Philio on 2008-11-16
> **fezzasus said:**
> Yes,

Haven't had a chance to try 8.04 yet - will do hopefully tonight or tomorrow morning.

Be interesting to see if it works, I've got a couple of DL360's here that don't have OS installed yet if it does turn out to be an 8.10 specific issue will have to install via the upgrade route myself. Hope it works for you!

---

### Post by ww4nc on 2008-12-01
Have any of you come up with any solutions to installing Ubuntu 8.10 on the DL380 G3?

I get all the way through the install, it reboots, and then just stops, with a blinking cursor.

Any help would be appreciated, as I am a new Linux user.

thanks,

---

### Post by raist8 on 2008-12-02
Same for me,

Any solution. Is this a Ubuntu 8.10 bug?
My server: DL380 G5

---

### Post by w9caf on 2008-12-06
It does seem to be a problem 8.10.
I have the same hardware and problem with 8.10. I spent many days trying to install different ways. Even tried OS type = other. All hung at loading hard drive (C). It would not load Grub.
I found this thread, read through and downloaded 8.04. Worked like a charm. I have no idea what changed from 8.04 to 8.10. I have yet to do the upgrade to 8.10. I doubt that it will be a problem.

Update:
I did the upgrade to 8.10, described here [http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server]("http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server"), and found that on reboot, the system would not fully come up. I got two errors. The first was /sbin/modprobe abnormal exit. The second was cannot access hardware clock via any known method. After that it hangs. I can do Ctrl-Alt-Del and it goes through the shutdown process.
As 8.04 is Long Term Release, I will stick with that for now.

---

### Post by Styles on 2008-12-11
Hey I'm having the same issue as well, I wish I found this thread first before I wasted all that time. Blah!!!!!

Cheers

---

### Post by theprinterguy on 2008-12-18
hello,

i just came into ownership of a DL380 G2. like most i don't want to install windows 2003 as i know it will be a massive hog on resources. i don't know much about Linux other then playing around with them here and there. like everyone before me in this thread i cant seem to boot 8.10 for the life of me after install. 

ive tried different raid configs, updating controllers/bios firmwares to no change. has anyone had a break through? also if not, where can i find the next version of ubuntu that works with this?

---

### Post by Ferret-Simpson on 2008-12-20
Heh. My post (15th time now?) Whould be made a sticky. There is a bug in Intrepid. HARDY IS FINE ON THESE MACHINES, INTREPID WILL NOT BOOT.

I'm the DL360 king. :D

---

### Post by Ferran Espigares on 2009-03-16
From personal experience from a recent install I did of Intrepid 8.10 on a DL380G3, there seems to be a few problems:

1.- The install script apparently didn't succeeded installing grub (although no error message is shown). This could be easily solved by rebooting from the install Cd on "rescue mode" and reinstalling grub (there's a dedicated option for it on the rescue menu).
2.- Some of the modules loaded by default by the standard kernel seg-fault on this hardware, specifically: "scb2_flash" and "cpqphp". They can be added to the blacklist on /etc/modprobe.d/blacklist and the system appears to boot normally. In order to add them to the blacklist you could as well use the "rescue mode" of the install Cd and launch a shell on the appropriate root partition.

So far it seems to work well (just installed, will report any further problems if any). ;)

I have yet to update the kernel to the last version to find out if any of the modules are updated/fixed and no longer crash.

Cheers.
Ferran.

---

### Post by tomcat2007 on 2009-04-04
> **w9caf said:**
> It does seem to be a problem 8.10.

<...>

I found this thread, read through and downloaded 8.04. Worked like a charm. I have no idea what changed from 8.04 to 8.10.


I'm running into the same problem, just got past the ACPI issue by setting the ACPI=OFF boot option to have it lock up again... only have an hour or so invested in the effort so it's not a big loss... I'm just wondering if I should install Hardy since folks here report it works or if it is worth the time to try Jaunty's present beta.  Anyone else tried it?

---

### Post by VoodooLoveDog on 2009-04-08
I'm having the same problem with 8.10. The install will get all the way through and then on reboot, GRUB will not load. Hangs on Attempting Hard Drive (C:). 

From some suggestions I've found, I'm trying 8.04.2 SE on the machine. As of writing this, the install is hanging on Scanning the Mirror... @28% done. :(

---

### Post by cphjst on 2009-04-16
Have just followed Ferran Espigares describtion step 2, and it works.

I have now dowload Ubuntu 9.04 (Jaunty Jackalope) Release Candidate, and it looks very fine.

---

### Post by gurpal2000 on 2009-09-10
> **cphjst said:**
> Have just followed Ferran Espigares describtion step 2, and it works.

I have now dowload Ubuntu 9.04 (Jaunty Jackalope) Release Candidate, and it looks very fine.

Hi could you be a little more specific please. I am trying to install 9.04 on a DL360 G3 (similar to DL380). Also were you able to make it less noisy :-)

---

