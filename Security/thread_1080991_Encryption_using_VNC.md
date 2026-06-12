---
title: "Encryption using VNC"
date: 2009-02-26
forum: Security
---

### Post by 9a8sy on 2009-02-26
I have a windows server with ultra-vnc on it which I use for remoting into using an encryption plug in. I recently loaded Ubuntu 8.1 on my laptop. I see there is a VNC type program preinstalled, but there doesn't seem to be a way to load encryption plug ins. Is there anyway I can long onto my windows server encrypted using ubuntu? Would I need to look into a VPN setup?

---

### Post by HermanAB on 2009-02-26
Uhmmm... Windows has a remote control system built in, called RDP (which MS bought from Citrix).  It works very well and is secure, you should use that, and control it from Linux using rdesktop.

VNC is good for training purposes as it allows both the local and remote users to see the desktop.  Otherwise, it is best avoided.

Cheers,

Herman

---

### Post by bodhi.zazen on 2009-02-26
Personally, if you use VNC, I advise you tunnel it over ssh.

Here is a nice how-to :

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

It is written for Windows, but can be easily adapted to Linux (with Linux you use ssh from the command line, although you can install putty if you like, it is in the repos).

---

