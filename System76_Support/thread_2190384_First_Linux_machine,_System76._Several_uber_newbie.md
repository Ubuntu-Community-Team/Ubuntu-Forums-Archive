---
title: "First Linux machine, System76. Several uber newbie questions on usability"
date: 2013-11-27
forum: System76 Support
---

### Post by xagent2 on 2013-11-27
Hey, I just got a System 76 laptop with Ubuntu 13.10. This is my first  personal Linux native laptop. I have used Linux for 10 years now, 4 in  college and 5 at work for the past years. However, there it has been  almost entirely to do development work from within a terminal (the bash  shell, cvs, make, acme, vim/emacs for coding, writing bash and tcl scripts, etc..... and that's about it). I know  more about the Linux kernel code itself, modifying it and compiling it, than  actually using it. So I have a few questions about usability

1. How the hell do I get a terminal window open? I  don't see any icon for a terminal. Perhaps I'm just blind and it is nearly 2AM. Normally I'd right click in the  desktop(in XFCE at work) and there's a terminal icon. Which brings me to  my next point - how do I right click?

2. This is my first laptop  w/ just one large touch pad. My previous laptop was a Lenovo. It has 3  buttons, left, middle right. How do I right click? Can't find a way to  configure multitouch in the touchpad System settings

3. How do I  middle click? I am very used to highlighting to copy and middle clicking  to paste. Ditto for middle clicking to auto open a link in a new  browser tab. 

4. I noticed that backspace doesn't go to the  previous page in Firefox. Alt + <-- works, but I'm habitually used to  a 1 keypress for perhaps the most common browser task

5. How do I  change this desktop environment? I actually did some web research on  this. Looks like this is a new desktop envronment called Unity. I see  several people complaining about Unity, and ways to update to Kubuntu /  Xubuntu. I'm thinking of switching to Xubuntu. Will that cause any  problems? If I want to, how do I revert back to the default? 

6. I've been hearing about a new desktp environment called Cinnamon. Thoughts? What are the pros and cons of using this vs. Gnome vs. XFCE vs. Unity?


Sorry  for all the newbie questions. I'm sure I could eventually find the  answers on Google but thought I'd consolidate them all here.

---

### Post by xagent2 on 2013-11-27
Ignore #4. I just found the answer to that via: [http://lifehacker.com/269945/set-backspaces-firefox-behavior](http://lifehacker.com/269945/set-backspaces-firefox-behavior)

Although I noticed that backspace did not scroll up a pagae like it said was default behavior in Linux. Backspace just did nothing.

---

### Post by xagent2 on 2013-11-27
:( it looks like middle click is not supported? Lame...

[http://ubuntuforums.org/showthread.php?t=1863198](http://ubuntuforums.org/showthread.php?t=1863198)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/971783](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/971783)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/754000](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/754000)

---

### Post by Bucky Ball on 2013-11-27
*Thread moved to **System76 Support**.*

You might have more luck here.

To install xfce4, simply open Software Centre, search for and install it.  Log out, choose it from the 'Sessions' pop-up. Log in.

---

### Post by 3rdalbum on 2013-11-27
> **xagent2 said:**
> 
1. How the hell do I get a terminal window open? I  don't see any icon for a terminal. Perhaps I'm just blind and it is nearly 2AM. Normally I'd right click in the  desktop(in XFCE at work) and there's a terminal icon.

A couple of ways:

Hit Control-Alt-T

or click the Ubuntu button, type "terminal", click the first result that comes up. Or click the Ubuntu button, click the Applications button, click "Filter Results" and "Accessories" and it should be one of the entries.

> 2. This is my first laptop  w/ just one large touch pad. My previous laptop was a Lenovo. It has 3  buttons, left, middle right. How do I right click? Can't find a way to  configure multitouch in the touchpad System settings

3. How do I  middle click? I am very used to highlighting to copy and middle clicking  to paste. Ditto for middle clicking to auto open a link in a new  browser tab. 

Right-click is probably a two-finger tap, not sure about middle-click but it's probably a three-finger tap.

> 5. How do I  change this desktop environment? I actually did some web research on  this. Looks like this is a new desktop envronment called Unity. I see  several people complaining about Unity, and ways to update to Kubuntu /  Xubuntu. I'm thinking of switching to Xubuntu. Will that cause any  problems? If I want to, how do I revert back to the default? 

6. I've been hearing about a new desktp environment called Cinnamon. Thoughts? What are the pros and cons of using this vs. Gnome vs. XFCE vs. Unity?

People complain about Unity, but mainly because it's different and takes some time to get used to. Once you're comfortable with Unity (this takes about a week) you'll probably love it and not want to use anything else - so maybe you should try sticking with it for a week or two.

You can install a different desktop environment by installing it in Ubuntu Software Center (or simply apt-getting the desktop you want) and then at the login screen, click the little Ubuntu button and change the session to the desktop environment you want to use.

Installing a different desktop won't cause any problems, and changing back is as simple as selecting it at the login screen.

Cinnamon has received, IMHO, an inordinate amount of press and hype for something so basic. It's pretty much the Windows 98 desktop, running on Gnome 3 infrastructure, with a different menu. The best part about Cinnamon is that its default theme is rather attractive. I've been using Cinnamon for the past six months on my netbook and honestly I'm going back to Unity. Cinnamon is stable enough (thanks to Gnome), but too old-fashioned for my liking. Lacking in features, too.

Gnome is pretty good, I still prefer Unity for its search and its efficient use of screen space, but Gnome is modern, innovative and attractive. XFCE is another fairly simple and lightweight desktop, and in Ubuntu it is configured to look like Ubuntu 10.04. You don't really need us to tell you which desktop to use, you can install them all and try them all on the same installation of Ubuntu.

---

### Post by xagent2 on 2013-11-27
> **3rdalbum said:**
> 


Right-click is probably a two-finger tap, not sure about middle-click but it's probably a three-finger tap.


Nope, neither work. I found out right click via trial and error: just single clicking the bottom right part of the touchpad. Single clicking the rest of the touchpad is left click/primary mouse button. 2 fingers to scroll works. But 2 finger tap and 3 finger tap both do nothing, and don't see a way to configure either in touchpad System Settings.

at least I found right click... still desperatly need middle for pasting. Where are the options to configure Multitouch? [rant] If there's one thing IBM/Lenovo did right, it was the design of their laptops. Solid keyboard, perfect tactile feedback, perfect touchpad, and it had 3 separate, distinct mouse buttons. So much easier than from using the multi-touchpad and gestures on my friends' Macbooks. Having a separate button from the touchpad also makes highlighting infinitely easier. Just keep button pressed and release finger and touchpad when it hits the end and go back to other side. With the touchpad+button combo re-adjusting the finger doing the highlifitng screws up the mouse pointer and my highlighting gets all messed up! :( :([/end rant]

> People complain about Unity, but mainly because it's different and takes some time to get used to. Once you're comfortable with Unity (this takes about a week) you'll probably love it and not want to use anything else - so maybe you should try sticking with it for a week or two.

You can install a different desktop environment by installing it in Ubuntu Software Center (or simply apt-getting the desktop you want) and then at the login screen, click the little Ubuntu button and change the session to the desktop environment you want to use.

Installing a different desktop won't cause any problems, and changing back is as simple as selecting it at the login screen.

Cinnamon has received, IMHO, an inordinate amount of press and hype for something so basic. It's pretty much the Windows 98 desktop, running on Gnome 3 infrastructure, with a different menu. The best part about Cinnamon is that its default theme is rather attractive. I've been using Cinnamon for the past six months on my netbook and honestly I'm going back to Unity. Cinnamon is stable enough (thanks to Gnome), but too old-fashioned for my liking. Lacking in features, too.

Gnome is pretty good, I still prefer Unity for its search and its efficient use of screen space, but Gnome is modern, innovative and attractive. XFCE is another fairly simple and lightweight desktop, and in Ubuntu it is configured to look like Ubuntu 10.04. You don't really need us to tell you which desktop to use, you can install them all and try them all on the same installation of Ubuntu.

Thanks. Still getting used to Unity. Now that I have a terminal window open, i'm a lot more comfortable. I was just going to install it via apt-get. This search feature and Software App Center is really new to me. Are they trying to be like Apple or what? Personally lol, I prefer a GUI w/ a taskbar (where's the taskbar in Unity?!)... and I actually like the Windows 98 look. I still run Windows 7 in the "Classic Theme". Call me old fashion/utilitarian... Im going to go to XFCE for now since it's what we use on our build and dev servers at work and since it's pretty barebones

---

### Post by Bucky Ball on 2013-11-27
Yea, xfce4 suits me on a minimal install. Don't install xubuntu-desktop or it will drag in the whole of Xubuntu. You only want xfce4:

```
sudo apt-get install xfce4
```

If you like bare-bones, you might like to put a minimal together on the side:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

