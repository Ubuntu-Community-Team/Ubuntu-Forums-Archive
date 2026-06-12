---
title: "where to start"
date: 2012-01-08
forum: Server Platforms
---

### Post by bluexrider on 2012-01-08
I want to set up a headless server. I plan to remote in for maintenance and updates. Would like to use VNC

I may use it as a Print-Server as well as storage

I have 10.04 which I would like to use and the box is a Dell GX260

Pentium 4   2.6 Ghz
DIMM 1Gb

2 WD80Gb HDD

Not the fastest and certinally not pretty.

---

### Post by cj13579 on 2012-01-09
Hi I'm not sure what your question is here? First step would be to install Ubuntu (with a GUI if you want to VNC) onto the box :)

---

### Post by lykwydchykyn on 2012-01-09
Well if you must have an X11 GUI, definitely go with Lubuntu.  The GX260 is a pretty old box, and it isn't likely to play nice with regular Ubuntu.  Of course, since there aren't many graphical (X11) server administration tools for Ubuntu, having a GUI doesn't do much more than give you a nice environment for launching xterm.

I'd recommend instead using Webmin to work with the server; setting up samba in Webmin is pretty straightforward.  

CUPS comes with its own web-based interface, of course.

---

### Post by bluexrider on 2012-01-10
> **lykwydchykyn said:**
> Well if you must have an X11 GUI, definitely go with Lubuntu.  The GX260 is a pretty old box, and it isn't likely to play nice with regular Ubuntu.  Of course, since there aren't many graphical (X11) server administration tools for Ubuntu, having a GUI doesn't do much more than give you a nice environment for launching xterm.

I'd recommend instead using Webmin to work with the server; setting up samba in Webmin is pretty straightforward.  

CUPS comes with its own web-based interface, of course.

It is my understanding that if i use a GUI on the box it needs to have a monitor and keyboard attached. I wanted to VNC into the box without having to attach a monitor and keyboard. 

Is that possible?

---

### Post by jonobr on 2012-01-10
Hey there,

any reason for sticking with the GUI?

May be a good way of getting stronger with CLI and means your not taking up space/cycles for a GUI

---

### Post by KdotJ on 2012-01-10
> **jonobr said:**
> Hey there,

any reason for sticking with the GUI?

May be a good way of getting stronger with CLI and means your not taking up space/cycles for a GUI

I second this. If you want a headless server, have a proper headless server with no GUI.

For admin jobs (your maintenance and updates etc) you can SSH into the box via a terminal. As jonobr said, it will be great to strengthen your terminal skills.

---

### Post by arrrghhh on 2012-01-10
> **KdotJ said:**
> I second this. If you want a headless server, have a proper headless server with no GUI.

For admin jobs (your maintenance and updates etc) you can SSH into the box via a terminal. As jonobr said, it will be great to strengthen your terminal skills.

+...3?

Don't put a GUI on a server.
Don't put a GUI on a server.

Just don't.  You'll learn a lot with CLI-only, save processor cycles, and ssh is WAY easier to setup than VNC ;).

---

### Post by bluexrider on 2012-01-10
[SIZE=4]**[COLOR=Red]OUCH![/COLOR]**[/SIZE]

I think my arm just got twisted around my back. Okay, I get the picture. Better to not have a GUI. 

CLI means more free cycles, less space = better performance.


Well then, what would be better? Remember this is just a personal server for torrents and streaming media. 

10.04LTS or FreeNAS ????

---

### Post by arrrghhh on 2012-01-10
> **bluexrider said:**
> [SIZE=4]**[COLOR=Red]OUCH![/COLOR]**[/SIZE]

I think my arm just got twisted around my back. Okay, I get the picture. Better to not have a GUI. 

CLI means more free cycles, less space = better performance.


Well then, what would be better? Remember this is just a personal server for torrents and streaming media. 

10.04LTS or FreeNAS ????

I vote 10.04LTS, but that's because my server is running the same :D.  Never used FreeNAS - it seems great at what it does, but limited.  So keep that in mind... you might hit a wall with FreeNAS, where the sky is pretty much the limit on Ubuntu.

You're also in an Ubuntu forum ;).

---

### Post by BertN45 on 2012-01-10
Why do it the easy way, if you can do it the hard way! If your hobby is to do computing, as I had to do it in the stone age of computing with IBM360/370, PDP11 and VAX-VMS. Go ahead, but remember a small typo can have big consequences.

I would go for the 10.04 LTS desktop and install xrdp to get access to the server, using a relative modern and robust gui interface. The advantage of xrdp over vnc is that it is much faster than VNC.

I only use the cli, when I cannot avoid it. I control my file server and other PCs with rdp too and in a mixed environment it is ideal.

---

### Post by bluexrider on 2012-01-11
> **arrrghhh said:**
> 

You're also in an Ubuntu forum ;).

Yes, I know where I am, I think? Most of the time anyway!

---

### Post by KdotJ on 2012-01-11
Mine is running Debian, purely so i don't have to mess around with distro upgrades as often. Obviously 10.04 is LTS and supported for a long while anyway...

---

### Post by lykwydchykyn on 2012-01-11
> **bluexrider said:**
> It is my understanding that if i use a GUI on the box it needs to have a monitor and keyboard attached. I wanted to VNC into the box without having to attach a monitor and keyboard. 

Is that possible?

Yes.  You'd still need to install some kind of desktop environment, but the system won't be running Xorg.  There are a number of tutorials on how to set that up, here's one possible way: [http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html](http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html)

Everyone seems to be pushing you towards using the CLI.  If you're comfortable with that, it is an efficient way to manage the server.  However, there is nothing wrong with putting any kind of software on the machine if it helps you manage it effectively; don't let anyone guilt/shame you into making your server a frustrating experience.

I recommend web interfaces because they actually provide an interface to configure services, not just a desktop. Much simpler than mucking about with VNC and all that.

---

### Post by bluexrider on 2012-01-11
I think I will go with the 10.04.2 LTS server and drop LXDE on it. Call it being lazy, but I want convenience too.

Thanks for the replies

---

### Post by jonobr on 2012-01-11
hi There,

Despite what I said , I am a big believe in whatever works for you,
be it GUI, No GUI, Windows or whatever.

Godspeed!

Jonobr

---

### Post by bluexrider on 2012-01-11
Thank you for the reply

---

