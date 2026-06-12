---
title: "QQ and pure Python 3 and GTK3?"
date: 2012-06-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by forcecore on 2012-06-23
I heard that Python 3 will be default and GTK3 without gtk2 bloat anymore(default 12.10 iso).

---

### Post by MG&amp;TL on 2012-06-23
> **forcecore said:**
> I heard that Python 3 will be default and GTK3 without gtk2 bloat anymore(default 12.10 iso).

Python 3, I believe so, yes. Should be interesting, I've never actually touched python 3.

Gtk3 I'm not sure about, I'm pretty certain the likes of L.O., FF, and Thunderbird are still Gtk2. Could be wrong.

---

### Post by VinDSL on 2012-06-23
> **forcecore said:**
> I heard that Python 3 will be default [...]
SOURCE: [https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha1](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha1)
> [SIZE="+1"]Python 3.0[/SIZE]

**[COLOR="DarkRed"]For 12.10, we intend to ship only Python 3 with the Ubuntu desktop image, not Python 2.[/COLOR]** Alpha-1 begins this process, with the installer and some other applications ported to Python 3. There are still quite a few packages left to port, and so Python 2 and 3 are both installed for the time being.

If you have your own programs based on Python 2, fear not! Python 2 will continue to be available (as the python package) for the foreseeable future. However, to best support future versions of Ubuntu you should consider porting your code to Python 3. Python/3 has some advice and resources on this


> **MG&TL said:**
> Gtk3 I'm not sure about [...]
Dittos...

---

### Post by balloons on 2012-06-25
Yes, python 3 by default. Gtk3, no plans that I have heard. This bug would have to be solved first, among others:

[https://bugzilla.mozilla.org/show_bug.cgi?id=627699](https://bugzilla.mozilla.org/show_bug.cgi?id=627699)

Namely, we can't ship only gtk3 until all apps only use it. And then, most likely an app you would install afterwards would use or depend on gtk2 libs (until all apps are migrated).

---

### Post by xebian on 2012-06-25
> **guitara said:**
> Yes, python 3 by default....

....

Would appreciate it very much if you could ask them to include eric5 ( for python 3) as well.  eric4 is what we have in the repo, but this is for python2.

---

### Post by lolpenguin on 2012-06-26
GTK+2 won't be removed until all of the GNOME apps have been ported to GTK+3, which will be a few years, since GIMP gets stable releases about every three years...

---

### Post by forcecore on 2012-08-12
any status updates, currently i tried to remove Python 2.7 and still it wants to destroy half of desktop. Do 12.10 really be compot of versions i assume like GTK2+GTK3 and Python2.7+Python3?

Can this mixture affect performance?.

---

### Post by Harry33 on 2012-08-12
> **forcecore said:**
> any status updates, currently i tried to remove Python 2.7 and still it wants to destroy half of desktop. Do 12.10 really be compot of versions i assume like GTK2+GTK3 and Python2.7+Python3?

Can this mixture affect performance?.

GTK2 will be part of Ubuntu for a long time.
This is because a number of applications are using it for the GUI (like firefox, thunderbird, gparted, synaptic, metacity, gimp, libreoffice).

Python2.7 and Python3 can very well be installed together.
Porting from Pyhton2.7 has only begun now and will not be ready during QQ dev phase.
So, it is Python3, which is less needed right now.
There are a few packages that depend on it, however (like bluez, libpeas-1.0-0, lsb-release).

---

### Post by forcecore on 2012-08-12
Harry33: thanks, so now myself and everyone can be sure that 12.10 will be mixed with GTK and Python versions, thats why size is 750mb too i think.

---

### Post by vexorian on 2012-08-12
I doubt gtk2 is a big factor in that.

---

### Post by lion.guo on 2012-09-26
[http://people.canonical.com/~ubuntu-archive/transitions/onlypy3oncd.html](http://people.canonical.com/~ubuntu-archive/transitions/onlypy3oncd.html)

70Packages.

I think it`s too late to remove Python2.7, there are so many packages depend on them.
If switch all them to python3, who do it, who test it. 
Now it's impossible.

---

### Post by forcecore on 2012-10-01
Lets hope 13.04 will drop Python 2 from default .iso, yes it is too late for 12.10

---

