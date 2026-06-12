---
title: "Installing Windows 7 procedure on partitioned disc?"
date: 2009-01-28
forum: Windows
---

### Post by keithwwalker on 2009-01-28
I currently have 2 partitions on my hard disc.  One is loaded with Ubuntu 8.10 ~150GB and the other is empty (~350GB).

What is the procedure for loading up Windows 7 from the DVD?

I have read discussions on using Virtual Box and that sounds as if it wouldn't use the other partition.

I would rather load to the empty partition

Currently, I get two bootup screens, one from the motherboard, then GRUB.

Both have options to bootup from the DVD drive, but no options about choosing a particular partition.  

Is there a command in GRUB that should be done, or does the Windows 7 installation procedure prompt for which partition to use?

I got to the Windows 7 screen where there is an option to either repair the OS, or install.  I didn't 'install' as I was afraid that there wouldn't be a prompt for which partition to use and all my data would get wiped...

Help anyone????

---

### Post by djb6 on 2009-01-28
I orginally had two partitions as well, one with vista and an empty one.  I was also nervous about clicking that install now button, but the next screen or two later, they give the option of either an upgrade or a custom (clean) install.  If you choose custom, you can choose the partition to install to.  That is what happened when I installed it.

---

### Post by keithwwalker on 2009-01-28
My hard drive thanks you...

Follow on question, once both systems are installed, how does startup work?  Will Grub load first and then you choose between which OS to load?

Thanks

---

### Post by mamamia88 on 2009-01-28
> **keithwwalker said:**
> My hard drive thanks you...

Follow on question, once both systems are installed, how does startup work?  Will Grub load first and then you choose between which OS to load?

Thanks

you just have to restore grub from the live cd [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by keithwwalker on 2009-01-29
I assume you used the 'Quick Start' method and that lets you select either OS at startup?

Thanks

> **mamamia88 said:**
> you just have to restore grub from the live cd [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

