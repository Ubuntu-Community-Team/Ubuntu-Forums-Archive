---
title: "Xubuntu 17.10 is looking good so far"
date: 2017-09-25
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2017-09-25
Installed the ISO from a USB stick this morning and after some playing around with it. I have the Nvidia drivers, Cairo Dock, Compiz and even the cube working pretty well.

[[IMG]http://en.zimagez.com/miniature/screenshot2017-09-2517-41-40.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2017-09-2517-41-40.php")

```
System:    Host: cavsfan-Le-Beast Kernel: 4.13.0-11-generic x86_64 bits: 64 gcc: 7.2.0
           Desktop: Xfce 4.12.3 (Gtk 2.24.31) Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: MICRO-STAR model: G31M3-L V2(MS-7529) v: 1.0 serial: N/A
           BIOS: American Megatrends v: V2.8 date: 03/11/2010
CPU:       Quad core Intel Core2 Quad Q9550 (-MCP-) arch: Penryn rev.10 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 22743
           clock speeds: max: 2842 MHz 1: 2842 MHz 2: 2842 MHz 3: 2842 MHz 4: 2842 MHz
Graphics:  Card: NVIDIA G92 [GeForce 9800 GT] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.3 ) drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce 9800 GT/PCIe/SSE2 version: 3.3.0 NVIDIA 340.104 Direct Render: Yes
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-11-generic
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e800 bus-ID: 03:00.0
           IF: ens33 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1500.3GB (29.0% used)
           ID-1: /dev/sda model: WDC_WD5003ABYX size: 500.1GB
           ID-2: USB /dev/sdb model: FANTOM_DRIVE size: 1000.2GB
Partition: ID-1: / size: 14G used: 5.3G (40%) fs: ext4 dev: /dev/sda7
           ID-2: swap-1 size: 0.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A gpu: 0.0:46C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 177 Uptime: 56 min Memory: 923.1/3948.0MB Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121) inxi: 2.3.37 

```

[[IMG]http://en.zimagez.com/miniature/screenshot2017-09-2517-42-21.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2017-09-2517-42-21.php")

Of course I also customized the grub screen too.

---

### Post by RobGoss on 2017-09-25
Looks great glad you have things working like you want them

---

### Post by PJs Ronin on 2017-09-26
Agreed CavsFan.   I've been looking at my options now that Gnome is becoming the default DE for Ubuntu; personally, not happy with that.   I cloned my default Unity partition to several branches and have played with maintaining unity, going the Gnome route and trying xfce/Xubuntu.   At your recommendation I also tried an Arch install, but the nightmares cost me too much sleep!   So far, swapping out unity and replacing with xfce has been an enlightening experience.   It's quick, rock solid, takes up less disk space and I can put panels anywhere, or nowhere, I want... bliss.

For intrerested parties, Yoko's weapon is a futuristic rail gun that fires anything she can fit into the breech.

[http://i.imgur.com/GPwCZaE.png](http://i.imgur.com/GPwCZaE.png)
[IMG]http://i.imgur.com/8ZvTGwD.png[/IMG]

---

### Post by ajgreeny on 2017-09-26
If you fancy trying a simpler OS based on Arch that does not require the same amount of prior knowledge to get it running well, have a good look at Antergos.

I have it running just as a *look-see* in VBox, using the xfce4 desktop, which I chose during the installation; I think 6 DEs are available, so choose just one, not all of them just so you can check them all out.

It runs very well for me and could even be a distro I would use if the *ubuntu family ever bit the dust and disappeared; seems unlikely, but you never know.

---

### Post by Cavsfan on 2017-09-26
I've been hooked on Xubuntu since Paramvir, the VinDSL conky and conky weather programmer, first suggested that I install Arch Linux. I tried Gnome at first but, everything was so big and I didn't want to mess with resizing it all.
So I installed Xfce and my DE. 

Trust me Arch was not easy for me to install. I installed the Arch Wiki viewer on my android phone: [https://play.google.com/store/apps/details?id=com.jtmcn.archwiki.viewer&hl=en](https://play.google.com/store/apps/details?id=com.jtmcn.archwiki.viewer&hl=en)

I tried and tried and after about 5 days I gave up, not knowing if I had it in me to get it installed. I gave it a few days and thought about it all, then I tried it again with a fresh mind and I managed to get it installed.
Initially you have nothing and have to install a DM, DE and all of the apps you want to use including Firefox and anything else you need. It comes with absolutely no pre-installed apps and it has only what you add to it.

With Paramvir's help I was able to even do away with a DM and boot into TTY1, then enter userid and password and X is started along with startxfce.

Arch has Wiki's for everything but, I could not find the one that tells you how to that right now, but I'll find it.

Xubuntu 17.10 Grub screen as default:
[[IMG]http://en.zimagez.com/miniature/20170925113707.jpg[/IMG]]("http://en.zimagez.com/zimage/20170925113707.php")

I used the same background on my custom Grub screen as my wallpaper:
[[IMG]http://en.zimagez.com/miniature/20170926094742.jpg[/IMG]]("http://en.zimagez.com/zimage/20170926094742.php")

But, installing Arch Linux is doable you just have to make notes and take your time. I gave 200GB of my HD to Arch Linux.
What is sweet about it is that it never needs a clean install or an upgrade to the next version because it is a rolling release.

The default kernel, along with everything else is cutting edge but, you can install an LTS kernel if you choose to. I did add an LTS kernel and have used it off and on.
But, I have 3 Ubuntu installations too. I like to have alternatives if I have a problem with one of them.

---

### Post by VMC on 2017-09-26
Yes, I went the Arch root a few years ago. It took a week to get it just like I wanted, but in the end Xubuntu was just as good. Yes, I know all about the learning you get from Arch, but I'm into using my OS and not having to re-invent the wheel.

---

### Post by ClickXT on 2017-09-26
> **ajgreeny said:**
> If you fancy trying a simpler OS based on Arch that does not require the same amount of prior knowledge to get it running well, have a good look at Antergos.

I have it running just as a *look-see* in VBox, using the xfce4 desktop, which I chose during the installation; I think 6 DEs are available, so choose just one, not all of them just so you can check them all out.

It runs very well for me and could even be a distro I would use if the *ubuntu family ever bit the dust and disappeared; seems unlikely, but you never know.

This. Same goes with Manjaro. I've been really enjoying Manjaro XFCE. I'm pretty happy.

Glad to hear 17.10 Xubuntu is going well.

---

### Post by ventrical on 2017-09-26
@cavsfan

Yep .. +1 to xubuntu so far.

---

### Post by Chanath on 2017-09-26
> **ventrical said:**
> @cavsfan

Yep .. +1 to xubuntu so far.

If there should be a change of the default Ubuntu, it should've been Xubuntu. It is safe and stable. Thunar doesn't go jerky. There is a bottom panel (well, its on the top, but can be brought down) and a very familiar menu -- Whisker menu. Anyone leaving Windows would've found a similar look and feel. Zorin has forked the Gnomenu to match that feeling, even though using Gnome.

If money would be brought into a distro, it'd be from the enterprise users. The well known proprietary enterprise Linux distro knows about that and gives those users something they know how to use, not the gnome-shell, but the gnome-classic -- two fixed panels, one on top and one on the bottom, and a start menu. It would be interesting to find strategy to get the Ubuntu's enterprise users to drop Unity and learn Windows 8 like system in about an year or so. Just imagine a guy searching for icon on a 21" monitor.

---

### Post by lammert-nijhof on 2017-09-26
Xubuntu is looking good and reliable and it support 3D graphics for Virtualbox unlike Ubuntu 16.04 or 17.10. Since I run my main distros in Vbox, it is an essential requirement for me.

---

### Post by Cavsfan on 2017-09-27
> **RobGoss said:**
> Looks great glad you have things working like you want them

Thanks! It didn't work (compiz and wobbly windows) until I rebooted and then everything was perfect. I used it for over 5 hours yesterday and it did not break once.

> **PJs Ronin said:**
> Agreed CavsFan.   I've been looking at my options now that Gnome is becoming the default DE for Ubuntu; personally, not happy with that.   I cloned my default Unity partition to several branches and have played with maintaining unity, going the Gnome route and trying xfce/Xubuntu.   At your recommendation I also tried an Arch install, but the nightmares cost me too much sleep!   So far, swapping out unity and replacing with xfce has been an enlightening experience.   It's quick, rock solid, takes up less disk space and I can put panels anywhere, or nowhere, I want... bliss.

For interested parties, Yoko's weapon is a futuristic rail gun that fires anything she can fit into the breech.

[http://i.imgur.com/GPwCZaE.png](http://i.imgur.com/GPwCZaE.png)
[IMG]http://i.imgur.com/8ZvTGwD.png[/IMG]

I never really got into Unity, I was always using gnome-classic as I re-call. But, when I got into Arch and Xfce I discovered Xubuntu was nearly the same thing so I've been using it ever since.
Because I have to have a few operating systems on my PC. I have windows 10 for the wife and to keep up with it in case I need to help out a friend. Plus I have Need For Speed Most Wanted from 2004-5 and I never wanted to deal with Wine and I don't think it would run it anyway. My son and I tried it one time and it was having none of it lol.
Nice screenshot BTW. I wish I could show you my Arch conkys but, we're testing version 7 of Conkywx so I can't. But, I'm running 19 conkys and it's not even using that much CPU. Paramvir wrote his own Conky called conky-cairo available in the AUR.
It is phenomenal!

> **VMC said:**
> Yes, I went the Arch route a few years ago. It took a week to get it just like I wanted, but in the end Xubuntu was just as good. Yes, I know all about the learning you get from Arch, but I'm into using my OS and not having to re-invent the wheel.

Not, sure what you mean about having to re-invent the wheel. Arch is what you make of it; nothing more and nothing less, which is why I like it. 
No need to do any clean installs etc. and it has nothing whatsoever that I did not implicitly install.
Plus Arch has things like the Fusion-Icon and a whole bunch of things that still work. I can use that to switch window managers like Compiz to Xfwm4 or Metacity.
And the Fusion-Icon will change window decorators from Emerald (my favorite :P) to GTK+ window decorator.
I don't need things like Pidgin and a bunch of other things that come pre-installed with Ubuntu of any flavor.
 
Don't get me wrong, I used raw Linux commands on a server at work at one time but, basically started out with Ubuntu and will always have at least one LTS version plus the latest version so as to keep up to date on Grub changes for my Wiki.

BTW, I could not find the wiki that shows you how to boot into Arch w/o a DM but, I found my notes and you have to have a ~/.bash_profile file:
```
#
# ~/.bash_profile
#


[[ -f ~/.bashrc ]] && . ~/.bashrc
################ ~/.bash_profile file Start
if [[ -z $DISPLAY && $(tty) = /dev/tty1 ]]; then
  exec /home/cavsfan/bin/go
  # setsid /home/cavsfan/go >& .xlog; logout
  # exec startx
  # Could use xinit instead of startx
  # exec xinit -- /usr/bin/X -nolisten tcp vt7
fi
################ ~/.bash_profile file End

```

Which *if* you are on TTY1 when you login, it executes this file:

```
################ ~/bin/go file Start
#!/bin/bash


# startx  >/dev/null 2>&1;
# startx -- :0  >/dev/null 2>&1;


startx
################ ~/bin/go file End

```

And it you have an ~/.xinitrc file, startx executes that file and it looks like this:
```
################ ~/.xinitrc file Start
#!/bin/sh
#
# Executed by startx (run your window manager from here)


## test for an existing bus daemon, just to be safe
 if test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
    ## if not found, launch a new one
    eval `dbus-launch --sh-syntax --exit-with-session`
    echo "D-Bus per-session daemon address is: $DBUS_SESSION_BUS_ADDRESS"
 fi


exec startxfce4
################ ~/.xinitrc file End

```

Then you are looking at Arch Xfce.

Here is a screenshot showing the Fusion-Icon but, no conkys:
[[img]http://en.zimagez.com/miniature/screenshot2017-09-2718-25-44.png[/img]](http://en.zimagez.com/zimage/screenshot2017-09-2718-25-44.php)

---

### Post by Cavsfan on 2017-09-28
I've been running Xubuntu 17.10 for several hours and it's still not giving me any problems.

I forgot to mention a few things I really like about Xubuntu versus any other flavor. One is that you can open as many Thunars as you want and it doesn't go back to the single one that is already open like most 'buntus do.
It opens a separate one every time and same with terminal. I really like that. Just starting to get my conkys all going and they are looking good. I copied them from Xubuntu 16.04 so they are already setup, just some tweaking needs done.

I post a screenshot here in awhile as this is the released version 6 and then I'll load up the developmental version 7.

@PJs Ronin, you are still testing version 7 as well aren't you?

Cheers

---

### Post by Cavsfan on 2017-09-28
Well here is my version 6 of Conkywx:

[[IMG]http://en.zimagez.com/miniature/screenshot2017-09-2818-04-55.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2017-09-2818-04-55.php")

And yep, still have the kitty, :lolflag:

---

### Post by Chanath on 2017-09-28
Fully upgraded Xubuntu 17.10 is doing very well. 
I have only one conky. I use inxi to find other info, if I need them.
I also have Slingshot Launcher from Natty days as an additional eye-candy menu, DockbarX applet, Hotcorners and Skippy-xd to spread all open windows.
Nothing got broken by any upgrade.

---

### Post by PJs Ronin on 2017-09-28
> **Cavsfan said:**
>  ...

@PJs Ronin, you are still testing version 7 as well aren't you?

Cheers
I am indeed.   I have wx7 running on an xfce install which started life as a Unity partition; 16.04 dist-upgraded to 17.10.   I was impressed with how easy the xfce/conkywx7 transform went.   The partition is rock solid and snappy.

As you know I'm also trying to install an xfce/conkywx7 combo on an Arch distro, so far with minimal success... but that's due more to my own noobness (word?) with Arch.   From what I have so far, this install will perform better than the xfce/*buntu combo.

In both cases, it's the xfce DE that makes the party swing... super impressed with the capabilities.

---

### Post by Cavsfan on 2017-09-29
> **PJs Ronin said:**
> I am indeed.   I have wx7 running on an xfce install which started life as a Unity partition; 16.04 dist-upgraded to 17.10.   I was impressed with how easy the xfce/conkywx7 transform went.   The partition is rock solid and snappy.

As you know I'm also trying to install an xfce/conkywx7 combo on an Arch distro, so far with minimal success... but that's due more to my own noobness (word?) with Arch.   From what I have so far, this install will perform better than the xfce/*buntu combo.

In both cases, it's the xfce DE that makes the party swing... super impressed with the capabilities.

Good deal mate! So many things work on Arch that do not work any longer on other distros it's incredible. Even the compiz fish tank is there. You can install the version 8 or 9 of compiz.
 I went with version 8 because it worked better for me and had a bunch of older things that no longer show up in other distros of Linux.

Arch is pretty hard to break once it's installed. Us newbies all thought when something happened that we broke it and needed to re-install it. Paramvir was like "oh no, that is not a big deal, just do this...".
I accidenatally deleted my /etc directory and he helped me recover from that. So, I'd say Arch is a beast!
Plus it helps to  have someone as experieced with Arch as he is. Arch is the only thing he uses and he doesn't even have the lts kernel installed. I installed it because "why not". :lolflag:

But, there is documentation out there usually in the form of Wikis that help with anything and everything.

But Xubuntu is and has been rock solid. I had to restart a couple of times because my conky's were all out of wack. I fixed one and then noticed others were so I rebooted and they were back to normal.
But, of course I had to change back what I had "fixed".

So, on to version 7 of comkywx on 17.10 which will be more testing of the beta version too.

---

### Post by Cavsfan on 2017-09-29
I tried to post this yesterday but, I could not no matter what I did.

If anyone likes the Buuf icons in the pictures I've posted I found what has to be the easiest way to install them I have seen yet:

cd /usr/share/icons
sudo wget [https://dl.opendesktop.org/api/files/download/id/1479324062/buuf3.22.tar.xz](https://dl.opendesktop.org/api/files/download/id/1479324062/buuf3.22.tar.xz)
sudo tar -xvf buuf3.22.tar.xz
sudo rm -Rf buuf3.22.tar.xz

I got that from here - [https://www.2daygeek.com/install-buuf-icon-theme-on-ubuntu-fedora-debian-opensuse-manjaro-arch-linux-mint/#](https://www.2daygeek.com/install-buuf-icon-theme-on-ubuntu-fedora-debian-opensuse-manjaro-arch-linux-mint/#)

Then you just go Menu >> Settings >> Appearance >> Icons “Choose Buuf 3.2 from the list” >> Finally close

---

### Post by Cavsfan on 2017-09-29
Here is a link with a preview of the new Conkywx version on Arch w/Xfce. 


[https://ubuntuforums.org/showthread.php?t=1771033&page=260&p=13691910#post13691910](https://ubuntuforums.org/showthread.php?t=1771033&page=260&p=13691910#post13691910)


Now, my goal is to install that on all 3 of my Xubuntu versions.

---

### Post by Cavsfan on 2017-10-09
Xubuntu 17.10 is still running smoothly. Not a single hiccup or bug report...

---

### Post by Chanath on 2017-10-09
> **Cavsfan said:**
> Xubuntu 17.10 is still running smoothly. Not a single hiccup or bug report...

I agree that Xubuntu works without a hiccup, but...

There is one, a minor one for us, but for not experienced users, it is a big one. The thumbnails don't show by default. One has to enable that, but not all users know how to. The devs most probably consider that the Xfce users are sort of tinkerers, but that shouldn't be.  Xubuntu is such a nice distro, the devs should consider ***all users as not-experienced ones*** and release a ready to use distro with everything working. Everything works in Xfce4, so why not give all in default to the users?

---

### Post by flocculant on 2017-10-10
> **Chanath said:**
> ...  The thumbnails don't show by default. One has to enable that, ...

What did you need to do to enable it?

---

### Post by Chanath on 2017-10-10
> **flocculant said:**
> What did you need to do to enable it?

Thunar>Edit>Preferences>Display
The downloaded distro usually comes with Last active view and Local files only. But, that "last active view"[FONT=&amp] is[/FONT] of the dev's computer, who created the live iso. He might not care too much for thumbnails. Not having thumbnails showing is a problem for normal users. I change the last active view to icon view and close Thunar. If I get the thumbnails showing, I change it back to last active view and everything is okay. Sometimes, after changing to icon view, you have to logout and login. It may look like a minor matter, but for non-technical users, it is a big matter. "Oh, in Windows I can see my pictures..." I've heard this many times.

*Xubuntu should be tweaked to its utmost, before releasing.* Move the panel to bottom, make the panel size about 32pix, put the categories in Whisker menu to the left, put some icons (Firefox, Thunar, LibreOffice, Media player, Image viewer) on the panel. Words like Parole, Ristretto don't say anything to normal users, so some normal words have to be found. 

Xubuntu is such a positive distro, it should be ready to use for child of 7 out of box. And, for old people too. There are lot of older people, who don't know much, but know if you click on a picture, it'd open in viewer. First you have to see the thumbnail to click on it. The Image viewer should open as a window, not full screen. Media player opens in a window, Image viewer doesn't. 

Maybe the devs should think of adding DockbarX, as it allows pinning app icons to the panel. 

Xubuntu can be configured, but that's for people, who wants to read how-tos. But, if Xubuntu comes fully configured, so a child of 6 can immediately use it, then no other distro can beat it.

---

### Post by flocculant on 2017-10-10
> **Chanath said:**
> Thunar>Edit>Preferences>Display
The downloaded distro usually comes with Last active view and Local files only. But, that "last active view"[FONT=&amp] is[/FONT] of the dev's computer, who created the live iso. He might not care too much for thumbnails. Not having thumbnails showing is a problem for normal users. I change the last active view to icon view and close Thunar. If I get the thumbnails showing, I change it back to last active view and everything is okay. Sometimes, after changing to icon view, you have to logout and login. It may look like a minor matter, but for non-technical users, it is a big matter. "Oh, in Windows I can see my pictures..." I've heard this many times.

*Xubuntu should be tweaked to its utmost, before releasing.* Move the panel to bottom, make the panel size about 32pix, put the categories in Whisker menu to the left, put some icons (Firefox, Thunar, LibreOffice, Media player, Image viewer) on the panel. Words like Parole, Ristretto don't say anything to normal users, so some normal words have to be found. 

Xubuntu is such a positive distro, it should be ready to use for child of 7 out of box. And, for old people too. There are lot of older people, who don't know much, but know if you click on a picture, it'd open in viewer. First you have to see the thumbnail to click on it. The Image viewer should open as a window, not full screen. Media player opens in a window, Image viewer doesn't. 

Maybe the devs should think of adding DockbarX, as it allows pinning app icons to the panel. 

Xubuntu can be configured, but that's for people, who wants to read how-tos. But, if Xubuntu comes fully configured, so a child of 6 can immediately use it, then no other distro can beat it.

Ok - so that's a lot of things 'you' like.

This bit from this forum's description "Please Note: Ubuntu Developers do not usually read the forums," works for Xubuntu as well.

The place to put forward your ideas to Xubuntu devs is on our mailing list > [email]xubuntu-devel@lists.ubuntu.com[/email] (also bear in mind we are a small team, so mails won't get answered immediately)

Cheers.

---

### Post by Chanath on 2017-10-11
> **flocculant said:**
> Ok - so that's a lot of things 'you' like.

This bit from this forum's description "Please Note: Ubuntu Developers do not usually read the forums," works for Xubuntu as well.

The place to put forward your ideas to Xubuntu devs is on our mailing list > [EMAIL="xubuntu-devel@lists.ubuntu.com"]xubuntu-devel@lists.ubuntu.com[/EMAIL] (also bear in mind we are a small team, so mails won't get answered immediately)

Cheers.

Its not *just* what I like, its what I'd like Xubuntu to come with, that is, if Xubuntu would care to be the most liked Ubuntu derivative. I can do the things I mentioned myself, but that's not the case. It is that most devs forget that the user is not the same as the dev. What becomes released is the last working install of the developer, with all the configurations he likes and some he had forgotten to delete. The thumbnails is not showing in default is something the devs had forgotten to look into.

There are lot of things devs forget to clear up (not only in Xubuntu), and that state had been there for years - if you look at 12.04 or even before, you'd see the same files. There are lot of unnecessary files around, forgotten. Here's an example; look in /usr/share/python-apt/templates. You get Tanglu, Blankon, gNewsense etc. Overworked people forget, which is, of course, normal. 

Xubuntu had been a bug free distro for quite a while, only slight stuff like thumbnails not showing by default. With a little QA, it could be the best ever in the Ubuntu family.

---

### Post by flocculant on 2017-10-11
As I said "The place to put forward your ideas to Xubuntu devs is on our mailing list > [email]xubuntu-devel@lists.ubuntu.com[/email] (also bear in mind we are a small team, so mails won't get answered immediately)"

---

### Post by Cavsfan on 2017-10-12
> **flocculant said:**
> Ok - so that's a lot of things 'you' like.

This bit from this forum's description "Please Note: Ubuntu Developers do not usually read the forums," works for Xubuntu as well.

The place to put forward your ideas to Xubuntu devs is on our mailing list > [EMAIL="xubuntu-devel@lists.ubuntu.com"]xubuntu-devel@lists.ubuntu.com[/EMAIL] (also bear in mind we are a small team, so mails won't get answered immediately)

Cheers.

> **Chanath said:**
> Its not *just* what I like, its what I'd like Xubuntu to come with, that is, if Xubuntu would care to be the most liked Ubuntu derivative. I can do the things I mentioned myself, but that's not the case. It is that most devs forget that the user is not the same as the dev. What becomes released is the last working install of the developer, with all the configurations he likes and some he had forgotten to delete. The thumbnails is not showing in default is something the devs had forgotten to look into.

There are lot of things devs forget to clear up (not only in Xubuntu), and that state had been there for years - if you look at 12.04 or even before, you'd see the same files. There are lot of unnecessary files around, forgotten. Here's an example; look in /usr/share/python-apt/templates. You get Tanglu, Blankon, gNewsense etc. Overworked people forget, which is, of course, normal. 

Xubuntu had been a bug free distro for quite a while, only slight stuff like thumbnails not showing by default. With a little QA, it could be the best ever in the Ubuntu family.

I never really noticed this and haven't had to do anything besides drag most of the main folders like Documents, Downloads, etc. to the left bottom side of Thunar under Places to have them easily accessable.
The icons seem to show up ok although my settings are still unchanged in [COLOR=#000000]Thunar>Edit>Preferences>Display. Is this because I'm not new to Xubuntu?

[/COLOR]

---

### Post by ventrical on 2017-10-12
> **Chanath said:**
> Its not *just* what I like, its what I'd like Xubuntu to come with, that is, if Xubuntu would care to be the most liked Ubuntu derivative. I can do the things I mentioned myself, but that's not the case. It is that most devs forget that the user is not the same as the dev. What becomes released is the last working install of the developer, with all the configurations he likes and some he had forgotten to delete. The thumbnails is not showing in default is something the devs had forgotten to look into.

There are lot of things devs forget to clear up (not only in Xubuntu), and that state had been there for years - if you look at 12.04 or even before, you'd see the same files. There are lot of unnecessary files around, forgotten. Here's an example; look in /usr/share/python-apt/templates. You get Tanglu, Blankon, gNewsense etc. Overworked people forget, which is, of course, normal. 

Xubuntu had been a bug free distro for quite a while, only slight stuff like thumbnails not showing by default. With a little QA, it could be the best ever in the Ubuntu family.

Been testing it since 2010. Moving windows were choppy then and they are choppy now. But I like the theme and the structure. There is a lot to be said about that. It's hard to teach to noobs as a migration alternative. If you have a good sense of linuxesque then it is the desktop for you, otherwise, expect your potential converts to go  running back to windows.

Regards..

---

### Post by Chanath on 2017-10-12
> **ventrical said:**
> Been testing it since 2010. Moving windows were choppy then and they are choppy now. But I like the theme and the structure. There is a lot to be said about that. It's hard to teach to noobs as a migration alternative. If you have a good sense of linuxesque then it is the desktop for you, otherwise, expect your potential converts to go  running back to windows.

Regards..

That's why I say that the devs must remember that the users are not like the devs, but simply ordinary ones, who might try out a new distro. And, for them to stay, the distro must work out of the box.:)

---

### Post by ventrical on 2017-10-12
> **Chanath said:**
> That's why I say that the devs must remember that the users are not like the devs, but simply ordinary ones, who might try out a new distro. And, for them to stay, the distro must work out of the box.:)

I should frame this and make it a permanent sidekick. :)

It has been my argument from day one.But we've come a long way since then. Ubuntu has set the bar. Well,actually, Ubuntu/Canonical founder has set the bar that Ubuntu is "the best operating system on the planet" and therefore all that is left are excuses. Lucid/Maveric with Gnome2 worked out of the box with 10.10 probably being the most versatile and reliable. 12.04 Unity with Unity2D was a real moon shot that was bang on for more legacy machines. I remember one of the members, Ronac, used to say , "if it ain't broke, don't fix it". :) It's so easy to forget where we came from.

Regards..

---

### Post by sgtkeebler on 2017-11-29
How did you get all those widgets on the right? Please share secrets.

---

### Post by howefield on 2017-11-29
Closed.

---

