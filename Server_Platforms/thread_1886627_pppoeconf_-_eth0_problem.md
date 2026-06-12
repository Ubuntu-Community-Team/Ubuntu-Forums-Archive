---
title: "pppoeconf - eth0 problem"
date: 2011-11-25
forum: Server Platforms
---

### Post by markomk on 2011-11-25
Hi, on my ubuntu server first I made pppoeconf connection, after few days I delete and want to make eth0 manual connection wired.
But I have problem with that,
"Rather than invoking init scripts through /etc/init.d, use the service( 8 ) untility, e.h. service networking start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start( 8 ) untility, start networking"

Probably the pppoeconf make me problem, I try to remove it, but I'm not sure I did it. The wired manual settings are fine, they work on win7.
I tried 
/etc/init.d/networking restart

 *Running /etc/init.d/netwroking restart is deprecated because it may not enable some interfaces
 *Reconfiguring network interfaces...
RTNETLINK answers: No such process
Faild to bring up eth0.                                    [OK]


I got this message, how to solve this?
thank you :)

---

### Post by markomk on 2011-11-25
With hard work and tried everything that is possible, only 1 thing left to try. I was skeptic but it WORKS! I found the solution on the forum: 

"NetworkManager is the best way for end-users to configure their network I think these problems are happening with people who configured their networks using the command line using some cut-and-paste fiddling with pppoeconf or stuff in /etc.

To have NetworkManager manage all interfaces without editing ifupdown/interfaces files, this should work.

Check /etc/network/interfaces.

Press alt+F2 and paste in:
Code:

gksudo gedit /etc/network/interfaces

Remove everything but
Code:

auto lo
iface lo inet loopback

Then Check /etc/NetworkManager/nm-system-settings.conf
Press alt+F2 and paste in:
Code:

gksudo gedit /etc/NetworkManager/nm-system-settings.conf

set

Code:

 [ifupdown]
managed=false

Restart computer or NetworkManager service.
From now on, only configure the network using the NetworkManager applet in the notification area (aka system tray).

For more info See: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

If this doesn't work, post here again."

---

