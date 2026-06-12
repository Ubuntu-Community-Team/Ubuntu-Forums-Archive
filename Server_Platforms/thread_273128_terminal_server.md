---
title: "terminal server"
date: 2006-10-07
forum: Server Platforms
---

### Post by yugotpinky on 2006-10-07
Ok.  Looking for a bit of help here...

I'd like to set up Ubuntu (have Edubuntu installed right now) as a terminal server that I can log into using windows remote desktop.

I can use a VNC connection (3rd party) and can access the file system with no problem, but I can't seem to figure out how to get RDC to recognize it as a terminal server ("no terminal servers on your network").

---

### Post by Charlotte on 2006-10-08
Hallo,

I'm not quite sure of what you are wanting to achieve. If you are looking for some means of controlling your ubuntu machine from a windows machine.

If so, this might be a good point to start:
[http://www.jfitz.com/tips/ssh_for_windows.html](http://www.jfitz.com/tips/ssh_for_windows.html)

HTH,
Charlotte

---

### Post by baastie on 2006-10-08
Hi,

Try freenx,

[http://www.nomachine.com/](http://www.nomachine.com/)

A terminal server solution for linux or just for remote control.... The RDP counterpart.. but better :D 

Cheers,

---

### Post by yugotpinky on 2006-10-08
windows rdc allows customized logins and auto program running - for instance, i can set it to login and then startup an email client immediately.  (and other stuff)

the real advantage is that its an integral part of XP, as opposed to running a 3rd party app.

---

### Post by baastie on 2006-10-09
Hi,

With freenx you can create published applications.. but from the default login with the freenx client you cannot start a program.

You can however do this on first login at the desktop.

And yes it's a third party... but that's a lot of stuff in linux :)

You could try ltsp which comes default in Ubuntu. But that's also a integrated thirt party app / project .. 

Cheers,

---

### Post by fnjordy on 2006-10-09
If you want RDC compatibility try XRDP:

[http://xrdp.sourceforge.net/](http://xrdp.sourceforge.net/)

---

