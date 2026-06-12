---
title: "Need truth: How to install RAID"
date: 2005-02-15
forum: Server Platforms
---

### Post by Rottweiler on 2005-02-15
I read with interest this thread which says you need a custom kernel for RAID, blah, blah, blah:
      
      [http://ubuntuforums.org/showthread.php?t=7293&highlight=raid+kernel]("http://showthread.php?t=7293&highlight=raid+kernel")
     
 So I filed a bug report asking for a RAID-enabled kernel, but the developer says that thread is hogwash and RAID is already well supported:
     
     [https://bugzilla.ubuntu.com/show_bug.cgi?id=5655]("https://bugzilla.ubuntu.com/show_bug.cgi?id=5655")
     
     But the installer says bluntly "it won't boot" if you put /boot or / (root) in a RAID device.
     
     So I'm trying right now to build a simple server like this:
     
     md0: /boot
     md1: /
     md2: /home
     
 But after all the base install is done, it won't install GRUB. Console Alt-F3 shows that it's trying to install GRUB to the master boot record of MD0 which won't work of course. No matter how many times I tell it to use /dev/hda or (hd0) it still goes to MD0.
     
 What gives? Installing RAID1 via Anaconda on RH/FC was never any challenge. Why does it have to be shrouded in such mystery and mythology here?
     
 Is it possible to actually install RAID1 on Ubuntu? I know it can be set up after the fact on a running system but that's a lot more work.
     
     Truth would be appreciated about RAID on Ubuntu.

---

### Post by Rottweiler on 2005-02-16
Anyone?
  
  Surely there is an authoritative answer out there somewhere about how to do RAID on Ubuntu.
  
  Ok, found this:
  [http://www.ubuntulinux.org/wiki/InstallingToRAID1]("http://www.ubuntulinux.org/wiki/InstallingToRAID1")
  
 But that answer is completely unacceptable (requires that you switch to LILO - surely that isn't necessary; still won't allow /boot to be in RAID1).
  
  Any help?
  
  Please.

---

### Post by jdodson on 2005-02-16
removing until i find more info.

---

### Post by Rottweiler on 2005-02-18
It's really starting to worry me that there seems to be no answer for this.
 
 Anyone out there?

---

### Post by Juergen on 2005-02-18
IMHO the problem is, you can't software-RAID partitions that are needed before the kernel and the raid drivers are loaded - chicken egg problem.

I've read before that RH/FC can do this, but I won't install that only to look what tricks they implement ;-)

If you want a fully RAIDed system you (again IMHO) have to buy a RAID-controller with it's own processor - not the ones that again need 'drivers'.

But you could simply copy those two partitions, create a slighly modified fstab on the mirror and if somthing happens to disk1 still boot from disk2 with a second entry in GRUB. 
RAIDing only /home and /var still protects your valuables...

---

### Post by Rottweiler on 2005-02-18
> **Juergen]IMHO the problem is, you can't software-RAID partitions that are needed before the kernel and the raid drivers are loaded - chicken egg problem.
   
   I've read before that RH/FC can do this, but I won't install that only to look what tricks they implement  said:**
> You can do this because RH/FC, like you said, does this. In fact it's so trivial to set it up in Ananconda it never occured to me that it was something difficult or mysterious.
   
 [quote]If you want a fully RAIDed system you (again IMHO) have to buy a RAID-controller with it's own processor - not the ones that again need 'drivers'.That would certainly be the optimum solution. But it isn't always feasible. And it shouldn't be required.
   
   Anyway, I filed a (rather odd) bug report: [https://bugzilla.ubuntu.com/show_bug.cgi?id=6721]("https://bugzilla.ubuntu.com/show_bug.cgi?id=6721")
   
   If nothing else, maybe it will be an avenue to get an "official" answer.

---

### Post by Rottweiler on 2005-02-18
I found this excellent article: [http://www.linux-sxs.org/hardware/raid_for_idiots.html]("http://www.linux-sxs.org/hardware/raid_for_idiots.html")
   
 This makes me think that the better plan might be to get in the habit of activating RAID post install. This would be a more versatile skillset to learn than letting the installer do the work.
   
 A quote from that article:> As of this writing, I am using a vanilla 2.6.6 kernel with all support built-in for boot-up to avoid the necessity of using an initrd. 
  
 The important point for this kernel is that you build in the RAID support. So in your choice of configuration menus select "Device Drivers" --> "Multi-device support (RAID and LVM)" and ensure that RAID support and at least the RAID level you want to use is built in, not a module. Does anyone know if the Ubuntu stock kernels are configured that way? (I don't have kernel sources installed on any of my boxes right now.)

---

### Post by tonym on 2005-02-19
I don't beleive the kernels do include raid or LVM,  except as modules.  I run with LVM2 on RAID1  ,  created post install,  using an initrd to load the modules.  Its not a major problem to set up - there's plenty of info around on the Internet.  I've been running like this for a while both on Debian and Ubuntu without problems.

---

### Post by Rottweiler on 2005-02-19
[QUOTE=tonym]I don't beleive the kernels do include raid or LVM, except as modules. I run with LVM2 on RAID1 , created post install, using an initrd to load the modules. Its not a major problem to set up - there's plenty of info around on the Internet. I've been running like this for a while both on Debian and Ubuntu without problems.[/QUOTE]Thank you. Do you have your /boot and / (root) partitions RAIDed? Are you using GRUB?

---

### Post by dmatrix on 2005-02-19
Be curious to know as well if you are using GRUB. According to some things I have read GRUB + RAID1 does not boot between hard drive devices, but I have not tested this myself.. It would be nice to have decent RAID1 support with GRUB if that is the case, since using LILO kinda sucks.

---

### Post by tonym on 2005-02-23
[QUOTE=Rottweiler]Thank you. Do you have your /boot and / (root) partitions RAIDed? Are you using GRUB?[/QUOTE]
 I have a separate /boot on a RAID1 device.  I think it isn't possible to put /boot on LVM but may be wrong.  When setting up I mounted my RAID1 device as /mnt and copied the contents of the old /boot.  My RAID device /dev/md0 maps to /dev/hda1 & /dev/hdb1 so I then rebooted and in GRUB set up the boot info on both mirrors by

root (hd0,0)
setup (hd0,0)

root (hd1,0)
setup (hd1,0)

I have everything else on LVM2 on RAID including root.  Again I created the logical volumes and in turn mounted them as /mnt and copied the data from old partitions.  Stop udev before copying root.  Don't forget to update /etc/fstab in your new root.  (I did forget once). 

You then have to create a new initrd file by 

mkinitrd -o /boot/newfilename -r /dev/vg1/root 

where /dev/vg1/root is my LV for root!

Note - next time you install a new standard kernel it will create a corresponding initrd file itself so you don't need to repeat this.

Reboot, change your load parameters at boot time to test it out then update /boot/grub/menu.lst if you are happy.

One gotcha I hit is if you haven't space for the new RAID device for root as well as your existing system.  You can create the RAID1 deviev with only 1 mirror,  set up the system,  trash you rold system and use the space to create the second mirror.  Once you have brought in the new device and synchronised you need to run mkinitrd again otherwise it will have forgotten the 2nd mirror when you reboot.

Regards

Tony Middleton.

---

### Post by jdusablon on 2005-02-24
Your bugzilla bug is a little vague...which RAID do you mean?

Mirroring shouldn't be a problem, but striped arrays cannot contain the kernel unless the HDD controller hardware is good enough to fool the os into thinking that it's only one volume.

---

### Post by Rottweiler on 2005-02-24
[QUOTE=jdusablon]Your bugzilla bug is a little vague...which RAID do you mean?

Mirroring shouldn't be a problem,[/QUOTE]Huh? Please read it again. It says in the 2nd paragraph, 1st sentence:

"Is there some way to install Ubuntu on a software RAID1 system ..."

---

### Post by Nebvin on 2005-03-11
I installed directly to a software raid0, of course I did not raid /boot though. The stock kernel has everything needed.

---

### Post by Rottweiler on 2005-03-11
[QUOTE=Nebvin]I installed directly to a software raid0, of course I did not raid /boot though. The stock kernel has everything needed.[/QUOTE]Thanks. I believe you are correct.

As best I can tell now, Warty's problems are all in the installer and not in the kernel as some thought.

It appears this is all much improved in Hoary. See the last entry made by me today (3/11) in my Bugzilla bug:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6721]("https://bugzilla.ubuntu.com/show_bug.cgi?id=6721")

---

### Post by Cerin on 2008-05-30
> **Rottweiler said:**
> Is it possible to actually install RAID1 on Ubuntu?

I just installed 8.04, and have been having nightmares trying to get RAID1 working, so I guess the answer after 3 years is still a resounding *no*. This is so depressing.

---

### Post by Rottweiler on 2008-05-30
I've been using RAID1 with no problems on Dapper LTS (6.06) and RAID5 on Gutsy (7.10). I haven't tried it on anything newer. When the new 8.04 LTS server hits in July (?) I'll be upgrading several systems and building some new ones.

---

### Post by Cerin on 2008-05-30
> **Rottweiler said:**
> I've been using RAID1 with no problems on Dapper LTS (6.06) and RAID5 on Gutsy (7.10). I haven't tried it on anything newer. When the new 8.04 LTS server hits in July (?) I'll be upgrading several systems and building some new ones.

I tried two methods. First, using the "alternate install CD", since the main 8.04 desktop install CD no longer supports RAID for some mysterious reason. That install fails with the error "Kernel panic: linux-generic".

The second method I tried was using my motherboard's BIOS RAID support to do fakeRAID, but all I get when I boot is an endless series of "Grub loading stage1.5...Grub loading stage1.5...Grub loading stage1.5..." I'm sure I missed something at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) but I really don't have the time to dig through such convoluted instructions just to do something so simple as RAID-1.

---

