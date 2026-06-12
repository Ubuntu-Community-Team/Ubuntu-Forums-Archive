---
title: "Strange Grub Problems..."
date: 2013-01-15
forum: Server Platforms
---

### Post by 1egoman on 2013-01-15
Hello fellow linux users,

I have a strange problem here. I have an ubuntu server 12.04 installation, and every time I reboot the computer grub fails to make the computer boot. In order to make the server boot, I must insert a flash drive with ubuntu on it and run the tool boot repair. Then, It will boot. However, none of the startup applications (such as apache2) actually start ACCEPT ssh. What is exactly happening here, because I have spent countless hours trying to figure out!

Thanks for reading...

---

### Post by cariboo on 2013-01-15
Just to make sure all the i's are dotted, and the t's are crossed, bott from your live usb, and chroot your / partition. Once at the desktop, run the following commands:

```
sudo mount /dev/sdaX /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo mount chroot /mnt
```

/dev/sdaX = your / partition

Once at the prompt type:

```
install-grub /dev/sda
```

grub must be installed on your first hard drive, then type:

```
update-grub
```

you should see a listing of the kernels you have installed, and memtest.

once the last command has completed, press Ctrl-d twice, and reboot.

---

### Post by 1egoman on 2013-01-16
> **cariboo907 said:**
> Just to make sure all the i's are dotted, and the t's are crossed, bott from your live usb, and chroot your / partition. Once at the desktop, run the following commands:

```
sudo mount /dev/sdaX /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo mount chroot /mnt
```

/dev/sdaX = your / partition

Once at the prompt type:

```
install-grub /dev/sda
```

grub must be installed on your first hard drive, then type:

```
update-grub
```

you should see a listing of the kernels you have installed, and memtest.

once the last command has completed, press Ctrl-d twice, and reboot.
Thanks for the reply... FWIW, I needed to mount dev and usr, but now I'm just booting into a grub terminal.... What do I do now?

---

### Post by YannBuntu on 2013-01-16
Hi > **1egoman said:**
> In order to make the server boot, I must insert a flash drive with ubuntu on it and run the tool boot repair. Then, It will boot.

Please indicate the URL that appears after using the Recommended Repair ?

---

### Post by cariboo on 2013-01-17
> **1egoman said:**
> Thanks for the reply... FWIW, I needed to mount dev and usr, but now I'm just booting into a grub terminal.... What do I do now?

Each line in the code box is a separate command, you have to press enter after each one. If you just copied and paste the commands as one whole command, it won't work properly.

In line number 2 is where /dev is mounted, so you shouldn't have to mount it separately. I assumed you have all the directories in / so you shouldn't have to mount /usr too. 

If you do copy/paste all the commands at once. they should be separated by a && eg:

```
sudo mount /dev/sdaX /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo mount chroot /mnt
```

---

### Post by 1egoman on 2013-01-17
@YannUbuntu: [http://paste.ubuntu.com/1539231/](http://paste.ubuntu.com/1539231/)

@Cariboo907: I did type each of the commands in on a seperate line, and 'sudo mount chroot /mnt' gave me an error (can't remember what exactly). Then, I tried just sudo chroot /mnt and I got > chroot: failed to run command `/bin/bash': No such file or directory

So then after mounting dev and usr (and bin I think too), I successfully chrooted and I ran 'grub-install /dev/sda' and 'update-grub'. I rebooted and got a grub terminal. Would the link above help out at all?

---

### Post by YannBuntu on 2013-01-19
> **1egoman said:**
> @YannUbuntu: [http://paste.ubuntu.com/1539231/](http://paste.ubuntu.com/1539231/)

ok.
Boot-Repair's Recommended Repair does the following:
1) it reinstalls grub into the MBR of sdb
2) and it reinstalls grub into the MBR of sda.

( cariboo907's procedure does step 2, so unfortunately it won't do better.)

Next time you have boot problem, please immediately run Boot-Repair --> Create BootInfo , and tell us the new URL that will appear.

Also please make sure that your BIOS is set up to boot your 60GB disk first.

---

### Post by 1egoman on 2013-01-19
> **YannBuntu said:**
> ok.
Boot-Repair's Recommended Repair does the following:
1) it reinstalls grub into the MBR of sdb
2) and it reinstalls grub into the MBR of sda.

( cariboo907's procedure does step 2, so unfortunately it won't do better.)

Next time you have boot problem, please immediately run Boot-Repair --> Create BootInfo , and tell us the new URL that will appear.

Also please make sure that your BIOS is set up to boot your 60GB disk first.
Ok. I can tell you the 60gb disk is set to boot. I'll reboot it tomorow and post the result.

---

### Post by YannBuntu on 2013-01-19
> **1egoman said:**
> Ok. I can tell you the 60gb disk is set to boot. I'll reboot it tomorow and post the result.

ok.
Also disconnect the 1TB disk, and check if the bug persists or not?

---

### Post by 1egoman on 2013-01-20
> **YannBuntu said:**
> ok.
Also disconnect the 1TB disk, and check if the bug persists or not?
With 1TB Disk: [http://paste.ubuntu.com/1552315](http://paste.ubuntu.com/1552315)
Without 1TB Disk: [http://paste.ubuntu.com/1552328](http://paste.ubuntu.com/1552328)

---

### Post by 1egoman on 2013-01-22
---- Bump - Sorry, I really need Help! ----

---

