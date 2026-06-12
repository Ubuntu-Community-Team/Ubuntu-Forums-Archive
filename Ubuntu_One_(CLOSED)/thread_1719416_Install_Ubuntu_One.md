---
title: "Install Ubuntu One"
date: 2011-04-01
forum: Ubuntu One (CLOSED)
---

### Post by puller on 2011-04-01
Hi, I am using Kubuntu 11.04 64bit (I had to switch to 11.04 to have the new intel sandy bridge graphic support) and I'd like to have U1 working.
With Kubuntu 10.10 I just installed three packages:
ubuntuone-client-gnome
ubuntuone-client
python-ubuntuone-client
and I was able to synchronize files and notes (tomboy) using ubuntu one.

With 11.04 I have been struggled for 2 days without success.
I also tried to blindly install everything U1-related (sudo apt-get install ubuntuone*), and I could start the gtk ubuntu one control panel, but I was not able to sign in getting this warning: "there was a problem while retrieving the credentials".

An extreme solution would be to install ubuntu 11.04 and then install KDE, but I would prefer to just install U1 in Kubuntu (matter of complementarity)!

Could someone help me please?

---

### Post by -=gr!n=- on 2011-04-05
sudo apt-get install ubuntuone-control-panel-gtk aptdaemon.gtkwidgets gnome-keyring

---

### Post by puller on 2011-04-05
Thank you very much, I'll try this as soon as I will be able to boot my system again, as after today updates it is completely gone.
I cannot even use the rescue mode (it hangs).

---

### Post by puller on 2011-04-06
> **-=gr!n=- said:**
> sudo apt-get install ubuntuone-control-panel-gtk aptdaemon.gtkwidgets gnome-keyring

Wow, that worked!
Thanks you very much!

EDIT: I had to install also libsyncdaemon-1.0-1 in order to syn my notes with tomboy.

---

### Post by -=gr!n=- on 2011-04-11
python-aptdaemon.gtkwidgets and desktopcouch-ubuntuone are also needed

---

### Post by puller on 2011-04-11
I didn't explicitly installed them, however everything is working just fine.

---

