---
title: "Where to type commands in Gnone gui (ubuntu server)"
date: 2010-10-22
forum: Server Platforms
---

### Post by mubashirzia on 2010-10-22
Hi all
I am new to Linux, have used KDE/SLAX before but am now attempting to use linux on my old computer to accomplish these objectives:
 
1) Run an FTP so I (& my mates) can access files anywhere wit ease(no dramas).
2) Enable sharing of my drives so I can put files from Laptop into this computer
 
Now I have successfully Installed Ubuntu Server (Finallllly) but then messed up cuz I installed the Gnome GUI and now cant find any place where I can type any sudo commands. vsftpd should work for me right??
 
Any help would be really appreciated. thanks

---

### Post by arrrghhh on 2010-10-22
You installed the Gnome GUI on a server...?  Do you need that?

SSH would be the place where I access the box remotely - to type "sudo" commands as you put it.

Assuming you want to use Gnome, hit Alt-F2 and type 'gnome-terminal' in the box - that's your console.

I wouldn't put Gnome on a server, it's completely unnecessary overhead.  See the [ServerGUI](https://help.ubuntu.com/community/ServerGUI) documentation for more.

---

### Post by mubashirzia on 2010-10-22
I know I shouldn't put gui in there but as I told you am a new user and was struggling a bit with editing vsftpd.conf
Can I just remove Gnome GUI
 
Also I tried Alt+F2 --> gnome-terminal but it still wont work
 
P.S. I know m a noob but not for long definitely =D

---

### Post by arrrghhh on 2010-10-22
So remove Gnome, or at least remove it from init.d.

```
sudo update-rc.d gdm remove
``` - will leave Gnome on the system but prevent it from starting on its own.

---

