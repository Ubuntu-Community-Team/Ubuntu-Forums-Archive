---
title: "VirtualBox resolutions too big?"
date: 2008-10-08
forum: Virtualisation
---

### Post by noorez on 2008-10-08
I'm trying to install Fedora into VirtualBox to give it a try. After I installed it I rebooted but the Welcome screen resolution was too big. It went off the edge of the virtual machine window. I stopped the virtual machine and added MaxGuestResolution as 1280x800 but that didn't work. The resolution did not shrink. How can I fix it so that the default Fedora resolution will automatically detect a maximum of what I set?

---

### Post by bangmalley on 2008-10-09
try install the Guest Addition.
Devices->Guest Addition

---

### Post by noorez on 2008-10-09
This is not what I meant. I'll be a little more clear. When Fedora is first started, you have to some first time configuration, (set time zone, create a new user....). The resolution of this screen is too big. The scroll bars on the Virtual Machine window are disabled so it is impossible to even scroll through the entire window to get through the configuration wizard properly. If I try to go to a virtual terminal in the guest, you can't login to one so its impossible to install it from there.

Is it possible to put a limit on an available resolution to a guest. Just like if I were to install fedora on my hard drive directly, it would (or hopefully should:P) detect a maximum resolution of 1280x800 which is what my screen is capable of. If not then 1074x768? ...

---

### Post by MystaMax on 2008-10-09
I had the same problem when I was testing Fedora. It looks like the GDM is displaying at a higher resolution. You have two options (that I'm aware of). You can:

run from the commandline
```
 sudo dpkg-reconfigure xserver-xorg 
```remove all the resolutions you do not want enabled.

or you can edit your xorg.conf file manually:

```
 sudo gedit /etc/X11/xorg.conf 
```or

```
 sudo nano /etc/X11/xorg.conf 
```Look for the Display subsection, and remove any resolution that you do not need. I believe GDM will use the first resolution listed under "Modes". Heres mine on my Dell D630 laptop:

```
 
SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
EndSubSection

```

Why can't you log into virtual terminals? If you cant log in at all, you can always use the recovery mode from grub. If it comes to this, you'll have to use the second recommendation (editing xorg.conf manually).

---

