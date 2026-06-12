---
title: "How to use Convirt trought Web Browser"
date: 2009-06-29
forum: Virtualisation
---

### Post by juancarlospaco on 2009-06-29
I need to use Convirt 1.1 via Web Browser,
X-Server can be installed but not running *(RunLevel 3)*,
can't use VNC since is not encripted *(so no VNC4Server)*,
its OK to use NX NoMachine if necesary.

[LIST]
[*]The server is Ubuntu Server+KVM+SSH.
[*]The PC to control Convirt via Web Browser are MS Windows XP.
[/LIST]
[I]
How to do it?
Step by step, what to do first?[/I]

:p Thanks...

---

### Post by bodhi.zazen on 2009-06-29
[http://www.convirture.com/wiki/index.php?title=Installation](http://www.convirture.com/wiki/index.php?title=Installation)

Where are you in this how to ?

---

### Post by juancarlospaco on 2009-06-29
**I sucessfully finished this How To.**

All up and running, Servers on RunLevel 3,
but i need a way to control the Convirt via web browser,
because the PC are running MS Windows XP, and can't use VNC, can't install Xming.

---

### Post by bodhi.zazen on 2009-06-29
Xming does not need to be installed, it runs as a portable application (I run Xming from a usb + putty).

You can also vnc over ssh, also from portable apps. Use putty to establish a tunnel, forward your ports (5900) and launch a vnc viewer on Windows.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

### Post by juancarlospaco on 2009-06-29
no, i repeat, i can not use VNC.

*Sorry *:(

---

### Post by bodhi.zazen on 2009-06-29
may I ask why not ? I do not understand that.

You probably have many potential solutions, all these apps can be run as portable apps (Xming, putty, VNCViewer), you can tunnel over ssh, and / or you could probably configure a VPN .

Your problem sounds as if it may be an access issue (are you trying to connect form work or from behind a firewall? that is a different problem / issue then you do not want to open a VNC port, which can be solved by tunneling over ssh or VPN, which is different from VNC is too slow in which case try xming ???).

---

