---
title: "Gnome-Shell on armhf Tegra3 Tablet"
date: 2014-07-18
forum: Ubuntu Development Version
---

### Post by f-jandl91 on 2014-07-18
I am struggling to get this running, i have a tegra 3 tablet (Transformer TF700T) and must pin most of the Xorg Packages so that I can upgrade to Trusty. The latest working X version is from raring (abi 13). 
I have only GLES support, but since @Tista could run gnome-shell on saucy, I would like to know if it is possible to run gnome-shell on old Xorg and GLES. 
Right now I only get a blank screen after boot, when I downgrade gnome-session to 3.6 I have a blank screen with working cursor, but dependency problems.

Old thread for reference: [http://ubuntuforums.org/showthread.php?t=2160224](http://ubuntuforums.org/showthread.php?t=2160224)

---

### Post by tista on 2014-07-19
Hi f-jandl91,

Unfortunately I've moved my focus to Intel Bay-Trail-T/M Atom devices already... 
Because we couldn't hope any chances to keep armhf "core" desktop on those android devices. 

I'm not sure how your TF700T failed to kick stock gnome-shell in Trusty, but I could explain this reason, I suppose this could be the one of evil:

**MetaIdleMonitor / GnomeIdleMonitor**
From Gnome3 3.10.x, they had a new function named "IdleMonitor". It works as "display handler" without any X11 extensions, by connecting dbus directly from inside of mutter/gnome-session routines. So today gnome-shell can run perfectly on Wayland (means completely independent from X11 resources) to handle display devices (active, external, sleep, and so)... By all means of this function, we now could NOT mix stock gnome-shell and downgraded gnome-session/mutter/settings-daemon anymore... if you forced to run old gnome-session by hand, so gnome-shell might fail to find any active monitors within initializing session.

In Utopic, Ubuntu has a "forked" settings-daemon (named unity-settings-daemon) to run unity/gnome-flashback which didn't have IdleMonitor compatibility.

Best regards,
Tista

---

### Post by f-jandl91 on 2014-07-21
Thank you very much for your reply!

Although I tried running trusty, I am completely fine with saucy. What was the latest setup you can remember running? [https://wiki.gnome.org/MichaelHill/Nexus7](https://wiki.gnome.org/MichaelHill/Nexus7) Michael Hill says he was able to run 3.9.5, did you succeed in running >= 3.9.90? Do you have the binaries from back then?

Again, thank you very much for your help!

---

### Post by tista on 2014-07-22
Hi f-jandl91 ;)

Yeah I've succeeded to run 3.9.90 series on Raring/Saucy mixed platform in these days..
[https://drive.google.com/folderview?id=0B9cS96ptLZMeWHFyUS0zdWRYVHc&usp=sharing#list]("https://drive.google.com/folderview?id=0B9cS96ptLZMeWHFyUS0zdWRYVHc&usp=sharing#list")

And above link (Google Drive of mine) shows pre-built binaries to be able to run on that mixed raring. But today raring/saucy were completely outdated, so you'd better to rebuild those packages to fit your 'current' release by your hands... ;) I know that's so hard to rebuild a hundreds of packages on your local machine, though.

Oh forgot to mention, 3.9.90 series means '3.10 pre-release' states, so those could not be maintained anymore (devs serve 3.10 series as stable release).

Anyway I wish you could do something excited, and let us know if you could... ;)

Best Regards,
Tista

---

