---
title: "When will GNOME 40 have the desktop interface for Ubuntu?"
date: 2021-06-03
forum: Ubuntu, Linux and OS Chat
---

### Post by norbertcserpnyak16 on 2021-06-03
**Hello!**
*I would like to ask you, as Ubuntu users, when to expect GNOME 40 on Ubuntu.*


**I look forward to hearing from you!**

---

### Post by dddman on 2021-06-03
I have no idea about the official g40 release, but if you want it now...

[https://ubuntuhandbook.org/index.php/2021/04/install-gnome-40-ubuntu-21-04/](https://ubuntuhandbook.org/index.php/2021/04/install-gnome-40-ubuntu-21-04/)

---

### Post by deadflowr on 2021-06-03
The Ubuntu Desktop team is working on it, hopefully it'll be in 22.10,
You can keep up with the Desktop team's status here: [https://discourse.ubuntu.com/c/desktop/team-updates/23]("https://discourse.ubuntu.com/c/desktop/team-updates/23")

---

### Post by dddman on 2021-06-03
Update

Instructions in the above link worked without issue and I am now running gnome 40.  Think I'll run it for a while before going back to 20.04.

---

### Post by Dennis N on 2021-06-03
I have to use Fedora 34 part of the time, and don't see an advantage to the new gnome shell 40 arrangement - at best, its a draw. I especially miss the dock being visible from the desktop. Maybe Ubuntu will get dash to dock working.

---

### Post by dddman on 2021-06-03
Yep, I'm not crazy about the new dock either.  I do like having the desktops in the app menu.

---

### Post by TheFu on 2021-06-03
> **dddman said:**
> Update

Instructions in the above link worked without issue and I am now running gnome 40.  Think I'll run it for a while before going back to 20.04.

Beware, if the same config files are used, they've probably been modified for the gnome4 meanings and could break any earlier Gnome or Gnome-based DE if/when you go back.

The best practice around trying different DEs is to always use a different login userid for each test until you finally decide on one. This way, the settings laid down by each DE in your HOME won't become incompatible.

Going between KDE and Gnome-whatever shouldn't matter. I'd say that risk is low.  It's a Qt vs GTK+ thing.

In the old days, before DEs existed, we could mount or HOME directories to all sorts of different Unix-like systems and run almost any Window-Manager, WM, that we liked.  Those days seem to be gone, even more so with Ubuntu since Snaps appear to be mandatory in recent Ubuntu Desktops.

---

### Post by dddman on 2021-06-03
Hello

I cloned (vbox) my existing install and then added gnome40.  So no worries this time.

---

### Post by dddman on 2021-06-03
I have both gnome and ubuntu session installed in 20.04 and they are a bit different in layout.

Gnome 40 right now is a gnome session only, I think a ubuntu session will be different.

---

### Post by zebra2 on 2021-06-08
Currently running gnome 4 session on Impish 21.10.  I did a new OS install on a new drive for testing purposes. It is still immature and have duplicated various reported bugs but posting to this thread from Gnome 4 just the same.

---

### Post by zebra2 on 2021-06-08
I just changed the ppa repos back to impish because the hirsute repos was trying to give me some incompatible routines. I will have to give It time to catch up.  In the mean time I have found some screens that have some real nice 3D.

---

### Post by zebra2 on 2021-06-09
Now after continuous updates the flickering and a few other bugs are gone. I now have a PC using Gnome v4 dev on Impish 21.10 dev

```

System: Host: zebra3-110-15ISK Kernel: 5.11.0-18-generic x86_64 bits: 64   compiler: gcc v: 10.2.1 Desktop: GNOME 40.1 tk: GTK 3.24.29 
  wm: gnome-shell dm: GDM3 Distro: Ubuntu 21.10 (Impish Indri) 
$DESKTOP_SESSION
gnome
$XDG_SESSION_TYPE
wayland
GNOME Shell 40.1
Version: 40.1-0shemgpubuntu2
Version: 3.38.4-1ubuntu3
loginctl type
Type=wayland
zebra3@zebra3-110-15ISK:~$ 
```

---

### Post by zebra2 on 2021-06-10
Currently getting some display freezing. At times it can be cleared with an "Activities" click or <Super> click. Other times requires a logout login accessed by a ctrl alt del. Also, the min/max click on windows is missing. 
Note: My Gnome 40 is running on a fresh Impish OS Legacy mode. Not on Hirsute!

---

### Post by dddman on 2021-06-10
I guess mileage will vary.  Currently running gnome 40 and have min/max buttons and title box.  No screen freeze here.  It just works on 21.04, but also this is only the second time I have used this install.  I think it's time for me to upgrade to 21.10 and see what happens.  Be back

---

### Post by dddman on 2021-06-10
The upgrade took 10 minutes, I'm impressed.  Now running 21.10 + gnome 40

Been on it for 5 minutes and it's working just fine.  I'm beginning to think your install is hosed.

---

### Post by dddman on 2021-06-10
> gnome-shell-extensions : Depends: gnome-shell (< 3.39) but 40.1-0shemgpubuntu2 is to be installed

nautilus : Depends: libnautilus-extension1a (= 1:3.38.2-1ubuntu3) but 1:40.2-0shemgpubuntu3 is to be installed

There are bumps in the road, but small stuff.  Think I'll run it for a while.

---

### Post by dddman on 2021-06-10
Can you update and download packages?  I'm getting a message that I need to fix broken packages first.  This is a fairly vanilla install cloned from another test install.  Not going to invest any time in it, I have my finger on the nuke button, we are ready to launch :-({|=

---

### Post by zebra2 on 2021-06-10
@dddman
Sorry about the delay getting back, I don't use the company network for personal.
I see you managed to get to the same cliff that I did. Congrats!  I will be on it for the duration of the cycle so will be posting results if the problems begin to clear.

---

### Post by zebra2 on 2021-06-10
Just ran updates and received gnome 40 and gsettings 40 updates from proposed.  I have disabled the PPA and am now getting gnome 40 updates from the downstream and not the PPA. Most of the problems have since disappeared. I am now getting updates from the 21.10 repos and not from the 21.04 repos that I hacked to get this going.

---

### Post by zebra2 on 2021-06-12
Well! after a complete reinstall last night and avoiding some errors in my previous procedure, I managed to get a smooth trouble free installation of Gnome 40 on a 21.10 Installation. I Installed the 21.04 PPA with proposed turned off and also changed the repository in the ppa to "Impish" and then after update when the Gnome40 session came up I turned off the PPA, enabled proposed and updated again. After a few more upgrades it all settled down. 

```

zebra1@zebra1-110-15ISK:~$ inxi1
System:
  Host: zebra1-110-15ISK Kernel: 5.11.0-20-generic x86_64 bits: 64 
  compiler: gcc v: 10.2.1 Desktop: GNOME 40.1 tk: GTK 3.24.29 
  wm: gnome-shell dm: GDM3 Distro: Ubuntu 21.10 (Impish Indri) 
$DESKTOP_SESSION
gnome
$XDG_SESSION_TYPE
wayland
GNOME Shell 40.1
Version: 40.1-0shemgpubuntu2
Version: 3.38.4-1ubuntu3
loginctl type
Type=wayland
zebra1@zebra1-110-15ISK:~$  
```

---

### Post by dddman on 2021-06-13
Congrats zebra2

You have to tell us how well wayland + gnome 40 work.

---

### Post by zebra2 on 2021-06-13
@dddman
I have been using Wayland since it was introduced to the Ubuntu desktop by Canonical. I think about Wayland about as much as I think about Systemd. They are just reality. Gnome 40 works just fine with Wayland but I can't say how well it works without it. If I want 3D I need Wayland and if I need 2D Wayland gives me Xwayland which farms out 2D to X. Gnome 40 is a Desktop concept that is developed by Gnome and uses what the System Environment provides. I personally use Wayland because I stay on the experimental edge. That is why I put Gnome 40 on 21.10 and not 21.04. I don't use released versions. If that costs me a reinstall that is ok because thats what I do. I have never asked a support question on this forum because "support" serves "stable". What I Have right now is Ubuntu 20.10 Wayland with the Gnome 40 Desktop which I like very much.  My wife is on Focal Wayland. I keep her on LTS because of its stability. Thanks for your involvement with this thread. Our lifestyles seem to be out of sync so there is a time lapse in the conversation but I'm glad the OP got this going.  Gnome 40 wasn't on my radar at all until now. It is currently my working desktop. Since neither Ubuntu Gnome 40 nor Ubuntu 21.10 have been released this entire conversation probably ought to be in the Development section.
PS: I think that @Fu was on target when he brought config files into the conversation. Most likely they where involved in my reinstall. I suggest that if anyone here is "stable" oriented to not go down this road and wait until it is released as stable (Gnome 40).

---

### Post by dddman on 2021-06-13
Well I tried and tried to get wayland to work for me.  Afterall I wanted to be on the latest and greatest, but in the end I ended up on xorg.  IMO wayland needs some more time in the oven.

I still like to hear in a week how things are with you.  That's plenty of time for those little "got ya" to move in :)

---

