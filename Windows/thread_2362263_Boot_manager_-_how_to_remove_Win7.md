---
title: "Boot manager - how to remove Win7"
date: 2017-05-26
forum: Windows
---

### Post by jaro27 on 2017-05-26
Hallo,
 
can you please help me to remove the second win7 from my boot manager?

Details:
I did split my disc into two, installed different win7 on each one.
Than deleted the second win7 , merged the discs into one again.

Problem is, the deleted win7 still appears in boot manager..cant remove it..

What I tried and not worked for me:
OS-Uninstaller
Boot repair
grub-customizer (booted Ubuntu from USB - Grub doesn't see my wins..)
bootrec.exe via WIN install usb
msconfig (cant run it - limited rights in my first win)


Thanks a lot!
J.

---

### Post by wildmanne39 on 2017-05-26
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by Bucky Ball on 2017-05-26
Welcome. Can we see your fstab file, please? Open a terminal and issue this:

```
nano /etc/fstab
```

Post that file here between code tags, please.

If you deleted the Win partition, no need to do all that other stuff you're doing. Probably just an entry in fstab, not the OS. What happens when you choose that entry? Error? Nothing? Back to grub list?

---

### Post by howefield on 2017-05-26
Moved to the [s]"*General Help*"[/s] "*Windows*" forum.

---

### Post by jaro27 on 2017-05-26
hi, my fstab file:
```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```
When I choose the second win from boot menu, some kind of error is shown..just want to delete that option from boot manager..the other win is booting smoothly, no problem.

---

### Post by ajgreeny on 2017-05-26
That is a very strange **/etc/fstab** file.

Can you please check again and tell us more about your Ubuntu installation.  You do have Ubuntu installed don't you?

---

### Post by jaro27 on 2017-05-26
[COLOR=#222222][FONT=Verdana]really sorry I haven't made myself clear in my original post.. am uninstalling all OS, leaving this comp with the original WIN7 only.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Ubuntu (17.04) is started from [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]my usb, am in Ubuntu right now..[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]I did successfully uninstall Ubuntu 14.04 and 15.04 in past, just cant delete that second win7 from boot manager...god.)[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I am willing to do any Ubuntu/win7 installation, if it helps to edit that boot manager somehow..[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Thx again
[/FONT][/COLOR]

---

### Post by yancek on 2017-05-26
Your hard drive does not have any Linux/Ubuntu/Grub.  You have Syslinux boot code in the MBR of your windows hard drive.  Use your windows installation DVD with the Repair option to overwrite this code as explained at the windows 7 forum below:

[https://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](https://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Once you do that, if you still have the second windows entry in your boot menu, you will need to use the windows tool 'bcdedit' to remove.  Lots of tutorials on it's use.  I don't see how you would be able to do that from any Linux and you don't have Linux on your computer.

---

### Post by jaro27 on 2017-05-29
Thanks a lot guys, did exactly what Yancek suggested in last post, worked perfectly for me.)

---

