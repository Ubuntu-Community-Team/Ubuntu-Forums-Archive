---
title: "[B]Which V.Box configuration is better?[/B]"
date: 2013-02-09
forum: Virtualisation
---

### Post by AMKawam on 2013-02-09
I need to install ubuntu and windows7 on my machine and work simultaneously. 

I have a modest CPU speed, but with 8 GB of memory.. 

Would it be better to use ubuntu as my primary OS, and install Windows7 on virtual box?

Or would if be better to do it the other way around.. Windows7 as primary and Ubuntu on VBox?

---

### Post by Rebelli0us on 2013-02-09
I think the Linux kernel is more stable than Windows and VBox seems to work better in Linux as Host OS.  Also Win 7 often puts VBox in "compatibility mode". So I use Linux as host and windows as guest.

---

### Post by belorios on 2013-02-12
That depends on what you are gonna do on each system. If you doesn´t need to run programs that are heavy on the graphics I would recommend Ubuntu as host using the same arguments as Rebelli0us. 

But if you are thinking of playing games, working in photoshop and stuff like that I would recommend using Windows as host.

---

### Post by MrKaliman on 2013-02-18
Correct use Windows as Host if your daily apps/games are running in Windows only.
Install virtualbox and install ubuntu as a guest until you are comfortable enough to use ubuntu as Host.

---

### Post by SeijiSensei on 2013-02-18
I have a machine with a Windows host and an Ubuntu guest.  It took me a while to get the guest to run in a 16:9 resolution like the host does.  You have to install the extension pack and then generate and edit an xorg.conf file to add extra resolutions.  I don't think that's a likely scenario for most users.  Windows in Ubuntu, on the other hand, works excellently.  Make sure to install the extension pack if you need to access the host's USB ports from the guest.  That's true regardless of which OS you make the host.  The extension pack also takes advantage of features in the video hardware to improve the emulated display.

I like Seamless Mode with my Win7 panel at the top of the screen and my Kubuntu panel on the bottom.  You can also pin the Win7 session to a virtual desktop and keep it out of the way until you need it.

---

### Post by hashky on 2013-03-15
Great info here!  

I have 1 box set up with Ubuntu as Host.  I don't know of a good way to backup the root configuration - like Virtualbox installation, change ownership of partitions, automount, etc.  Are these changes made in root or home?  If I had to reload the OS, would I have to do all the tweaking manually - again?

If I use Windows as host, I could use Acronis to make the Win 7 Host backup - automatic, "hot backup" in the background.  I haven't found any thing like Windows Volume Shadow Copy in Ubuntu.  What am I missing?

Ron Spruell

---

