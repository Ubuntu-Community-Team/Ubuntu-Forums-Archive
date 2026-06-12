---
title: "Relatively new to virtualization; a few questions..."
date: 2010-07-21
forum: Virtualisation
---

### Post by treyk4 on 2010-07-21
Hey all,
  I've used Ubuntu for a few years now on multiple computers (started with Feisty). I've finally come to the conclusion that Ubuntu is sufficient to be my primary system. The setup I have envisioned is having two partitions as I do now: one for GRUB and Ubuntu, and the other for Windows 7. I plan on booting into Ubuntu most of the time, and having one virtual desktop dedicated to running the Windows partition under VirtualBox (or VMWare? I'm not sure which is better for me) on boot. I wish I could just stick to WINE, but it doesn't work with many programs I regularly use.

So, questions:
[LIST]
[*]**Is VirtualBox, VMWare Server, or VMWare Workstation better for me?**
[INDENT]I don't care too much about open source or not. I could deal with paying for VMWare Workstation, if it is considerably better.[/INDENT]
[*]**How could I get the virtual machine to behave as described above?**
[INDENT]I've heard of this being done on VirtualBox, but VMWare?[/INDENT]
[*]**How much would this bog down my system?**
[INDENT]My current computer doesn't support hardware virtualization, although I plan on buying one that does.
Oh, also: is one of the above softwares better at utilizing machines with this feature?[/INDENT]
[*]**How reliable would a setup like this be?**
[INDENT]Needless to say, this makes me worry for my Windows partition[/INDENT]
[/LIST]

Thanks for any help!
-Trey

---

### Post by roxette on 2010-07-21
not much different between vbox & vm workstation
and it it easy to get sn for vm workstation
if you would like to close the window but want to keep the guest os running, you may try vm server, it's free

currently, i am still using ubuntu (8.04 hardy) and winxp
cus vm server cannot be installed on lucid

---

### Post by Ginsu543 on 2010-07-22
The answer does depend on what you use your Windows environment for. If you need it for games, then forget virtualization altogether; it's better to just run Windows natively. But if it's to run certain Windows-only software, then virtualization can work really well.

In my case, I run a Windows XP guest on my Ubuntu 10.04 host using VirtualBox. I need Windows for two primary reasons: (1) to run BibleWorks (a Windows-native Bible study software) and (2) to run iTunes to sync my iPhone. For both of these purposes (and Microsoft Office), VirtualBox with USB support (the PUEL version, not the one found in the repos) provides a seamless integration with my Ubuntu environment. With Windows XP running in a window, I am able to seamlessly go back and forth from Ubuntu to Windows and vice versa. This setup has proved very reliable. Not only that, since I am using a 40GB .vdi file as my Windows "partition" (rather than a physical partition), I can easily back up the entire "partition" by simply copying the .vdi file to another folder. This adds the extra benefit of being able to run the same exact Virtual Machine on any of my computers running Ubuntu. I just need to have a copy of VirtualBox installed on each and a copy of the .vdi file. Regardless of the physical specs of the computers, I can run Windows XP on all of them without having to reinstall.

To be fair, I've only used VirtualBox and have never tried VM stuff. But for what I do, VirtualBox has been great. I don't know if VirtualBox will allow you to boot from your Windows partition, but you can have it set up so that you can access files on it. Not having hardware virtualization support will slow things down, especially in file transfer using the USB or shared folders. But for desktop publishing and websurfing, it should still be quite usable.

As you can see in my siggy, my current computer has enough cpu and ram resources to devote quite a bit to my VM, so running Windows XP in VirtualBox is way faster and smoother than it used to be running Windows natively on my older machines. I seriously forget that I am using a virtual PC. But VirtualBox gives you the option of assigning as much (or little) cpu and ram resources as you need, so you can play around with it to achieve the best results for you.

---

### Post by dcstar on 2010-07-22
> **treyk4 said:**
> 
..........
So, questions:
**Is VirtualBox, VMWare Server, or VMWare Workstation better for me?**
[INDENT]I don't care too much about open source or not. I could deal with paying for VMWare Workstation, if it is considerably better.[/INDENT]
.........

Why pay for VMware Workstation when VMware Player is free?

---

### Post by varunendra on 2010-07-23
> **roxette said:**
> not much different between vbox & vm workstation
Roxette, there is considerable difference between them.
In VMware workstation you can simply copy-paste or drag'n-drop files and text between host and guest, in Virtualbox you can't. Pause a running machine, supporting some non-iso cd/dvd images, virtual BIOS, creating a 'team', better networking options are some other useful advantages of VMware workstation over Virtualbox. These are my personal experiences.
However, Virtualbox is quite lightweight and thus can run faster on low-resource systems. It is also said that VMware is more stable, but I personally haven't experienced any problem so far with Virtualbox!


> **Ginsu543 said:**
> The answer does depend on what you use your Windows environment for. If you need it for games, then forget virtualization altogether........................................ .........................
+1 (for the whole post of Ginsu543).
To add to it, directly using a physical partition (or a whole fixed drive) with any virtual machine is a bad idea! There is risk of the file-system being accessed by both host and guest OSes at the same time that may cause (sometimes irrecoverable) data loss!:shock:
However, making the file-system 'read-only' for either of the OSes should avoid this clash. But I'm not sure how to do it and whether it is a guaranteed solution. So the best alternative is what Ginsu is using- i.e., use a large virtual hard disk instead of a whole physical partition. You can always access its contents from the host OS as long as the guest OS is in a running state.

> **dcstar said:**
> Why pay for VMware Workstation when VMware Player is free?
+1.
The only noticeable drawbacks are: 1)you can't pause a running vm, 2)you can't take multiple snapshots. (Also, AFAIK, player doesn't come with vmware tools, i.e., virtual drivers for the guest OS)


Finally, here's my humble opinion:
> **treyk4 said:**
> 
[LIST]
[*]**Is VirtualBox, VMWare Server, or VMWare Workstation better for me?**[INDENT]I don't care too much about open source or not. I could deal with paying for VMWare Workstation, if it is considerably better.[/INDENT]
[/LIST]

[LIST]
[*][INDENT]For a low-resource system, Virtualbox is best. If the system is powerful enough (dual-core cpu + 1GB or above RAM), go for VMware player (it supports copy-paste between host & guest, server doesn't). If you are planning Win7 as guest, then RAM should be 2GB or above.
[/INDENT]
[/LIST]
> **treyk4 said:**
> 
[LIST]
[*]**How could I get the virtual machine to behave as described above?**[INDENT]I've heard of this being done on VirtualBox, but VMWare?[/INDENT]
[/LIST]

[LIST]
[*][INDENT] accessing physical partition from virtual machine? I'd say better don't even try that[-X!!
[/INDENT]
[/LIST]
> **treyk4 said:**
> 
[LIST]
[*]**How much would this bog down my system?**[INDENT]My current computer doesn't support hardware virtualization, although I plan on buying one that does.
Oh, also: is one of the above softwares better at utilizing machines with this feature?[/INDENT]
[/LIST]

[LIST]
[*][INDENT] Typically, the requirement for Virtualbox is= minimum requirement for host OS + minimum requirement for guest OS + 64MB or more of RAM. For VMware it would be more. But as Ginsu suggested, there should be no or negligible effect on a powerful system (with virtualisation support)
[/INDENT]
[/LIST]
> **treyk4 said:**
> 
[LIST]
[*]**How reliable would a setup like this be?**[INDENT]Needless to say, this makes me worry for my Windows partition[/INDENT]
[/LIST]

[LIST]
[*][INDENT] More than you can expect- as long as you go with standard methods. However, chances of a system crash in a virtual machine are as much as in a physical machine. Only the recovery is quite easier (but not always guaranteed) and quicker with snapshots as compared with physical machines. Copying the whole folder- when the vm is working fine- is a more guaranteed backup solution. Often compressing these folders reduces their size to 1/4th to 1/5th of their original size.
[/INDENT]
[/LIST]

---

### Post by Ginsu543 on 2010-07-24
> **varunendra said:**
> 
So the best alternative is what Ginsu is using- i.e., use a large virtual hard disk instead of a whole physical partition. You can always access its contents from the host OS as long as the guest OS is in a running state.

I suppose you can make the virtual hard disk as large as you want, but I've found that practically 40GB is just about the right size. It's large enough to install and run most if not all of the software I want and files. If I need more room for files, then I just save it on to my one of my 1TB NTFS-formatted drives. But 40GB is also small enough that backing it up (i.e., copying it to my backup folder) doesn't take forever. It's nice to be able to back it up without having to use a backup utility or disk imaging software.

> **varunendra said:**
> 
For a low-resource system, Virtualbox is best. If the system is powerful enough (dual-core cpu + 1GB or above RAM), go for VMware player (it supports copy-paste between host & guest, server doesn't).

VirtualBox also allows you to copy-paste between guest and host. So I can fire up OpenOffice in Ubuntu, open up a file, copy content, and paste it into another file open on Microsoft Office in Windows VM.

---

