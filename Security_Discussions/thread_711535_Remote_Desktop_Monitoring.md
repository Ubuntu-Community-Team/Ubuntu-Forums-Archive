---
title: "Remote Desktop Monitoring"
date: 2008-02-29
forum: Security Discussions
---

### Post by ChaosParser on 2008-02-29
Does anyone know of any packages/programs that can be used to remotely monitor a windows desktop session and manipulate it without this being obvious to the end user?

---

### Post by HermanAB on 2008-02-29
The WinXP terminal server only allows one connection.  Win2003 allows three.

Another way to connect is to install Cygwin with sshd and connect using ssh.  An advantage is that a Windows desktop session can be blue screened while ssh may still work, so one can log in via ssh and reboot the machine remotely.

---

### Post by Mr. C. on 2008-02-29
I'm not seeing how one will manipulate a remote user's desktop "without this being obvious to the end user".  I dunno... but I'd get a bit suspicious if I started seeing my mouse moving on its own, and menus popping up all over the place!  :-)

---

### Post by ChaosParser on 2008-03-01
> **Mr. C. said:**
> I'm not seeing how one will manipulate a remote user's desktop "without this being obvious to the end user".  I dunno... but I'd get a bit suspicious if I started seeing my mouse moving on its own, and menus popping up all over the place!  :-)

Apparently it's possible windows to windows with some program/protocol, not sure which.  Verizon's internal helpdesk has the ability to remotely connect and do things without it showing on the end user's screen, they call it Shadowing. We're using Clonezilla with DRBL and LTSP in an educational setting to teach troubleshooting skills. Basically, we have broken images that we have techs try to fix; but we want to be able to change things in real time to make it more challening.  The connection has to be undetectable by the end user, as do any changes made.

---

### Post by Mr. C. on 2008-03-01
Interesting.  Stay away from my system dude! :-)

---

### Post by HermanAB on 2008-03-01
VNC can run co-sessions.  That is useful for training.

---

