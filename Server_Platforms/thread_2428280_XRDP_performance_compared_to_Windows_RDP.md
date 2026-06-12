---
title: "XRDP performance compared to Windows RDP"
date: 2019-10-02
forum: Server Platforms
---

### Post by ah005 on 2019-10-02
Hi people,
did anyone analyse why the performance of XRDP is so bad?

I set up Ubuntu (Gnome, xfce4) on a machine with xrdp and x2go. For both performance when for example web browsing was horrible. Now I installed Windows 10 on the same machine and I'm posting this from it with no issues.

Network is not an issue. The network connection is very good.

Thanks in advance!

BR

---

### Post by TheFu on 2019-10-02
Which version of RDP is being used on the server and client sides?  Are they compatible?

For x2go, if you change the "bandwidth" setting inside the client-connection to be ISDN, more compression is used. This drastically speeds up all drawing.  Over a GigE wired LAN connection, I set the compression to 4K-jpeg. 

If you seek multimedia support over RDP, I believe that is only possible within Microsoft's OSes. They withhold the RemoteFX and AVC1/h.264 video extensions on only their clients.  Also, check your avahi settings. That's the zeroconf implementation used by Linux desktops to find Windows services. If it isn't enabled (or not installed at all, like on Linux servers), then timeouts must happen before alternate connection attempts are made.

Would be helpful to know many more details, so someone willing might be able to reproduce the issue.  I don't have either Win10 or 18.04, so I cannot.  I do use SPICE/QXL, x2go, rdp and VNC between Win7 and Ubuntu 16.04 systems.  Most of the time, I need console access to Windows, so rdp can't be used. Microsoft deliberately prevents RDP connections from doing the things I need.  OTOH, SPICE connections are pretty great on the LAN.

Gnome3 is a very heavy desktop and really wants direct GPU access.  Best to stick with xfce or some other lite desktop for all remote connections.  In 20.04, there should be good Gnome3 -to- Gnome3 remote desktop capabilities from the reading I've done, but it does not appear to be in 18.04 or earlier releases.  YMMV, since your hardware and everyone elses are definitely different.

---

