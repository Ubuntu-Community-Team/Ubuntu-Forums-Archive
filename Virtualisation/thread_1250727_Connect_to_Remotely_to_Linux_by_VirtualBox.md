---
title: "Connect to Remotely to Linux by VirtualBox"
date: 2009-08-26
forum: Virtualisation
---

### Post by Kdar on 2009-08-26
Hello.

My University have a CentOS Linux Server with a lot of accounts for students.

I can connect to my home directory by using ssh

```
ssh -Y username@machine-name.eng.uah.edu
```

But is there a way to open that desktop, that session, in VirtualBox on my laptop? So that I can able to see it graphically (just like I would if I would connect to the server in the Lab).

---

### Post by zubin71 on 2009-08-26
yes it is possible.
check out [http://www.rdesktop.org/](http://www.rdesktop.org/)

remote desktop connections in linux work over a protocol named vnc. the vnc server for GNOME is called vino.

hope this link can furthur help you :-

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

---

