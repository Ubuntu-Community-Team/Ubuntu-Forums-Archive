---
title: "Ubuntu one in Ubuntu-based distros"
date: 2012-04-02
forum: Ubuntu One (CLOSED)
---

### Post by M_Mynaardt on 2012-04-02
Hi!

I'm still pretty new to Ubuntu One.  I think I'm doing pretty good to get it working nicely on both my laptop (Lubuntu) and PC (Xubuntu).  But I've also got several USB HDD's each of which I use as "emergency back up OS", as well as a way of checking out a different Linux OS.

So, what I was wondering is; can you install Ubuntu One Sync and all of that on an Ubuntu-based OS outside of the Ubuntu family proper?  That is, can you install it in, say, Mint, Peppermint, Elementary, AriOS, or any of the other Ubuntu based operating systems out there?

I've not had a chance to try it out myself, and am just curious about it.

Thanks in advance!

---

### Post by duanedesign on 2012-04-06
If you have installed Ubuntu One on other non-Gnome Ubuntu based distros you should have little problems doing it on others.

You can install ubuntuone-client and that should pull in all the necessary packages to do file sync. You do not want to install ubuntuone-client-gnome. That will pull in a lot of Gnome stuff, like Nautilus, that you do not want.

You will want to become familiar with the command line tool u1sdtool. You will use this tool to access all the features in a non-Gnome environment. [Here is a nice page]("https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl") discussing the u1sdtool. The u1sdtool is a commandline program that talks to ubuntuone-syncdaemon over dbus, and allows you to do nearly everything you can do via the Nautilus plugin. The only thing not implemented in u1sdtool is sharing a folder with somebody via email. I'd recommend you use the sharing feature in the web interface.

---

### Post by M_Mynaardt on 2012-04-06
> You will want to become familiar with the command line tool u1sdtool. You will use this tool to access all the features in a non-Gnome environment. [Here is a nice page]("https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl") discussing the u1sdtool. The u1sdtool is a commandline program that talks to ubuntuone-syncdaemon over dbus, and allows you to do nearly everything you can do via the Nautilus plugin. The only thing not implemented in u1sdtool is sharing a folder with somebody via email. I'd recommend you use the sharing feature in the web interface.


Right on!  That answers my questions and gives me more information on the features (a.k.a. *"STUFF"*) to check out with Ubuntu One.

Thanks so much!

---

