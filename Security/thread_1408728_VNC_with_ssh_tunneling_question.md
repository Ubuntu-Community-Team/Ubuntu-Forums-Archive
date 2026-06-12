---
title: "VNC with ssh tunneling question"
date: 2010-02-16
forum: Security
---

### Post by sonic_beatnik on 2010-02-16
I am attempting to set up a VNC with ssh tunneling for remote desktop between my laptop (opensuse 11.2) and my desktop (kubuntu karmic) and using the instructions here:

[http://softsolder.wordpress.com/2009/01/04/kubuntu-remote-desktop-via-ssh-tunnel]("http://softsolder.wordpress.com/2009/01/04/kubuntu-remote-desktop-via-ssh-tunnel")

and here:
[https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC")

but I am having trouble getting remote desktop to work once I establish the ssh tunnel

I start out with
```
ssh <user@remotepc> -p <non22port> -L 5900:localhost:5900
```

That seems to wok and connect properly

The problem comes when I try to use a remote desktop client on the laptop to initiate the VPN desktop sharing and point it to 
```
localhost:5900
```

Thats when I get a notification on the host saying:
```
Refused uninvited connection attempt from 127.0.0.1
```

and on the laptop i get
```
VNC server closed connection
```

I have tried messing with the few settings in Krfb, but none seem to have any impact.

How do I open localhost:5900 and allow VPN tunneling to the host machine?

---

### Post by suseendran.rengabashyam on 2010-02-17
Hi,

Can you try accessing the VNC display using

```
localhost
```

or

```
localhost::5900
```

The syntax of the vncviewer/xtightvncviewer is :

vncviewer [options] [host][:display]
vncviewer [options] [host][::port]

5900 is the port and hence you can use the second syntax above for that, where as display number is likely 0 and you can skip mentioning that.

---

### Post by CharlesA on 2010-02-17
Are you using the built in VNC client on the Ubuntu box? If so, that machine needs to be logged in locally for that to be active.

---

