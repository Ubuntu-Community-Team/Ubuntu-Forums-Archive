---
title: "Customize Grub2."
date: 2017-06-07
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-06-07
Hi everybody.  TodayI installed  Ubuntu 17.10 daily, so far so good.  What I need helpwith is grub2.  Grub Customizer will not be available until afterrelease.  So far I have found guides to change resolution and remove memtest, now I need to also remove advanced options and rename entries. The two guides I found worked and I saved the webpages to myUbuntu favorites folder in browser.  Can anyone help me with the last two?


Henry.

---

### Post by deadflowr on 2017-06-07
> The two guides I found worked and I saved the webpages to myUbuntu favorites folder in browser.
What two guides? So we don't refer you to something you might already have read.

But my two cents would be to follow cavfans guide:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")

Once you get your custom entries sorted, I would boot into them to make sure they work as expected.
Then you can just disable the default entries with
```
sudo chmod -x /etc/grub.d/10_linux
```
this will remove the Advance options you would see for the default OS (or the top entries, if you will)

If you want to also disable the os-prober (that is used to probe the machine for other operating systems)
You can actually do that from within the config file /etc/default/grub.
just add the line:
```
GRUB_DISABLE_OS_PROBER=true
```

That make any sense?

---

### Post by Hewjr100 on 2017-06-07
The following are the guides I used.

[https://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution](https://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution)

[https://askubuntu.com/questions/608632/how-can-i-remove-memtest-from-boot-menu](https://askubuntu.com/questions/608632/how-can-i-remove-memtest-from-boot-menu)

Henry.

---

### Post by Cavsfan on 2017-06-07
Thanks for the mention deadflowr.

If you make up a text file like this with your drives and partitions, you will get what I think you want.
The only text you will see on the grub menu is what you put between the quotes.

I'm booting Arch Linux, Xubuntu Xenial Xerus 16.04 LTS, Xubuntu Zesty Zapus 17.04 and Windows 10.

```
#!/bin/sh
echo 1>&2 "Adding Arch Linux, Xubuntu Xenial Xerus 16.04 LTS, Xubuntu Zesty Zapus 17.04 and Windows 10"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Arch Linux" {
    set root=(hd0,2)
        linux /boot/vmlinuz-linux root=/dev/sda2 rw quiet
        initrd /boot/initramfs-linux.img
}
menuentry "Arch Linux (Recovery Mode)" {
    set root=(hd0,2)
        linux /boot/vmlinuz-linux root=/dev/sda2 rw single
        initrd /boot/initramfs-linux.img
}
menuentry "Arch Linux (Fallback)" {
    set root=(hd0,2)
        linux /boot/vmlinuz-linux root=/dev/sda2 rw quiet
        initrd /boot/initramfs-linux-fallback.img
}
menuentry "Arch Linux (LTS Kernel)" {
    set root=(hd0,2)
        linux /boot/vmlinuz-linux-lts root=/dev/sda2 rw quiet
        initrd /boot/initramfs-linux-lts.img
}
menuentry "Arch Linux (LTS Kernel Fallback)" {
    set root=(hd0,2)
        linux /boot/vmlinuz-linux-lts root=/dev/sda2 rw quiet
        initrd /boot/initramfs-linux-lts-fallback.img
}
menuentry "Xubuntu Xenial Xerus 16.04 LTS" {
    set root=(hd0,4)
        linux /vmlinuz root=/dev/sda4 ro quiet splash
        initrd /initrd.img
}
menuentry "Xubuntu Xenial Xerus 16.04 LTS (Recovery Mode)" {
    set root=(hd0,4)
        linux /vmlinuz root=/dev/sda4 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Xubuntu Zesty Zapus 17.04" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
menuentry "Xubuntu Zesty Zapus 17.04 (Recovery Mode)" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 10" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}

```

You only need the UUID of the windows partition and you would save this file as **/etc/grub.d/06_custom**

**sudo blkid** will give you the disk/partitions you need.

This may be needed since you are booting Windows UEFI: 
[https://help.ubuntu.com/community/UEFIBooting#Non-Mac_x86_64_UEFI_specific_info](https://help.ubuntu.com/community/UEFIBooting#Non-Mac_x86_64_UEFI_specific_info)

I don't think you'll need anything else for Ubuntu but, it will be somewhere on that page if you do.

Once you are confident that all entries do what you want, you can make the other files unexecutable (I find this the easiest way).
Mentioned here: [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Final_changes](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Final_changes)

Also labeling your partitions is a good idea as it's easier to see which partition is which:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labelling_the_partitions](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Labelling_the_partitions)

Here is my current grub menu on 17.04:
[[IMG]http://www.zimagez.com/miniature/20170419165958.jpg[/IMG]]("http://www.zimagez.com/zimage/20170419165958.php")

With these three colors:
```
    echo " set color_normal=yellow/black"
    echo " set menu_color_normal=cyan/black"
    echo " set menu_color_highlight=red/black"
```

---

### Post by Hewjr100 on 2017-06-07
Ok got it.  Will start working on it now.

Henry

---

### Post by Cavsfan on 2017-06-08
> **Hewjr100 said:**
> Ok got it.  Will start working on it now.

Henry

Forgot this but, you'll need to make **/etc/grub.d/06_custom** executable after you have created it.

**sudo chmod +x /etc/grub.d/06_custom** and then **sudo update-grub** for the new menu to show up.
Everything that is default will still show up below this new menu.

Every time you make any change to any grub file you will need to enter **sudo update-grub** in terminal for the changes to "stick" upon rebooting.

This is all redundant as you are reading the wiki, all of this is in there.

Let me know if you need any assistance by posting your issue in the blue link in my signature or this thread will do if you prefer.

Regards

---

