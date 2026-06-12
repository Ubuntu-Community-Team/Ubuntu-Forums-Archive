---
title: "Had to exchange the motherboard, ram and gfx."
date: 2016-11-08
forum: Server Platforms
---

### Post by marcin5 on 2016-11-08
Hello,

I had a little mishap with my NAS running LTS14 (04 as I remember). It was running fine for a few years now, and a few days ago the PSU died and took the mobo and ram with it. I'd really like to use the old system with the new hardware, but as you can image it doesn't work after connecting the old drives.

What I had:
Gigabyte GA-890GPA-UD3H ( [http://www.gigabyte.com/products/product-page.aspx?pid=3342#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3342#sp) ) - this one had the ATI gfx integrated

What I have:
Gigabyte GA-970A-UD3P ( [http://www.gigabyte.com/products/product-page.aspx?pid=5194#sp](http://www.gigabyte.com/products/product-page.aspx?pid=5194#sp) )[FONT=arial]
[/FONT]And some cheap ASUS GeForce 210 on PCI-E.

In addition to that I would love to take the advantage of the downtime and switch the OS drives - RAID0 3x500GB to 3x2TB (mdadm).
In this regard can I just dd the drives while running some live CD and then expand the partitions/mdadm/fs (ext4) ? Or do I need to create a new mdadm array on the new drives and copy the OS ?

In the regard of the new hardware. I know that USB 2.0 works before booting, but it gets switched off during the boot process (until now I've only booted to recovery, just in case). USB 3.0 works all the time. I know that LAN doesn't work. I've updated (manually) the MAC in the /etc/udev/rules.d/70-persistent-net.rules, and I can see (via the LED colors on my router) that during boot the LAN card starts as 100mbit and then negotiates to 1gbit connection. But after trying to run recovery with networking enabled I'm getting to the point that the 'br0' (I do have that bridged with eth0 for kvm) is trying to send some dhcp stuff, but it keeps on going and going and nothing. Is there maybe some command that I can run that will go through the new hardware and update the config files ? Or maybe some list of things that I need to do to get it running on the new hardware ?

Thanks for any advice in advance.

Best regards
Szafran

---

### Post by oldfred on 2016-11-08
New board is UEFI, but should work in CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  


But if you are redoing drives, you then may want to reinstall using gpt partitioning and UEFI boot.
Or at least gpt partitioning, but you cannot dd from MBR to gpt. You can rsync or cp.
Often best to reinstall system, and copy data, configurations and list of installed apps to reinstall. That should be your normal backup to just restore.

AMD Gigabyte boards may  need boot parameters.

 Some Gigabyte boards need acpi=off boot parameter also
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370) 

I have a Gigabyte Intel based board and while having to make many UEFI settings changes, it worked without issue. Used just Intel video.
On my other system with an Asus motherboard and GT620 video card, I was able to boot 16.04 without having to use nomodeset. Always before with nVidia, I had to use nomodeset.

---

### Post by marcin5 on 2016-11-08
Thank you for the reply.
Thought so, that reinstalling would be the easiest way to fix the new hardware issues.
But it'll take me days to reinstall and reconfigure all the software (the old config files remember the times when the Ubuntu versioning numbers were still in the single digit state). That's why I haven't done it yet.
I'll try that soon (unless I'll find a way to make it work without reinstalling).

---

### Post by oldfred on 2016-11-08
Software config files are mostly in /home.
Hardware or system wide configurations are in /etc, but some may not apply to a new install.

You can export list of installed apps and reinstall in new system. And then apps pick up config files.

But servers typically have more configuration/settings/software in /etc. Which you should be backing up anyway.

---

### Post by marcin5 on 2016-11-09
Ok. There's another Q.
Do I need UEFI boot ?
What will that give me ?
Will normal booting from USB etc still work ?
I have a Verbatim external enclosure that acts as an external HDD + virtual ODD. I use it every time something goes wrong as I have lots of live CDs on it - something like all in one recovery. Also I install OSes from it - will it work as before ?

Do I need gpt ?
The resulting mdadm array will be grater than 2.2TB, but under it everything will be under 2TB. As I understand it grub runs from a single drive, then runs the compressed init files that setup arrays. So in theory this should work without gpt.

---

### Post by mastablasta on 2016-11-09
> **marcin5 said:**
> Ok. There's another Q.
Do I need UEFI boot ?
What will that give me ?
Will normal booting from USB etc still work ?
I have a Verbatim external enclosure that acts as an external HDD + virtual ODD. I use it every time something goes wrong as I have lots of live CDs on it - something like all in one recovery. Also I install OSes from it - will it work as before ?

by UEFI boot it is meant "secure boot" used and promoted by Microsoft supposedly to make it all more secure, but in reality mostly to lock in hardware to Microsoft Windows. by disabling it you will get the old type of boot which as i understand is what you actually want based on your first post..

> 
Do I need gpt ?
The resulting mdadm array will be grater than 2.2TB, but under it everything will be under 2TB. As I understand it grub runs from a single drive, then runs the compressed init files that setup arrays. So in theory this should work without gpt.
the need for GPT depends on partition size.

---

### Post by darkod on 2016-11-09
If you replace the disks with 2TB disks you don't need gpt table on them. 2TB disk can still work with msdos table even if there is only one large partition spanning the whole disk.

I still don't understand why are you talking that much about reinstalling. In theory changing MB+CPU+RAM doesn't need you to reinstall your OS. If you want to switch to larger disks that's another subject. But just to make the machine running after replacing few components, it should still be able to boot with current disks.

Another thing, you mention raid0 with three disks. Are you really sure you want to run raid0? I assume you are aware of its dangers and that it is not any kind of redundancy raid, right?

In fact, if it doesn't boot with current disks, are you sure that none of them is damaged by the power surge too? Because if you lost one disk from raid0, it is normal that it won't work, the whole array falls apart.

---

### Post by marcin5 on 2016-11-09
Yes, I know what raid0 is. I also know what raid6 is, which i do have configured for my 16x2TB array.

It boots with current disks - guys I wrote in the first post that I can boot fine to the recovery mode. Just not all HW is working that's why I'm not booting it normally (It would probably boot fine to, but without the LAN and USB 2.0 it's useless to me - and untill that's working I'm not going to connect the additional controlers with the rest of the hdds). And for eg. If I boot into gparted live cd everything works fine (LAN, USB 2.0 and 3.0), so the HW is ok. And rather old live cd can use it - so it shouldn't be a problem for much newer config.

Previously I wrote about Verbatim vODD enclosure - sorry it's actually Zalman ;)

Ok, so I don't need UEFI boot, and also don't need GPT. How about the new hardware ? How can I make it to work ? (the raid moving to new disks is a thing that I'm going to take care of after new HW is working fine).

---

### Post by 1clue on 2016-11-09
UEFI is simply a more modern way of booting. I use it on my new hardware and don't plan to go back.  It's different, it takes some getting used to but it's no worse for Linux than anything else.

GPT is superior to MBR in every way.

MBR originally had a hard maximum of 32 megabyte disk sizes.  When it was first designed that much space was almost inconceivable. No, it's not a typo.  MBR partition table format has been hacked/modified several times in order to account for larger and larger disks. It's still limited to 4 primary partitions though, and the idea of extended partitions was another hack to account for the antiquated MBR format.

GPT has its partition table backed up -- a primary table at the front of the disk, and a backup at the end.  This means that if your disk gets corrupted for some reason, you have a better chance of recovering your data.  GPT can have more than 100 primary partitions, no need for extended partitions.  GPT many more possibilities for partition types as well, and has limits well beyond the capabilities of the largest drives currently made.

---

### Post by darkod on 2016-11-09
If just part of the HW is not working, you can google for some procedure to re-detect HW. That's probably all it needs, to activate the correct modules (drivers) on boot. I have never actually changed main components on my server yet (only HDDs) so I really don't know if you need to re-detect it, but it sounds like it.

Ubuntu server surely supports USB2, in fact I would say it should work without any detection needed. And it does support many LAN chips too, but it might be a question of modules not being active because this HW was not present on installation.

PS. I assume you tried booting the normal mode at least once after replacing the HW right? Because if you are booting only into recovery mode in the root shell (is that the option you are using, drop to root shell?), that loads the root partition in RO mode, so even if the OS want's to make changed after detecting new HW, it can't. Either remount the root partition as RW in recovery mode root shell and try some HW detection, or try booting in normal mode and see how it goes.

PPS. Maybe something like this happened to the LAN card?
[http://myconfigure.blogspot.com.es/2013/07/re-detect-network-interface-card-in.html](http://myconfigure.blogspot.com.es/2013/07/re-detect-network-interface-card-in.html)
If it is really detected with another name, your setup in /etc/network/interfaces will not refer to the correct adapter any more and you will need to modify it.

---

### Post by marcin5 on 2016-11-10
I think I got it working.
Adding amd_iommu=soft and iommu=soft to grub command line helped.

But I'm still considering using a clean install (I've made one allready on the new hdds, but came back to old hdds to troubleshoot the mobo problems)

---

### Post by marcin5 on 2016-11-14
Thank you for all the help guys. I'll be doing a final setup soon on the new hardware. Hoping it'll all work fine.

I have another Q. In what case is the acpi=off boot parameter helpful? I'd like to know just in case something comes up.

---

