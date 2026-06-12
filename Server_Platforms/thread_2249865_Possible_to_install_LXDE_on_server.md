---
title: "Possible to install LXDE on server?"
date: 2014-10-25
forum: Server Platforms
---

### Post by Kale_Freemon on 2014-10-25
Hello all!

Currently I have an old Dell running as a server with Windows Server 2008. It's probably in my signature.

My question is whether or not I can install LXDE the server edition of 14.04 LTS, or would I be better off install Lubuntu? I'm mainly looking for opinions more than anything.

As a secondary question, does anyone have any links to tutorials on setting up multiple HDDs as one volume? I want to completely eliminate the slow Windows Server platform and turn it into a Ubuntu server, but would like to be able to sort of mirror my original setup (except this time I intend to make it cleaner). I only ask because I don't really have a lot of time to look it up myself while working extra hours for six days straight and being really tired afterwards. If I have to, I'll look it up myself, but it would be an extreme help.

Thanks in advance! :D

---

### Post by mörgæs on 2014-10-25
Some of the Dimension 4500's have weak Intel 8xx graphics. First, let's see if it applies to yours.

Please do a live boot, run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by koenn on 2014-10-25
re your secundary question :
it looks like you're looking for lvm (Logical Volume Manager)

it goes something like this : [http://users.telenet.be/mydotcom/howto/linux/disks2.htm](http://users.telenet.be/mydotcom/howto/linux/disks2.htm)
note that that page is old, and lvm may have changed significantly since then. I'm just giving it for you to get an idea what to google for.

---

### Post by nerdtron on 2014-10-25
Why need GUI? Do you have any program that would use a GUI?

Can you tell us more about the hard drive count, layout and setup of your current machine so that we can have more accurate recommendations.

---

### Post by Kale_Freemon on 2014-10-27
> **mörgæs said:**
> Some of the Dimension 4500's have weak Intel 8xx graphics. First, let's see if it applies to yours.

Please do a live boot, run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Sorry. It's definitely not an Intel. It's an ATI Rage 128. I'm pretty sure that it'll run LXDE because it will run MATE pretty well. I'm just wanting to know if LXDE can be installed on the server variant of 14.04 because, as far as I know, the server variant is supported longer than the desktop.

As far as doing a live boot, I don't have any blank CDs or DVDs until tomorrow after work, and the Dell can't boot from USB.

> **nerdtron said:**
> Why need GUI? Do you have any program that would use a GUI?

Not necessarily. I just like being able to use the GUI as opposed to the CLI. Personal preference. That, and I like using the "Samba" application in the software center to set up the samba server. It's just easier and works nearly 100% of the time.

> 
Can you tell us more about the hard drive count, layout and setup of  your current machine so that we can have more accurate  recommendations.

Four HDDs. An 80GB that is used as the OS drive, and three 40GB drives. All internal. Currently, I use the 40GB drives as one volume to store all the files on the server and access via SMB on the local network and FTP on external networks. I manage it locally via RDP.

It has 1GB of DDR RAM and a Pentium 4 processor clocked at 2GHz.

It is plugged into the router via ethernet.

Thanks for the LVM suggestion! :D I'll look into it.

---

### Post by mörgæs on 2014-10-27
A Rage 128 is from 1998-1999. I'm surprised that you use the term 'pretty well' for a card that old, but if that's the case just go ahead with LXDE or Lubuntu. I would begin searching for what I could get for $ 10-20 (or for free), though.

Support for a Lubuntu 14.04 desktop package is three years no matter if you install a desktop from scratch or you install a server and add a desktop later. If you add the desktop then don't use the system after april 2017 no matter if parts of the system are supported longer. Security is searching for the weakest link. 

I hope you have air flow between the hard disks. Four in a tight cluster is likely to overheat.

---

### Post by nerdtron on 2014-10-27
LVM is the definitely the way here to combine all hard drives into a single volume. But you don't use RAID? What if a single hard drive fails? All you data will be lost.

---

### Post by TheFu on 2014-10-27
> **nerdtron said:**
> LVM is the definitely the way here to combine all hard drives into a single volume. But you don't use RAID? What if a single hard drive fails? All you data will be lost.

These forums are full of people seeking help after 1 drive in either an LVM or RAID setup failed.  Backup, backup, backup. If you span a file system across 2 drives, that is 2x more likely to loss data.  3 drives? 3x ... every drive added to the LVM/RAID means one for device that has to work perfectly.  RAID is for HA only, not backups. Know it, learning, love it. ;)

There are other ways to spread data out across drives without RAID or LVM .... I've used symbolic links to move virtual machine storage from /var/lib/libvirt ... to a different physical disk - since the location under /var .... appeared to be identical still, KVM didn't care.  

There are other solutions for non-business uses (think home media collections) where aufs (and similar stuff) are workable.

Regardless - backups are always required.

---

### Post by lukeiamyourfather on 2014-10-28
> **Kale_Freemon said:**
> My question is whether or not I can install LXDE the server edition of 14.04 LTS, or would I be better off install Lubuntu?

Yes, desktop environments can be installed on Ubuntu Server. The real question is why would you want to? Server applications are configured with text files so it's unnecessary. If you want a desktop environment then just start with Lubuntu or whatever desktop environment you want and then install the server applications from there. Though I'd encourage you to try configuring things with the terminal or SSH as that's the de facto way to manage Linux servers and for lots of good reasons (security, efficiency, simplicity to name a few).

> **Kale_Freemon said:**
> As a secondary question, does anyone have any links to tutorials on setting up multiple HDDs as one volume?

Linux software RAID is the most common way of doing this, with three drives for data you could setup a RAID 5 array. If the machine has ECC memory consider ZFS (has RAID like features plus lots of other benefits). If you simply want volume spanning this can be done with LVM. Like TheFu has said, don't forget backup.

---

### Post by Kale_Freemon on 2014-10-29
Ok. Thank you everyone for all the suggestions. I wound up just installing Lubuntu 14.04 on the Dell server. I decided against using RAID or any other method to expand one volume accross three different drives. Instead, I just setup a shared folder on one drive and then set it up to back up the contents of that one drive to the other two drives every morning.

So far, everything is working just fine. I just gotta get the FTP part of it working now.

---

### Post by TheFu on 2014-10-30
> **Kale_Freemon said:**
> So far, everything is working just fine. I just gotta get the FTP part of it working now.

I hope you mean sftp, not FTP. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

---

### Post by Kale_Freemon on 2014-11-07
> **TheFu said:**
> I hope you mean sftp, not FTP. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

Ya. I got it working. Thanks. :)

Windows Server 2008 doesn't have sftp as an option, so I always used ftp. But, I got sftp working on Lubuntu.

---

### Post by gordintoronto on 2014-11-08
I know everyone marches to their own drummer, but I am astonished by how much effort people will put into dreadful old hardware. I can spend $130 at my local off-lease refurbisher, and get a system which completely blows away a Dell 4500 -- and it will run Xubuntu (personal preference) like gang busters. Plus, it supports SATA hard drives, so I can bump the available space up to 2 TB for $80.

No criticism implied: good for you, getting further use out of "electronic landfill."

---

