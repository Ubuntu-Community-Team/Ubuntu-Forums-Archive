---
title: "Add services to the SERVICES applet?"
date: 2006-09-14
forum: The Cafe
---

### Post by radiojef on 2006-09-14
Is it possible to add services to the services applet? Here is why I ask...

I have a Wireless adapter that I have to use 'ndiswrapper' on everytime I reboot. I setup 'ndiswrapper' for the correct driver and device, so when I restart I open a terminal and type:```
sudo modprobe ndiswrapper
```
Not a big deal, but part of the fun of Linux is figuring out how to automate your system details, right? I tried to write a script and add it to the sessions > startup programs manager...the script looked like this```
#! /bin/bash
modprobe ndiswrapper
```
This didnt work. Not sure why. Anybody got any ideas?

---

### Post by ComplexNumber on 2006-09-14
add it to the file: /etc/rc.d/rc.local
mine looks like this now:
> #!/bin/sh
#
# This script will be executed *after* all the other init scripts.
# You can put your own initialization stuff in here if you don't
# want to do the full Sys V style init stuff.

touch /var/lock/subsys/local

/sbin/modprobe ndiswrapper

---

### Post by radiojef on 2006-09-14
Thanks!
Can you explain what the 'touch' line is actually doing? 

Appreciate it.

---

### Post by ComplexNumber on 2006-09-14
>  Can you explain what the 'touch' line is actually doing?  don't worry about that. just add '/sbin/modprobe ndiswrapper' to the file. i'm running fedora and the 'touch' statement was in there since i first installed it.

---

### Post by John.Michael.Kane on 2006-09-14
Heres some info in reguards to the touch command [http://www.bellevuelinux.org/touch.html](http://www.bellevuelinux.org/touch.html)

---

### Post by Ramses de Norre on 2006-09-14
All modules in /etc/modules are loaded when you boot, so this line will automate the loading through an inbuilt and secure method:
```
echo "ndiswrapper"|sudo tee -a /etc/modules
```

---

### Post by jdong on 2006-09-14
1. There is /etc/rc.local, which is a script executed at the end of every bootup

2. For modules, you should really be using /etc/modules.

3. For ndiswrapper, using sudo ndiswrapper -m should set this up for you automatically.

---

### Post by radiojef on 2006-09-14
In other words, I should add "sudo ndiswrapper -m" at the end of the modules file in /etc/?

---

### Post by ComplexNumber on 2006-09-14
> **radiojef said:**
> In other words, I should add "sudo ndiswrapper -m" at the end of the modules file in /etc/?
either there or in /etc/rc.d/rd.local. thats where i've put mine and i've been connected wirelessly for the past month or so.

---

### Post by jdong on 2006-09-14
sudo ndiswrapper -m is a command you issue at the command line. It will do the /etc/modules work for you.

---

### Post by radiojef on 2006-09-15
It worked when I used sudo ndiswrapper -m in the terminal. But ComplexNumber...I dont have the directory you specified. See the attachment.

---

### Post by NoTiG on 2006-09-15
Speaking of which........ If i do ndiswrapper -m and write it to my modules.d directory...... it will cause my gnome login to take about 5 minutes... whereas if i just wait till gnome loads and them type sudo modprobe ndiswrapper in the terminal... it works instantly. im not sure why it is doing this... i filed a bug on launchpad. but it would be nice to try a different way and maybe use the rc.d thing.... but i dont have an rc.d directory. i have rc0.d and rc1.d etc...........

---

### Post by radiojef on 2006-09-15
> **NoTiG said:**
> Speaking of which........ If i do ndiswrapper -m and write it to my modules.d directory...... it will cause my gnome login to take about 5 minutes... whereas if i just wait till gnome loads and them type sudo modprobe ndiswrapper in the terminal... it works instantly. im not sure why it is doing this... i filed a bug on launchpad. but it would be nice to try a different way and maybe use the rc.d thing.... but i dont have an rc.d directory. i have rc0.d and rc1.d etc...........

That is odd. Adding it to modules caused no noticable lag in the GNOME bootup for me. Anybody?

---

### Post by ComplexNumber on 2006-09-15
> **radiojef said:**
> But ComplexNumber...I dont have the directory you specified. See the attachment.
 if you look about 5/6 of the way down, you will see that you do have rc.local file.

---

### Post by radiojef on 2006-09-15
Oh yeah, but its not in the /rc.d/ directory. Are the two the same?

---

### Post by ComplexNumber on 2006-09-15
> **radiojef said:**
> Oh yeah, but its not in the /rc.d/ directory. Are the two the same?
they are like peas in a pod - ie exactly the same.

---

### Post by radiojef on 2006-09-15
10-4 buddy. Thanks.

---

### Post by maniacmusician on 2006-09-15
the correct procedure to get ndiswrapper to start at boot is this:

sudo ndiswrapper -m

sudo kate /etc/modules  ---> add ndiswrapper to the list of modules. 

save the file you can replace kate with the editor of your choice. hehe you dont have to make it so complicated.

---

### Post by ComplexNumber on 2006-09-15
> the correct procedure to get ndiswrapper to start at boot is this:

sudo ndiswrapper -m

sudo kate /etc/modules  ---> add ndiswrapper to the list of modules. 

save the file you can replace kate with the editor of your choice. hehe you dont have to make it so complicated. thats the first i've heard.

---

