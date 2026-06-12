---
title: "Is VNC safe?"
date: 2009-03-30
forum: Security
---

### Post by wlraider70 on 2009-03-30
I just setup a VNC connection over the internet, it strikes me that it might not be the most secure, in the future i may move some sensitive data.

Is vpn more secure?

---

### Post by issih on 2009-03-30
No it is not secure...

Probably the most common way to secure it is by tunnelling the vncserver's port via ssh. A full blown vpn probably would work though.

Hope that helps

---

### Post by wlraider70 on 2009-03-30
can anyone tell me a little more about SSH.

---

### Post by Bios Element on 2009-03-30
> **wlraider70 said:**
> can anyone tell me a little more about SSH.

[http://tinyurl.com/b7jdww](http://tinyurl.com/b7jdww)

---

### Post by wlraider70 on 2009-03-30
I guess you don't know.

let me rephrase that...Can anyone recommend a program for ssh. 
I've seen some stuff on putty, is it any good?

---

### Post by issih on 2009-03-30
From a linux box, chances are you will have ssh built in, just use it from the treminal (man ssh should tell you all you need to know)

putty works just fine from windows..

---

### Post by bodhi.zazen on 2009-03-30
> **wlraider70 said:**
> can anyone tell me a little more about SSH.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Yes from Windows user putty (if you like putty, you can install it on linux as well).

---

### Post by wlraider70 on 2009-03-31
so, let me see if i got this right

im going to use ssh (putty or not) to create a secure connection on port 22 (is that optional or is it 22 only?)

then i will start a vnc connection, on port 5900? 

how does vnc "tunnel" though ssh? is that automatic?

---

### Post by HermanAB on 2009-03-31
SSH is a kind of ad-hoc VPN system. Once you have SSH server installed, you don't need VNC anymore.

Simply do:
$ ssh user@server gnome-panel

Then you can go click happy.

---

### Post by movieman on 2009-03-31
You can do:

1. Start the VNC server on bar.com (your remote system) and set it to allow access from localhost only.

2. On your local system, ssh [email]foo@bar.com[/email] -L localhost:5901:localhost:5901

That will forward the :1 VNC server on bar.com to your local machine, so you can connect to it at localhost:1. The communication between the VNC viewer and server will be encrypted and passed through the SSH connection so it can't be seen on the network.

Note that the VNC viewer is often too smart for its own good, and if you connect to a localhost address it will turn all the quality settings to max on the assumption that there's high bandwidth and low latency; so if you do this you may need to set those values manually. Personally I use a 64-color display, which seems the best compromise between quality and performance using VNC over the Internet.

---

