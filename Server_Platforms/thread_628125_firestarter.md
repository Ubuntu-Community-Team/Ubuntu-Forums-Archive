---
title: "firestarter"
date: 2007-11-30
forum: Server Platforms
---

### Post by Multi-Booter on 2007-11-30
I was going to play with firestarter... but it is not on my menu in Gutsy 64-bit.

Why isn't it there?

---

### Post by DDuong on 2007-12-01
Is it installed?  It seems like it's not.

If you want to install it, run the following:

> 
sudo apt-get install firestarter


---

### Post by Multi-Booter on 2007-12-01
I was thinking this, yet wondering why it wasn't...

But I haven't been motivated to dig up the command to check what is installed.

I think it is... 
> ]dpkg --get-selections
But it looks like that's not giving me a full list really.

I need to grab a book for reference, but I'm not digging it out now... I'm going to bed!

---

### Post by phimurh on 2007-12-01
to launch firestarter use

sudo firestarter --start

I prefer

sudo firestarter --start-hidden &

---

### Post by ruibernardo on 2007-12-01
If firestarter is installed, there should be a menu entry at System > Administration > Firestarter. To start using and configuring iptables with Firestarter check this page: [http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

---

### Post by Multi-Booter on 2007-12-01
> **epimeteo said:**
> If firestarter is installed, there should be a menu entry at System > Administration > Firestarter. To start using and configuring iptables with Firestarter check this page: [http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

Yeah, it was not there... but I didn't want to just assume.

I checked at the command line and it's definately not installed.
I wonder why though?

Is this what you guys are using?

---

### Post by ruibernardo on 2007-12-01
Did you do what DDuong told you to in post #2 to install Firestarter?

Firestarter is the easiest tool to configure iptables. There are many other tools, just open Synaptic and search for "firewall" there, but none is so easy as Firestarter for a new Linux user.

---

### Post by phimurh on 2007-12-01
> **Multi-Booter said:**
> Is this what you guys are using?

I use firestarter as well and it is not a perfect system

---

### Post by holyowned on 2007-12-02
I have Firestarter installed in 7.10.  It worked great in 6.04 LTS.  When I click System Admin Firestarter, it launches, but after a few minutes, it shuts down.  Any ideas?  I have completely uninstalled, re-downloaded, and reinstalled via Synaptic.
TIA

---

