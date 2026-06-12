---
title: "Load Windows 7 beta on usb for install?"
date: 2009-01-23
forum: Windows
---

### Post by norcim on 2009-01-23
I'm using Ubuntu64 bit (single OS), and I want to load win7 64bit iso into a USB for install. However, it keeps giving me a message to insert a bootable floppy. 

I have seen many tutorials that say to just copy the iso and install but something is missing because I already loaded the mbr with install-mbr. The boot flag is set using gparted.

The same drive was used to install ubuntu so I don't know what is missing.

---

### Post by cariboo on 2009-01-25
THe reason you could install ubuntu from a usb device, is that it was an image of the LiveCD. You can't run windows from a LiveCD without doing a lot of work. With windows you have to do it the okd fashioned way, Either install it from the cd onto your hard drive, or install it in a vm using something like virtualbox. Virtualbox is available in the repositories.

If you do want to try and build a Windows7 LiveCD have a look at [Bart's PeBuilder]("http://www.nu2.nu/pebuilder/")

I've used the above a couple of times, and it works quite well.

Jim

---

### Post by dcstar on 2009-01-25
> **norcim said:**
> I'm using Ubuntu64 bit (single OS), and I want to load win7 64bit iso into a USB for install. However, it keeps giving me a message to insert a bootable floppy. 
........

If only installed Windows had such effective anti-malware protection!  ;)

---

### Post by norcim on 2009-01-25
Can I create a bootable disk from inside VirtualBox ? There are simple tutorials for creating the disk from windows.

---

### Post by Alterax on 2009-01-25
I see no reason why you couldn't create a boot floppy from within VirtualBox; just make sure to set up the virtual machine to access your floppy drive and you should have no problem.

---

### Post by bapoumba on 2009-01-25
Moved to Windows Discussions.

---

