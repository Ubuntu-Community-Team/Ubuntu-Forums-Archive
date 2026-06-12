---
title: "Help about LTSP: Can I have &quot;thin clients&quot; outside my current network?"
date: 2009-11-22
forum: Server Platforms
---

### Post by pc2009open on 2009-11-22
Hi,

I am a newcomer needing help.   ^_^

I have a Ubuntu 9.10 server set up, with a fixed IP address and 2 ethernet cards. According to my study, a typical (Linux Terminal Service Project) LTSP system will have the server and all thin clients connected through a switch within the same physical area.

Is it possible to have thin clients NOT inside the current network? I mean, can a computer somewhere in the Internet being included in the system? 

Thanks a lot.

Best regards,

paylong

---

### Post by david_crick on 2009-11-23
> **pc2009open said:**
> Hi,

I am a newcomer needing help.   ^_^

I have a Ubuntu 9.10 server set up, with a fixed IP address and 2 ethernet cards. According to my study, a typical (Linux Terminal Service Project) LTSP system will have the server and all thin clients connected through a switch within the same physical area.

Is it possible to have thin clients NOT inside the current network? I mean, can a computer somewhere in the Internet being included in the system? 

Thanks a lot.

Best regards,

paylong
I also have the similar question. Can anybody help?

---

### Post by aseibert on 2010-01-07
I'm working on something like this for my employer. We're an ISP and thinking about dropping pay-per-use kiosks throughout our city.  We'd be running everything over DSL lines through our own dslam.  Only hurdle - thin clients connect over a 10/100/1000 network... running outside of a lan you'd A) Need some way for the client to know where the tftp server is etc. (easy if you're an isp - run a dhcp server over a segmented vlan for the clients.) and B) BANDWIDTH.  It'll take a looooong time for things to transfer on most internet connections.  One possible solution is to use "fat clients" (all processing done on client vs. server).  So i'll work on something and post it when I figure it out

---

### Post by beniwtv on 2010-01-07
Well, there are actually two parts in an LTSP setup. The first part is where the server hands the thin client machine a minimal image to boot. This is usually done via network boot. 

Once the client boots up, it will display a log-in screen which, in reality, runs all programs on the server but displays them on the thin client's screen (this is X.org over the network).

Now, the thin client normally boots over LAN, so that you don't have to install any OS and software on it. But what you can also do is to just put in a small memory stick into the thin client and boot up the client from there. Once booted, it will connect to the server as with the regular thin client.

Theoretically, this should be quite possible. However, the reality is, that there would be much bandwidth required and X.org is not exactly good over WAN connections (latency, etc).

So in the end, I think LTSP per se might not be the best solution. 

If I had to do such a thing, I would set up a server, with users (each user = one kiosk, for example), adjust their rights and settings (lock down, install software, change themes, etc),  and then install FreeNX server. That way, it will be possible to log-in to the server as this user (think of as user=kiosk machine). Use SSH and iptables to restrict IP access to the server (and secure the server in general).

Now, for the client part, prepare a very slim ubuntu minimal distro, on a SD card for example (or a small HDD), which runs X and the NXClient software on boot. Configure NX to autologin to the server IP, or similar and make sure the machine is locked down and has the correct drivers.

NX is very good over slow links in my tests, but all of that varies depending on your latency to the server. I hope I have given you some ideas, though.

Cheers,

---

