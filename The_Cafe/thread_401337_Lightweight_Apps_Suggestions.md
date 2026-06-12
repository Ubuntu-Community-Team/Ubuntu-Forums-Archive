---
title: "Lightweight Apps: Suggestions?"
date: 2007-04-04
forum: The Cafe
---

### Post by VileTimes on 2007-04-04
I have a Toshiba Tecra 8100, a PIII 500mghz laptop with 256Meg of RAM, and after installing XFCE4 over Ubuntu 6.10 Server and following a few [tweaking]("http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html") [guides]("http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/"), my old laptop is far more responsive than it ever was under Windows XP.

One of the more important stages of keeping my old laptop as snappy and responsive as I would like has been choosing lightweight applications.  My ideal application needs to strike the balance between functionality and speed. With all of the choice in open source software, however, it can be a rather daunting task to be aware of *everything* available.

Here is a list of the applications I currently have installed on my laptop and why. If anyone has any alternatives to suggest, please do.

**File Manager: Xfe**

Faster than Thunar. PCManFM is supposed to be quite good as well, but Xfe does everything I need it to do.


**Web Browser: Swiftfox**

Installed the Swiftfox build specific to my CPU (a PIII), and after using [these tweaks]("http://www.freerepublic.com/focus/f-news/1299854/posts"), it is far quicker than Firefox. I gave Iceweasel a try, but I couldn't figure out how to change the Iceweasel's menu fonts to match my system font (Tahoma). Kahehakase had potential, but it froze twice during a span of 10 minutes worth of browsing. I'll definitely be keeping my eye on future builds of this.


**Instant Messaging: Gaim**

Gaim doesn't have as many features as aMSN, but the huge fonts in aMSN have kept me a Gaim user.


**Samba Network Browser: SMBC**

A console application that does everything I need. I don't think anything else is as lightweight as this.


**Text Editor: Leafpad**

I'd love to have something with PHP/HTML/CSS/JavaScript syntax highlighting, but I'm not about to install Java to run Jedit. I only ever edit code, so something like Abiword or OpenOffice is completely superfluous.


Something I would like to find is a lightweight archive manager that can handle various compression formats. Currently, I have Xarchiver and the command-line rar/unrar tools installed.

Thanks in advance for any suggestions.

---

### Post by tkjacobsen on 2007-04-04
> **VileTimes said:**
> 
**Text Editor: Leafpad**

I'd love to have something with PHP/HTML/CSS/JavaScript syntax highlighting, but I'm not about to install Java to run Jedit. I only ever edit code, so something like Abiword or OpenOffice is completely superfluous.


Try nedit. It has good code highlighting and is in the reops.

---

### Post by VileTimes on 2007-04-04
> **tkjacobsen said:**
> Try nedit. It has good code highlighting and is in the reops.

Thanks for the suggestion. I installed nedit via aptitude from the Ubuntu repositories and got this error:

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Serial number of failed request:  291
  Current serial number in output stream:  301

```

So I downloaded the [_nedit 5.5_]("ftp://anonymous:email%40notset%2Ecom@ftp.fu-berlin.de/unix/editors/nedit/v5_5/executables/nedit-5.5-Linux-x86.tar.gz") executable from [_nedit.org_]("http://nedit.org/"). The application worked until I tried to open an existing file with "Open...", at which point it crashed with the cryptic statement:

```

Segmentation fault

```

Oh well. Most unfortunate because it certainly had potential.

---

### Post by johnc4510 on 2007-04-04
I don't need the blot of Open Office. The most I need is a word processing program, so I use abiword. It is very fast and launches in seconds.

---

### Post by Nils Olav on 2007-04-04
links2 in graphical mode is pretty light (and graphical!).

---

### Post by DoctorMO on 2007-04-04
why arn't you using vi or kate or even gedit they all have syntax highlighting.

---

### Post by tbroderick on 2007-04-04
Second vi. Also try mc instead of xfe, bitlbee instead of gaim.

---

### Post by brentoboy on 2007-04-04
try fluxbuntu
[http://www.fluxbuntu.org/](http://www.fluxbuntu.org/)

Its significantly lighter than xubuntu.

there site looks temporarily down, but here is a torrent link
[http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.torrent](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.torrent)

---

### Post by IYY on 2007-04-04
Dillo is a very lightweight browser. Rox is a lighter alternative file manager (although XFCE's Thunar is fast as well). I'd suggest to just use as many command-line apps as possible; they're the fastest, and also tend to be better for some purposes. For example, I use vi to write LaTeX documents, and then view the final result with xdvi.

---

### Post by mips on 2007-04-04
Another vote for fluxbuntu or fluxbox. Much lighter than XFCE.

---

### Post by VileTimes on 2007-04-04
> **Nils Olav said:**
> links2 in graphical mode is pretty light (and graphical!).

Nice little browser. I'll still keep Swiftfox installed for more complex websites, but this is fine for most sites that I visit. Thanks!


[quote=DoctorMO]why arn't you using vi or kate or even gedit they all have syntax highlighting.[/quote]

I tried vi many moons ago and I found I was learning all of the keyboard shortcuts and what they all do instead of coding. As far as Kate and gedit are concerned, I don't see why I should install of those Gnome/KDE libraries for a simple text editor.


[quote=tbroderick]Also try mc instead of xfe, bitlbee instead of gaim[/quote]

Ah! Good ol' mc! Of course. And thanks for the heads-up on bitlbee. I never knew this existed. Very handy.


[quote=brentoboy]try fluxbuntu[/quote]

Will definitely try it on a clean install once Feisty Fawn is released.


Thanks for your suggestions, folks. Keep'em coming. I have some new keepers and it has only been a few short hours since this thread was posted.

Thanks again.

---

### Post by fuscia on 2007-04-04
i've found opera to be lighter and faster than swiftfox. leafpad is pretty quick. openbox and icewm were always much more responsive to me than xfce.

---

### Post by kerry_s on 2007-04-04
WM: Fluxbox rulz!

File Manager: emelfm, way more programmable the xfe, does archives with a click, does not require icons, small and fast.

Text Editor: Try geany if you want pretty, just turn off, all the settings you don't want to see.

Burner: graveman

---

### Post by ynnhoj on 2007-04-04
i think dillo and rox have both been mentioned, but i'll recommend them again anyways.  dillo is great; you can keep swiftfox (or opera?) around for when you need certain sites to display properly, but you'll get all the content just fine with dillo (and i think the installation of a few patches can help quite a bit).  rox takes some getting used to, but after a while it'll grow on you.

i'll also second the recommendation to find command-line solutions.  vi is great, and it'll do everything you need it to i'm sure.  midnight commander could come in handy.  if you need a bittorrent client, i really really like rtorrent..

a lighter window manager would also help out, though i'm sure you can get by okay with xfce.  i guess that's yer call.

---

### Post by reacocard on 2007-04-04
I second the suggestion for geany. It's very light and works beautifully for code editing. PCManFM is awesome, and looks better than XFE.

---

### Post by brentoboy on 2007-04-04
the folks at Damn Small Linux are devoted to fast light stuff.
Here is the list of apps on thier liveCD:
[http://damnsmalllinux.org/applications.html](http://damnsmalllinux.org/applications.html)

---

### Post by VileTimes on 2007-04-04
More excellent suggestions.

I took a look at emelFM and it would replace xfm on my system however, considering how ugly the fonts are (why don't these lightweight apps use my system defined font?), I may as well stick with MC. However...

[quote=reacocard]PCManFM is awesome, and looks better than XFE.[/quote]

Agreed. Whatever "performance loss" I might experience is greatly made up for in functionality.


[quote=reacocard]I second the suggestion for geany. It's very light and works beautifully for code editing.[/quote]

Wow! Thanks to you and kerry_s for the tip. Exactly what I was looking for.


I'll also have to take a closer look at Dillo. I played around with DamnSmallLinux for a while and it left me a little cold, although I never did look into the plug-ins...

---

### Post by icheyne on 2007-04-05
Some excellent light apps here:

[http://snurl.com/gunnix](http://snurl.com/gunnix)

---

### Post by Mateo on 2007-04-05
anyone know of a lightweight alternative to tomboy?

---

### Post by graabein on 2007-04-05
The [Xubuntu wiki]("https://wiki.ubuntu.com/Xubuntu/ProposedPackages") has a very handy list.

---

### Post by tbroderick on 2007-04-05
> **Mateo said:**
> anyone know of a lightweight alternative to tomboy?

hnb

---

### Post by DJiNN on 2007-04-05
> **tbroderick said:**
> hnb

Is that in the repos?

---

### Post by Mateo on 2007-04-05
anyone know of a lightweight browser that has tabs, but isn't depedant on mozilla/firefox?

---

### Post by Nils Olav on 2007-04-05
> **Mateo said:**
> anyone know of a lightweight browser that has tabs, but isn't depedant on mozilla/firefox?

links hacked but I wouldn't recommend it.

---

### Post by Mateo on 2007-04-05
i meant a graphical browser. I already use elinks for a CLI browser ;)

---

### Post by Nils Olav on 2007-04-05
> **Mateo said:**
> i meant a graphical browser. I already use elinks for a CLI browser ;)

Actually it is a graphical browser.

---

### Post by tbroderick on 2007-04-05
> **DJiNN said:**
> Is that in the repos?

Yes.

---

### Post by DJiNN on 2007-04-05
> **tbroderick said:**
> Yes.

Thanks tbroderick. :)

---

### Post by VileTimes on 2007-04-07
Well, I'm sold.

I bit the bullet and eliminated XFCE4 from my humble laptop and installed Fluxbox and Rox Filer. It took a day to get everything configured, but I most certainly do not regret taking the time. Everything looks great and most importantly, my Tecra 8100 is moving faster than ever.

The whole experience led me to understand what a desktop is really for.

A desktop is meant to deliver applications in X as fast and efficiently as possible. If the desktop software takes up too much RAM or CPU cycles, it is hindering the efficiency of the applications people rely on to get through the day. Gnome and KDE might look and act "sweet", but what point do they serve if all of your apps run slower?

Ubuntu has done great things in bringing Linux to people that would never have considered it an option as a primary OS (heck, I'm one of them). Once one gets over the Windows-to-Linux "culture shock", however, (s)he can do away with desktop bloat and focus the system's resources on what allows us to be productive: the applications we use.

Thanks again folks. Fluxbox and Rox is going to be installed on all of the computers I have, no matter how fast/powerful they might be.

---

### Post by Onyros on 2007-04-07
Fluxbox is great, indeed! Very good choice, mate! Did you get the hang of the automatic tabbing, yet? It's THE killer feature for Fluxbox. That and the fact that you can group any application with whichever app you want with tabs, as well.

As for Rox-Filer, please do take a look at PCManFM. You don't have to trade in functionality for speed with that. You won't notice the speed difference and PCManFM is way more functional than Rox (at least in my opinion, but I suppose I'm not alone there).

---

### Post by graabein on 2007-04-07
**PCManFM** is great. I use that instead of Thunar on Xfce. 

What do you guys use for **searching** and **rss feeds**?

---

### Post by reacocard on 2007-04-07
> **graabein said:**
> **PCManFM** is great. I use that instead of Thunar on Xfce. 

What do you guys use for **searching** and **rss feeds**?

Tracker is great for search, takes a mere 8MB of RAM.

For RSS, Google Reader. Why bother installing an app when you can do it within your browser? :D

---

### Post by moore.bryan on 2007-04-11
[I]my top 5 lightweight apps:
1. openbox (hands-down for me; tried all the others and hated them)
2. xfe (ugly, but i believe nothing is lighter)
3. sylpheed
4. aterm 
5. feh

[/I]

---

### Post by tbroderick on 2007-04-11
> **moore.bryan said:**
> [I]my top 5 lightweight apps:
1. dwm (hands-down for me; tried all the others and hated them)
2. mc (ugly, but i believe nothing is lighter)
3. mutt
4. urxvt 
5. feh
[/I]

fixed it for you :D

---

### Post by moore.bryan on 2007-04-11
[I]that's nothing but a low-down, dirty trick.
:biggrin:

and lightweight doesn't mean no-weight... 
[/I]

---

### Post by spupy on 2007-08-12
If you use Rox as desktop manager (not sure if thats what its called, it gives you desktop with icons), its lightning fast and lightweight.

Thru the 0install system there are some light apps for rox[desktop] which are pretty good too. One of them is a very simplistic archiver - you just drop files on its icon and it does the  job.

For tomboy replacement i would recommend xpad (uses gtk).

---

### Post by quixotic-cynic on 2007-09-03
> **Mateo said:**
> anyone know of a lightweight alternative to tomboy?

didiwiki works as a lightweight alternative to tomboy (but it is not exactly how I would like it)

wikidpad is quite good (python based) with fewer dependencies but you will have to get the binaries off the website

---

### Post by thisllub on 2007-09-03
> **VileTimes said:**
> 
I tried vi many moons ago and I found I was learning all of the keyboard shortcuts and what they all do instead of coding. 


Learn a dozen keystrokes and you have the best editor. 

Only this year have I taken the trouble to learn it and there really is nothing as good.
I even cut and paste into word processors now.

---

### Post by chris4585 on 2008-01-29
> **graabein said:**
> **PCManFM** is great. I use that instead of Thunar on Xfce. 

What do you guys use for **searching** and **rss feeds**?

i like beagle search tool, but... catfish is good too, i prefer beagle even though it uses more ram but for a light search tool go with catfish

---

### Post by kartal on 2009-10-30
I use Gnome Commander as dual pane file browser. I like Krusader but it is quite slow compared to GC.

---

