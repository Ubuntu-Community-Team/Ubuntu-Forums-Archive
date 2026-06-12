---
title: "Remote Desktop requests from random IPs on firewalled box"
date: 2013-10-10
forum: Security
---

### Post by Fuzzplug Jones on 2013-10-10
I've got an Ubuntu 13.04 box onto which I've installed kubuntu-desktop. All updates have been applied. This is a local file server behind a router in a home. It has internet access but is not on the DMZ and I have no port forwarding set up. In other words, this box should in no way be reachable from the outside.

I need to have VNC access to it though, because it's in the basement and sometimes I need to get at it from my MacBook Pro. In Unity there was a Desktop Sharing app installed, which I used. In KDE, I had to install krfb. Now I can access the box from my Mac, but about every twenty minutes, for hours now, I get a popup from krfb telling me there's been a remote access request from some random external IP address. It's not every minute but it's been pretty constant all day.

[IMG]http://s11.postimg.org/teat7vnhf/Screen_Shot_2013_10_10_at_5_42_54_PM.png[/IMG]

This scares the crap out of me because like I said, this has a local (192.168.x.x) address, is behind a router, and not on the DMZ. Externally-initiated connections should NOT be reaching it. How is this even happening? Does krfb talk to the router and open ports? If so, isn't that insane? What could be causing this? I've triple-checked the router, DMZ is not on and there's no port forwarding, and I had not used VNC prior to this.

---

### Post by CharlesA on 2013-10-10
Do you have UPNP enabled on the router?

I sure hope you are using a password for that VNC server.

As a sidenote, take a look at NX as it sends data over SSH instead of in the clear, so it's more secure.

---

### Post by Fuzzplug Jones on 2013-10-10
Strong password. UPNP might be enabled on the router - but it doesn't seem very Linuxey for a program to open ports on a router, UPNP or not, without asking, or without providing a way for me to disable it in the settings. Can you help me figure out where to disable this behavior in krfb?

---

### Post by CharlesA on 2013-10-10
I don't use it, but it should at least give you the option of disabling UPNP. You should probably disable it on the router, too.

---

### Post by Fuzzplug Jones on 2013-10-10
It doesn't. Maybe I should file a bug report. Thanks.

---

