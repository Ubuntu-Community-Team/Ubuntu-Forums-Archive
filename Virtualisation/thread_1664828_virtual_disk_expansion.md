---
title: "virtual disk expansion"
date: 2011-01-11
forum: Virtualisation
---

### Post by rpscaringe on 2011-01-11
I have a virtual machine running on  VirtualBox 3.1.6_OSE,  The on-line user manual describes the --resize option for the  "VBoxManage modifyhd" command, but this option is not recognized by version 3.1.6_OSE of the  Virtual Box Command Line Interface.  
Will the --resize option be available sometime soon?
Is there another way to increase the virtual  disk space for the virtual machine?

---

### Post by gmargo on 2011-01-13
You could always add second virtual hard disk.  Just like in the non-virtual world. :-)

Very little googling turned up this procedure to create a bigger disk and copy over your old disk: [http://www.my-guides.net/en/content/view/122/26/](http://www.my-guides.net/en/content/view/122/26/)

---

### Post by darkhelmetchris on 2011-01-13
The resize option is great, when and if it works.  If you can't get it to go, you can do this sort of thing...

Your Ubuntu LiveCD image .ISO is a wonderful tool for this.  

1.  Backup, backup, backup (don't say you were not warned)
2.  Add a second larger disk to your virtual machine.
3.  Start your virtual machine using Ubuntu Live via CD image .ISO
4.  Use "dd" to copy your disk to the new disk (note that this step will take time, and depends on your disk size), substituting your own device identifiers here like this:
```
dd if=/dev/sda of=/dev/sdb
```5.  Start GParted from your Live session, and increase the size of your partition on the new disk to suit your needs, and set the bootable flag as needed.
6.  Shut down the virtual machine, unlink the original disk image (hold on to it until you're happy and can delete it), assign your new disk image as your primary drive
7.  Start 'r up.

---

### Post by rpscaringe on 2011-01-19
You guys are good, worked like a charm, thanks.
darkemetchris-the process was as you said, but that wasn't enough detail for me
gmargo- couldn't have done it without the web tutorial you googled up...recommended!
all-the VirtualBox gui has changed enough that you'll need to compensate a bit

---

### Post by rpscaringe on 2011-01-19
You guys are good, worked like a charm, thanks.
darkemetchris-the process was as you said, but that wasn't enough detail for me
gmargo- couldn't have done it without the web tutorial you googled up...recommended!
all-the VirtualBox gui has changed enough that you'll need to compensate a bit

---

