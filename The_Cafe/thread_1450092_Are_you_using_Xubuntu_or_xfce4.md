---
title: "Are you using Xubuntu or xfce4 ?"
date: 2010-04-08
forum: The Cafe
---

### Post by MooPi on 2010-04-08
I'm doing the beta Lucid testing of a minimal Ubuntu install with xfce4 but not Xubuntu. I've used Xubuntu before and found it sluggish because of all the small services that were running. A simple xfce4 desktop by comparison is very light on it's feet. 
So if anyone is doing this could share your thoughts and favorite apps while in this environment.
I currently have just multimedia stuff up and running and may add some offices stuff later.
Just looking for a light nimble setup and apps that fit the style
Mplayer
Mencoder
xmms2
Promoe
xfburn

---

### Post by kerry_s on 2010-04-08
i'm using lubuntu(lxde) beta, with the xfce4 stuff i like, it's been very quick & lite.

hows your resource use looking?
mine uses 85mb on startup & around 200mb just browsing the web all day.

---

### Post by MooPi on 2010-04-08
[http://dl.dropbox.com/u/5209151/2010-04-08-194042_1440x900_scrot.png](http://dl.dropbox.com/u/5209151/2010-04-08-194042_1440x900_scrot.png)

I'm using a bit more, but the 64bit setup will. The lxde is a very different beast though and is an Openbox environment versus hte xfce. Would you believe I have an Intel Atom box that boots to 47 mb.

---

### Post by NightwishFan on 2010-04-08
I like XFCE4, especially Thunar. I plan to take a look at lxde for lighter boxes.

---

### Post by kerry_s on 2010-04-08
> **MooPi said:**
> [http://dl.dropbox.com/u/5209151/2010-04-08-194042_1440x900_scrot.png](http://dl.dropbox.com/u/5209151/2010-04-08-194042_1440x900_scrot.png)

I'm using a bit more, but the 64bit setup will. The lxde is a very different beast though and is an Openbox environment versus hte xfce. Would you believe I have an Intel Atom box that boots to 47 mb.


thats not bad at all, i figured you would be a least 300+mb.
i used to use xfce4 as my main long ago, but just lost interest in it. i still love a lot of the xfce4 stuff. i think the xfce4-panel is this best, most people don't even realize you can just drag & drop in the properties window to add launchers, in xfce4 you can do it from app finder as well, i just did mine from the file manager applications folder.

---

### Post by handy on 2010-04-08
Until quite recently I was using Mint-Xfce-6 on my 2nd box, it was really light on its feet, I was very impressed.

I replaced Mint on my 2nd machine with Arch, which I also use on my 1st box.

Arch/Openbox/xfce4-panel, is how I like it, quick & simple as can be.

---

### Post by Psumi on 2010-04-08
This setup beats all:

[http://forums.debian.net/viewtopic.php?f=20&t=50703](http://forums.debian.net/viewtopic.php?f=20&t=50703)

Also, if you don't play non-free codecs, I suggest stripping them out.

---

### Post by Warpnow on 2010-04-08
[http://img203.imageshack.us/img203/4032/20091014004137800x600sc.png](http://img203.imageshack.us/img203/4032/20091014004137800x600sc.png)

Karmic with XFCE4 and a handful of other packages.

---

### Post by mkvnmtr on 2010-04-08
I am using a xfce4 minimal install of 10.04 in virtual box. It is great. I do not install gdm just log in and startx. That seems to make it use a lot less resources. I have used the same in 9.04 and 9.10. When 10.04 releases I believe I will replace gnome with this miminal install xfce4.

---

### Post by Warpnow on 2010-04-08
> **mkvnmtr said:**
> I am using a xfce4 minimal install of 10.04 in virtual box. It is great. I do not install gdm just log in and startx. That seems to make it use a lot less resources. I have used the same in 9.04 and 9.10. When 10.04 releases I believe I will replace gnome with this miminal install xfce4.

If you want a lighter weight login manager Slim works really well.

---

### Post by MooPi on 2010-04-08
I've chosen xfce4 to test because I think it would be easiest for a good friend to try. He recently decided that he couldn't deal with all the bull coming out of his Windows box. I'm testing and tweaking so I can make it work for him when I do load it. It seems very promising and a ton easier than the Openbox I use.

---

### Post by Paqman on 2010-04-08
I'm actually writing a script to automate building up systems from the minimal install. What do you think the minimum packages for a good generic XFCE4 install would be?

---

### Post by NightwishFan on 2010-04-08
On Debian I use: xfce4 xfce4-goodies xorg slim midori pidgin

---

### Post by Psumi on 2010-04-08
> **NightwishFan said:**
> On Debian I use: xfce4 xfce4-goodies xorg slim midori pidgin

As for midori, here are the bugs I have with it:
```
http://www.twotoasts.de/bugs/?do=index&opened=411&type[0]=&sev[0]=&due[0]=&cat[0]=&status[0]=open&percent[0]=&reported[0]=
```

None of them have been fixed, or anything really.

---

### Post by MooPi on 2010-04-08
So far I'm very impressed. I actually screwed up and loaded the 64bit version, but it's turning out good enough. 
Here's my List: Minimal install                     xfce4
                       xarchiver .....                             alsa-utils
                       vorbis-tools.......                           evince
                       xmms2                                  .......Promoe
                       cdparanoia .....                           htop
                       firefox                                   ......scrot
                       gimp                                     .....default jre
                       icedteaplugin.......                         xfburn
                       mplayer ......                                mencoder
                       easytag                                 .........synaptic

---

### Post by Psumi on 2010-04-08
> **MooPi said:**
> So far I'm very impressed. I actually screwed up and loaded the 64bit version, but it's turning out good enough. 
Here's my List: Minimal install                     xfce4
                       xarchiver .....                             alsa-utils
                       vorbis-tools.......                           evince
                       xmms2                                  .......Promoe
                       cdparanoia .....                           htop
                       firefox                                   ......scrot
                       gimp                                     .....default jre
                       icedteaplugin.......                         xfburn
                       mplayer ......                                mencoder
                       easytag                                 .........synaptic

wtf, why synaptic? That pulls too many gnome deps.

Use apt-get in terminal. Also, it's xfce4-terminal for xfce's terminal.

Also google **parole media player PPA**. Parole media player is an xfce4 gstreamer based player like totem.

---

### Post by NightwishFan on 2010-04-08
Beauty of open source, I can contribute to Midori if they need it. On a light system I prefer Webkit browsers. I will toy with Epiphany or Kazehakase as well. Perhaps Galeon, which is essentially Epiphany.

Edit: Psumi, epic master of minimalism at work. Hey nothing wrong with that, I love giving old life to my old machines or add some nice responsiveness to my new ones. I generally just use XFCE4 and GTK+(not gnome) apps when possible. A pity Gnome Mplayer does not work well for me, it would fit well.

This page is kind of helpful:
[http://wiki.xfce.org/recommendedapps](http://wiki.xfce.org/recommendedapps)

---

### Post by Psumi on 2010-04-08
> **NightwishFan said:**
> Beauty of open source, I can contribute to Midori if they need it.

I **_*can't*_**.

---

### Post by MooPi on 2010-04-08
> **Psumi said:**
> wtf, why synaptic? That pulls too many gnome deps.

Use apt-get in terminal. Also, it's xfce4-terminal for xfce's terminal.

Also google **parole media player PPA**. Parole media player is an xfce4 gstreamer based player like totem.
You have to take into consideration that this is a test for a friend and apt-get would be to tough for my noob buddy. Synaptic fills the gap if he decides to start adding to the install. I'm setting up scripts for everything else( dvd movie, recording CD's recording movies) etc..........

---

### Post by handy on 2010-04-09
> **MooPi said:**
> I've chosen xfce4 to test because I think it would be easiest for a good friend to try. He recently decided that he couldn't deal with all the bull coming out of his Windows box. I'm testing and tweaking so I can make it work for him when I do load it. It seems very promising and a ton easier than the Openbox I use.

You're right, it *is* easier than Openbox; you don't have to mess with those 3 files in .config/openbox/ not that they have to be hard to deal with anyway.

& .xinitrc really doesn't count in this one I guess.

---

### Post by Mark76 on 2010-04-09
Raw unadulterated Xfce4 is much closer to Win 98/XP in looks, isn't it.

---

### Post by handy on 2010-04-09
> **Mark76 said:**
> Raw unadulterated Xfce4 is much closer to Win 98/XP in looks, isn't it.

Not from my experience.

I ran my DE (when I ran Xfce on Arch) & do run my WM; Openbox/xfce4-panel on Arch, on a custom GTK2 theme.

I also don't use icons or windows, so my desktop probably doesn't look like most people's (I think).

Anyway, my Xfce never looked anything like win98/xp.

---

### Post by Warpnow on 2010-04-09
The post I made earlier in the thread has a link to my xfce desktop, which is using a prepackaged theme and has no visual enhancements aside from conky.

---

### Post by Mark76 on 2010-04-09
> **handy said:**
> Not from my experience.

I ran my DE (when I ran Xfce on Arch) & do run my WM; Openbox/xfce4-panel on Arch, on a custom GTK2 theme.

I also don't use icons or windows, so my desktop probably doesn't look like most people's (I think).

Anyway, my Xfce never looked anything like win98/xp.

This is a screenshot from an account I created when I was thinking of doing a ROX desktop tutorial for ostalk (the original one having been lost in the great crash)

[ATTACH]152726[/ATTACH]

That's without any distro specific alterations or branding.

---

### Post by medic2000 on 2010-04-09
I use Xfce4 on my ArchLinux system and it is very very lightweight. The Xubuntu does not reflect the lightness of Xfce. I use these applications(all of them lightweight):

-Firefox
-Zim(desktop wiki-great and light app.)
-Xfce Notes app
-Evince-gtk(the pdf reader but stripped of its gnome depends.And its very FAST compared to standard evince)(Build from AUR-Arch User Repo)
-Smplayer
-Gmusicbrowser(fast and reliable-no gnome depends.)
-Thunar
-Guake(drop down terminal app)
-Geany(IDE)
-Mousepad(simple text editor)
-Transmission(Bittorrent client)
-Stardict(Awesome dictionary)
-Catfish(very light search tool-using it with its integration with thunar)
-Wicd(for wireless and cable network)
-Xfburn(cd-dvd burner)
-Emesene and pidgin
-Xarchiver(archive tool)
-Galculator(calculator)
-Bleachbit(for cleaning unnecessary files)

---

### Post by XubuRoxMySox on 2010-04-09
I love Xfce4's simplicity and versatility. I use it on Debian Testing and it's very fast and responsive if it isn't loaded up with all the Gnome cruft that Xubuntu used to add.

In fairness, Xubuntu is not really aimed at users looking for lightweight stuff. It's Ubuntu, after all, still aiming at being an "all things to all users" kinda distro, but using Xfce instead of Gnome by default. Users in search of a truly lightweight system have options, though:

*Minimal* Ubuntu or Debian with Xfce-4 (and not all the other Gnome stuff), or Lubuntu (LXDE) when it's ready (Slim seems to help eliminate several of LXDE's "**'Buntu bugs**" - the persistent little problems that plague LXDE on Ubuntu but not on many other distros).

I find no perceptible difference in speed between LXDE and Xfce-4 on minimal Debian. I love the Xfce-4 panel options, applets, and other goodies that don't slow it down a bit.

-Robin

---

### Post by MooPi on 2010-04-09
Glad to see other minimalist out there. None of my computers could be classified as slow or old. I just use minimal and xfce4 and openbox because I hate the cruft as "dixiedancer" put it. Speed and functionality is what matters most to me. I'm actually surprised by the speed of xfce on a mini setup. Besides using the minimal is like spinning your own distro.

---

### Post by RiceMonster on 2010-04-09
I used Xfce4 for over a year. It's really good. I'd say I like it just as much as GNOME and KDE. It's lightweight and modular, yet it's still easy to use and it doesn't take a lot of messing around to get it set up.

---

### Post by handy on 2010-04-09
> **dixiedancer said:**
> ...
I find no perceptible difference in speed between LXDE and Xfce-4 on minimal Debian. I love the Xfce-4 panel options, applets, and other goodies that don't slow it down a bit.

-Robin

As previously stated, these days I use xfce4-panel on Arch/Openbox.

When playing around with Xfce stuff on Openbox, I discovered that I could run just about all of Xfce4 on Openbox, due to Xfce's modularity (not that I do, I just use the panel a a few plugins). 

As soon as I added xfce4-session, I lost the Openbox speed advantage. It is the Xfce session manager that slows Xfce down.

So for any Xfce users out there I suggest disabling xfce4-session & seeing the difference in speed.

If you need a session manager, there is a range of session managers out there that are happy to work with Xfce4.

Personally I don't need a session manager so I don't run one.

---

### Post by medic2000 on 2010-04-09
> **handy said:**
> As previously stated, these days I use xfce4-panel on Arch/Openbox.

When playing around with Xfce stuff on Openbox, I discovered that I could run just about all of Xfce4 on Openbox, due to Xfce's modularity (not that I do, I just use the panel a a few plugins). 

As soon as I added xfce4-session, I lost the Openbox speed advantage. It is the Xfce session manager that slows Xfce down.

So for any Xfce users out there I suggest disabling xfce4-session & seeing the difference in speed.

If you need a session manager, there is a range of session managers out there that are happy to work with Xfce4.

Personally I don't need a session manager so I don't run one.

Good point. I will try to replace it. What does exactly session managers do?

---

### Post by handy on 2010-04-09
> **medic2000 said:**
> Good point. I will try to replace it. What does exactly session managers do?

They vary a bit, between automated & manual configuration; opening up everything just the way you left it when you shut down the machine is what some will do.

In Openbox, the session management allows you to have certain applications open on certain desktops & to configure some other things. This is done manually in the ~/.config/openbox/autostart.sh file.

This page tells you about xfce4-session:

[http://www.xfce.org/documentation/4.2/manuals/xfce4-session](http://www.xfce.org/documentation/4.2/manuals/xfce4-session)

This man page gives some info about the session manager xsm:

[http://linux.die.net/man/1/xsm](http://linux.die.net/man/1/xsm)

---

