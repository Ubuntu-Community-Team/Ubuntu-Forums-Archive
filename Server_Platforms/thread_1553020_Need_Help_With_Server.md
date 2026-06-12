---
title: "Need Help With Server"
date: 2010-08-14
forum: Server Platforms
---

### Post by wzhaicthtaarkyer on 2010-08-14
In an attempt to add ubuntu desktop to ubuntu server 64 but some thing went wrong.
my system auto starts in X but i want to start in command line and request the GUI when necessary  
the code i used was

sudo apt-get update 

sudo apt-get install ubuntu-desktop

sudo dpkg-reconfigure xserver-xor

---

### Post by Sporkman on 2010-08-15
You have to not have the gdm service start at boot. 

There's some way to do it - via update-rc or something along those lines.

---

### Post by rubylaser on 2010-08-15
This should do it...

```
sudo nano /etc/default/grub
```

find out this line:
```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
```
change it to:
```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”
```

Update grub and done!
```
sudo update-grub
```

Reboot and you should be all set.  When you want to use the GUI just type startx.

---

### Post by wzhaicthtaarkyer on 2010-08-16
thank you for the help its working just fine now

---

