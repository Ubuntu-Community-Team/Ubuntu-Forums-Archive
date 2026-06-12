---
title: "Ubuntu one less well integrated in Xubuntu?"
date: 2014-02-23
forum: Ubuntu One (CLOSED)
---

### Post by zircon_34 on 2014-02-23
I used Ubuntu 13.10 Saucy and had installed Ubuntu One, no problem, I even had a little cloud in the upper panel showing the sync. However, I run now XUbuntu 13.10 and I find Ubuntu one less well integrated (doesnt run out of the box). I am newbie so still have to learn, any comment would be great.

Problems:
- To get an Ubuntu icon in the panel, instead of automatic, I had to run in the terminal (not sure if that stays at reboot)
```
ubuntuone-control-panel-qt --with-icon
```
The icon in the panel is an "U" in XUbuntu instead of the cloud in Ubuntu.

- I get an error when syncing in the Ubuntu one window: File sync error (auth failed AUTH_FAILED), I dont know how to fix this.


I installed the following packages in synaptic:
python-ubuntuone-client
python-ubuntuone-control-panel
python-ubuntuone-storageprotocol
ubuntuone-client
ubuntuone-client-data
ubuntuone-control-panel
ubuntuone-control-panel-qt

Am I maybe missing  some package that may cause the sync error?
In the software center there was only the control panel qt.

---

### Post by zircon_34 on 2014-02-24
aha, it seems I'm not the only one with a sync problem right now...

[http://www.omgubuntu.co.uk/2014/02/ubuntu-one-sync-issues-reported](http://www.omgubuntu.co.uk/2014/02/ubuntu-one-sync-issues-reported)

---

### Post by Irihapeti on 2014-02-24
I think the sync problems have been fixed - at least, my own machines are working properly now. You might need to reboot or restart the syncdaemon before it will behave properly, though.

---

### Post by zircon_34 on 2014-02-26
It is still not working, same error message... In OSX it works though, strange. Am I maybe missing some installed package?

---

### Post by zircon_34 on 2014-03-01
Ok I fixed it. 

on Xubuntu you need to install Seahorse using software center and follow this:

[https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/](https://one.ubuntu.com/help/faq/what-should-i-do-if-authentication-fails-auth_failed-state/)

This happens when you install and deinstall Ubuntuone...

---

