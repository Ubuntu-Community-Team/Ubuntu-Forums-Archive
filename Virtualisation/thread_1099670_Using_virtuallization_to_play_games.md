---
title: "Using virtuallization to play games"
date: 2009-03-18
forum: Virtualisation
---

### Post by houseonfire on 2009-03-18
I'm wondering if its possible for me to virtualize XP to play games.
In virtualbox, you can only use 128mb of video memory, and I think I read somewhere that it doesn't use the actual video card memory.
I'm trying to find a way to do this because I don't want to install XP on my other hard drive. 
Is there a virtualization app that will use my video card so I can run games at full speed?
Thanks.

---

### Post by bodhi.zazen on 2009-03-18
At this time probably not.

Virtualization uses a virtual emulated video card and does not directly use your videocard.

although under rapid development, in general the graphics options are limited.

---

### Post by D3ath on 2009-03-18
> **houseonfire said:**
> I'm wondering if its possible for me to virtualize XP to play games.
In virtualbox, you can only use 128mb of video memory, and I think I read somewhere that it doesn't use the actual video card memory.
I'm trying to find a way to do this because I don't want to install XP on my other hard drive. 
Is there a virtualization app that will use my video card so I can run games at full speed?
Thanks.

In a perfect world it would be nice but DirectX10 makes it impossible to use in linux.  If your a game your going to have to have a dual boot system.  I mean there are games like Half-Life2 and portal that i play in linux but its not perfect yet. There is nothing wrong with using a worthless operating system to play games. I know it hurts to see that windows logo.  Thats why i make windows look like ubuntu that way i feel much better when i log it! lol

---

### Post by RealG187 on 2009-03-19
What about older games? I can play RCT and RCT2 in Wine but not Mall Tycoon, would that work in a VM?

What about all those games that only work in 98, could I virtualize 98 for them, I thought that's how you play these older games...

---

### Post by D3ath on 2009-03-19
> **RealG187 said:**
> What about older games? I can play RCT and RCT2 in Wine but not Mall Tycoon, would that work in a VM?

What about all those games that only work in 98, could I virtualize 98 for them, I thought that's how you play these older games...

Yea for older games of course! But I was talking about the new games if there are games that are only for certain systems then go for it it will work. But I have never done or wanted to run 98 in a VM.  There may be audio issue or something along those lines but I'm sure nothing that no one else hasn't came across yet. If you don't play the up-to-date games then like i said VM should work.

---

### Post by RealG187 on 2009-03-19
I have tried to run 98 in a VM, but could only get a low resolution and I could not connect to the host computer through samba, when I would connect it would ask for a password (and not username like 2000/XP) and I would enter my password but it wouldn't go.

---

### Post by D3ath on 2009-03-19
> **RealG187 said:**
> I have tried to run 98 in a VM, but could only get a low resolution and I could not connect to the host computer through samba, when I would connect it would ask for a password (and not username like 2000/XP) and I would enter my password but it wouldn't go.

I find that funny for some reason! Doze is terrible!

---

### Post by binbash on 2009-03-19
Old games mostly work.Virtualization needs more development to get decent games working.

---

### Post by Ng Oon-Ee on 2009-03-19
Anything which uses OpenGL works. I'm playing Warcraft III no problem (but the graphics are a bit different, some colors are shades apart from the 'real' colors you'd see in a windows computer). Completely playable though, if you have problems you may have to disable compiz.

Of course, this is for VBox PUEL, not OSE. Version > 2.1

---

### Post by RealG187 on 2009-03-19
> **D3ath said:**
> I find that funny for some reason! Doze is terrible!

I think it's because Windows 98 doesn't support modern encryption. Is there a way I can transfer files between host and guest other than samba, maybe FTP? For software I can mount ISO images, but that only lets me transfer data from the host to the guest...

---

### Post by bodhi.zazen on 2009-03-19
> **RealG187 said:**
> I think it's because Windows 98 doesn't support modern encryption. Is there a way I can transfer files between host and guest other than samba, maybe FTP? For software I can mount ISO images, but that only lets me transfer data from the host to the guest...

You can use samba, ftp, http, and ssh (scp).

---

### Post by RealG187 on 2009-03-20
Well windows 98 isn't compatible with the encryption used by an Ubuntu samba server...

What is ssh? Is it like telnet or VNC? Does it let you transfer files or run a remote session (like telnet).

I have an [NSLU2]("http://bestwikiever.wikidot.com/NSLU2") which is a tiny Linux computer with only two USB ports and an ethernet port, there is no keyboard or monitor,you operate it by typing it's IP into a browser (similar to routers and network printers) or by using telnet to get a remote sesssion, but when you enable telnet it gives a security warning a reccomends you get SSH (why woulnd't it come with SSH). But when I run gFTP I can connect to an SSH server like it was a file server.

Is SSH both?

---

### Post by 123456789123456789123456 on 2009-03-20
Try VMWare for linux
unfortiantly you will have to pay for the software, but it is vetter equiped to run virutal machines, it uses the full abilities of your system.  If you have 2gb ram, VMware can use 1.9gb ram for a virtual machine, not suggested, but can.  It can also emulate 2 processors.  it is extreamly easy to install

I have on my mac virtual pc, which is perfect if all you emulate is xp, 2000.  but can not emulate anything else.  that is simular to most other virtual imulaters.  however vmware has no limits, I have emulated everything, from 98-the most weired versions of linux.  with no problems.

---

### Post by RealG187 on 2009-03-20
I am using VM Ware Server, does it give the full capibilities?

---

### Post by RealG187 on 2009-07-06
Is it possible with Virtualbox 3.0?

[http://ubuntuforums.org/showthread.php?t=1191258&highlight=games](http://ubuntuforums.org/showthread.php?t=1191258&highlight=games)
[http://kubuntuforums.net/forums/index.php?topic=3104618.new;topicseen#new](http://kubuntuforums.net/forums/index.php?topic=3104618.new;topicseen#new) (Telengard's post, 9th post)

---

