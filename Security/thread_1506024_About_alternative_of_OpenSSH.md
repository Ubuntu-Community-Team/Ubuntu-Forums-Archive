---
title: "About alternative of OpenSSH"
date: 2010-06-09
forum: Security
---

### Post by satimis on 2010-06-09
Hi folks,

Most the time I run OpenSSH/SSH taking control of a remote Linux/Unix PC for administration via Internet/Public IP.  Now I need taking remote control of a Windows PC through Internet/Public IP.  But OpenSSH dosen't work on Windows.  OpenVPN/VPN is only attaching the local PC to a remote network through a secured line.  What will be the alternative of OpenSSH which works on Windows.  I don't need GUI only to work on console.  TIA

B.R.
satimis

---

### Post by HermanAB on 2010-06-09
Howdy, SSH does work on Windows.  I'm using it every day. You should install Cygwin and PuTTY.  There are many howtos on the web about installing a SSH Server on Windows.

However, if you have XP Pro or similar, then you can use rdesktop on Linux, with RDP on Windows.

---

### Post by edenCC on 2010-06-10
I'd prefer to use RDP instead, as I know only a little about the windows system.

---

### Post by bodhi.zazen on 2010-06-10
> **edenCC said:**
> I'd prefer to use RDP instead, as I know only a little about the windows system.

I would not RDP over the internet.

I would also remind you, this is an Ubuntu forums. We are trying to send Debian questions to the Debian forums, Arch to Arch , Fedora to Fedora.

In this case, you should ask on a Windows forums.

You can install openssh on windows if you wish, look at cygwin.

With that I am closing this thread.

---

