---
title: "using lilo breaks mounting / rw"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by FrancisBacon on 2012-02-15
I've been trying to get 12.04 to boot with lilo, and everything seems to work, until very late  in the boot process, after the fsck I get:

> 
fsck from until-linux 2.20.1
/dev/sda3: clean, 11/1703936 files, 150961/6811134 blocks
The disk drive for / is not ready yet or not present.
Continue to wait, or Press S to skip mounting or M for manual recovery
What is putting out that message?
Why does it work with grub and not with lilo?

My lilo config:
> 
boot = /dev/sda
lba32
change-rules
  reset
vga = normal
large-memory
image = /boot/vmlinuz-3.2.0-15-generic
  root = /dev/sda1
  initrd = /boot/initrd.img-3.2.0-15-generic
  label = Ubuntu
  append = "ro"
As far as I can tell grub is only giving the kernel "root=UUID... ro quiet slash vt.handoff=7" none of which should change what a process thinks is the root device.

Help and understanding would be  appreciated. Thanks.

---

### Post by VMC on 2012-02-15
I haven't used lilo in years, but I have read others use in current distros all the time. 

My current Precise iso install doesn't have 'vmlinuz-3.2.0-15-generic', but 3.2.0-16. Are you sure you have 3.2.0-15? Probably so or else you should have a message stating that.

---

### Post by effenberg0x0 on 2012-02-15
Not a lilo user here. But I'd check a couple stuff:

If root really is at /dev/sda1, what is at /dev/sda3?
In fstab, wheres /?
```
cat /etc/fstab
```Checking UUIDs...
```
sudo vol_id -u /dev/sda1 
```or
```
sudo vol_id -u /dev/sda3
```Which /dev/sda(n) is equal to the UUID you see in Grub?
```
cat /proc/cmdline
```

Or you can get more info by:
```
sudo blkid
```or
```
ls -la /dev/disk/by-uuid/*
```Regards,
Effenberg

---

### Post by FrancisBacon on 2012-02-16
> **VMC said:**
> I haven't used lilo in years, but I have read others use in current distros all the time. 

My current Precise iso install doesn't have 'vmlinuz-3.2.0-15-generic', but 3.2.0-16. Are you sure you have 3.2.0-15? Probably so or else you should have a message stating that.

Thanks for your question. I had not done a dist-upgrade to that image.
But Lilo would not have found the kernel to boot it if the name was incorrect.
This error happens well after the kernel is loaded.

---

### Post by FrancisBacon on 2012-02-16
> **effenberg0x0 said:**
> Not a lilo user here. But I'd check a couple stuff:

If root really is at /dev/sda1, what is at /dev/sda3?


Root is /dev/sda1
/dev/sda3 is an extra data partition. I added that line for context so people knew which part of the boot process I was asking about (ie. after the fscks have started)

Sorry for the confusion.
> 
In fstab, wheres /?
my fstab  contains the following for /dev/sda1

```

# / was on /dev/sda1 during installation
#UUID=39e4f1a9-8ab9-45f8-adb7-a2753b3feb88 /               ext4    errors=remount-ro 0 
/dev/sda1 /               ext4    errors=remount-ro 0 

```and blkid gives me:

```


# blkid /dev/sda1
/dev/sda1: UUID="39e4f1a9-8ab9-45f8-adb7-a2753b3feb88" TYPE="ext4" 

```And they are equal.
As are /dev/disk/by-uuid/

If I change fstab to use UUID or device to mount / it doesn't matter. I still hit "The disk drive for / is not ready yet or not present."

Any other ideas?
Is there a easy way to grep all of the Ubuntu boot up program source so I can find out what program is producing the "The disk drive for / is not ready yet or not present." message? I could probably back trace this easier if I just knew the program or script that is producing the error.

Thanks.

---

### Post by FrancisBacon on 2012-02-16
> **FrancisBacon said:**
> 

Is there a easy way to grep all of the Ubuntu boot up program source so I can find out what program is producing the "The disk drive for / is not ready yet or not present." message? I could probably back trace this easier if I just knew the program or script that is producing the error.



So, I got of my butt and let my fingers do the walking...

 find / -xdev -type f -print0 | xargs -0 fgrep -l "The disk drive for" 2>/dev/null

/sbin/mountall

So, this is where the error is coming from, which makes sense, because mountall is making the fsck messages.

Now I just have to build my own mountall with debugging turned on, and maybe I can get to the heart of the matter.

---

### Post by cariboo on 2012-02-16
What do you hope to accomplish by using lilo instead of grub?

---

### Post by FrancisBacon on 2012-02-16
> **cariboo907 said:**
> What do you hope to accomplish by using lilo instead of grub?

I hope this thread won't get side tracked off of the technical problem of getting lilo working, but to answer your question, grub is too helpful for a hostile user environment. I need a boot loader that gives no options to the user in front of the keyboard.

Also grub's package install and removal are far too helpful, bringing up unscriptable ncurses displays, and I have never found a easy way to hack the debconf entries for grub to do the right things. The best solution for all these problems is to toss grub and use another boot loader, in this case lilo.

---

### Post by cariboo on 2012-02-16
Question answered, thank you, now back to the regular thread. :)

---

### Post by effenberg0x0 on 2012-02-16
I think "boot", "root" and "append" parameters could be defined before "image". I'm not sure if the other parameters are valid.
Try this in lilo.conf:
```
boot = /dev/sda
root = /dev/sda1
append = "ROOT=/dev/sda1 ro"                      
lba32
change-rules
reset
vga = normal
large-memory
image = /boot/vmlinuz-3.2.0-15-generic
initrd = /boot/initrd.img-3.2.0-15-generic
label = Ubuntu
```Regards,
Effenberg

---

### Post by FrancisBacon on 2012-02-16
> **effenberg0x0 said:**
> I think "boot", "root" and "append" parameters could be defined before "image". I'm not sure if the other parameters are valid.
Try this in lilo.conf:
```
boot = /dev/sda
root = /dev/sda1
append = "ROOT=/dev/sda1 ro"                      
lba32
change-rules
reset
vga = normal
large-memory
image = /boot/vmlinuz-3.2.0-15-generic
initrd = /boot/initrd.img-3.2.0-15-generic
label = Ubuntu
```Regards,
Effenberg

Thanks for the suggestion. In lilo there are two areas to configure options like root=.
One is globally, and the other is per image. Since I have one 'image' it should not
matter which section it is in. 

I have tried it as your suggested changes without any difference. It still dies in mountall.

---

### Post by effenberg0x0 on 2012-02-16
> **FrancisBacon said:**
> Thanks for the suggestion. In lilo there are two areas to configure options like root=.
One is globally, and the other is per image. Since I have one 'image' it should not
matter which section it is in. 

I have tried it as your suggested changes without any difference. It still dies in mountall.

Just checking: You tried the append = "ROOT=/dev/sda1 ro" line right?

I'm telling you this because initramfs-tools was patched for the exact same bug you are having by the end of 2011. A function that reads the device in the /dev/sd(n) format and transforms it in a (${Major},${Minor}) device representation (as required by the bootloader) would fail to understand the device name unless it was clearly mentioned in the append line and declared before the image name.
 
Another possibility I was thinking was if you simply need to update your initramfs
On lilo tutorials, that was done with "cd /boot && mkinitramfs  -o initrd.lilo  `uname -r`", but we do have "sudo update-initramfs -u" in Ubuntu.

So, I think I would let the boot go until mountall fails, choose 'M' to recover it manually. At this point, you can probably remount it RW with mount -o remount,rw / because fstab is correct. Then cd /boot and update-initramfs -u. If you Ctrl+D from there it will boot, but you can just shutdown -r and see how a cold boot goes. Just a blind attempt though, as I don't have a lilo-based system to try it now.

Regards,
Effenberg

---

### Post by FrancisBacon on 2012-02-23
> **effenberg0x0 said:**
> Just checking: You tried the append = "ROOT=/dev/sda1 ro" line right?


Thank you for your reply. This did finally fix the problem.

I tried this last week but for some reason it failed, but after a dist-upgrade
and a new kernel, trying it again succeeded.

In case other people are having the same problem I'll add some extra documentation.

With my normal lilo.conf append lile of just 'ro' the kernel gets:

```

[    0.000000] Command line: auto BOOT_IMAGE=Ubuntu root=801 ro
[    0.000000] Kernel command line: auto BOOT_IMAGE=Ubuntu root=801 ro

```but with:

append = "root=/dev/sda1 ro"

It gets:

```

[    0.000000] Command line: auto BOOT_IMAGE=Ubuntu root=801 root=/dev/sda1 ro
[    0.000000] Kernel command line: auto BOOT_IMAGE=Ubuntu root=801 root=/dev/sda1 ro 

```And mountall does correctly mount /

Thanks again for the help.

---

