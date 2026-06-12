---
title: "Gazelle Pro Constantly Locking Up"
date: 2011-05-13
forum: System76 Support
---

### Post by moab on 2011-05-13
I just received a new Gazelle pro last night, running 11.04. 

I only had time to install wireshark, chromium, and vlc before bringing it into work today. That's it.

When I first turned it on today, it locked up immediately after logging in. This happened twice on Unity and twice on the old ubuntu. It booted into safe mode fine. I then did a normal restart, and got into Unity.

I then updated and upgraded from command line, and now the entire  machine is locking up every 5 minutes. The only way to reboot is the  alt+prt scr sequence. And it will still occasionally freeze after login.

Freezes happen at random during normal operation (for example, while trying to import firefox bookmarks), but they can be  induced by trying to use chromium (listening to Internet radio seems to  make the freezes happen quickly) and trying to use unity features (like  application search). But it still happens in the old ubuntu style as  well.

Is anyone else experiencing this?

---

### Post by isantop on 2011-05-13
Could you try running from an Ubuntu LiveCD and see if that helps? Though rare, it is possible for software glitches to slip in during the imaging process.

---

### Post by moab on 2011-05-13
I ran live and didn't have any problems, but the live disk doesn't have any drivers or video features. 

I've also restored to factory settings, reinstalled drivers, and tried Ubuntu without graphical features and haven't had any improvement. 

Should I just do a fresh install?

---

### Post by isantop on 2011-05-16
At this point, I think that may be your best option.

---

### Post by moab on 2011-05-16
I reformatted and installed a fresh 11.04. I then updated/upgraded,  installed system 76 package, and from the system 76 package installed  the drivers and restored it to factory state. Then restarted.

I then installed chromium-browser and flash for both Firefox and  Chromium. I tired both the normal 32-bit and experimental 64-bit flash  versions, and started up some websites that use flash (since at first it  seemed like flash was the cause of crashes, which I realize doesn't  make any sense since it was locking up right after logging in). 

Fortunately, I am no longer getting log-in lock-ups, but I am still  getting crashes when web browsers are open (although less frequently).

While I was letting a flash program run in the background, I noticed a few behaviors that sometimes seem to trigger a lock up:

- Scrolling too fast (ie, grabbing the scroll bar and moving it quickly)
- Typing in a program too fast after hitting the command key

I'm not sure what could be causing that other than a video driver.

---

### Post by isantop on 2011-05-19
Are you using the Nvidia Proprietary Driver?

---

### Post by Island Usurper on 2011-07-06
I have this problem *when* I use the proprietary nVidia driver. The hard drive gets really hot, so I think that's where the lock-up comes from. I've already had the hard drive replaced once in my Gazelle Pro for this reason, so at this point I've been settling for the open-source driver. The experimental open 3d acceleration driver wasn't cutting it for the games I wanted to play, but this is supposed to be a work laptop anyway.

---

