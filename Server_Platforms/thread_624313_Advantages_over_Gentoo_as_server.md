---
title: "Advantages over Gentoo as server"
date: 2007-11-26
forum: Server Platforms
---

### Post by onlythetim on 2007-11-26
Hello.  I currently have an old desktop set up with Gentoo as a server. I run a small minimal trafic personal webpage, and use it as a media server, as well as an svn repository and for backups.  However, I've been lazy about keeping it up to date, and I'm worried there are some blatant security holes that I just don't know about (I don't have a whole lot of networking experience).

So I am wondering what the advantages are of Ubuntu Server, and if it is likely to be more secure for the beginner, or will it require just as much know-how to set up a secure server as gentoo?

Thank you!

---

### Post by p_quarles on 2007-11-26
> **onlythetim said:**
> Hello.  I currently have an old desktop set up with Gentoo as a server. I run a small minimal trafic personal webpage, and use it as a media server, as well as an svn repository and for backups.  However, I've been lazy about keeping it up to date, and I'm worried there are some blatant security holes that I just don't know about (I don't have a whole lot of networking experience).
Never used Gentoo, but many distros have security mailing lists that will let you know when you need to update certain apps. If you're not on such a list then, yes, I would suspect that your server has some vulnerabilities.

> So I am wondering what the advantages are of Ubuntu Server, and if it is likely to be more secure for the beginner, or will it require just as much know-how to set up a secure server as gentoo?!The only advantage is that Ubuntu will download stable binary updates, rather than compiling source code. From what I understand about emerge, this isn't a question of know-how as much as it's a question of time (for both you and your CPU).

Basically, if you want to spend less time with this server -- and keep it secure and stable -- Ubuntu Server Edition is a good choice. Debian Stable is an even better choice, imho.

---

### Post by HermanAB on 2007-11-27
Linux is Linux is Linux...  There is no hard advantages bettween distributions.  The main differences are the wizards.  So for a server the differences are minimal.  You could install an Ubuntu server and if you don't maintain it, it will get just as bad as an unmaintained Gentoo server.

---

### Post by crouton on 2007-11-27
p_quarles is spot on.  Gentoo gives an edge in speed by compiling code to suit your hardware.  Debian/Ubuntu gives an edge in maintainability by having binaries ready-to-go.  Fedora is usually on the leading edge with new updates and technologies.

---

### Post by reckless2k2 on 2007-11-27
I would not suggest updating that Gentoo box using emerge because it can be problematic as well as shutdown that machine for hours if not days getting it up to date. 

In my opinion, Gentoo is more volatile than running Fedora with too much 3rd party repo craziness. The advantage of Ubuntu is that it's VERY well documented similar to Gentoo but more usable in terms of maintaining the distro. Gentoo has to recompile everything and it takes too long to be real world usable in critical environments. 

Again, it's my opinion and if you server gets very little traffic you might not mind the down time during emerge or more than likely instability caused by an update. 

Chances are that you can backup your critical data and have all server functions up and running on Ubuntu faster than installing Gentoo. The key is the ease of use with Ubuntu and the ease of updating it with little or no incident.

---

### Post by Arador on 2007-11-28
Gentoo is making you life too hard IMHO. Ubuntu requires way less maintaining. I'll take that over any marginal speed advantage.

---

