---
title: "how to get ubuntu server 9.4 to have a graphical interface"
date: 2009-05-26
forum: Server Platforms
---

### Post by fabianus on 2009-05-26
Hello !

with ubuntu server 8.10 the graphical interface was automatically installed. I would like to have a graphical interface with ubuntu server 9.4, too. Could someone tell me how to get this ?

Thanks a lot for any feedback !

Regards, 
Fabianus

---

### Post by netztier on 2009-05-26
> **fabianus said:**
> 
with ubuntu server 8.10 the graphical interface was automatically installed.

Ouh? - It must've escaped me - but my 8.10 server fresh install didn't have a GUI, and I would've removed it instantly if there had been one.

No. Ubuntu server installations don't come with a graphical user interface; it's a **design decision**. If your installation had one, the someone must've set the correspondig options via tasksel or a manual run of *aptitude install ubuntu-desktop*.

Please also read this thread: [GUIs and Servers, time and time again.]("http://ubuntuforums.org/showthread.php?t=1091273") and this document it refers to: 

[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

[edited]
No, I still don't see the point of having a GUI on a server - but that's my personal opinion, and there's a few people on the forum agreeing on this. Just as many though have valid arguments for having a GUI on a server.
[/edited]

regards

Marc

---

### Post by windependence on 2009-05-26
Hehe, I was just going to suggest we have a sticky on this. I guess we already do.

Thanks Netztier.

-Tim

---

### Post by LepeKaname on 2009-05-26
If you want a more minimalistic window manager for your server (instead the whole ubuntu-desktop packages) I recommend you to install blackbox (very simple but not as friendly as gnome).

---

