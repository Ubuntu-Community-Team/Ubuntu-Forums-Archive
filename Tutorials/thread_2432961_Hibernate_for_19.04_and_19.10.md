---
title: "Hibernate for 19.04 and 19.10"
date: 2019-12-11
forum: Tutorials
---

### Post by GhX6GZMB on 2019-12-11
Getting Hibernate working on Ubuntu is hairy, but absolutely doable. Here's the recipe:

First, forget making a "swap file", it won't work. You really need a **swap partition *** [There are other opinions, but this is my experience]*

Here's the way to do it successfully:

1: repartition your HDD/SSD to make a swap partition that's as large or larger than your RAM. In my case it's **/dev/sda2**

2: make a swap partition using **sudo mkswap /dev/sda2**

3: execute **sudo swapon /dev/sda2**

4: verify the partition with **sudo lsblk** and **sudo blkid** and copy the UUID of **/dev/sda2** 

5: configure initramfs by creating (or editing) **/etc/initramfs-tools/conf.d/resume** to contain the following line: **RESUME=UUID=***yourswapUUID*

6: modify **/etc/default/grub** by adding **resume=UUID=***yourswapUUID* within the quotes in **GRUB_CMDLINE_LINUX_DEFAULT=**"quiet splash ..."

7: check that the **/etc/fstab** file contains **UUID=***yourswapUUID* **none swap defaults 0 0 **if not, create the line

8: execute **sudo update-grub** and[B] sudo update-initramfs -u
[/B]
9: update policies by creating (or editing) **/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla** with the following content:


```


 [Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

 [Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=yes 


```

10: edit /etc/default/grub and add this line: **GRUB_RECORDFAIL_TIMEOUT=$GRUB_TIMEOUT**

11: execute **sudo update-grub**

12: reboot

13: On many PCs, XSreenSaver is the default screensaver and causes trouble when hibernating. Disable "Power Management Enabled" under the "Advanced" Tab in XScreenSaver.

14: for CLI Hibernate, you'll need to install: **sudo apt install hibernate**. Then **sudo hibernate** will work.

Hibernate is now set up and enabled, if you want to use the Lid switch it just needs to be set as such [eg, Preferences -> LXQt Settings -> Power Management]. Enjoy :)

---

