---
title: "Boot Repair help needed."
date: 2015-03-31
forum: Ubuntu/Debian BASED
---

### Post by linch2 on 2015-03-31
So today I tried installing an Ubuntu based OS alongside windows and it worked except for one thing...

On starting my system I am greeted by a grub menu listing Ubuntu, ubuntu advanced options, memory testing environments, Windows 8 and windows recovery environment
(only the first 3 options actually work).
When I choose any one of the windows options the system informs me that the boot data or some data cannot be found and it then tells me to insert installation media for 
windows in order to resolve this problem. I checked my HDD and SSD and all my windows data is still there, the system is just unable to access it on startup. When I created partitions 
for my installation I shrunk a partition in my SSD to create free space(20GB) for my install.

**This is how I partitioned upon install:**
[LIST]
[*]'/dev/sda'  -used for device bootloader installation      (on HDD) 
[*]'/dev/sda9' -used for the root file system "/"               (on SSD) 
[*]'/dev/sda10' -used for "/home"                                  (on SSD) 
[/LIST]
           (I left all of the other partitions unused during installation because they were being used by windows files)

After I realised that my installation was faulty I tried "**Boot-Repair**" and it** did not fix the problem**.
_Here is the link created from boot repair program_:  [http://paste.ubuntu.com/10713356/](http://paste.ubuntu.com/10713356/)[INDENT]**1.** What can I do to resolve this problem so that I can choose to boot Windows or Ubuntu upon startup ?
[/INDENT]
[INDENT]**2.** Do I need to select any of the options in 'advanced options' in the Boot-Repair program or do I need to change something else ?
**3.** Would I need to change my UEFI settings/Boot settings or will I need to change my partitioning?
**4. **If so, how would I do this?

[/INDENT]
If anyone could help I would greatly appreciate it.
Thank you.

---

### Post by corneliuss2 on 2015-03-31
That is a Windows error. Ubuntu will never ever tell you to insert Windows installation media :)

---

### Post by linch2 on 2015-03-31
So how do i fix it?

---

### Post by corneliuss2 on 2015-03-31
How did you shrunk your partition? Have you used Windows DiskPart or with the Ubuntu installation media?

---

### Post by linch2 on 2015-03-31
I shrunk the partition using Windows DiskPart and then when installing Ubuntu I assigned the free space to '/' and '/home' .

---

### Post by linch2 on 2015-03-31
If I need to change my partitioning how would I do this? If not, what do I need to change?

---

### Post by ajgreeny on 2015-03-31
I am no expert but it looks as if you have fallen foul of the UEFI problem that you installed Ubuntu in legacy BIOS mode but Windows 8 is in UEFI mode.

I have never used Boot-repair so I can not tell you the best way to proceed, but it may be simplest to install Ubuntu again, making sure that the USB or DVD is booted in UEFI mode. The entries in the list of boot devices you see when you press the appropriate key will start with UEFI for those devices that you must use or you will end up in the same situation.  Grub is currently in the MBR of sda which is incorrect for a UEFI system.

With luck our UEFI guru, oldfred may see this thread and give you some advice on how best to proceed; he may suggest you use the boot-repair default suggestion but I would not do that without further advice, and I haven't used windows for several years so can not tell you anything more helpful about how to move forward from here.

Regarding your partitions, I believe you will need to rethink what you have done as you have allowed only 6GB for the Ubuntu install;  Whilst you might just get an installation in that sized partition, depending on exactly which OS this is, there will be little spare space for additional applications or files.  My root partition is now just over 8GB in size and I'm using Xubuntu which is not as large as Ubuntu when first installed, if I remember correctly.

---

