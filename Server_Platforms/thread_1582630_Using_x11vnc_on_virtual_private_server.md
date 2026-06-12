---
title: "Using x11vnc on virtual private server"
date: 2010-09-26
forum: Server Platforms
---

### Post by Liboicl on 2010-09-26
I have a virtual private server that I am trying to connect to using x11vnc.
I ran this through ssh to setup gnome

sudo apt-get install gnome-core
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg

I later ran

sudo apt-get install ubuntu-desktop

to see if that would help.
```
#cat /etc/issue
Ubuntu 10.04.1 LTS \n \l


``````
#sudo startx
Fatal server error:
xf860OpenConsole: Cannot open /dev/tty0 (No such file or directory)
```I assume this is because it probably doesn't have a video card.

```
#sudo xterm
xterm Xt error: Can't open display: %s
xterm:   DISPLAY is not set
```Warning: This program is an suid-root program or is being run by the root user. The full text of the error or warning messae cannot be safely formatted in this environment. You may get a more descriptive message by running the program as a non-root user or by removing the suid bit on the executable.
It wouldn't include that inside the code tags. It goes with the xterm.
```
#sudo gdm
gdm-binary[20254]:  WARNING: Unable to load file '/etc/gm/custom.conf': No such file or directory
gdm-binary[20254]:  WARNING: Unable to find users: no seat-id found
gdm-binary[20254]:  WARNING: GdmDisplay: display lasted 0.037319 seconds
gdm-binary[20254]:  WARNING: Could not spawn command: Failed to fork  (Cannot allocate memory)
gdm-binary[20254]:  WARNING: Could not start command '/usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display2': Failed to fork  (Cannot allocate memory)
```Does this mean I need more memory?

---

### Post by windependence on 2010-09-26
It looks to me like you need a swap file and you don't have one. The Failed to fork message is an indicator of that.
 
-Tim

---

### Post by Liboicl on 2010-09-26
First of all, thanks for the quick reply.

How would I go about doing that through SSH? This is my first real usage of Ubuntu. I use Puppy Linux on my home computers.

Also, for reference it only has 64MB of RAM with a burst of 128MB, that is because it's a VPS and can use more at certain periods. I was thinking it might need more, but I figured I would try and see.

---

### Post by windependence on 2010-09-26
Yes, that's why ot can't fork a new process, because there isn't enough memory for it. You would need to either give it more memory or free up some space and create a swap partition. Without knowing your partitioning scheme it's hard to give you step by step.
 
-Tim

---

### Post by Liboicl on 2010-09-26
Can you give me some general instructions? I think I can work it out from there. I assume I'd use fdisk, correct?
If I run fdisk -l it outputs:
cannot open /proc/partitions
I assume this is probably because it's a VPS.
How much RAM would it need to run GNOME without a swap?

---

