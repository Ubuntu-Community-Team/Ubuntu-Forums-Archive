---
title: "Help with arch on USB? I created a chart, but need some help."
date: 2009-03-25
forum: The Cafe
---

### Post by dragos240 on 2009-03-25
Okay, i want to install arch linux to my flash drive, trouble is, it doesn't want to boot, i have made a plan, i scanned it and cropped it, i hope you can read my sloppy handwriting,  i can't really get the first part down, becuase i don't know what the requirments are to make a USB boot, the livecd works good, but i want an arch USB that i can save files to while using arch, not the cruddy read-only filesystem, can anyone help me?

[ATTACH]107620[/ATTACH]

---

### Post by Skripka on 2009-03-25
> **dragos240 said:**
> Okay, i want to install arch linux to my flash drive, trouble is, it doesn't want to boot, i have made a plan, i scanned it and cropped it, i hope you can read my sloppy handwriting,  i can't really get the first part down, becuase i don't know what the requirments are to make a USB boot, the livecd works good, but i want an arch USB that i can save files to while using arch, not the cruddy read-only filesystem, can anyone help me?

[ATTACH]107620[/ATTACH]

1st things 1st.


Are you CERTAIN, that your BIOS will let you boot off USB?

---

### Post by dragos240 on 2009-03-25
absolutely, i used the linux version of unetbootin to install the livecd of arch core to the usb and booted it. It worked, but i can't save any files becuase of the read only filesystem.

---

### Post by Skripka on 2009-03-25
If you have an Arch installed and configured on a machine, you could just rsync that install to the drive, and then (re)configure the GRUB on it....I think.

Or.


As I recall the beginners Wiki talks about running the installer CD and setting the destination to the USB flash volume.

---

### Post by dragos240 on 2009-03-25
i did, but it doesn't want to boot that way, there must be something that helps USB drives boot. Thats what i want to figure out.

---

### Post by dragos240 on 2009-03-25
Okay i read an arch wiki page about installing arch to a usb stick and it is very confusing, can someone explain [this]("http://wiki.archlinux.org/index.php/Installing_Arch_Linux_on_a_USB_key") to me? I don't know how to "modprobe" anything, i also don't know what to edit when i am editing /arch/setup lines 95 and 98, i am pretty darn confused with this :(.

---

### Post by dragos240 on 2009-03-26
Bump!

---

### Post by smartboyathome on 2009-03-26
Have you tried Larch? It should work for you. :)

---

### Post by .Maleficus. on 2009-03-26
My first install of Arch was onto a USB drive.  The installation should be no different than a normal install, a few tips though.

1.  Use ext2 for /.  No need to journal on such a small amount of space.
2.  For your Grub, use UUIDs.  

Other than that, like I said, it's no different than a normal install.

---

### Post by dragos240 on 2009-03-26
my problem though is mounting the usb drive.

---

### Post by .Maleficus. on 2009-03-26
I guess I can't help with that then since the partitioner recognized mine automatically.


Edit:  You could try opening up another v/c and running "blkid" to see what the device is listed as.  After that it should just be a matter of running "mount" with the correct parameters.

---

### Post by dragos240 on 2009-03-26
Hmm... yeah, even in the ubuntu i am running right now it doesn't recognise it via blkid (is that block id?)

---

### Post by dragos240 on 2009-03-27
bump

---

