---
title: "startx automatically"
date: 2008-04-14
forum: Server Platforms
---

### Post by phillips321 on 2008-04-14
Hi guys,

have just installed ubuntu server and have added fluxbox for a basic frontend.

I need the command "startx" to be run automatically after boot.

This is a headless box and im planning to vnc into it, if i run startx locally i can then access the box via vnc just fine, sadly i cannot issue the "startx" command over ssh


 cheers for your help

---

### Post by FakeOutdoorsman on 2008-04-14
From Arch Linux Wiki, but should work fine for Ubuntu: [Start X at boot]("http://wiki.archlinux.org/index.php/Start_X_at_boot")

---

### Post by ibutho on 2008-04-14
One method I use to access desktops remotely is via ssh. I start a new X session on the local machine by doing CTRL-ALT-F1, login to the CLI and run "xinit -- :1". That will start a new X session with just a terminal running. You can then SSH into your remote machine by doing "ssh -X -Y somehost" from the terminal, login to the remote host and then execute the session you wish e.g. gnome-session, startkde etc. Hope this will be of some help.

---

### Post by kerry_s on 2008-04-14
> **FakeOutdoorsman said:**
> From Arch Linux Wiki, but should work fine for Ubuntu: [Start X at boot]("http://wiki.archlinux.org/index.php/Start_X_at_boot")

that won't work with ubuntu, ubuntu uses a different startup process. it doesn't have /etc/inittab. it uses /etc/event.d/*

if was debian that would be fine, i use a similar to start my debian system.

---

### Post by netlogic on 2008-04-14
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

---

### Post by kerry_s on 2008-04-14
> **phillips321 said:**
> Hi guys,

have just installed ubuntu server and have added fluxbox for a basic frontend.

I need the command "startx" to be run automatically after boot.

This is a headless box and im planning to vnc into it, if i run startx locally i can then access the box via vnc just fine, sadly i cannot issue the "startx" command over ssh


 cheers for your help

if your using ssh, i think you put startx in /etc/bash.bashrc to get x to start

---

### Post by kerry_s on 2008-04-14
> **netlogic said:**
> [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

it's not fluxbox he needs help with. :lolflag:

---

### Post by netlogic on 2008-04-14
right... also, it gives some clue how to fix it. 
i doubt people will spend 2pages about apt-get install fluxbox. unless they type it 400x.

---

### Post by kerry_s on 2008-04-14
> **netlogic said:**
> right... also, it gives some clue how to fix it. 
i doubt people will spend 2pages about apt-get install fluxbox. unless they type it 400x.

nothing about starting X over ssh has anything to do with fluxbox. read the op post!

---

### Post by netlogic on 2008-04-14
i guess you haven't read it.
you can install gdm, kdm, or xdm and search about .xintrc
have you clicked links on the bottom? i am sorry to be rude. this topic has been covered in this forum few thousand times.

=====
searching the forum is a good thing. there is a reason, they search things for you before you post. of course, we can go... 'WE SEE NOTHING... WE SEE NOTHING!!!"

---

### Post by kerry_s on 2008-04-14
> **netlogic said:**
> i guess you haven't read it.
you can install gdm, kdm, or xdm and search about .xintrc
have you clicked links on the bottom? i am sorry to rude. this topic has been covered in this forum few thousand times.

=====
searching the forum is a good thing. there is a reason, they search things for you before you post.

no, you don't have to install a log in manager to get X, that's just bloat and unneeded.

but sounds like you've done it a thousand times, so i'll let you handle it. :)

---

### Post by netlogic on 2008-04-14
> **kerry_s said:**
> no, you don't have to install a log in manager to get X, that's just bloat and unneeded.

but sounds like you've done it a thousand times, so i'll let you handle it. :)

gdm/kdM/xdm 
how much xdm eats? 200k? DAMN THAT IS SOOO BLOATED. Do you really use Debian. Xdm was their default manger in the past. it took them a while to switch to gdm.

what is .xintrc?

---

### Post by FakeOutdoorsman on 2008-04-14
> **kerry_s said:**
> that won't work with ubuntu, ubuntu uses a different startup process. it doesn't have /etc/inittab. it uses /etc/event.d/*

if was debian that would be fine, i use a similar to start my debian system.

Curses!  Foiled again.

---

### Post by netlogic on 2008-04-14
Instead one of us type this over and over again. Someone wrote a doc many moons ago.

[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

---

### Post by kerry_s on 2008-04-14
> **netlogic said:**
> gdm/kdM/xdm 
how much xdm eats? 200k? DAMN THAT IS SOOO BLOATED. Do you really use Debian. Xdm was their default manger in the past. it took them a while to switch to gdm.

what is .xintrc?

yes i use debian etch/lenny, i start from a base install and build up from there.
xdm is old as hell and don't have auto log in, his only choice would be gdm or kdm, which have auto log in feature, but who needs all that.

i don't use a log in manager for mine, i use rungetty to log me in and ~/.bash_profile to start X.

if he were using debian, it's a cinch to setup auto start up, but he's using ubuntu, which has gone outside the box for there start up. 

.xinitrc would be where you put the command to start programs and the window manager.(see pic of mine)

---

### Post by netlogic on 2008-04-14
> **kerry_s said:**
> yes i use debian etch/lenny, i start from a base install and build up from there.
xdm is old as hell and don't have auto log in, his only choice would be gdm or kdm, which have auto log in feature, but who needs all that.

i don't use a log in manager for mine, i use rungetty to log me in and ~/.bash_profile to start X.

if he were using debian, it's a cinch to setup auto start up, but he's using ubuntu, which has gone outside the box for there start up. 

.xinitrc would be where you put the command to start programs and the window manager.(see pic of mine)

dude... just chill... you aren't even reading what others have recommended.
also fakeoutdoorsman partially right. LTS still an active distro. READ. 
wow.. you are frugal with jvm... does it matter?

---

### Post by kerry_s on 2008-04-14
> **netlogic said:**
> dude... just chill... you aren't even reading what others have recommended.
also fakeoutdoorsman partially right. LTS still an active distro. READ.

yeah, i need some coffee. :lolflag:

---

### Post by netlogic on 2008-04-14
na.... we all be chilling and illing with the 40s.

---

