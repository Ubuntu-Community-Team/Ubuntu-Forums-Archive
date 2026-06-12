---
title: "HOWTO: Links2 with graphics mode (using DirectFB) as user"
date: 2007-05-24
forum: Tutorials
---

### Post by jdarias on 2007-05-24
This is my first HOWTO. So please be patient if there are some typos or if you find my english a bit awkward.
It is assumed that you have **links2** and **gpm** (general purpose mouse) installed. 
A console resolution of 1024x768 16M color is recommended. [Click here for more info about this.](http://ubuntuforums.org/showthread.php?t=258484)
Last but not least, the disclaimer: I am not responsible to any damage caused to your system by the use of this gude. Use ta your own risk (and joy). I hope it works for everybody.
I tested on Ubuntu 7.04. Hopefully it will work on earlier versions, but i can't be sure.
You can skip the following part if you know what the problem is.
> PROBLEM: Links2 can use DirectFB to disply graphics, but to use it on a default Ubuntu installation root privileges are required.

if you use links2 -driver directfb it won't start. instead it'll give you an output like this:
```
~$ links2 -driver directfb

---------------------- DirectFB v0.9.25 ---------------------
(c) 2000-2002 convergence integrated media GmbH
(c) 2002-2004 convergence GmbH
-----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-10-17 10:09)
(*) Direct/Memcpy: Using MMXEXT optimized memcpy()
(!) DirectFB/core/vt: Error opening `/dev/tty0'!
--> Permission denied
(!) DirectFB/Core: Could not initialize 'system' core!
--> Initialization error!
svgalib: Cannot get I/O permissions. 
```
The option -g can be used to disply graphics, but they will be in 16 colour mode and mouse will work awkwardly, with no wheel suport.
To allow links2 use DirectFB and the mouse in a virtual console it is necessary to do some editing of the 40-permissions.rules file.
[B]First make a backup of this file by issuing the command
```
sudo cp /etc/udev/rules.d/40-permissions.rules /etc/udev/rules.d/40-permissions.rules.backup
```
If you run into trouble roll back the backup:
```
sudo cp /etc/udev/rules.d/40-permissions.rules.backup /etc/udev/rules.d/40-permissions.rules
```[/B]
Here's how to do it:

1) open a console and type:
```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```

2) Find a line wich looks like this:
```
KERNEL=="tty[0-9]*",			GROUP="root"
```

3)Make the following change to make it look like this:
```
KERNEL=="tty[0-9]*",			GROUP="root",** MODE="0666"**
```

This wiil grant us permissions to /dev/tty0 or the other virtual consoles. Don't close gedit yet.

Now let's grant us permissions for the mouse:

4)In the end of the same file, add the following line:
```
KERNEL=="mice",				MODE="0666"
```

5) Now restart your computer. 
Let's check out if everything is ok: Open up a terminal and type 
ls -l /dev/tty0
You should get something like this:
```
crw-rw-rw- 1 root root 4, 0 2007-05-24 08:47 /dev/tty0
```
Notice the read-write permissions for users.
Same thing should happen to /dev/input/mice:
```
jdarias@familia-arias:~$ ls -l /dev/input/mice
crw-rw-rw- 1 root root 13, 63 2007-05-24 08:47 /dev/input/mice

```

That's it! Now just type links2 -g in a virtual console and enjoy full DirectFB support!

---

### Post by siafok on 2007-06-04
I followed this how-to but "links2 -g " in directfb is in different resolution than my VC which I have in 1024x768. The display is blurry and mouse movement deletes text. In svgalib mouse dont work properly (it needs some /etc/vga tweaking), display is better but I must run it in sudo mode which is, I supose, not safe for Internet.
I have NVIDIA GeForce MX400 with Xubuntu FF.
Any advice for directfb display mode improvement?

---

### Post by jdarias on 2007-06-08
maybe try links2 -driver directfb

---

### Post by siafok on 2007-06-11
I did but it was like I wrote.

---

### Post by revaso on 2012-01-09
No longer working under 11.10. Any changes needed?

---

### Post by dilidon on 2013-05-31
> **revaso said:**
> No longer working under 11.10. Any changes needed?

I know this is an old thread but I found it myself in search of a solution, so perhaps someone else will too.
So an update: I found that under 12.04 two things helped get *links2 -g* working in framebuffer right after installing links2:

1) installing gpm (not sure if #2 would have worked already on its own - I installed gpm before)
2) sudo dpkg-statoverride --update --add root root 4755 /usr/bin/links2 (got the solution from here: [http://forums.debian.net/viewtopic.php?t=75704#p419582](http://forums.debian.net/viewtopic.php?t=75704#p419582))

PS. I did none of the mods indicated in this howto.

---

