---
title: "ubuntu VNC client to UltraVNC server hosted on WinXP"
date: 2007-06-24
forum: Server Platforms
---

### Post by BluewookieJim on 2007-06-24
Once again looking for some help or advice here.

I have an UltraVNC Server, version 1.0.2, running on my Windows XP Pro system at home. I also have Cygwin running, but that is another story.

Anyway, I can't seem to get my Ubuntu client to connect to the Win XP UltraVNC server. I get the following result when I try to connect.

[INDENT]jim@jim-dell-i6000d:~$ vncviewer 192.168.1.130
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.4 (viewer 3.3)
Unknown authentication scheme from VNC server: -6
[/INDENT]

Anyway, any help would be appreciated.

---

### Post by Mr. C. on 2007-06-24
How is your VNC server configured to authenticate?  Check its Admin Properties.

MrC

---

### Post by BluewookieJim on 2007-06-24
I've got VNC Password set, and also Require MS Logon and New MS Logon selected.   I normally only connect via a SSH tunnel, so the MS Logon stuff probably isn't necessary. I'll have to give that a whirl.

Edit: well, that worked, kind of. I can connect now, but without all of the settings I can set in VNC viewer, it is almost unusable. It's pixelated, blocky, can't handle multiple monitors well, etc...

---

### Post by Mr. C. on 2007-06-24
You've got it - disable the MS login.

---

