---
title: "when will Ubuntu 14.04 start nighlty building an Alternate CD"
date: 2014-03-16
forum: Ubuntu Development Version
---

### Post by gmoore777 on 2014-03-16
I am waiting for the nightly build of Ubuntu Trusty Tahr to produce an Alternate CD.

I imagine on March 27th, when the "Final Beta" is available, there will be one, but I want one today.

The Lubuntu distribution, has an Alternate, and has had one for weeks, why not the 
regular (Unity) version of Ubuntu?

Anxiously waiting.

---

### Post by PaulW2U on 2014-03-16
No longer available - [http://askubuntu.com/questions/207635/why-are-there-no-alternate-cds](http://askubuntu.com/questions/207635/why-are-there-no-alternate-cds)

---

### Post by sudodus on 2014-03-16
But you can get the ***mini.iso*** alias ***Netboot*** at this link, and from that you can build any of the flavours with a text screen interface of the same kind as Lubuntu Alternate.

[http://www.fr.php.net/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/](http://www.fr.php.net/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/)

---

### Post by gmoore777 on 2014-03-16
thank you PaulW2U, I will stop my anxious waiting and begin finding an alternative immediate solution for my needs.

thank you Sudodus, I will look into mini.iso and netboot.

My needs are to install Ubuntu with LVM, RAID and Encryption without using work arounds and manual edits.

The Lubuntu Alternate CD was excellent in providing LVM, RAID and Encryption on 2 of my machines.

I'll see if the regular Ubuntu nightly LiveDVD can do this, and will report back.

---

### Post by Elfy on 2014-03-16
*Thread moved to **Ubuntu +1**.*

---

### Post by gmoore777 on 2014-03-16
Just booted up the Ubuntu TrustyTahr LiveDVD from nightly build dated 2014-03-16 on 
a machine that I already have set up with RAID, LVM and Encryption.

I got to the partitioning step, and it did not see my RAID devices, nor LVM volumes.

There were no buttons to "turn on" Raid, nor to "activate" encrypted volumes.

And seems like there should be a choice to NOT choose a device for boot loader installation.
I would want my MBR to remain unchanged; to boot the other Ubuntu distribution, first, that I have on this machine,
and then boot any newer installs from that Grub menu(after I `update-grub`).

So my choices are to use the Lubuntu Alternate install, and learn to like that window environment.
Sadness.

---

### Post by Elfy on 2014-03-16
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-August/035675.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-August/035675.html)

is the dev discussion that took place when this got dropped

---

### Post by sudodus on 2014-03-16
Did you try the mini.iso ?

Anyway, Lubuntu is not bad ... I like LXDE

---

### Post by Ian_Worrall on 2014-03-16
If you want full-fat Unity, you could install from your Lubuntu Alternate disc, then "sudo apt-get install ubuntu-desktop"?

---

### Post by gmoore777 on 2014-03-16
I have not tried the mini.iso yet, but i was reading some documentation about the "debian-installer" which, I think, the 
mini.iso uses.
It says:
"Limitations: Although most questions used by debian-installer can be preseeded using this method, there are some notable exceptions. You must (re)partition an entire disk or use available free space on a disk; it is not possible to use existing partitions. "

That is what I want to do. I want to install my Nth Linux installation on existing partitions on a machine that has already been configured with RAID-1, and an Encrypted LVM volume.
So if that "Limitation" applies to the mini.iso, then the mini.iso is not a solution for me.

Ian_Worrall's suggestion of `sudo apt-get install ubuntu-desktop` seems reasonable on paper.
Would the "clobbering" of the Lubuntu desktop with the "ubuntu-desktop" behave?
Could I remove the Lubuntu desktop package (not sure what the name of it is), or would it have a chain of dependencies
that would in fact remove every package on the machine?

---

### Post by gmoore777 on 2014-03-16
I think the Lubuntu desktop package is called "lubuntu-desktop" and doing a `sudo apt-get remove lubuntu-desktop`
will only remove that one package. So that's good to know.

In either case, I don't want to create a customized installation of Lubuntu with Ubuntu desktop on top of that.
In case I run into issues that are related to that, I would be wasting my and others time tracking down the source of problems.

I will give up here, something I don't particularly like doing, and just assume that my machine setup, which 
I didn't think was that complicated (or I should say, out of the norm), evidently, is way too complicated for the 
Ubuntu LiveCD and for the Mini.iso to comprehend.
I'm not totally sure about the Mini.iso, but the Ubuntu Live CD can't disect a pre-existing machine
with RAID-1, and an Encrypted LVM.

I will just get used to the Lubuntu setup which seems perfectly fine to me, and install the apps that are missing,
like the LibreOffice suite, Thunderbird, the terminal windows that come with Ubuntu, etc.

I will also pray that the Lubuntu team not discontinue their Alternate install in 2016 when I come out of my cave
again, to upgrade/build machines with that LTS version.

Thanks for reading this thread and helping me out.

---

### Post by sudodus on 2014-03-16
> **gmoore777 said:**
> I have not tried the mini.iso yet, but i was reading some documentation about the "debian-installer" which, I think, the 
mini.iso uses.
It says:
"Limitations: Although most questions used by debian-installer can be preseeded using this method, there are some notable exceptions. You must (re)partition an entire disk or use available free space on a disk; it is not possible to use existing partitions. "

I have used the mini.iso and reused existing partitions.
> 
That is what I want to do. I want to install my Nth Linux installation on existing partitions on a machine that has already been configured with RAID-1, and an Encrypted LVM volume.
So if that "Limitation" applies to the mini.iso, then the mini.iso is not a solution for me.

Ian_Worrall's suggestion of `sudo apt-get install ubuntu-desktop` seems reasonable on paper.
Would the "clobbering" of the Lubuntu desktop with the "ubuntu-desktop" behave?
Could I remove the Lubuntu desktop package (not sure what the name of it is), or would it have a chain of dependencies
that would in fact remove every package on the machine?

Well, having double sets of some programs clobbers the menus / the dash, but it is not a big problems. Things work. It is *not* straight-forward to remove the Lubuntu part of it.

---

### Post by sudodus on 2014-03-17
> **gmoore777 said:**
> I think the Lubuntu desktop package is called "lubuntu-desktop" and doing a `sudo apt-get remove lubuntu-desktop`
will only remove that one package. So that's good to know.

In either case, I don't want to create a customized installation of Lubuntu with Ubuntu desktop on top of that.
In case I run into issues that are related to that, I would be wasting my and others time tracking down the source of problems.

I will give up here, something I don't particularly like doing, and just assume that my machine setup, which 
I didn't think was that complicated (or I should say, out of the norm), evidently, is way too complicated for the 
Ubuntu LiveCD and for the Mini.iso to comprehend.
I'm not totally sure about the Mini.iso, but the Ubuntu Live CD can't disect a pre-existing machine
with RAID-1, and an Encrypted LVM.

I will just get used to the Lubuntu setup which seems perfectly fine to me, and install the apps that are missing,
like the LibreOffice suite, Thunderbird, the terminal windows that come with Ubuntu, etc.

I will also pray that the Lubuntu team not discontinue their Alternate install in 2016 when I come out of my cave
again, to upgrade/build machines with that LTS version.

Thanks for reading this thread and helping me out.

The Lubuntu team wants to keep the alternate iso installer. But how long will we be successful? We don't know if it will survice into the next-next LTS release, 16.06, 'X X'. Maybe ***you*** will help make it possible :-)

---

### Post by gmoore777 on 2014-03-18
Short Story:
The mini.iso behaves exactly like the Alternate install
in regards to understanding RAID, Encryption and LVM.
I'm very, very happy that this mini.iso exists in light that the Alternate
install is (or has been) disappearing.

Longer Story:

I started from scratch with the TrustyTahr Lubuntu Alternate Install and re-carved my machine
with RAID, and Encrypted LVM, creating extra partitions/volumes for future installs and manipulations.
(In hindsight, I probably could have used the mini.iso, but wanted to do this with the Alternate install due to my
 comfort level with that install.)

I then downloaded and burned a CD with the mini.iso and booted off of that.
Lo and behold, that little guy, looks very similar to the "Alternate" install.
It did recognize my RAID devices, but not the Encrypted LVM. After choosing
--> Configure encrypted volumes --> Activate existing encrypted volumes --> 
the mini.iso recognized my Encrypted volume and all my LVM volumes.
I then installed the (regular) Ubuntu Desktop from the very long interesting software list,
 into an existing LVM volume, with /boot in an existing regular partition.
(I could have created new partitions/volumes, but that isn't the way I
 wanted to do this install.)
In other words, the mini.iso behaves exactly like the Alternate install
in regards to understanding RAID, Encryption and LVM.

This is how one machine is carved out.
The 2 1-TB Hard Drives are in a software RAID-1 configuration(partition to partition):

      6 GB /boot partition. RAID-1. NOT encrypted. No LVM. (may hold other .iso's for booting)
      2 GB /boot partition. RAID-1. NOT encrypted. No LVM. (for installations in the encrypted LVM area)
      2 GB /boot partition. RAID-1. NOT encrypted. No LVM. (for installations in the encrypted LVM area)
      X GB Extended partition
      2 GB /boot partition. RAID-1. NOT encrypted. No LVM. (for installations in the encrypted LVM area)
      2 GB /boot partition. RAID-1. NOT encrypted. No LVM. (for installations in the encrypted LVM area)
    40 GB spare partition. RAID-1. NOT encrypted. No LVM. (for full installations)
    40 GB spare partition. RAID-1. NOT encrypted. No LVM. (for full installations)
    40 GB spare partition. RAID-1. NOT encrypted. No LVM. (for full installations)
   866 GB Encrypted, RAID-1, LVM  physical partition.
     100 GB LVM Volume for TrustyTahr Ubuntu,                        <--  installed via Mini.iso
     200 GB LVM Volume for Backups,                                      <-- mounted as: /forBackups
      20 GB LVM Volume for TrustyTahr Lubuntu,             <-- this Alternate install carved everything out, initially.
      20 GB LVM Volume for PrecisePangolin,       
      20 GB LVM Volume for MythUbuntu,            
      20 GB LVM Volume for Xen,                  
     500 GB LVM Unallocated 

Thanks for everyone's input, and the people who maintain both the 
Lubuntu Alternate install and the little, but overly capable, mini.iso.

---

### Post by tsengs on 2014-04-24
I tried the mini.iso, but my company uses a preseed template to answer the questions about what packages/software to install. How can we combine that in/with the mini.iso?

---

### Post by coffeecat on 2014-04-24
This sub-forum is for the discussion of the current development version, now 14.10. 14.04 has now been released. If anyone needs support for 14.04, please start a thread in one the regular support sections of the forum.

Thread closed.

---

