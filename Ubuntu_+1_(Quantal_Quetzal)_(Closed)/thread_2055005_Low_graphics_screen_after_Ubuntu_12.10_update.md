---
title: "Low graphics screen after Ubuntu 12.10 update"
date: 2012-09-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by rolltide101x on 2012-09-08
My GPU does not work in Linux (AMD 7690m) but after the update Ubuntu is trying to make it work so I get this screen. How can I tell Ubuntu to ignore the AMD GPU and just use the integrated Intel GPU? It has to be through command line in recovery mode because I for the life of me (probably my dumbness lol) can not figure out how to select anything in low graphics "mode". It has 4 choices I cant remember what they are. Thanks for any help!

I am 99% sure this is the problem since Ubuntu would do this in 12.04 if I attempted to install the AMD drivers but apparently the new kernel thought it had the correct drivers and wants to use them. It will be a while before I get back on so please leave detailed answers. Thanks again

---

### Post by mips on 2012-09-08
Dunno if this is related to your problem but have a look at this link [http://ubuntuforums.org/showthread.php?t=1988444](http://ubuntuforums.org/showthread.php?t=1988444)

---

### Post by rolltide101x on 2012-09-08
> **mips said:**
> Dunno if this is related to your problem but have a look at this link [http://ubuntuforums.org/showthread.php?t=1988444](http://ubuntuforums.org/showthread.php?t=1988444)


Thanks alot for trying but I have attempted several times to get my GPU working in Ubuntu and it just does not work. The new kernel thinks that the AMD gpu is the one to use but I just want it to ignore the AMD completely and just use the Intel gpu. I only use the AMD gpu in Windows for gaming (and that is really all I use it for LOL)

---

### Post by rolltide101x on 2012-09-09
Anyone? Is this not possible?

---

### Post by dino99 on 2012-09-09
i suppose your bios can deactivate it ):P (and fglrx is known as buggy at time)

---

### Post by rolltide101x on 2012-09-09
> **dino99 said:**
> i suppose your bios can deactivate it ):P (and fglrx is known as buggy at time)

I do not believe my BIOS has an option for that (but it may) but I would rather not since I use my gpu in Windows. That method seems to treat the symptoms and not the cause. Would removing fglrx fix this issue?

---

### Post by huwshimi on 2012-09-09
> **rolltide101x said:**
> Would removing fglrx fix this issue?

I had a similar issue after upgrading and removing the fglrx drivers and rebooting worked for me.

From memory I did:

```
sudo apt-get remove --purge fglrx fglrx-amdcccle
```

---

### Post by rolltide101x on 2012-09-10
I tried that earlier but I get this

[B]clate@clate-Lenovo-IdeaPad-Y470:~$ sudo apt-get remove --purge fglrx fglrx-amdcccle
[sudo] password for clate: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'fglrx' is not installed, so not removed
Package 'fglrx-amdcccle' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
clate@clate-Lenovo-IdeaPad-Y470:~$ 

[/B]It wont/cant uninstall it because the driver is in the kernel. There has to be a solution to this!

If I disable my AMD gpu in the BIOS it boots and works perfectly on Ubuntu 12.10, there must be a solution that is more professional than this though

---

### Post by cariboo on 2012-09-10
Are you sure that you are using the fglrx driver? What's the output of:

```
sudo lshw -C display
```

---

### Post by huwshimi on 2012-09-10
Do you possibly have the updates packages installed, or did you install drivers manually?

You could try:

```
sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates
```

---

### Post by rolltide101x on 2012-09-10
I have solved this on my own the solution is to blacklist the radeon driver.
[B]
sudo gedit /etc/modprobe.d/blacklist.conf

[/B]then add this to the file

blacklist radeon 


That is it! Never thought I would out do the Linux gurus! :lolflag:

---

### Post by rolltide101x on 2012-09-10
> **cariboo907 said:**
> Are you sure that you are using the fglrx driver? What's the output of:

```
sudo lshw -C display
```


A driver for this gpu has been added to the kernel

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames [Radeon HD 7670M]

All Radeon drivers are determined that this is my gpu but it is the 7690m. So the kernel autoloaded this driver thinking that was my GPU causing me to go to "Low graphics" mode because it was trying to use the wrong driver for my GPU (7690m has crappy Linux support) All I wanted to do is use my Intel integrated graphics and blacklisting the radeon kernel driver did the trick.

---

### Post by rolltide101x on 2012-09-10
> **huwshimi said:**
> Do you possibly have the updates packages installed, or did you install drivers manually?

You could try:

```
sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates
```

Neither were ever installed. Only the drivers directly in the kernel 3.5.0-14-generic were present

---

