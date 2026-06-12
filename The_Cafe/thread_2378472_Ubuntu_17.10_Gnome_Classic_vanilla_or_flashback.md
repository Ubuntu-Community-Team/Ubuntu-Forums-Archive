---
title: "Ubuntu 17.10 Gnome Classic: vanilla or flashback?"
date: 2017-11-23
forum: The Cafe
---

### Post by siggi2 on 2017-11-23
Hi,

I am using Ubuntu 17.10 Gnome Classic. I have tried both flashback and vanilla. Which one would be better with respect to the upcoming Ubuntu 18.04?

Vanilla:
```
sudo apt-get install vanilla-gnome-desktop
```

flashback:
```
sudo apt-get install gnome-panel gnome-flashback gnome-session-flashback indicator-applet-appmenu
```

On Ubuntu 17.10 I use Gnome Classic and not Gnome because the neatly arranged "Classic" menu is essential for me (much better than classicmenu-indicator for 17.10)

Thanks,

siggi2

---

### Post by ChuangTzu on 2017-11-23
only you can decide which you like, try them all out on liveCD's.

---

### Post by oldfred on 2017-11-23
Moved to Cafe since not really a help question, but opinion.

I have gnome-panel on 18.04, have booted into it a couple of times and it seems ok. But very early in 18.04 updates, so who knows what may change.

I use 16.04 with gnome-panel as my main working install.

---

### Post by siggi2 on 2017-11-24
Sorry, bad phrasing on my side. I rephrase my question:

Since I depend on the old Gnome's Applications Menu, I tried both Flashback and Vanilla 17.10. They seem to be the same, except that Vanilla takes verly long to start and in contrast to Flashback it shows a strange symbol of an intertwined "U" and upside down "V" before the log-in screen appears. Otherwise they seem to be the same, both have the Application Menu.

My **questions:** 
*** 1 *** I never used anything "flashback" or "vanilla" in Ubuntu. Is it safe to use either one of them? 

*** 2 *** Is there an other way to get the Application Menu of the old Gnome on Ubuntu's 17.10 default Gnome or Gnome on Xorg?

And sorry for the duplicate, I do not know how this happened :confused:

---

### Post by oldfred on 2017-11-24
If you have done this:
# for gnome3
sudo apt-get install gnome-panel gnome-color-chooser

Then either reboot or relog in and in little gear icon choose desktop.

Do not know what vanilla is?
We support official flavors. 
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by siggi2 on 2017-11-24
> **oldfred said:**
> If you have done this:
# for gnome3
sudo apt-get install gnome-panel gnome-color-chooser
Then either reboot or relog in and in little gear icon choose desktop.

Thank you. I did it- Then at log-in I could choose Gnome flashback (Metacity)
It is almost excatly what I had with my Flashback option in my first post

**What is Metacity? **Whar does it mean?

However, with my vanilla option, I log in with Gnome Classic which gives me also the Appliation menu PLUS the Activities option as in Gnome 3. So, it is much more comfortable than Metacity.
> **oldfred said:**
> Do not know what vanilla is?
 No, I do not know vanilla, except that it is a very comfortable desktop. Do you know it?

---

### Post by siggi2 on 2017-11-24
This is vaniila. Found it in synaptic - could have thought earlier of that!
> Vanilla GNOME metapackage
 
This package depends on the core GNOME packages with minimal Ubuntu
branding similar to what was offered by Ubuntu GNOME. Ubuntu GNOME
was an Ubuntu flavor that offered a mostly pure GNOME experience until
it was discontinued after the 17.04 release.

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.


---

### Post by ChuangTzu on 2017-11-24
ok.  Vanilla is basically upstream no or very little branding.  You get what upstream (in this case Gnome) intended and not Ubuntu or Debian etc...

There are Gnome extensions to simulate the old Gnome 2 ex: [https://extensions.gnome.org/extension/13/applications-menu/](https://extensions.gnome.org/extension/13/applications-menu/)

Metacity is the window manager its less intensive then mutter (Gnome 3 window manager).

---

### Post by siggi2 on 2017-11-25
Thank you for your comments. Since I see in [in Bionic's packages]("https://packages.ubuntu.com/bionic/allpackages?format=txt.gz") that vanilla-gnome-desktop will remain I am happy because I love to have both the Application Menu and the Activities Overview :)

---

