---
title: "Gufw interface doesn't work"
date: 2011-12-16
forum: Security
---

### Post by kr0n1x on 2011-12-16
Hi, I got a problem with gufw.
This is the problem:
[IMG]http://img820.imageshack.us/img820/6674/istantanea1712201101581.png[/IMG]

The interfaces misses icons... buttons... all the menus are grey (I can only use Exit and Informations menus).
I tried launching the application with sudo, with gksu, or even by the xfce menus. Nothing.

I made a _sudo aptitude purge gufw gir1.2-polkit-1.0_ and reinstalled gufw but it didn't help.

ufw (command line) seems to work. Just the gui (gufw) seems broken.

What could the problem be?

I'm using Xubuntu 11.10 64 bit.

Thanks.

---

### Post by Dangertux on 2011-12-16
You need to unlock policy-kit you can do so by clicking on the (\) symbol in the lower right hand corner. The correct icon should be a pad lock.. Not sure why your icons are broken, but you will be prompted for a password and it should unlock the interface.

Hope this helps.

---

### Post by oklokl on 2011-12-17
Start Manager -> Activation
PolicyKit Authentication Agent
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

---

### Post by kr0n1x on 2011-12-17
> **Dangertux said:**
> You need to unlock policy-kit you can do so by clicking on the (\) symbol in the lower right hand corner. The correct icon should be a pad lock.. Not sure why your icons are broken, but you will be prompted for a password and it should unlock the interface.

Hope this helps.
ok i clicked the lower right icon and it asked me for a password, thanks :popcorn:

> **oklokl said:**
> Start Manager -> Activation
PolicyKit Authentication Agent
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
that's already activated in my session manager

---

### Post by Dangertux on 2011-12-17
Did it unlock the controls for GUFW after you provided your sudo password?

---

### Post by kr0n1x on 2011-12-19
> **Dangertux said:**
> Did it unlock the controls for GUFW after you provided your sudo password?

Yes, it does, but the two buttons in the lower left corner are still broken (just the icon is broken, clicking on it does work).

I mark the topic as solved.

---

### Post by marquinos on 2011-12-19
Hi! It'll be fixed in the next release :)
[https://bugs.launchpad.net/gui-ufw/+bug/878639](https://bugs.launchpad.net/gui-ufw/+bug/878639)
Thanks!

---

