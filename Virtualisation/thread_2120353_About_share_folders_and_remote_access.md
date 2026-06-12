---
title: "About share folders and remote access"
date: 2013-02-26
forum: Virtualisation
---

### Post by satimis on 2013-02-26
Hi all,

host - Ubuntu 12.04 desktop 64bit
guests - all 64bit Ubuntu 12.04/Debian 6.0/Windows Server 2008/Windows7/Windows8 etc.
Virtualizer - VirtualBox

1)
Would be be possible to share folders/directories between Linux<->Linux, Linux<->Windows, Windows<->Windows guests?  If YES, pls advise how.

2)
How to setup remote access Linux<->Windows and Windows<->Windows guests?

TIA

satimis

---

### Post by TheFu on 2013-03-01
> **satimis said:**
> host - Ubuntu 12.04 desktop 64bit
guests - all 64bit Ubuntu 12.04/Debian 6.0/Windows Server 2008/Windows7/Windows8 etc.
Virtualizer - VirtualBox

Virtualbox is great for Desktop-on-Desktop virtualization, but I'd never use it to virtualize servers. KVM would be a better option, IMHO.

> **satimis said:**
> 1)
Would be be possible to share folders/directories between Linux<->Linux, Linux<->Windows, Windows<->Windows guests?  If YES, pls advise how.
There are many ways, NFS, CIFS(also called samba), Windows Shares.  Treat each VM just like a real server, setup your networking and file sharing as though they were normal machines.

> **satimis said:**
> 2)
How to setup remote access Linux<->Windows and Windows<->Windows guests?

The same applies to remote access.  Most of the time, using ssh for remote access is the most secure AND the most efficient.  If you need a remote desktop or a remote GUI program, then you'll want to read this: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) then come back and ask a few more questions.  I use NX to access remote desktops on Linux - it is about 2-3x more efficient than other options.  For Windows ... well, I use the built-in RDP, but actually connect to a Linux machine over NX first since NX is secure and RDP is not. [http://blog.jdpfu.com/2012/10/23/remote-desktops-rock](http://blog.jdpfu.com/2012/10/23/remote-desktops-rock)

I've actually been 6,000 miles away from home, remoted to a Linux desktop there using NX, then connected to the Windows7 Media Center and toggled some TV shows to be recorded.

Right now, I'm using a remote desktop to my home "main" desktop running in a private cloud to respond to you ... all over NX.

Spice is a newer method for remote access. I've only used it internally and it was less than perfect, so I switched back to NX.  VNC is built into Linux systems, but lacks real security. Using it means you also need a VPN or SSL tunnel.  NX is more efficient and based on ssh, so it is already secure, doesn't require a VPN, and doesn't require any other ports to be opened.

---

