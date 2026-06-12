---
title: "Itunes in Virtual Machine"
date: 2008-02-08
forum: Virtualisation
---

### Post by adamsjw2 on 2008-02-08
Hi all,
I need to use my Iphone with Ubuntu. Crossover office doesn't support the newest versions of Itunes. Would it work to install vmware or some other VM to install itunes? Is there another work around?
I don't want to give up my iphone or Kubuntu.
TIA

---

### Post by cyberdork33 on 2008-02-08
you can install windows in a vm, yes.

---

### Post by adamsjw2 on 2008-02-09
Cyberdork33,
Thanks for your quick reply. Running Windows isn't the problem, there's a problem with gettin Windows in the VM to recognize the USB when I plug in itunes.

---

### Post by lswest on 2008-02-09
if you use Virtualbox you can install the guest additions, and those also support USB devices.  Give it a try. [www.virtualbox.org]("www.virtualbox.org")

---

### Post by adamsjw2 on 2008-02-09
lswest,
Thanks. I will give this a try.
JA

---

### Post by lswest on 2008-02-09
no problem, happy i could help.  Btw, virtualbox is in the repos.  just remember to add yourself to the vbox group after the install^^

---

### Post by p_quarles on 2008-02-09
Moved to Virtualization.

This link will help get USB devices working with VBox:
[http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices](http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices)

That said, people haven't had the best of luck getting iPods/iPhones to sync with a virtualized instance of iTunes.

---

### Post by GooglieS on 2008-10-19
I tried to do this with vmware, but virtual winXP shows me a BSOD when i connect the iPhone to it :( How about vBox? Everything is ok with it?

---

### Post by iblanken on 2008-10-20
What version of VMWare are you using? I have Player 2.5.0 build-118166 and my iPhone works perfectly with a WIndows XP SP3 vm. I expose my mp3s using VMWare's Shared Folders (looks like a network drive in the VM) and iTunes Library Updater to keep iTunes in sync with my collection.

I did have to get the VMware tools package from my Server 2 installation. Right now the the VMWare server 2 beta is still free.

---

### Post by GooglieS on 2008-10-20
I am using vmware workstation 6.5.0 build-118166
WinXP SP2
Very strange.... I'll try to test it with VMWare server 2 beta later.

UPD: I fixed that! All i need - is to enable USB 2.0 in my old vmware image.

---

### Post by quyla on 2010-07-28
I can't seen to get iTunes working in a VM at all. Running WinXP in VBox on Ubuntu 10.04 doesn't seem to work for iTunes. It installs fine, but once i try to do the first-run thing (i.e. "automatically associate AAC and MP3 files with iTunes", "Keep my folder organized"), iTunes "encounters an error and has to close". Any help?

---

### Post by Ginsu543 on 2010-07-29
Be sure to download and install the PUEL version from [_VirtualBox.org_]("http://www.virtualbox.org/wiki/Linux_Downloads"), not the OSE version from the repos. The PUEL supports USB, the OSE does not.

Try these steps:
1) Make sure VT-x hardware virtualization is enabled in BIOS (this requires you to have both a hardware virtualization capable CPU and motherboard)
2) Install the PUEL version
3) Add yourself as a user in vboxusers group (System --> Administration --> Users and Groups --> Manage Groups --> vboxusers)
4) Install GuestAdditions
5) Make sure your iPhone is selected under Devices --> USB Devices
6) Install latest iTunes

Right now as I type, I'm syncing my iPhone 3GS (iOS 4.0.1) with iTunes 9.2.1 on a Windows XP guest in VirtualBox. Both my iPhone and iTunes works 100% and very stable.

---

