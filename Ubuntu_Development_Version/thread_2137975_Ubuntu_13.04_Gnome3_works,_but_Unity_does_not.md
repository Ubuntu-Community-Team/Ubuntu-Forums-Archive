---
title: "Ubuntu 13.04 Gnome3 works, but Unity does not"
date: 2013-04-22
forum: Ubuntu Development Version
---

### Post by mkstallings1 on 2013-04-22
I'm sure there is an easy fix for this, but after I upgraded from 12.10 to 13.04, Unity does not seem to be working.  When I log in to the Gnome3 DE, everything seems fine, but when I log into the Unity DE, I have no top bar of side bar.  Right-click also doesn't work.  I can get a terminal emulator with Ctrl-Alt-T and Guake works fine with my F12 shortcut, but nothing works as far as the display.  All I have is the wallpaper.  I have taken all the updates.

---

### Post by Redalien0304 on 2013-04-22
did you use Ubuntu Gnme edition or Unity edition try reinstalling Unity.

---

### Post by Frogs Hair on 2013-04-22
Try these command if you haven't already.

If not installed:  ```
sudo apt-get install dconf-tools
``` Reset Unity:```
setsid unity
``` Reset Compiz if needed:```
dconf reset -f /org/compiz/
```

---

### Post by mkstallings1 on 2013-04-22
This was an upgrade from plain Ubuntu 12.10 to Ubuntu 13.04.  I reinstalled Unity through synaptic, but it made no difference.

---

### Post by Gnobody on 2013-04-22
I had this issue but it was my NVIDIA drivers missing the kernel module, apparently the gnome-shell LLVMpipe-fallback works while Unity just crashes and burns.

---

### Post by mkstallings1 on 2013-04-22
> **Frogs Hair said:**
> Try these command if you haven't already.

If not installed:  ```
sudo apt-get install dconf-tools
``` Reset Unity:```
setsid unity
``` Reset Compiz if needed:```
dconf reset -f /org/compiz/
```

None of this changed anything.  It made the screen reset, but all I have is still just the wallpaper.

---

### Post by BlinkinCat on 2013-04-22
Hi,

Getting back to basics - copy and paste then run the following command in a terminal -

```
/usr/lib/nux/unity_support_test -p
```

This will show if your present setup is capable of running Unity.

Good luck - :)

---

### Post by mkstallings1 on 2013-04-22
Results are

Not software rendered:     yes
Not blacklisted:               yes
GLX fbconfig:                   yes
GLX texture from pixmap:   yes
GL npot or rect textures:   yes
GL vertex program:           yes
GL fragment program:        yes
GL vertex buffer objects:   yes
GL framebuffer object:       yes
GL version is 1.4+:            yes

Unity 3D supported:           yes

---

### Post by Gnobody on 2013-04-22
make sure you have all the needed packages ```
sudo apt-get install ubuntu-desktop
```

---

### Post by mkstallings1 on 2013-04-22
> **Gnobody said:**
> make sure you have all the needed packages ```
sudo apt-get install ubuntu-desktop
```

No luck "sudo apt-get install ubuntu-desktop" yielded that I already had the most recent package, so I reinstalled it, and still no change.

---

### Post by mkstallings1 on 2013-04-22
Any ideas?

---

### Post by mkstallings1 on 2013-04-24
Alright, now it is working fine.  I'm not sure why, maybe my last update fixed it.

---

### Post by nonparity on 2013-04-26
> **mkstallings1 said:**
> Alright, now it is working fine.  I'm not sure why, maybe my last update fixed it.

Did you just do a straight ubuntu update or what was the last update you did?

I am having this same issue but odd thing is it only seems to be with one user on the system.  I created a new user and it works okay but I really dont want to have to migrate everything of mine to the new user account.

---

### Post by mkstallings1 on 2013-04-26
I always update through the terminal using "sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get autoremove; sudo apt-get autoclean".  That, and messing around with additional drivers is all I did.  I did several updates while in Gnome3, so I'm not sure which one fixed everything, or if somehow changing drivers back and forth made it finally work right.

---

### Post by boonkui on 2013-05-01
I tried many of the above suggestions but nothing seemed to work. However, I found that Unity 3D worked for a new user that I created. While logged-in to the new user, I switched to the problematic user - this seemed to fix my problem. Hope this might help someone.

---

### Post by pognonec on 2013-05-16
> **boonkui said:**
> I tried many of the above suggestions but nothing seemed to work. However, I found that Unity 3D worked for a new user that I created. While logged-in to the new user, I switched to the problematic user - this seemed to fix my problem. Hope this might help someone.

It did help someone! I am in the same exact situation, and loging in the guest session, then shifting to mine, allowed me to go back to my normal desktop. Once "on", going back to guest session to close it, and coming back to mine was no problem. Cumbersome, by it does work. Thanx again, Boonkui!

---

### Post by emrebulutlar on 2013-05-25
> **boonkui said:**
> I tried many of the above suggestions but nothing seemed to work. However, I found that Unity 3D worked for a new user that I created. While logged-in to the new user, I switched to the problematic user - this seemed to fix my problem. Hope this might help someone.


sure, i had the same problem but fixed by this 

```

[FONT=Ubuntu Mono]dconf reset -f /org/compiz/ 

[/FONT][FONT=Ubuntu Mono]unity --reset-icons &disown[/FONT]
```

---

### Post by zika on 2013-05-25
Funny: It works if I turn Unity plugin on in CCSM while in Fallback(with compiz) but, it does not work if I choose Unity from LightDM or GDM... (GS+Ricotz PPAs all on)... Yes, I've reset everything... ;)

Update&#8321;: Found some spare time to play around... Main complaint if I try to start Unity from Xinit is that it can not find r600 driver... GS and all other work nicely... If I search through logs there are no complaints about r600, it is loaded and initialized OK, problem is just/only with Unity...
Update&#8322;: Checked: it does not have nothing to do with 3.10-999 that I use... The same is with Saucy official 3.9-2...
Update&#8323;: Done some reading... It seems that GS and Unity are going to be very divergent and taking into account Mir, Wayland, etc. we are going to have very dispersed ocean-shore soon...

---

### Post by veresdaniel on 2013-06-05
I have the same problem, do not know how to fix it. Gnome 3.8 working without problems but ubuntu desktop (unity) freezes. Tried to reinstall ubuntu-desktop, vga drivers, but no luck. I found, turning off "Have file manager handle the desktop" option soles this problem, but in this case neither desktop wallpaper not icons are shown.

I'm using nautilus 3.8.1.
Should I try to downgrade Nautilus? How to do it?

My vga is ncore 630m.

Any idea?

Thanks.

---

### Post by zika on 2013-06-07
Saucy&Gnome fully up-to-date (GS3 PPAs and Ricotz PPAs)...
Unity restored to defaults...
All Gnome sessions (GS, Fallback, Fallback-compiz) work just fine...
Unity: black screen...(both if I envoke it as Ubuntu-session or I start Fallback-compiz and turn Unity on)...
&#8222;Have FM handle the desktop&#8220; is off for months now...
ATI open-source driver (if that matters)
All sessions above work either from LighDM, or GDM, or startx/xinit...
Not that I need Unity, just to report and to try to see what's new... ;)

Update&#8321;: After this I do not hope in Unity to start working at all:
```
~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  gir1.2-rb-3.0 libdmapsharing-3.0-2 librhythmbox-core7 libwayland-client0
  libwayland-cursor0 python3-feedparser rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-zeitgeist
  rhythmbox-plugins rhythmbox-ubuntuone unity-scope-audacious
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine
  unity-scope-colourlovers unity-scope-devhelp unity-scope-deviantart
  unity-scope-firefoxbookmarks unity-scope-gallica unity-scope-github
  unity-scope-gmusicbrowser unity-scope-googlenews unity-scope-gourmet
  unity-scope-guayadeque unity-scope-home unity-scope-manpages
  unity-scope-musicstores unity-scope-musique unity-scope-openclipart
  unity-scope-openweathermap unity-scope-soundcloud unity-scope-texdoc
  unity-scope-tomboy unity-scope-virtualbox unity-scope-yahoostock
  unity-scope-yelp unity-scope-zotero
The following packages will be upgraded:
  firefox-trunk gir1.2-gtk-3.0 gnome-control-center-signon
  gstreamer1.0-plugins-bad gstreamer1.0-plugins-good gstreamer1.0-pulseaudio
  libaccount-plugin-1.0-0 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2
  libgail-3-0 libgstreamer-plugins-bad1.0-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libnux-4.0-0 libnux-4.0-common libpocketsphinx1
  libunity-core-6.0-5 nux-tools unity unity-common unity-services upstart
  xserver-xorg-video-intel
```
(just joking, I'm always optimistic...)

---

### Post by VinDSL on 2013-06-07
Last few times I tried to start Unity, it segfaults on me.

Haven't had enough free time to investigate further...

---

### Post by rrnbtter on 2013-06-10
Greetings,
I had the problem with my Saucy installation after an upgrade. I did all of the Dconf settings mention with no luck. I then opened a terminal on my blank desktop Ctrl Alt T and manually installed all of the held back packages which brought my desktop back. I had to use compizconfig to restore my preferred settings.

---

### Post by sammiev on 2013-06-10
After yesterdays updates Unity booted with no problems after using Gnome3.

---

### Post by zika on 2013-06-11
Same here, all G3 and Ricotz PPAs active...
Now I'm sorry that I've reset Unity ... ;)

---

