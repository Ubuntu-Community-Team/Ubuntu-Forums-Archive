---
title: "Network Manager slowing system down when not connected"
date: 2007-08-22
forum: System76 Support
---

### Post by octathlon on 2007-08-22
I discovered a problem with Network manager when I took my laptop (panv3) to work today and did not connect to a wireless network.   It is in roaming mode. 

The system became very slow -- for example, launching a terminal window took about 45 seconds; launching Open Office took about 3-4 minutes (as opposed to about 2-3 seconds normally).  I found that if I disabled networking, things returned to normal for a few minutes, then became very slow again; enabling/disabling again resolved it again for a while; lather rinse repeat.  Subsequent bootups were also excruciatingly slow.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=405736") describing the problem but their suggestion was disabling networking, which as I said didn't work for me.  

Since I almost always just use my home wireless network, I am thinking about not running Network Manager at all and using the regular Network settings instead, which (I hope) will solve this problem.   My question is how to completely exit Network Manager and/or keep it from automatically starting, and also be able to start it up and use it to connect to a different wifi network once in a while.

---

### Post by thomasaaron on 2007-08-22
You can keep Network Manager from starting with your session by going to System > Preferences > Sessions and un-checking it.

You can start it whenever you want to by going to a command line and entering:

sudo /etc/dbus-1/event.d/25NetworkManager restart
(or you can make a launcher on your upper toolbar to do it. If you go that route, the command would be:
gksu /etc/dbus..................blah...............

That said, are you connecting via static IP?

---

### Post by octathlon on 2007-08-22
> **thomasaaron said:**
> 
That said, are you connecting via static IP?

Thanks!

No, I'm not using a static IP -- yet.  But this weekend I am planning to figure out how to get networking going between my 3 computers and I might wind up having to set static IPs for that.  Right now each of the two Linux computers can see the WinXP computer, but none can see the Linux computers).

---

### Post by octathlon on 2007-08-22
More problems:  I had noticed from the beginning that every so often the wireless connection would be lost and it would reconnect itself.  Now today, ever since these problems with the system running very slow started, the wireless kept losing the connection and tonight it simply would not keep the connection.  (WinXP laptop staying connected the whole time, so it's not the router).

I decided to uncheck the NM checkbox in Sessions and switch to a manual configuration, which I have done a lot on my other notebook with liveCDs lots of times.  So I unchecked it, logged out and back in --NM did not start, as expected.  I set up the manual settings as usual, enabling the wireless connection and entering my WEP key, but it did not connect.

Ever since then, no matter what I do,l my system is in excruciatingly slow mode.  And I mean unusably slow, like several minutes to process any action.  I have tried disabling the wireless connection in Network, and re-checking the NM process (putting settings back to how they were, rebooting (takes about 4-8 minutes to reboot and wireless still did not work).  I also tried unchecking the NM again, leaving wireless disabled in the manual setup, restarting, and same thing.

Also a couple of the times after logging in, after about 5 minutes, I got these errors:
The panel encountered a problem while loading "OAFID:GNOME_MultiloadApplet"  Do you want to delete the applet from your configuration? 
I replied No, then got it again for "OAFIID:GNOME_BattstatApplet". 

I now not only have no wireless, the system is running very very very slow.

edit: tried restarting with : wireless disabled, with and without roaming mode enabled. no difference
tried running System76 driver, no difference
I also restarted a couple of times with the wired connection plugged in and the second time I did that it ran fast again.  Then I logged out, unplugged it, logged in and it was back to slow.

Update Thursday a.m.: I've been looking at the N-M bug reports and when I get home this evening I'll try the workaround reported in ubuntu bug #78263 which looks promising.

---

### Post by thomasaaron on 2007-08-23
I don't think that networking is causing your problems. There is something else going on, I think, that is hogging cpu time.

We are not seeing this problem at all on our shop panv3, and from a tech support perspective, I've not heard anybody else mention it.

So, let's start by doing this... Let's make sure your interfaces file is up to speed. Once that is done, go to a terminal whenever things start to slow down and run this command: top

Post the output here and we'll try to see what's going on.

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to 
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little 
computer monitor).

---

### Post by octathlon on 2007-08-23
OK, I'll do that as soon as I get home at 5pm Central time.

A little more info in case it helps:
I just got the machine last Thursday and I haven't made any system changes other than install Flash and gstreamer and add a system monitor to the panel.

I had no problems other than NM occasionally dropping and auto-reconnecting to the wireless connection, until I took it to my office yesterday with no wireless connection.  This is when the slowdowns started and "disable networking" temporarily resolved it -- that's why I suspected NM as then problem.  While booting or starting programs, it seems like they are just sitting and waiting, with system resource usage staying at 0-11%

---

### Post by thomasaaron on 2007-08-23
The delay when booting is typical of a hosed /etc/network/interfaces file, which often results from manually configuring your network connection via System > Administration > Networking.

---

### Post by octathlon on 2007-08-23
Commenting out the extra lines in /etc/network/interfaces worked. :-D Thanks! 

Now there are two important questions:
1) when I can't connect my laptop to a network for whatever reason, how do I avoid the system slowdown issue? (the slowdown problem happened before I ever touched System>Administration>Network; it happened as soon as I couldn't connect to a network)

2) When I set up my home network, it sounds like  I should not set up static IP addresses for my computers if I want to avoid more problems wth NM.  But I'm not sure how to reliably get my linux machines to see each other on the network without setting static IPs. - Is it possible to set up the home network and still use DHCP?  If so, I'll go read up on that; if not, are there other steps I need to take to be able to use NM with a static IP?

thanks!!

---

### Post by palintheus on 2007-08-23
Depending on what router you have you can set it to reserve IPs by MAC address that way, even though its DHCP, each computer will get the same IP upon connect.

---

### Post by octathlon on 2007-08-23
The slowdown problem seems to be fixed :), but the Network Manager problems continue. :( As I said, it occasionally drops the connection, but had usually reconnected automatically.

Well, it was working fine for a couple of hours tonight, then dropped the connection again while all I was doing was browsing the web--I had just downloaded a Firefox extension at the time.  It never reconnected.  I logged out and back in, it showed disconnected, I clicked the name of the network, it tried to reconnect endlessly.  Tried turning "enable wireless" on its menu off and on too.  I rebooted and it came up showing no connection again.  My network no longer appeared on the menu (nor the other nearby one I usually see there).  So again, no wireless is available and I can't get it back, just like yesterday.  It acts like it just suddenly lost its knowledge of my network and key.  (BTW, the WinXP laptop did not lose its connection, so network is OK)

At least the system is acting at normal speed again, but I am sick of this NM application by now.  But apparently ubuntu depends on it and apps use it to get network status so I can't just uninstall it. 

edit:  About 30 minutes or so after the above, up popped a prompt asking for my keyring password, and a little while after I entered it, I was reconnected.  What in the world is going on here? :confused:

Thx,

---

### Post by palintheus on 2007-08-23
You could try WICD, it works, you may just have to do some work to get it working, I used it to connect to an unsecure network, but was having issues with my WPA network, but only spent about 20-30 min messing with it.

---

### Post by octathlon on 2007-08-23
> **palintheus said:**
> Depending on what router you have you can set it to reserve IPs by MAC address that way, even though its DHCP, each computer will get the same IP upon connect.

Thanks for that info.  I have a Linksys WRT54G; I'll see if it's capable.

[QUOTE=palintheus]You could try WICD, it works, you may just have to do some work to get it working, I used it to connect to an unsecure network, but was having issues with my WPA network, but only spent about 20-30 min messing with it.[/QUOTE]

Thanks, though in any case, I'll still have to resolve the Network manager issue.  Hopefully I can just stop the service. (I noticed yesterday that it was still listed as running even after I unchecked it in Sessions and re-logged in).  I'm just using WEP, but that's leftover from when WPA was still such a pain.  I should switch over to WPA now I guess.

---

### Post by palintheus on 2007-08-23
WICD replaces Network Manager

---

