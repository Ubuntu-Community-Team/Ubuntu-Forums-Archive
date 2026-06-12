---
title: "Ubuntu won't proceed further than the log on screen"
date: 2016-02-22
forum: Virtualisation
---

### Post by Javeria_Qureshi on 2016-02-22
Hello everyone,

I am a new user to the Ubuntu community, and I am facing some problems with the install. I have installed Ubuntu on a virtual machine (virtual box) using an ISO image. After the installation finished, I restarted the VM and logged onto my account. However, after I log on I see the Ubuntu wallpaper for a time (1 minute) and then I get prompted to enter the password again. This process keeps on repeating  and repeating. What should I do?

---

### Post by sandyd on 2016-02-22
Hi, what settings are you using for the VirtualBox VM?

I find that sometimes VirtualBox recommends a bit too little RAM by default. 1GB minimum should be allocated for a working system, 1GB+ if you need multiple programs running. If you want the VM to require less memory, use a lighter flavor of Ubuntu such as Xubuntu or Lubuntu which come with lighter desktop interfaces.

---

### Post by Javeria_Qureshi on 2016-02-23
> **sandyd said:**
> Hi, what settings are you using for the VirtualBox VM?

I find that sometimes VirtualBox recommends a bit too little RAM by default. 1GB minimum should be allocated for a working system, 1GB+ if you need multiple programs running. If you want the VM to require less memory, use a lighter flavor of Ubuntu such as Xubuntu or Lubuntu which come with lighter desktop interfaces.

Hello, I am using 2048MB of memory and 20GB hard disk space. I am mostly going to be using Ubuntu to practice the linux commands that I learn in college and not run multiple programs.

---

### Post by kevdog on 2016-02-23
Can you provide a screencap of your Ubuntu setup within VM?

---

### Post by howefield on 2016-02-23
Moved to the "*Virtualisation*" forum.

---

### Post by Javeria_Qureshi on 2016-02-23
> **kevdog said:**
> Can you provide a screencap of your Ubuntu setup within VM?

Here the pictures. One shows the settings, and the other the log on screen that keeps coming again and again.

---

### Post by MAFoElffen on 2016-02-24
So at that login screen you are logging in with your password... and if loops back to the screen, without an error message?

If so, then use the vm's menus for Machine > Shutdown > Reboot. On Reboot, at the Grub boot menu, <ArrowDown> to the recovery menu item and select it. When it boots to the Recovery menu, Select "Network", which will mount the filesystem. Then Drop to Root prompt:
```

# change the following "userName" to your own user name...
cd /home/userName 
rm .Xauthority
touch .Xauthority
chown userName:userName .Xauthority
chmod 600 .Xauthority
sudo shutdown -r now

```
What that does is replace an set your personal X profile file, which the correct permissions and with you as the owner. Remember to replace the text above "userName", with your own user name.

---

