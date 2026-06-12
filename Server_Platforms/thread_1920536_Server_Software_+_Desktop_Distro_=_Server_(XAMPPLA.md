---
title: "Server Software + Desktop Distro = Server? (XAMPP/LAMP)"
date: 2012-02-05
forum: Server Platforms
---

### Post by Stisfa on 2012-02-05
Hi all,

It's been almost a year since I posted [this thread]("http://ubuntuforums.org/showthread.php?t=1734295"), so I've let the time pass me, but I still have the same question that I had intended to ask since April of last year: **By installing XAMPP, or the "lamp-server^" package, am I opening security holes through Apache?**

This question was spurred on by 2 items, the first being Response #7 from [my earlier thread]("http://ubuntuforums.org/showthread.php?t=1734295"), as quoted partially below:

> You only need to get really concerned about security once you run a server that is actually listening on the net. So if you are developing web sites, make sure that you understand Apache security and so on.

From my current understanding, to get a server to listen on the net, and to do the inverse, requires NAT configuration with a public IP address provided by my ISP.  Furthermore, there's far more configuration required to make it work at all, at least, this was the impression I got from [this thread]("http://ubuntuforums.org/showthread.php?t=1899700").

The second reason why my mind is not settled on this matter is because of a few statements from [bodhi.zazen's comprehensive sticky on security]("http://ubuntuforums.org/showthread.php?t=510812"):
> However, installing "server software" will cause ports to open, so some people like to use a firewall as a catch-all layer to find mistakes in their configuration.

> 
_[SIZE="3"]Running Servers[/SIZE]_
Part of setting up a server is reading/learning how to secure it. Common servers include NFS, Samba, FTP, SSH, VNC, RDP, and HTTP. If the "how-to" you are following does not review security, you need to keep looking ...***"Desktops" become "Servers"*** if server software is installed.


In consideration of the entire context, the answer seems to be this: **Don't worry about "server-level security" unless you're setting up a server to listen and broadcast to the entire world.  Installing server software on a desktop distro doesn't make it a server, even if it has internet access; it only becomes a server, with security concerns, when one is deliberately making efforts to make that box be heard.**  Putting it this way makes sense to me, but I'd like to confirm this statement with the gurus here.

I also wanted to ask this: Even if the desktop distro has server software with the sole intention of internal development/testing, is it still possible for me to be at some sort of security risk?  What I'm trying to ask is, "Are there any security holes introduced by XAMPP/LAMP, such as ports being opened?  If so, what do I need to do to secure it?  Why is it a security concern, especially since I'm not setting up the computer to act as a server?"

**At the end of the day, my end goal is just to have a Linux distro that I can develop PHP with, safe from the dangers of the interwebs (despite the installation of Apache).**

---

