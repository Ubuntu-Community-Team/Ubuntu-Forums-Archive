---
title: "How do Xubuntu &amp; Unity Get Along?"
date: 2016-03-23
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2016-03-23
Thinking of installing the Xubuntu Desktop on a Unity Installation so my daughter can try out Xubuntu. Anything I should look out for? I stopped installing dual DEs a little while back. I remember, for instance, that Nautilus used to fight with Thunar over control of the XFCE desktop/wallpaper. One had to shut down nautilus after booting into XFCE. There might have been an inelegant hack, but I don't remember it now.

And if anyone cares to recommend what DE's should **_not_** be mixed with Unity, that might also be useful info.

---

### Post by sammiev on 2016-03-23
I'm not a fan of mixing DEs.

If you have room to dual boot, show your daughter the real thing or maybe a Xubuntu live from a USB stick.

Hope she enjoys Xubuntu.

---

### Post by 6975 on 2016-03-23
I used to but no more If I want to run I'll dual patition no more mixing DE.
Beside there is Ubuntu minimal CD if you want a lighter Xubuntu 
or Pure XFCE on Ubuntu core without mixing stuffs with unity.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by grahammechanical on 2016-03-23
I do not think that alternative desktops should be mixed at all. I doubt that anyone is working on alternative desktops from the point of view that they should all play nice with each other. It is a case of installing the desktop code and what you get is what you have got.

From time to time we get posts from users who want to remove the alternative desktop and get back the original. It is very difficult to do because configuration files have been replaced. In my experience, re-installing is the less painful (to the brain) option. At least I can put my feet up while most of the installation progresses.

Regards

---

### Post by neu5eeCh on 2016-03-23
Okay, three votes against. Unity is working. She likes it. I won't mess with it. I might encourage her to try out Unity 8 though, once 16.04 is released. I'm assuming there shouldn't be a problem with 7 & 8 on the same install.

---

### Post by vasa1 on 2016-03-23
> **VTPoet said:**
> Okay, three votes against. Unity is working. She likes it. I won't mess with it. I might encourage her to try out Unity 8 though, once 16.04 is released. I'm assuming there shouldn't be a problem with 7 & 8 on the same install.

Re. Unity 8, [http://askubuntu.com/questions/740470/will-ubuntu-16-04-run-unity-8-on-the-desktop](http://askubuntu.com/questions/740470/will-ubuntu-16-04-run-unity-8-on-the-desktop)

---

### Post by neu5eeCh on 2016-03-23
My understanding is that it can be installed on 16.04, even 15.10,  (though it's not default):

```
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install unity8-desktop-session-mir
```

---

### Post by fallenshadow on 2016-03-24
From my experience XFCE and Ubuntu (Unity) don't mix very well. I installed XFCE in Ubuntu and it has messed up the nice notifications top right of the screen. Also experienced random issues such as the wallpaper being inherited from the one I last logged into.

---

### Post by sudodus on 2016-03-24
I agree with the majority here. Do not mix standard Ubuntu and Xubuntu.

But I enjoy mixing Xubuntu and Lubuntu. My current system was installed as **Xubuntu** with the meta-packaged **lubuntu-desktop** added afterwards. It gives me a system that is better for me than either of the pure systems. Most of the time I'm using the Lubuntu desktop. My hardware is getting old and I want the fast response and the good video playing of the LXDE desktop environment that comes with Lubuntu. And I have many good tools and system configurations of Xubuntu.

---

### Post by mastablasta on 2016-03-24
virtualbox solves most issues with regards to testing DE.

---

### Post by kurt18947 on 2016-03-24
> **mastablasta said:**
> virtualbox solves most issues with regards to testing DE.

True dat. A guest O.S. in Virtualbox doesn't take much room and seems to function pretty well.

---

### Post by Bucky Ball on 2016-03-24
When people are saying 'I installed xfce and it screwed my system', are people meaning they installed xfce4, logged out, chose xfce4 from the session menu then logged in to an xfce4 session or are people saying they installed xubuntu-desktop? 

A really common mistake and point of confusion around here is people installing xubuntu-desktop (but same applies to any *buntu-desktop) because they think that is equivalent to installing xfce, the desktop environment. It's not! Sure, you'll get xfce4 ... along with the rest of Xubuntu! Installing *buntu-desktop is equivalent to installing the whole kaboodle on top of what you already have installed.

So, to anyone that was intending to just install the desktop environment xfce and installed xubuntu-desktop, go back, wrong way (not that there's any going back after that gaff). If you want to install the desktop environment, install the desktop environment xfce4, not xubuntu-desktop: Xubuntu on top of Ubuntu. If you go that route, yea, expect issues. 

> sudo apt-get install xfce4

That's it. The desktop environment only. Having said this, no, I don't mix desktop environments anymore, either, but I do mix apps from other flavours without issues (I generally install the minimal and drag in what I want/need, which isn't much).

I just wanted to make this absolutely clear because, as mentioned, it is a common cause of confusion. If you want to install a desktop environment and are installing *buntu-desktop, you're missing it. You only want the desktop environment. If you were running xubuntu and wanted to try Unity, would you install ubuntu-desktop? No. That would leave you with Xubuntu PLUS Ubuntu on the same install! You would install Unity, the desktop environment used by Ubuntu.

Just providing some clarity on this for those who might be mixing up *buntu-desktop with installing JUST the DE, and end of rant. :D

---

### Post by neu5eeCh on 2016-03-24
Hmmm... It's very likely I'm not as knowledgeable, but based on my experience I'm not sure I would agree. 

I've done it both ways in the past (and I've installed desktops using Ubuntu's minimal/network install option.)

So, I've done what you're suggesting, but have found the "xfce4 desktop" as opposed to Xubuntu, significantly lacking. Xubuntu provides a good deal of customizability [is that a word?] and functionality that is missing in a bare bones XFCE4 desktop install. For example: Installing just the desktop doesn't pull in any of the "panel extras". These will have to be installed afterward along with other dependencies at which point one might as well have installed Xubuntu-Desktop. And again, in my experience, the notion that you're duplicating applications by installing Xubuntu over Ubuntu isn't entirely true. Xubuntu desktop isn't going to pull in dependencies or apps that are already available by virtue of an Ubuntu installation. It's only going to pull in items like panel-extras and a handful of XFCE specific applications -- some Control Panel options for example.

It *will* pull in Thunar and XFCE4 Terminal (which are duplicative), I think, but installing the desktop will do that also.

---

### Post by Bucky Ball on 2016-03-24
> **VTPoet said:**
> And again, in my experience, the notion that you're duplicating applications by installing Xubuntu over Ubuntu isn't entirely true. Xubuntu desktop isn't going to pull in dependencies or apps that are already available by virtue of an Ubuntu installation. It's only going to pull in items like panel-extras and a handful of XFCE specific applications -- some Control Panel options for example.

Never suggested otherwise. ;)

---

### Post by mikodo on 2016-03-24
> **VTPoet said:**
>  - snippet - that might also be useful info.
Nothing useful here. I remember that thread of yours helping me out. I just searched for it thinking it was Toz who offered the "hack". I needed it as it was just while I was looking for a replacement DE before leaving 10:04 and its' Gnome2 DE. I had installed "Xubuntu-desktop" on it and though I liked the old Nautilus until the Gnome-devs dumbed it down, it was pretty heavy-handed in Xubuntu. It wasn't Toz. I miss him. He taught me a lot of things on the customizaton of Xfce desktops. 

Anyways, I wouldn't think that issue has changed any but, I don't know. Here's the thread for nostalgia sake:

[URL="http://ubuntuforums.org/showthread.php?t=1768245"]http://ubuntuforums.org/showthread.php?t=1768245

:)
[/URL]

---

### Post by Frogs Hair on 2016-03-24
I've used xfce4 + the goodies package which adds a host plugins . There was some duplicate/similar applications(see below). Using Thunar exclusively in the xfce session is a helpful because Nautilus wants to handle the desktop. For example, if a wallpaper is set from the pictures folder in Nautilus in the xfce session it takes over and the desktop context menu and functions change from xfce to what you would in the Unity session. All installed applications are of course visible in unity and all dual desktop installations are cluttered. 

```
This package will install the following Xfce4 related plugins:
  * Extra artwork (xfce4-artwork)
  * Battery levels monitor (xfce4-battery-plugin)
  * Clipboard history (xfce4-clipman-plugin)
  * CPU frequency management plugin (xfce4-cpufreq-plugin)
  * CPU utilisation graphs (xfce4-cpugraph-plugin)
  * Date and time plugin (xfce4-datetime-plugin)
  * Disk performance display (xfce4-diskperf-plugin)
  * Filesystem monitor (xfce4-fsguard-plugin)
  * Generic monitor, for displaying any command result (xfce4-genmon-plugin)
  * Mail watcher (xfce4-mailwatch-plugin)
  * Mount plugin (xfce4-mount-plugin)
  * Network load monitor (xfce4-netload-plugin)
  * Notes plugin (xfce4-notes-plugin)
  * Quick access to bookmarked folders, recent documents and removable
    media (xfce4-places-plugin)
  * Tiny launchers (xfce4-quicklaunchers)
  * Sensors plugin, frontend to lm-sensors (xfce4-sensors-plugin)
  * Smartbookmarks plugin (xfce4-smartbookmark-plugin)
  * System load monitor (xfce4-systemload-plugin)
  * Timer plugin (xfce4-timer-plugin)
  * Command line with history (xfce4-verve-plugin)
  * Wireless lan monitor (xfce4-wavelan-plugin)
  * Weather monitor (xfce4-weather-plugin)
  * Keyboard configuration (xfce4-xkb-plugin)
  * Archive management for Thunar (thunar-archive-plugin)
  * Media tags editor for Thunar (thunar-media-tags-plugin)
  * Alternate menu plugin (xfce4-whiskermenu-plugin)


It'll install some standalone applications too:
  * Tiny text editor (mousepad)
  * Images viewer (ristretto)
  * CD/DVD burner (xfburn)
  * Frontend to dictionnaries (xfce4-dict)
  * Notification daemon (xfce4-notifyd)
  * Tool to take screenshots (xfce4-screenshooter)
  * Task manager (xfce4-taskmanager)
  * Terminal emulator (xfce4-terminal)


Some packages are only suggested because they bring too much dependencies,
but you may find them interesting:
  * Cellular modem plugin (xfce4-cellmodem-plugin)
  * Search plugin, frontend to locate (xfce4-linelight-plugin)
  * DBus messaging plugin (xfce4-messenger-plugin)
  * Another commandline plugin (xfce4-minicmd-plugin)
  * Frontends to MPD (xfce4-mpc-plugin, xfmpc)
  * Radio plugin (xfce4-radio-plugin))
  * Fast-user switching plugin (xfswitch-plugin)
  * ThinkPads HDAPS plugin (xfce4-hdaps)
  * GIO/GVfs frontend to manage connections to remote filesystems (gigolo)
  * Media player (parole)
  * Power Manager (xfce4-power-manager)



```

---

### Post by vasa1 on 2016-03-24
> **VTPoet said:**
> ...
And if anyone cares to recommend what DE's should **_not_** be mixed with Unity, that might also be useful info.

DE's that try to be everything. DE's that try to give the user a seamless integrated experience.

> **mikodo said:**
> ... I miss him. ...+1.

---

### Post by neu5eeCh on 2016-03-25
> **mikodo said:**
> I miss him. He taught me a lot of things on the customizaton of Xfce desktops. 

Anyways, I wouldn't think that issue has changed any but, I don't know. Here's the thread for nostalgia sake:

[URL="http://ubuntuforums.org/showthread.php?t=1768245"]http://ubuntuforums.org/showthread.php?t=1768245

:)
[/URL]

Wow! Didn't think that was so long ago! Toz was amazing. I wish i had the hobbyist's time (he seems to have had) to really get into Linux. Wouldn't mind building it from scratch -- someday when I'm independently wealthy and all the kids are out of the house.

---

