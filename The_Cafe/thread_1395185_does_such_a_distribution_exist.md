---
title: "does such a distribution exist?"
date: 2010-01-31
forum: The Cafe
---

### Post by supermooshman on 2010-01-31
Hi all,

just something I was wondering; does a stripped down version of ubuntu exist?
Basically I am looking  for just the OS (evolution, tomboy, open office, games etc).

As I am using an eee, I am trying to save as much space as possible (even the UNR is a bit too bulky).

cheers

---

### Post by AllRadioisDead on 2010-01-31
UNR is bulkier than regular Ubuntu.
Check out Spry, Crunchbang or Masonux.

---

### Post by Psumi on 2010-01-31
Try using the mini.iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

When it says boot on screen, type cli and hit enter. it'll install a base CLI system, where you can install your own ubuntu system yourself, from the DM you use, to the window manager.

also, gnome-meta is probably still broken, so if you want a minimal gnome install:

```
sudo apt-get install gnome-core gdm xorg gnome-icon-theme
```

if you want a minimal xfce install:

```
sudo apt-get install xfce4 xorg wicd alsa-utils xfce4-terminal gnome-icon-theme
```

Then once you next login to the tty1, type startx and hit enter. When you want to change your volume, in terminal, type alsamixer and hit enter to open up the alsamixer.

Or LXDE minimal:

```
sudo apt-get install lxde-core wicd xorg alsa-utils lxde-terminal gnome-icon-theme
```

Do the same things to startx and alsamixer like above.

As for the "gnome-icon-theme" package, it's required for some things to work perfectly. Install it, then install whatever other icon packages you desire. You may want to install gnome-icon-theme separately on its own line with **--no-install-recommends** option, as it pulls some recommends from gnome.

I won't recommend a KDE minimal as I've seen KDE as being the heaviest DE.

---

### Post by tacantara on 2010-01-31
Are you looking to stay strictly with an Ubuntu variant, or would you consider a lightweight Linux version like Puppy Linux?

Here's a link for Puppy, if you're interested:

[http://www.puppylinux.com/](http://www.puppylinux.com/)

---

### Post by supermooshman on 2010-01-31
> **ihermit said:**
> UNR is bulkier than regular Ubuntu.

serious!? isn't UNR smaller due to some programs not included (like brasero or gimp)
> Are you looking to stay strictly with an Ubuntu variant, or would you  consider a lightweight Linux version like Puppy Linux?

I would like to try to stay with ubuntu as much as possible (just got most things figured :)

---

### Post by SuperSonic4 on 2010-01-31
> **Psumi said:**
> Try using the mini.iso: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

When it says boot on screen, type cli and hit enter. it'll install a base CLI system, where you can install your own ubuntu system yourself, from the DM you use, to the window manager.

also, gnome-meta is probably still broken, so if you want a minimal gnome install:

```
sudo apt-get install gnome-core gdm xorg
```

if you want a minimal xfce install:

```
sudo apt-get install xfce4 xorg wicd alsa-utils xfce4-terminal
```

Then once you next login to the tty1, type startx and hit enter. When you want to change your volume, in terminal, type alsamixer and hit enter to open up the alsamixer.

Or LXDE minimal:

```
sudo apt-get install lxde-core wicd xorg alsa-utils lxde-terminal
```

Do the same things to startx and alsamixer like above.

What this guy said.

There are other distros based on other bases but if you want to go with ubuntu

---

### Post by supermooshman on 2010-01-31
cool, I'm downloading the minimal cd as we type

hope for the best! (and if not you can expect me to come crying in a few days ;))

---

### Post by Psumi on 2010-01-31
> **supermooshman said:**
> cool, I'm downloading the minimal cd as we type

hope for the best! (and if not you can expect me to come crying in a few days ;))

I can help you with some possible issues you might have. For example, gstreamer may not work in the xfce4 or lxde minimal installs when you try to play something with totem.

You need libasound2 or whatever to fix one thing, as well as some other gstreamer codecs. if you want to search for something through apt without using synaptic: **apt-cache search <search terms>** in terminal. it's saved me quite the amount of gnome deps.

if you use lxde minimal like I said, your USBs won't automount and may not show in some applications until you use pcmanfm to mount them. QT Apps will not see the drive, and you'll need to navigate to /media/<nameofdisk> to browse it with QT (IE: smplayer.)

DO NOT use totem if you can. Use, instead, parole media player: [https://edge.launchpad.net/~stemp/+archive/xfce/+packages](https://edge.launchpad.net/~stemp/+archive/xfce/+packages) (get the kkxfce1 version for karmic or llxfce for lucid.)

To install a deb without a gui frontend: **sudo dpkg -i <path/to/deb>** and it will give you additional instructions in case something goes wrong. gdebi requires a bunch of gnome deps, but if you have gnome anyway, it won't matter.

---

### Post by juancarlospaco on 2010-01-31
**MinimalCD **

sudo apt-get install xorg icewm icewm-themes mc links bmon xpaint xterm mp3blaster kupfer pcmanfm htop midori wbar youtube-dl rsstail epdfview mirage gtkdiskfree xarchiver xtrlock ayttm twidge rtorrent xdesktopwaves moc catdoc antiword python grandr zenity sylpheed tkmixer unrar ttf-liberation smartpm wicd

make a login script like this:
**xdesktopwaves ; wbar -vbar -pos right -falfa 50 &**

You dont need a Login manager, 
login from console, and use a script to autostart the X.

PCManFM should not work, 
because no Gnome-Icons installed, dont install them, just:
**echo gtk-icon-theme-name="Tango" > $HOME/.gtkrc-2.0**

Midori should not display homepage but an error, 
because no Ubuntu-Artwork installed, dont install them, just:
**sudo mkdir -p /usr/share/ubuntu-artwork/home/ ; sudo touch /usr/share/ubuntu-artwork/home/index.html**

ttf-liberation makes you dont need Microsoft fonts and cabextract*(and dependencies)*.

smartpm replaces synaptic, is the First Package Manager developed by Canonical.

xtrlock locks your screen, just type user password and press ENTER and you unlock again

:)

---

### Post by Psumi on 2010-01-31
> **juancarlospaco said:**
> midori

it has a lot of issues on my end:

[http://www.twotoasts.de/bugs/index.php?do=details&task_id=615](http://www.twotoasts.de/bugs/index.php?do=details&task_id=615)

[http://www.twotoasts.de/bugs/index.php?do=details&task_id=708](http://www.twotoasts.de/bugs/index.php?do=details&task_id=708)

[http://www.twotoasts.de/bugs/index.php?do=details&task_id=709](http://www.twotoasts.de/bugs/index.php?do=details&task_id=709)

[http://www.twotoasts.de/bugs/index.php?do=details&task_id=725](http://www.twotoasts.de/bugs/index.php?do=details&task_id=725)

[http://www.twotoasts.de/bugs/index.php?do=details&task_id=727](http://www.twotoasts.de/bugs/index.php?do=details&task_id=727)

even with the PPA (0.2.2) version.

---

### Post by juancarlospaco on 2010-01-31
[I]All Webkit 100/100 AcidTest.org got some problems, but the problem is poor non-standard coded pages.
Check 3W standards test on the web you found problems, sometimes you find +500 errors. [/I]
(this page only got +32 errors)

---

### Post by Xbehave on 2010-01-31
Yes use the minimalCD and install just what you want (almost every distro has an option like this ubuntu,fedora,etc, some even have it as the default way to install arch,gentoo,etc)

---

### Post by gjoellee on 2010-01-31
> **supermooshman said:**
> Hi all,

just something I was wondering; does a stripped down version of ubuntu exist?
Basically I am looking  for just the OS (evolution, tomboy, open office, games etc).

As I am using an eee, I am trying to save as much space as possible (even the UNR is a bit too bulky).

cheers

My sister use Jolicloud on her EEE PC. It works very well...!

---

### Post by hhh on 2010-02-01
wattOS...
[http://www.planetwatt.com/](http://www.planetwatt.com/)

---

### Post by Psumi on 2010-02-01
> **hhh said:**
> wattOS...
[http://www.planetwatt.com/](http://www.planetwatt.com/)

Oh my~ It uses SLiM! I need to try that out!

---

### Post by hhh on 2010-02-01
@Psumi,

I should mention that the Live CD spits out error messages during boot, but they do not effect performance and they are not present (apparently) if you install it to hard drive. Also, the developer(s) forgot to add jockey-gtk to the current RC1 iso, so you'll probably want that to enable your graphic card's capabilities, see the forums for more info. I haven't installed it to hard drive (I'm happy running Karmic with standalone Openbox/tint2), but, like Ubuntu itself, sound, keyboard, mouse and my wireless USB adapter all worked out-of-the-box using the Live CD. The default app collection is really small, the iso is under 500MB.

---

### Post by Psumi on 2010-02-01
> **hhh said:**
> @Psumi,

I should mention that the Live CD spits out error messages during boot, but they do not effect performance and they are not present (apparently) if you install it to hard drive. Also, the developer(s) forgot to add jockey-gtk to the current RC1 iso, so you'll probably want that to enable your graphic card's capabilities, see the forums for more info. I haven't installed it to hard drive (I'm happy running Karmic with standalone Openbox/tint2), but, like Ubuntu itself, sound, keyboard, mouse and my wireless USB adapter all worked out-of-the-box using the Live CD. The default app collection is really small, the iso is under 500MB.

My graphic card is an ATI FireGL card, it is supported by the open-source drivers, and has 3D capabilities with them. However, I cannot use compiz, as it slows my computer to a stop.

---

### Post by markbuntu on 2010-02-02
The kuki linux team has just recently got kuki working on the EEE. It is a very small and fast ubuntu based distro for the aspire one and now for the eee as well. It is  works OOB without all the bloat but uses the ubuntu repo so you can add anything you want.

---

### Post by arnab_das on 2010-02-02
well i was going through this wiki page yesterday here: 

[http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions](http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions)

and going through each of them one by one. have to tell u, there were loads of relatively unknown distros which are apparently very light weight. nothing against ubuntu, but i'm just stunned at the no of distros linux has! i mean i knew the names of hardly 10!

---

### Post by markbuntu on 2010-02-03
If you want to see a lot of distros

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Warpnow on 2010-02-03
+1 to kuki
+2 to wattOS
+3 to minimal CD
+99999 to using jaunty instead of karmic on netbooks for the much better general compatability.

---

