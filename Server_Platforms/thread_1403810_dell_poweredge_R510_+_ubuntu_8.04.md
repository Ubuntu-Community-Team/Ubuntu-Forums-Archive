---
title: "dell poweredge R510 + ubuntu 8.04"
date: 2010-02-10
forum: Server Platforms
---

### Post by _fool on 2010-02-10
Hi folks,

is anyone using ubuntu 8.04 on the new dell poweredge R510 machines yet?  I have been unable to get the installer to recognize the CDROM drive--it boots from it but linux does not see it.

9.10 works fine, but this is a server we'd like LTS on and need up and running before April.

I'll be happy to harvest dmesg output (no mentione of the string 'hd' at all) and such if it would be of use to someone.

thanks!

---

### Post by dwarfimandel on 2010-04-02
Hi _fool , 
 
 
I have the same question , my mother's an ophtalmologist and the OS she required to work with her associate is Ubuntu Hardy Heron (8.04)
 
I thought Poweredge R510 looked perfect for her job with a solid architecture BUT is that system , are the components compliant with UBUNTU Hardy Heron ?
 
What do you advice me in terms of hardawre to get the most compliant system with Ubuntu ?
 
 
Thank you for your help !!
 
Raph

---

### Post by fang0654 on 2010-04-02
I've successfully installed it on the R510.  You need to create a bootable USB Flash drive from the Ubuntu Server .iso.  (I used unetbootin, very easy to do).

You will probably also run into trouble with the onboard NICs.  If you do, let me know, and I'll post how I got those to work (without downloading a new driver).

---

### Post by markpatella on 2010-04-09
Hi fang0654,

i would be very happy if you could post your solution for installing on the R510 including network drivers!

thanks a lot!

mark

---

### Post by fang0654 on 2010-04-09
Glad to!

As stated earlier, using unetbootin (which can be installed via synaptic), create a bootable USB with the 8.04.4 ISO.  Booting from USB you should be able to install fine.  After you are into your system, follow the directions here:

[http://blog.akkaya.de/jpabel/2010/01/22/NetXtreme-II-BCM5716-on-Ubuntu-8-04]("http://blog.akkaya.de/jpabel/2010/01/22/NetXtreme-II-BCM5716-on-Ubuntu-8-04")

You'll need to download the files it states in advance and put them on a flash drive, but other than that it is straight forward.

If anything still isn't working, let me know.  I'm calling this back from memory, so I may have left something out.

---

### Post by markpatella on 2010-04-14
Thanks for your answer!

But i still have a problem, when i try to install with an unetbootin-USB-Drive it says that it can't detect a cdrom and installation fails. Any suggestions for that?

mark

---

### Post by filgy on 2010-08-10
I am confirming this issue as well.

Booting from a usb stick does not make any difference. 
I even tried booting from the network w/ PXE and it complained about the NIC drivers.

We tried doing this with the alternate as well as server x64 .iso's.
It appears there is a problem with one of the hardware modules that is loaded at install or something.

Is there a bug report for this?

---

### Post by bnagy on 2010-09-30
Same problem as [markpatella]("http://ubuntuforums.org/member.php?u=1051170") and [filgy]("http://ubuntuforums.org/member.php?u=889953") here - cdrom/dvd boot results in an error of being unable to see the cdrom. USB boot has the same exact problem, despite not coming from the optical drive - it's asking for a cdrom driver and refusing to take no for an answer. I've got the usb drive showing up in dmesg as /dev/sda1 and can mount it just fine, but not nor specify that device in place of the cdrom. Nor does the installer seem to offer a away around requiring the cdrom and just pointing it to the file path.

PXE boot works, but then as expected above, complains of network not being present and being unable to access a mirror (running on an isolated network). My next step on that road would seem to be to try to set up an apt-mirror on the pxe boot machine, but that will take a while to sync up, and I am so close on the usb side.

[fang0654]("http://ubuntuforums.org/member.php?u=254411"), how exactly did you get the usb install to work without running into the cdrom trouble?

---

### Post by bnagy on 2010-09-30
Fixed the problem with using unetbootin - needed to be sure and select  the hd-image option for 8.04. However, now I'm stuck at the PERC H700's  virtual drives not being seen by the installer - just my usb key. 
  
  Found this bug listed in hardy heron: [https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/611844](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/611844)
  
  Tried Michael Jeanson's initrd.gz file in place under the latest PXE netboot, but that froze the netboot screen at keyboard selection. 

Fang, did you have to solve this problem, or did you not have an H700-family card to deal with?

Alternately, any pointers to produce an installer with the mpt2sas drivers built in? Or preferably that someone working on LTS might be able to get mpt2sas built into a 8.04.5 point release?

Oh wait. I see here: [https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)  that "Point releases [for 8.04] will cease once Ubuntu 10.04 is released. " Blast. 

Any suggestions for next steps?

---

### Post by Courser on 2011-04-05
Seems as if this thread has died out with no real solution. I have a new R510 that I need to restore an ubuntu 8.04 image on. My intention was to install 8.04.4 from cd/usb and then overwrite with the backup files. Having all the NIC and CDROM issues mentioned above when I try to install .  Tried all the solutions.  Nada!

Was able to install 10.04 with a USB Drive with no problems.  Created a USB with 8.04 using Unetbootin, same issues.

Any fix for this yet without full blown upgrade of the original server?

Courser

---

### Post by fang0654 on 2011-04-05
I apologize for not responding sooner.  I didn't have a PERC in the server I was using (I set it up with a software raid), and I didn't run into any issues installing from Unetbootin - installing the server ISO, not a network install.

The problem with the NIC was just that it was newer than the kernel that ships with the installer.  The drivers in place work for it, but don't recognize it, hence recompiling the driver in the blog earlier.  For getting the controller to work, you may need to compile the kernel driver on another machine, and manually modprobe it during install.

Another possibility would be to take a fully functioning (and updated) 8.04 machine, and make a bootable image out of it using Remastersys.

Unfortunately, that was the only box I ran into that on, and any servers I set up now I through 10.04 on, so I don't have any additional experience.

---

