---
title: "What happens on update to Windows 10 on dual boot?"
date: 2015-06-01
forum: Ubuntu, Linux and OS Chat
---

### Post by A.O._Stanley on 2015-06-01
Currently set up with Windows 7 and Ubuntu 15.04. Dual boot installation in place for about 4 years.

If I upgrade to Windows 10, which apparently everyone who has Windows 7 or above is being offered for free, is there a chance the installation will wipe out my Ubuntu partition?

---

### Post by VMC on 2015-06-01
If its an upgrade, then no, Windows won't remove your ubuntu partition. You will need to reinstall grub though. Its always good practice to backup/clone your ubuntu os.

---

### Post by A.O._Stanley on 2015-06-01
VMC, thanks for your reply. And so to install grub I'd need to have an installation disk, is that right? So I'd lose grub on the upgrade and the only way to get back to Ubuntu is to boot from the installation disk and install grub from there.

---

### Post by VMC on 2015-06-01
If you have mbr then read this guide:
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)

---

### Post by CantankRus on 2015-06-01
Enjoy your not for free Windows yearly subscription when you next upgrade your hardware.

---

### Post by A.O._Stanley on 2015-06-02
VMC, thanks for the link. It has everything I need to get ready for the upgrade.

CantankRus, from what Microsoft has said and from several articles I've read, Windows 10 does not turn into a subscription service. There has been quite a lot of speculation that MS would go subscription but apparently they're not, at least not for Windows 10. Only hitch I've read about is that the 'free' upgrade part ends 1 year after the release so if you have Win 7-8- or 8.1 then the upgrade is free within the first year of release. 

I have one program that requires Net framework to run so I have to have a Windows machine otherwise I would go Linux 100%.

---

### Post by kurt18947 on 2015-06-02
I had a system where I installed Windows in addition to an existing *buntu partition. The Windows installer broke GRUB as expected. A boot-repair CD set things right.

---

### Post by james139 on 2015-06-03
This never crossed my mind, although I'm not sure I will be upgrading. Microsoft's statement  '*we will continue to keep it current for the **supported lifetime of the device** – at no additional charge'* concerns me.

---

### Post by tristan16 on 2015-06-04
> **CantankRus said:**
> Enjoy your not for free Windows yearly subscription when you next upgrade your hardware.

It's not a yearly subscription. Windows is moving to a rolling-release platform, and IIRC, Ubuntu is planning to do this as well. Once you're on Windows 10, you have Windows. Just like once you have Mac, you have Mac.

That said, I'll still be using Ubuntu myself, but at least the Windows 8.1 dual-boot won't be so annoying.

---

### Post by kurt18947 on 2015-06-04
> **james139 said:**
> This never crossed my mind, although I'm not sure I will be upgrading. Microsoft's statement  '*we will continue to keep it current for the **supported lifetime of the device** &#8211; at no additional charge'* concerns me.

I have no inside knowledge about this - I'm not in the tech biz - but I would not be surprised to see something like this. 

I buy a new PC, it comes with Windows 10. It also comes with 3 (or however many) years support. If I want to continue to use my machine beyond the included support period/supported lifetime, I must pay some periodic fee for updates. If I were a manufacturer, I'd like to see that annual fee a significant fraction of a new machine. That would reduce substantially the number of people doing what people are doing now - continuing to use machines for 6+ years. It'd make financial sense to buy a new machine and get a hardware refresh rather than pay the periodic fee for updates.  Perhaps offer some sort of trade-in/recycling program? 

I wonder how much Microsoft makes on retail upgrade licenses? I'll bet not all that much. Perhaps they feel foregoing 1 year of upgrade license revenue is worth getting most people off XP, Vista, 7 & 8.x and onto one code base.

---

### Post by Telescope_Nerd on 2015-08-03
Just in case anyone is interested.... I ran the update to Windows 10 on my dual-boot machine last night. It did *not* overwrite grub! I was quite shocked. Reboot took me to my Ubuntu partition with no hassle at all. Maybe this is the new Microsoft..... Would be interested to hear other upgrade stories especially if grub did get binned for you.

---

### Post by grahammechanical on 2015-08-03
And then there is this person's experience

[http://ubuntuforums.org/showthread.php?t=2289205](http://ubuntuforums.org/showthread.php?t=2289205)

Regards

---

### Post by 0N3 on 2015-08-04
I also upgraded Windows 8.1 Pro to Windows 10 Pro while dual booting Ubuntu 14.04 64 bit and windows didn't wipe my grub. It boots Ubuntu as it did with Windows 8.1 nothing was affected!

---

### Post by Frogs Hair on 2015-08-04
Upgraded two devices rolled back one to  Win 7 due to hardware and software problems not detected prior to upgrade. Do some research on your computer or device on the ms community forum before upgrade even if you get the green light from the Win 10 App.

My internal Mic driver was not fully compatible, so no Cortana, working Mic, or driver update. Keep in mind you have a year to upgrade from 7-29. The go back application worked well for me and took 30 to 45 minutes. No grub problems on 1 of 2 computers.

---

### Post by DrPotoroo on 2015-08-16
I upgraded a 1st generation Surface Pro with Windows 8.1/Ubuntu dual boot to Windows 10 yesterday and everything worked fine. Ubuntu partitions unmolested, and grub survived the process.

---

### Post by robertzito on 2015-09-11
Really stupid question so bare with me because I am new to this but what is MBR? when I look at my partitions I get the below so when it states the below, where does grub go, SDA3?

lrwxrwxrwx 1 root root 10 Sep 10 15:57 DellUtility -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 10 15:57 OS -> ../../sda3
lrwxrwxrwx 1 root root 10 Sep 10 15:57 RECOVERY -> ../../sda2

---

### Post by nv-7 on 2015-11-01
I also just upgraded from Windows 8.1 to 10, on an old HB Elitedbook 8440P dual-booted with ubutnu studio. No problem whatsoever. UBUNTU and GRUB completely preserved. Perhaps MS have improved the upgrade procedure to become sensitive to this?

---

### Post by Kpenguin on 2015-11-02
I actually didn't have to do anything to fix grub or Ubuntu when I upgraded, which I'm very happy about. It helped improve Microsoft's standings in my mind. :)

---

### Post by 2912pwil on 2016-03-22
Just to confirm the above, Win 10 update worked fine, no grub or Ubu problems.... 

Wow! Never realised they could get things right....

---

### Post by verymadpip on 2016-03-24
Sadly I have a tale of woe:
I upgraded my dual boot (single HDD) Win7/Xubuntu 14.04 laptop & I lost grub & my Xubuntu partition.
My Xubuntu partition became unallocated space, but oddly enough it left swap alone.

Always back up your stuff  - Hopefully I have learned that after this latest mistake...
(The only real headache was losing my local email, I'm much more pragmatic & careful regarding my main machines).

---

### Post by oldfred on 2016-03-24
With MBR partitioning, many users have lost a Linux partition if it is a logical inside the Extended.
But with either testdisk or parted rescue it can be restored.
But always best to backup partition table before install.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ parts.txt
sudo sfdisk -d /dev/sdb > parts_sdb.txt 

If you do not do partition backup and lose partition:

 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by verymadpip on 2016-03-25
oldfred, that's precisely the scenario.
Initially I thought I'd just lost grub.
It was when I booted a live medium to fix grub I discovered my OS partition was gone.

---

