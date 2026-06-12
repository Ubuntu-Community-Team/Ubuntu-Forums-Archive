---
title: "Ubuntu: Live CD &amp; Install CD"
date: 2011-05-28
forum: The Cafe
---

### Post by GreenDance on 2011-05-28
Hi, I'd like to see the Ubuntu Team make two releases of future distros, not just one, a Live CD (that's the one released now) but also an Install CD (not a Live CD), so that the user has the choice of what programs should be installed, this would enable people to make more choices, this is only a suggestion and my opinion, it's just another way to allow people to make their own decisions, it would help a fair few people as well like system administrators, who install on many computers.

I think Windows 95 use to do it,

Something like this I think would be fantastic on the Ubuntu "Install CD"
[LIST]
[*]Full Install (like the "Live CD")
[*]Minimal Install (gnome + firefox)
[*]Custom Install (user chooses what to install)
[/LIST]

Thank You.

---

### Post by el_koraco on 2011-05-28
They already have that. The main CD, the alternate, and the minimal.

---

### Post by snowpine on 2011-05-28
This exists already :)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by aysiu on 2011-05-28
After you install the minimal CD, run the commands ```
sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu gksu synaptic --no-install-recommends
sudo service gdm start
``` Then run ```
gksu synaptic
``` and install whatever you want.

---

### Post by .psd on 2011-05-28
Hey aysiu! I'm at the command line right now from a fresh minimal install, this is what I see:

Ubuntu 11.04 mrt tty1
mrt login: _

If I type the commands you listed, will that be pretty much the essentials, and still minimal? And then if I get gnome through synaptec, will ubuntu cause it to download the bloated ubuntu-desktop version or will it be regular up-to-date gnome? Because bhodi.zazen, another forum admin, was trying to explain how to get gnome without the -dekstop because that pulled in ubuntu bloat or something.

---

### Post by DougieFresh4U on 2011-05-29
When I first saw this thread, it reminded me of the very first (Breezy) Ubuntu cd's I received in the mail. It was a 2 cd set. One was for live cd and the other was an install cd :)

---

### Post by aysiu on 2011-05-29
> **.psd said:**
> Hey aysiu! I'm at the command line right now from a fresh minimal install, this is what I see:

Ubuntu 11.04 mrt tty1
mrt login: _

If I type the commands you listed, will that be pretty much the essentials, and still minimal? And then if I get gnome through synaptec, will ubuntu cause it to download the bloated ubuntu-desktop version or will it be regular up-to-date gnome? Because bhodi.zazen, another forum admin, was trying to explain how to get gnome without the -dekstop because that pulled in ubuntu bloat or something.
Yes, the command I gave you gives you the very bare essentials to have a graphical interface and an easy graphical way to install more packages.

If you want the bare essentials of Gnome, install *gnome-core* instead of *ubuntu-desktop*.

---

