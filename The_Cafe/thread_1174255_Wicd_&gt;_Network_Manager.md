---
title: "Wicd &gt; Network Manager"
date: 2009-05-30
forum: The Cafe
---

### Post by Luke has no name on 2009-05-30
I've felt like this since I first tried it out, and I consistently come back to it. 

-Wicd has an actual window panel that comes up, rather than trying to be a hip little 'daemon' that sits in the task panel. This makes it more useful by displaying more information and being more persistent. You don't really change wireless networks that much, anyway, so bringing up a window isn't an issue.

-Wicd doesn't assume it should automatically connect to ANY wireless network. the user must tell wicd what wireless networks get to have autoconnect privileges.

-Wicd is more informative. It tells the encryption type, if any, and the precise signal strength of a wireless network.

-I was trying to get a good connection in Starbucks yesterday, and whenever I tried loading too many pages at once, the connection would lock up. I tried moving, I tried disabling/enabling wireless, but it kept messing up. On a hunch, I installed wicd and started using that. It fixed my problem.

-Wicd has a refresh network list button, newtorkmanager doesn't. WHAT THE HELL?

Several people have argued this to the Ubuntu devs, and several times they've been told down. Please refresh my memory.

---

### Post by Kareeser on 2009-05-30
Point 2 - nm-applet **assumes** you want to connect automatically when you add a network, yes... but you can easily uncheck it if you'd like on-demand connections.

Point 3 - nm-applet queries the wireless gateway and determines the encryption for you. You don't have to blindly guess (like in Windows), and it's more user friendly. If you're setting up the wireless connection yourself, there is a dialogue box to select an encryption setting, so it's not like the feature isn't implemented in the GUI.

Point 4 is valid... point 1 is a judgement call. I like hip little daemons :)

---

### Post by Icehuck on 2009-05-30
The CLI is imo the best way to manage your wifi. If you make yourself some scripts it works wonders.

---

### Post by mamamia88 on 2009-05-30
i like the daemon and i tried wicd in mint 7 and it froze everytime i tried to open it and i like the network manager interface way better

---

### Post by OutOfReach on 2009-05-30
To me, WICD and NM work the same, no problem with NM so I'm staying with it. If there ever is a problem, there's always WICD. That's the way I see it.

---

### Post by kerry_s on 2009-05-30
wicd is nice, but a bit heavy for my tastes and python's just to slow.

i use a manual network manager when i need to pop around other networks and a script for every day use set up just like it but faster to launch.

---

### Post by speedwell68 on 2009-05-30
I first came across WiCD when using Easy Peasy Linux on my Netbook.  When connected to a WPA network NM kept on dropping it's network.  I installed WiCD and the problem went away, since then I use it on every PC.  I too find it more informative, it has a proper network activity tray icon for a start.

---

### Post by chucky chuckaluck on 2009-05-30
wicd is moron-proof.

---

### Post by Polygon on 2009-05-31
never had a problem with nm-applet, except for a few bugs which are caused by my wireless driver rather then nm-applet, and would appear if i used wicd too.

if it ain't broke, don't fix it :o

---

### Post by Xbehave on 2009-05-31
most of your complaints seam to be against the gnome gui nm-applet, not NetworkManager.

Personally im not a fan of either, but i like where NetworkManager is heading and it creates few hiccups now (used to be a real PITA) i just hope:
1) somebody creates a CLI to it
2) the GUIs advance so that its easy for users to add scripts for NetworkManagerDeamon to launch (e.g i want a "safe"/"unsafe" script to run when i connect to certain hostspots but not other)

---

### Post by bigbrovar on 2009-05-31
I think the Wicd Network manager debate brings out the beauty of linux, which is choice. Personally i prefer network manager. I think network manager 7 offers great improvements over wicd. things like 3G connections, wireless sharing, and setting up ad-hoc connections to share internet are a breeze with network manager, a matter of few clicks which is the way networking should be (at least for end users). although i have to admit that on a few occasions i have had to install wicd for some of the students in my school, but that was network manager 0.6.

---

### Post by Harii on 2009-06-01
I like wicd but i'm always messing up wicd on upgrades - seems frail to me?
I always had more luck with rutilt or wifi-wiz.

On a weird note:
rutilt and wifi-wiz can see weaker signals - than wicd?
anyone knows why?
i can use three different wifi apps (not at the same time:D) and get three different outcomes?

---

### Post by Dimitriid on 2009-06-01
wicd used to be the only thing that would make my old laptop's wireless work. Now that broadcom is somehow more manageable, its the other way around: Network Manager is the only thing that will work. 

This seems to change constantly though which has lead me to believe that wireless adapters and using that technology is utterly pointless: Now I will just buy routers and hack some of them to function as wireless bridge.

This works for all my devices, from my consoles like the PS2 and the 360 to my desktop. 

In the end though, I think this is really a matter of largely unsupported or barely supported hardware. Maybe in a few years it will work out, something tells me that the current trends in this days of DRM schemes means that it will only get worst from here on.

---

### Post by lswb on 2009-06-01
One of the main problems I have with NM is that in locations with more than one wifi network, or even a single network with repeaters, it keeps roaming to another AP and interrupting the connection. It's for that reason that I also have rutilt installed on my laptop.

---

### Post by Ripfox on 2009-06-01
Wicd RULES hands down!! :)

---

### Post by papangul on 2009-06-02
I suffered a lot trying to configure NM to work with the linksys wmp54g adapter.The way NM deals with the /etc/network/interfaces file is highly suspicious and is comparable to the behaviour of a ghost in a haunted house. At one point I kept the interfaces file and NM open side by side and tried desperately to somehow get the interfaces file to fall in line but failed. 

Later I installed WICD and the wireless adaptor started to work flawlessly in a couple of minutes. The best part is that wicd doesn't mess with the interfaces file.

Disclaimer:I am on hardy and haven't used the later versions of NM.(but a lot of people faced networking problems in jaunty, a lot of which were solved by installing wicd)

---

### Post by anaconda on 2009-06-02
The WORST thing about nm is that IF your network connection is not understood by nm, then eg. firefox (and some other programs) will ALWAYS start in offline mode.

With Wicd this problem went away.. (and in 9.04 when nm FINALLY understangs my 3G dongle the problem will go away when I update.)

Still like wicd more.

---

