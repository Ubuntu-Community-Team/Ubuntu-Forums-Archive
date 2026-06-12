---
title: "Existing Ubuntu Karmic inside Vista"
date: 2009-10-29
forum: Virtualisation
---

### Post by Jack.Straw on 2009-10-29
Hi.  I'm wanting to using my existing Ubuntu 9.10 partition inside Vista via virtual box.  I found this tutorial:

[http://www.ltyer.com/wordpress/tutorial-boot-existing-ubuntu-partition-using-virtualbox-inside-windows](http://www.ltyer.com/wordpress/tutorial-boot-existing-ubuntu-partition-using-virtualbox-inside-windows)

However, 9.10 is using Grub2 which no longer uses menu.lst.  Can anyone tell me how I to create the boot.iso using grub2?  

On a side note, I have to say that i do not like grub2 so far.  No menu.lst, and we're not supposed to edit grub.cfg, so changing the boot order is a pain.  Re-ordering the items in /etc/grub.d changes the boot order in a general sort of way, but gives no real control over what gets displayed and in what exact order.  Should I just remove grub2 from Karmic and install grub?  Will Karmic udates revert me back to grub2 if i do?


Thanks for your time,
-Scott

---

### Post by wildweathel on 2009-11-02
Here's a rough idea for how to boot Karmic/Lucid/other-grub2-based system in Virtualbox.  I haven't tried this yet, but it seems like it should work.  Basically, we're going to create a small virtual hard disk to boot the virtual machine.  


* Get a CD image of Damn Small Linux.  We'll use this for setup.

* Follow the instructions you have to create a virtual disk that maps to your real disk.  Ubuntu must have access to its own partitions.  It **must not** have write access to Vista's.  Otherwise, you might accidentally chain-boot Vista on Vista and trash Vista's partition.  Ouch.

* Create a second small (100MB) expanding virtual disk.  You can use the Virtualbox GUI for this.  This will be the boot disk.  

* Mount the CD image and boot DSL in Virtualbox.

* Format the virtual disk as ext3.  Copy /boot/grub/core.img to this disk.

* Set-up grub-legacy on the virtual disk.  Basically, this will involve copying stage1 ext2_stage1_5 and stage2 from DSL to the disk, creating a menu.lst, then installing grub-legacy to the MBR of the virtual disk.  I have to try this to give exact details.

* Shut down the vm.

* Set up the vm to boot from the virtual disk.

* Start it up and enjoy Ubuntu-in-Vista.  Hopefully.

The menu.lst file should end up something like this:
```

timeout 1
hiddenmenu
title Ubuntu 9.10 (Karmic Koala)
root (*grub-legacy name of **ubuntu** root partition*)
kernel (*grub-legacy name of **virtual boot** partition*)/core.img
boot

```Rather than booting the linux kernel directly, this will load the grub2 bootloader.  The advantage of this is when Ubuntu installs a new kernel, it will automatically be added to the boot menu (rather than having to regenerate an ISO).  Unfortunately, there is a bit of a fly-in-the-ointment here.  This will use the same default in the virtual machine as the whole system.  That's why it's so important to keep Vista from shooting itself when it double-boots--and it's only a matter of time before it does.  We have to copy core.img, because grub-legacy can't read ext4.  I'd use grub2, but I'm not enough of a grub wizard to understand it.

---

