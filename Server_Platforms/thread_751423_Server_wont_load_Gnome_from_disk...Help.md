---
title: "Server wont load Gnome from disk...Help"
date: 2008-04-10
forum: Server Platforms
---

### Post by Moejoe1 on 2008-04-10
Please bare with me I am new!
I have a server and it seems to be in a dos mode. I have the gnome on a disk but i saw in a previous post that there is an alternate cd? this server is not for the internet but I need to load a desktop solution to this soon.

Please help me. Any recommendations on if I should use Gnome or something else?
:confused:

---

### Post by ianb72 on 2008-04-10
type in terminal:
[HTML]sudo apt-get update
sudo apt-get install ubuntu-desktop[/HTML]

That will install your gnome desktop on reboot.

If yours is like mine, when its all finished it just does nothing just type:
[HTML]sudo reboot[/HTML]

it will ask you for your password and reboot into the gnome desktop

---

### Post by Moejoe1 on 2008-04-10
Ok i rebooted and it looks like Ubuntu is already on this one but how do I access it from the dos-like screen?

:confused:

---

### Post by ianb72 on 2008-04-10
To access the shell or Terminal within Gnome, click on Applications on the top left hand side of the Desktop then Accessories and then click on Terminal, this will bring up the terminal shell

---

### Post by chuck jessup on 2008-04-10
if you have the ubuntu desktop installed, it should auto load into the GUI/desktop... 

there is a post to install a light GUI 

sudo apt-get install xserver xorg* gnome << ithink... im not at my computer (i liked it and im a windows lifer gone linux :) ) there is a post with the exact command and then restart the computer and it shoudl just go into it.

any who i hope this helps, Best Wishes

---

### Post by Moejoe1 on 2008-04-10
> **chuck jessup said:**
> if you have the ubuntu desktop installed, it should auto load into the GUI/desktop... 

there is a post to install a light GUI 

sudo apt-get install xserver xorg* gnome << ithink... im not at my computer (i liked it and im a windows lifer gone linux :) ) there is a post with the exact command and then restart the computer and it shoudl just go into it.

any who i hope this helps, Best Wishes



Thank you, but I don't believe that I know how to bring up the ubuntu desktop.
Like I stated, I'm still in this dos-like prompt screen.
Please help...this is driving me batty!](*,)](*,)

---

### Post by Moejoe1 on 2008-04-10
I did what you said Jesse and here is what is on the screen:

Package xserver is a virtual package provided by:
vncserver 3.3.7-8ubuntu2
tightvnserver 1.2.9-8ubuntu2
You should explicitly select one to install. 
E: Package xserver has no installation candidate


Any ideas???

---

### Post by Deathrend on 2008-04-10
Server installs as a command line only interface, to install the desktop, you have to log in using the command line.  This works like logging in using SSH, just type your username, then password (When it asks for it).

you should now see something like this:

```
deathrend@ubuntu password:
Linux ubuntu 2.6.24-12-server #1 SMP Wed Mar 12 23:34:17 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Thu Apr 10 08:14:40 2008 from <edit out>
deathrend@ubuntu:~$

```

Once you see
 ```
<username>@ubuntu:~$
```
type in the commands stated above:

```

 sudo apt-get update
password for user <user>: <your password>
lots and lots of scrolling..
....
...
....
Fetched 7470kB in 51s (144kB/s)
Reading package lists... Done
<username>@ubuntu:~$

```

Then type 

```

sudo apt-get install ubuntu-desktop

```

when that's done, type
```

sudo shutdown -rf now

```

It should boot to a GUI now :)

---

### Post by Moejoe1 on 2008-04-10
Ok so I did what you said and by the second command (install) it looks like it is trying to connect to the internet. This server will not connect to the internet for some odd reason. Is there  something else I can do?

---

### Post by chuck jessup on 2008-04-11
ok like i had said that i wasnt at my home computer and wasnt fully sure that i had the code exactly right but here it is - 

**sudo apt-get install xserver-xorg xfonts* gnome**   

this is the install code, it takes a bit to install, trust me i have done it a bunch 

after it installs you just need to type in :

**name@compname:~$ startx**

this will start the desktop screen and your in dont uninstall anything, it is a hastle to restart if you get rid of the wrong thing. 

best wishes

---

### Post by Deathrend on 2008-04-11
Yes, it connect to the internet to pull the packages, depending on how you did your install, normally the server sets up with DHCP, which let's you connect out without putting any settings in (Assuming you have an active network connection, if you don't, then it's not enabled.).

I would do this:
```

ifconfig eth0

```

if you get the message that it can't find the device, type

```

ifconfig eth0 up

```

which /should/ enable it with no settings other than DHCP (Asuming you didn't set a static IP during the install).  You should be able to connect over the internet after that.

Let us know if it's something else.

---

### Post by Moejoe1 on 2008-04-11
Hello everyone... I hate to be a thorn in your side but... I did the whole xserver-xorg.....stuff and it says E: Package xserver-xorg has no installation candidate.
Also says:
Building dep tree... done
Package xserver-xorg is not available, but is referred to by another package.
This may mean the package is missing, has been obsoleted, or is only available from another source
However the following packages replace it:
xserver-xorg-input xserver-xorg-input-ur98 xserver-xorg-input-tek4957
"Repeted...by 8 or so more lines
"
"
"
xserver-xorg-core
I hope this helps....

Also I did the ifconfig eth0 and it pulls up IP addresses and about 6 lines of info but doesnt say it cannot find anything, so Im assuming it is online, right?

---

