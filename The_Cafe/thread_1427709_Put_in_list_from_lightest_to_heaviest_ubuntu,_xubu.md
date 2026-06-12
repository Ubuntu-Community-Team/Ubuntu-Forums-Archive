---
title: "Put in list from lightest to heaviest: ubuntu, xubuntu, lubuntu, and jolicloud"
date: 2010-03-11
forum: The Cafe
---

### Post by theweasel2345 on 2010-03-11
System requirements wise

---

### Post by alfplayer on 2010-03-11
It probably is:

lubuntu
xubuntu
jolicloud
ubuntu

(not sure about two and three)

---

### Post by patchwork on 2010-03-11
You could always install the ubuntu-minimal and add a light window manager and file manager.

If gdm is too heavy for you, you can use xdm, use startx command from console, or add a line to your rc.local to startx automatically.

I prefer icewm, but some like fluxbox, openbox, etc.

---

### Post by snowpine on 2010-03-11
What are your system specs? :)
I haven't tried the other 2, but Xubuntu is a teensy bit "lighter" than Ubuntu.

---

### Post by pizza-is-good on 2010-03-11
I've only tried the first 2.
Xubuntu is lighter than Ubuntu, and LXDE is lighter than both of those. Is LXDE Lubuntu? Pardon my ignorance.:lolflag:

~pizza

---

### Post by dmillard10 on 2010-03-11
> **pizza-is-good said:**
> Is LXDE Lubuntu?

~pizza

I believe that it is.

---

### Post by alfplayer on 2010-03-11
Lubuntu is lighter than Xubuntu and Ubuntu because LXDE is lighter than XFCE and Gnome.

---

### Post by dmillard10 on 2010-03-11
What DE does Jolicloud use?

---

### Post by overdrank on 2010-03-11
Moved to The Community Cafe. :)

---

### Post by alfplayer on 2010-03-11
> **dmillard10 said:**
> What DE does Jolicloud use?

Gnome.

---

### Post by Grifulkin on 2010-03-11
I am just saying but Xubuntu is not that light anymore.  And besides that if you look at the lubuntu meta package there are quite a bit of gnome dependencies and runs a lot of gnome programs so it really isn't that lightweight either,  LXDE by itself is light and very nice.

---

### Post by tunyawat on 2010-03-13
From [http://www.linux-mag.com/cache/7520/1.html]("http://www.linux-mag.com/cache/7520/1.html")

The first test is simply to check how much memory is used after a fresh boot of the respective live CDs, all the way into the default desktop.
[COLOR="YellowGreen"]Lubuntu: 57,908 KB[/COLOR]
[COLOR="Red"]Xubuntu: 156,852 KB[/COLOR]
Ubuntu: 153,840 KB

It&#8217;s clear here that Lubuntu is the outright winner using almost two thirds less memory than the others. Interestingly, Xubuntu is using slightly more memory than its big brother.

The second test compares the amount of memory used when opening every day applications on the live system. While not completely realistic, it shows how application choice can greatly affect the performance of a system.

Lubuntu with every day applications loaded, including a terminal (LXTerminal), file manager (PCMan), calculator (Galculator), image viewer (GPicView), text editor (Leafpad), archive manager (Xarchiver), web browser (Firefox), mail client (Claws), chat program (Pidgin), bittorrent client (Transmission), audio player (Aqualung), video player (MPlayer):
[COLOR="YellowGreen"]Usage: 162,272 KB[/COLOR]

Xubuntu with every day applications loaded, including a terminal (Terminal), file manager (Thunar), calculator (Gcalctool), image viewer (Ristretto), text editor (Mousepad), archive manager (File-roller), web browser (Firefox), mail client (Thunderbird), chat program (Pidgin), bittorrent client (Transmission), audio player (Exaile), video player (Totem):
[COLOR="Red"]Usage: 311,560 KB[/COLOR]

Ubuntu itself with every day applications loaded, including a terminal (GNOME Terminal), file manager (Nautilus), calculator (Gcalctool), image viewer (F-Spot), text editor (Gedit), archive manager (File-roller), web browser (Firefox), mail client (Evolution), chat program (Empathy), bittorrent client (Transmission), audio player (Rhythmbox), video player (Totem):
Usage: 289,744 KB

Once again this shows that Lubuntu, with its lightweight desktop and carefully chosen applications, is certainly the lightest of all by a reasonable margin. Xubuntu manages to use slightly more memory than Ubuntu and almost twice as much as Lubuntu. If you&#8217;ve got a system with 256MB of RAM or less, Lubuntu is the only way to go.

---

### Post by DutchLoki on 2010-03-19
> **tunyawat said:**
> From [http://www.linux-mag.com/cache/7520/1.html]("http://www.linux-mag.com/cache/7520/1.html")

Thanks, helped me choosing the ubuntu melange for an old laptop.

---

### Post by -grubby on 2010-03-19
According to the Ubuntu wiki, Lubuntu's minimum requirements are probably a Pentium II and 128 MB of RAM.

As for Jolicloud, seeing as it's designed for netbooks, it should probably run on most netbooks since they're pretty similar and low powered.

The official system requirements for Xubuntu are 128 MB of RAM though it strongly recommends 256 MB

Ubuntu recommends 384 MB of RAM and at least a 700 mhz processor.

It would also be helpful if you could give us your reasons for asking this, i.e the system specs of what you want to install on.

---

### Post by BrokenKingpin on 2010-03-19
Xubuntu is a beast. You would be much better off installing with the mini iso and installing XFCE manually. Xubuntu has a lot of Gnome dependencies that make it just as heavy as Ubuntu.

Although LXDE is lighter than XFCE, I find the difference negligible in everyday use.

Here is a great article comparing the performance of the major DEs:
[http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1)

---

### Post by zoomy942 on 2010-03-19
i saw this thread when i wondering if a lighter version might be better on my netbook.  but from the looks of it xubuntu isnt all that light anymore

---

### Post by gsmanners on 2010-03-19
Xubuntu *per se* isn't light because of things like gdm, gnome screensaver, and all the gnome hardware support apps (like printers). The heaviest thing I'm using is Firefox, followed by xfdesktop, xfce-panel and its related apps.

However, even Gnome at its most bloated is nothing compared to what Firefox uses after a while. If you want a lightweight desktop, try using lightweight apps (like Midori instead of Firefox).

---

### Post by DutchLoki on 2010-03-21
@gsmanners

Lubuntu is doing this... choosing lightweight apps while still staying very usable AND still compatible with all the ubuntu stuff.

If ubuntu compatibility is not a big deal, than there are probably even lighter distros. Although if your using a 133 mhz or higher lubuntu should be okay.

---

### Post by my_wan on 2010-03-25
My play machine is an 800 mhz amd with a 100 mhz fsb and an nvidia GeForce FX 5200. It runs ubuntu (gnome) just fine with full desktop effects. LXDE is also installed and programs are noticeably perkier with that desktop.

I would be using LXDE all the time if I could stack two desk panels on the bottom. Perhaps I can find a hack to do that.

---

