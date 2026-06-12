---
title: "Kernel Panic and File Corruption"
date: 2008-01-02
forum: Server Platforms
---

### Post by tim.n9puz on 2008-01-02
I have a 386 based file server (no GUI) running 6.06.1 LTS. Yesterday, the building had some electrical problems and the machine won't boot normally.

The Grub menu lists the following two kernels:

2.6.15-28-server

2.6.15-26-server

The "-28" version is the one that fails with a kernel panic. The "-26" version boots just fine and I've edited /boot/grub/menu.lst to use it as the default for now.

What steps do I need to perform to remove the corrupted "-28" version from the system and then get a fresh copy with apt?

Tim

---

### Post by cdenley on 2008-01-02
I'm not sure, but maybe
```

sudo dpkg -P linux-image-2.6.15-28-server
sudo apt-get install linux-image-2.6.15-28-server

```

---

### Post by andol on 2008-01-02
If I were you I'd take a close look at the hard drive. It might have gotten itself somewhat of a kiss. In a case like this SMART should be able to tell you what's happened.

---

### Post by cdenley on 2008-01-02
You can also check for bad sectors by booting to a livecd and running "sudo cat /dev/hda>/dev/null" where /dev/hda is the path to your hard drive. If there is any unreadable data on the drive, it will give you an error.

---

### Post by tim.n9puz on 2008-01-02
Here's what I ended up doing after reading here and elsewhere. The system is running and booting normally now.

In the /boot directory I deleted all of the files that refered to the 2.6.15-28-server kernel (the one that would not boot.)

I edited /boot/grub/menu.lst to remove the references to the offending kernel and changed the default to the older kernel that I needed to get things running.

Reboot the computer with the following command: 

[INDENT][FONT="Courier New"]sudo /sbin/shutdown -r -F now[/FONT] [/INDENT]

to force a file system check by fsck on reboot.

Once the computer rebooted I checked the running kernel version with 
[INDENT][FONT="Courier New"]uname -a[/FONT][/INDENT] 
to verify it was the one I wanted.

Finally I ran 
[INDENT][FONT="Courier New"]sudo apt-get update && sudo apt-get dist-upgrade[/FONT][/INDENT] 
to download and install the latest kernel which was 2.6.15-29-server. I rebooted one last time to switch to the new kernel and all is right in the world.

---

