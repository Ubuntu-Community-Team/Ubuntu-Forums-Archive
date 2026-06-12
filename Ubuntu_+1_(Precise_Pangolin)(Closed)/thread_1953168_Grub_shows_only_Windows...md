---
title: "Grub shows only Windows.."
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Baldrick_NZ on 2012-04-05
Hi all,

Following the latest kernel upgrade, and changing the name with Grub Customizer (as I usually do), and rebooting, the only option I now get to boot to is Windows.

I did 'ls fdisk -l' using a live USB and my Ubuntu drive shows up, but I have no idea where to go from here to re-instate Ubuntu to my Grub menu.

Any help would be much appreciated!

Thanks in advance..

---

### Post by Quackers on 2012-04-05
It may be an idea to purge then re-install grub using the chroot method mentioned in this guide
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by ranch hand on 2012-04-05
> **Baldrick_NZ said:**
> Hi all,

Following the latest kernel upgrade, and changing the name with Grub Customizer (as I usually do), and rebooting, the only option I now get to boot to is Windows.

I did 'ls fdisk -l' using a live USB and my Ubuntu drive shows up, but I have no idea where to go from here to re-instate Ubuntu to my Grub menu.

Any help would be much appreciated!

Thanks in advance..
```

echo "Adding Lounge on sda11" >&2 
cat << EOF
menuentry "Lounge on sda11" {
    set root=(hd0,11)
        linux /vmlinuz root=/dev/sda11 ro splash quiet
        initrd /initrd.img
}
EOF

```
Add that to your /etc/grub.d/40_custom file.  Save the file as 06_custom.  Run;
```

sudo-update grub

```
This will give you,  after editing to match your partition table, a menuentry that will boot the newest Debian based kernel on the defined partition.

The stuff between the "" marks is up to you,  You can leave it as it is and it will still work.  The first is what you see when you run "update-grub" (thus the "echo" command).  The second is what you will see on the screen menu.

The part that does the bootloading is between the {} marks.  Make sure that matches your Ubuntu partition.

If you can't boot to ubuntu use the directions for chrooting in here;
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
contents number 12 so that you can run update-grub.

Learn to work with grub directly instead of using 3rd party apps.

While you are snooping around it your /etc/grub.d directory you may want to check the permissions on your 10_linux file.  I would say the thing is no longer enabled to be executed.  This is what generates your menuentries for the install handling bootloading chores.

You are seeing MS because it is handled by 30_os-prober which is responsible for the generation of all other installs.  It is obviously enabled to be executed.

---

### Post by Baldrick_NZ on 2012-04-06
> **Quackers said:**
> It may be an idea to purge then re-install grub using the chroot method mentioned in this guide
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

This worked a treat!

Thanks you guys, much appreciated.

---

### Post by mörgæs on 2012-04-06
Please mark the thread 'solved' using 'thread tools'.

---

