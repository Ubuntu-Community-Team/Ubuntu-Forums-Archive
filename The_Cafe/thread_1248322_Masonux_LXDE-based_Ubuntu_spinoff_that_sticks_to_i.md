---
title: "Masonux: LXDE-based Ubuntu spinoff that sticks to its roots"
date: 2009-08-24
forum: The Cafe
---

### Post by earthpigg on 2009-08-24
[Last Updated [COLOR="Red"]June 18, 2010[/COLOR]. Scroll down to read.]

Hello,

I'd like to share with you folks a project I have been working on, and maybe get some feedback.

[Masonux]("http://sites.google.com/site/masonux/"). Current version is 9.04-20090917.

Website is [http://sites.google.com/site/masonux/]("http://sites.google.com/site/masonux/")

256 mb of RAM is required for the *graphical installer* to work. 

Any i386-architecture CPU manufactured in the last decade or so is fine. 

2 gb of hard drive space will be plenty.

Older computers, netbooks, thumb drives, and any computer with a low tolerance for bloat: I am looking at you.

***For systems with less than 256 mb of RAM***, see the notes to myself page at the [website]("http://sites.google.com/site/masonux/") for install directions. (note as of 13 November 2009: that page is currently a work in progress as i am working on the 9.10 release. do not attempt to use the notes to myself as a how-to guide right now.)

I'll toss in some copypasta from the [website]("http://sites.google.com/site/masonux/") here:

>     * **LXDE**. LXDE is somewhat of a new kid on the block, but quickly gaining popularity. Here, and here are a few articles on LXDE written by third parties.

    * **Lightweight**. The heaviest part of Masonux is the installer. After it is installed, that 256mb of RAM will be plenty. A fresh install of Masonux uses about 1 gb of hard drive space and 65 mb of RAM at boot.

    * **Great to build up from**. Some people find it easier to build up to exactly what they want than to strip away bloat they don't want. This is great for people that prefer building something to suit their needs over tearing something down to suit their needs.

    * **Sticks to its roots**. Masonux uses unmodified Ubuntu packages and the default software repositories. Except for the desktop environment, Masonux very much is Ubuntu. Things like the Ubuntu "USB Startup Disk Creator" work flawlessly with it.

    * **Self-reliance**. One-man distributions of GNU/Linux pop up all the time. Because I have included the entire development model in the notes to myself, you yourself can recreate exactly what I have done incredibly easily should I fall off the earth tomorrow.

    * **Easy Networking**. The outstanding network applet included Ubuntu does not work by default with LXDE, but it _**does**_ work with LXDE in Masonux. This single small modification to a single configuration file, which is well documented in the notes to myself, is the only place where I modified a default setting.

The "blue" screenshot attached shows memory and hard drive usage on a fresh install of Masonux on the first boot.

The "pink" one shows the default Ubuntu wireless networking in action in LXDE - something that, as far as i know, is completely unique to this project. connecting via command line sucks, so instead of learning how to do it I learned to make nm-applet work in LXDE. This screenshot also shows that LXDE, after about 5 minutes of work, can look quite nice!

There really isn't _**that**_ much to this project at all -- please see the notes to myself page at the [website]("http://sites.google.com/site/masonux/") linked above if you would like to know exactly how this is put together.

What I would like to humbly request from the community:
-Any feedback would be greatly appreciated. :D Technical advice as well.
-Let me know how it runs on your machine! I can test in VM myself, but I only have a few computers laying around that I can actually install it on as the primary operating system.
-If anyone would like to help seed, it would be appreciated.



[digg it.]("http://digg.com/linux_unix/Masonux_Ubuntu_LXDE_spinoff_that_sticks_close_to_its_roots")


[SIZE="6"]UPDATES TO FOLLOW[/SIZE]

[COLOR="Red"]**_Project Ending:_**[/COLOR]
June 18, 2010

The niche once filled by Masonux is no longer a niche, and thus I've decided that Masonux no longer has a need to continue. It's been fun folks, and thank you for your support.

Check out Lubuntu, LXDE Mint, Remastersys LXDE Lite, and Peppermint for some other distros that use LXDE. 

[COLOR="Red"]**_Announcement relating to Masonux 10.04:_**[/COLOR]
May 16, 2010

I'm still a college student, for those unaware. One more week of lecture, and then Finals week. Once that is done, my little brother whom I haven't seen in a while is coming out to visit. Once that is done, summer school starts for me... Only taking one class, though.

My Agenda:
-Re-evaluate Lubuntu and the Linux Mint LXDE spin, and see if Masonux still needs to even exist. Compare hard drive, ram, and CPU usage on identical virtual machines.
-If it looks to me like Masonux still needs to exist, I'll get to work in earnest as my schedule allows.

If anyone wants to look at the [notes]("http://sites.google.com/site/masonux/home/notes-to-myself") from the 9.10 cut and start experimenting with 10.04, please let me know about any quirks you discover and if you were able to find workarounds.

-------------------------------------------------

1 December 2009....

hi,

I released [Masonux 9.10 beta2]("http://sites.google.com/site/masonux/news") today. It has some issues, you can read about them there.

Good news, though:

I updated the [Notes to Myself]("http://sites.google.com/site/masonux/home/notes-to-myself") page, so people that want to can now use that as a how-to guide to get a funcitonal LXDE/Ubuntu 9.10 desktop identical to Masonux onto a system with a wired internet connection.

It includes covering how to [make your own metapackage]("http://sites.google.com/site/masonux/home/notes-to-myself/metapackage") so you can remove things listed in the lxde metapackage without putting yourself in a situation wherein 'sudo apt-get autoremove' breaks your system -- this can ***also*** work if you want to get rid of some stuff included in ubuntu-desktop without borking your system.

As always, the content of the website aside from the software itself is licenced under the [WTFPL]("http://en.wikipedia.org/wiki/WTFPL").

-------------------------------------------------

9.10 Beta1 announcement to follow.

Hello,

[COLOR="Blue"][SIZE="3"]I'm happy to announce the first (and potentially only) Beta of Masonux 9.10.[/SIZE][/COLOR]

[http://dl.dropbox.com/u/1832211/masonux-9.10-beta1-i386.iso](http://dl.dropbox.com/u/1832211/masonux-9.10-beta1-i386.iso)

Notes:

-I am calling this a beta. That means do not use this in a production environment. I am asking the community to do me the favor of installing it in a VM or on extra non-critical computers and giving me feedback or advice - Especially in terms of hardware support when compared to Ubuntu/Masonux 9.04, and if you find a working solution to 9.10-related regressions, please share them.

-I decided that the "-20090821" method of distinguishing version is a bit... awkward. Now, releases will be numbered as such: "Masonux 9.10.1". I am calling this release "Masonux 9.10 Beta1" in my head. It may or may not be re-released as "Masonux 9.10.1" in the future.

-Masonux has a new look, and a new desktop background thank's to the artistic contribution of a certain ubuntuforums.org community member.

-The .iso does not play nicely with Ubuntu's "USB Startup Disk Creator". It does work with unetbootin.

-The "Install" icon on the desktop seems not to function. Entering "ubiquity" in a terminal works.

-There is currently no power manager aside from LXDE's native "battery monitor" panel applet.

-The current NetworkManager doesn't seem to like to place nicely outside of GNOME. The workaround I used for previous releases no longer works. Wicd, the most popular alternative to NetworkManager is now being used. If anyone here is able to get NetworkManager to work in this release, please let me know how you did so.

-The hardware support regressions present in Ubuntu 9.10 also exist in this release. In the case of my own Dell Mini 9, I'm having connection problems. The wireless card is recognized as "eth1", and seems to get stuck at "Obtaining IP address..."

-I will periodically try a command line install and sudo apt-get update && sudo apt-get upgrade to see if hardware support of 9.10 improves over time. If it does, a new point-release of Masonux will be released so folks can get that better hardware support OOB. This will be done because I had folks claiming the 9.04 release of Masonux (that came in august) supported hardware out of the box that Ubuntu 9.04 did not support. The only possible reason for this is because Masonux 9.04 came out in August, and thus included four months worth of upstream package updates that Ubuntu 9.04 did not.

-lxmusic is installed by default. There is a very real chance it will not be included in the final release.

-Hard drive and RAM use on my test machine (Dell Mini 9) remain about the same. 1gb and 65mb at first boot.

-Following Ubuntu's lead, empathy has replaced pidgin. Likewise, if Ubuntu where to replace Firefox with Midori - I would replace Firefox with Midori in my release. I have no love or dislike for empathy over pidgin, I am merely following Ubuntu's lead and will likely continue to do so. If you think my decision to follow Ubuntu's lead is mistaken, please share your opinion. If you think pidgin is better than empathy, please direct that part to the Ubuntu developers.

-The default sources.list (for now) looks like this:

```
deb http://geekconnection.org/remastersys/repository karmic/
deb http://mirrors.us.kernel.org/ubuntu/ karmic main restricted universe multiverse
```

you will need to run sudo apt-get update prior to installing additional packages, and if you want to tailor the menu.list to suit your needs you can use this tool to do so. I went with mirrors.us.kernel.org to do my part to lighten the load on Ubuntu's main US servers.

---

### Post by ugm6hr on 2009-08-24
It was not that long ago that this would have served me perfectly, but I have since disposed of that old laptop.

Looks like a worthwhile project...  I am sure there are users who would agree it simplifies using LXDE on Ubuntu.

---

### Post by HappinessNow on 2009-08-24
> **earthpigg said:**
> Hello,

I'd like to share with you folks a project I have been working on, and maybe get some feedback.

[Masonux]("http://sites.google.com/site/masonux/"). Current version is 9.04-20090821.

Website is [http://sites.google.com/site/masonux/](http://sites.google.com/site/masonux/)

I'll toss in some copypasta from the website here:



The two screenshots attached show memory and hard drive usage on a fresh install of Masonux on the first boot.

There really isn't much to this project at all -- please see the "[notes to myself]("http://sites.google.com/site/masonux/home/notes-to-myself")" page at the website linked above if you would like to know exactly how this is put together.

What I would like to humbly request from the community:
-Should i continue this project publicly, or simply remake it for myself every release?
-Any other feedback would be greatly appreciated. :D Technical advice as well.
-Let me know how it runs on your machine! I can test in VM myself, but I only have a few computers laying around that I can actually install it on as the primary operating system.
-If anyone would like to help seed, it would be appreciated. Right now, its just me at a paltry 160kb/s.
-If anyone would like to host the .iso file for direct download, that would be even more appreciated. If you like, I'll use _*your*_ google adsense stuff on the side bar while I am using your hosting services. It doesn't get much more low-budget than this project, so that is all I have to offer at present.

I was hoping for a Linux distro for the [FreeMasons]("http://en.wikipedia.org/wiki/Freemasonry")!

---

### Post by CJ Master on 2009-08-24
Very cool, remember hearing about it a few days ago. I'll look at your site.

---

### Post by OutOfReach on 2009-08-24
Very nice, I must check this out. The low memory usage really appeals to me

---

### Post by graabein on 2009-08-24
Please make the default look pretty while you're at it -- fonts, openbox theme and colours. Default LXDE and Ubuntu should be easy to outdo! ):P

Good luck with the project! I might use it on an old box I've got stored away at my parents house when it's time to upgrade Ubuntu.

---

### Post by mrgnash on 2009-08-24
Good move. I use a tiling window manager myself (Wmii), but LXDE is really cool for a stacking manager (Openbox) with a DE and anything that helps more people discover this very hardware-tolerant DE/WM is great :)

---

### Post by XubuRoxMySox on 2009-08-24
I built my own too, like you did (but yours looks nicer!), from a minimal Ubuntu installation plus LXDE and my favorite apps. I solved the network problem just by using wicd instead of the native network manager. 

Nice job with Masonux!

-Robin

---

### Post by kerry_s on 2009-08-24
is it live or just a installer?

---

### Post by Mighty_Joe on 2009-08-24
> **kerry_s said:**
> is it live or just a installer?

The page Mason linked to above mentions a Live CD.
Good luck Mason.  I'm a fan of CrunchBang for low-spec computers and heard good things recently about LXDE.  I'll give your distro a spin.

---

### Post by jaxxstorm on 2009-08-24
I don't understand the need for editing of nm-applet. It worked fine when I added it to Icebuntu

---

### Post by CJ Master on 2009-08-24
Here's a mirror for it:

[http://dl.getdropbox.com/u/1818534/masonux-9.04-20090821-i386.iso](http://dl.getdropbox.com/u/1818534/masonux-9.04-20090821-i386.iso)

---

### Post by Bölvaður on 2009-08-24
> **CJ Master said:**
> Here's a mirror for it:

[http://dl.getdropbox.com/u/1818534/masonux-9.04-20090821-i386.iso](http://dl.getdropbox.com/u/1818534/masonux-9.04-20090821-i386.iso)

the torrent has pretty good download even though that atm we are only 3 uploading

---

### Post by earthpigg on 2009-08-24
thanks for the feedback and encouragement! i wasn't really sure how this would be received by the community -- especially since i wasn't hosting source code (which i have never even seen...). i wasn't sure if my method/justification would pass public scrutiny.

> is it live or just a installer?

Just like Ubuntu, its a LiveCD with an install button on the desktop. :)

> I'm a fan of CrunchBang for low-spec computers


that is actually how this started. i didn't like how #!'s menu items did not update, and i did not like all the extra stuff included in #! by default. i added lxpanel and started stripping things away, tweaking here and there.... i stopped and just started from scratch with the mini.iso.

> I don't understand the need for editing of nm-applet. It worked fine when I added it to Icebuntu

cat /etc/xdg/autostart/nm-applet.desktop
```
[Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet --sm-disable
Terminal=false
Type=Application
_***#OnlyShowIn=GNOME;XFCE;***_
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
```

by default, that line is not commented out. maybe iceWM does it when it installs from the repos? lxde does not.

> Here's a mirror for it:

thanks a ton, CJ Master!! ill update the website right now, since apparently TPB is having issues...

> the torrent has pretty good download even though that atm we are only 3 uploading

i think there is some Swedish drama affecting the tracker i picked somewhat at random, at this very moment: [http://torrentfreak.com/the-pirate-bay-taken-offline-by-swedish-authorities-090824/](http://torrentfreak.com/the-pirate-bay-taken-offline-by-swedish-authorities-090824/)

ill get on that right now -- unfortunately, that means those of you kind enough to help me seed will need to take a moment redirect your efforts :\

edit: new .torrent: [http://www.mininova.org/tor/2882335](http://www.mininova.org/tor/2882335)

also, updated the [website]("http://sites.google.com/site/masonux/home") to link to CJ Master's mirror.

---

### Post by CJ Master on 2009-08-24
> **earthpigg said:**
> 
thanks a ton, CJ Master!! ill update the website right now, since apparently TPB is having issues...

No problem, it appears the mirror came just in time before they tackled TPB. :)

I created a dropbox account just for it, I could you give you username/password for it if you'd like.

---

### Post by kerry_s on 2009-08-24
> Just like Ubuntu, its a LiveCD with an install button on the desktop. 

sounds good, i'll probably give it a go later, i'm short on usb keys right now, i haven't put a cd drive in my nettop yet. :)

---

### Post by Stan_1936 on 2009-08-24
> **earthpigg said:**
> ...i didn't like how #!'s menu items did not update, and i did not like all the extra stuff included in #! by default. i added lxpanel and started stripping things away, tweaking here and there.... i stopped and just started from scratch with the mini.iso.....

You got any more screenshots?

---

### Post by CJ Master on 2009-08-24
> **Stan_1936 said:**
> You got any more screenshots?

[http://lxde.org/image/tid/1](http://lxde.org/image/tid/1)

---

### Post by Stan_1936 on 2009-08-24
> **CJ Master said:**
> [http://lxde.org/image/tid/1](http://lxde.org/image/tid/1)

I'm talking about this distro specifically....not LXDE in general.

---

### Post by earthpigg on 2009-08-24
> I created a dropbox account just for it, I could you give you username/password for it if you'd like.

you aren't spending money out of your pocket *_just for this_* are you?!?!??

> I'm talking about this distro specifically....not LXDE in general.
from my site: > It does not contain any custom artwork, logos, or any other modifications to any of those packages beyond those made by Ubuntu

the screenshots he linked are accurate. but i see your point, perhaps i should add more screenshots.

---

### Post by CJ Master on 2009-08-24
> **earthpigg said:**
> you aren't spending money out of your pocket *_just for this_* are you?!?!??

Oh haha no, it's free to set up a 2GB dropbox account, and your iso is only around 300megs.

---

### Post by Stan_1936 on 2009-08-24
> **earthpigg said:**
> ...the screenshots he linked are accurate. but i see your point, perhaps i should add more screenshots.

Yeah!  People would want to see more **screenshots of this distro**...menus, terminal, a few of applications when running.  It's boring to keep looking ONLY at the Openbox website for Crunchbang screenshots....

---

### Post by graabein on 2009-08-25
> **mrgnash said:**
> Good move. I use a tiling window manager myself (Wmii), but LXDE is really cool for a stacking manager (Openbox) with a DE and anything that helps more people discover this very hardware-tolerant DE/WM is great :)

That's a great idea! **earthpigg** why don't you add wmii or another tiling WM as an extra session option? I'm sure more people would like to try it especially on low end computers.

Do you have any plans for the boot process? 

I really think you should put together a [better]("http://icculus.org/openbox/index.php/Openbox:Themes") [looking]("http://www.box-look.org/index.php?xcontentmode=7402") theme than the default LXDE and Ubuntu. 

And remember to share the code :D

---

### Post by CJ Master on 2009-08-25
> **graabein said:**
> That's a great idea! **earthpigg** why don't you add wmii or another tiling WM as an extra session option? I'm sure more people would like to try it especially on low end computers.

Do you have any plans for the boot process? 

I really think you should put together a [better]("http://icculus.org/openbox/index.php/Openbox:Themes") [looking]("http://www.box-look.org/index.php?xcontentmode=7402") theme than the default LXDE and Ubuntu. 

And remember to share the code :D

Great idea, and why not Shiki Colors [Openbox edition?](http://www.box-look.org/content/show.php/Shiki%2BDark+Colors?content=105711) Familiar to many, awesome to all. :)

By the way, I burned a LiveCD and tried it out, and it was snappy! I'd use that if I had an old computer (unfortunately I don't. All my computers are rather awesome. :P )

---

### Post by earthpigg on 2009-08-25
i may look into art and theme stuff at a later date - to be honest, i'm a function over fashon kind of guy so didn't really even consider that until you mentioned it. 

given the limited scope of this project, any theme i use would need to be from the repos, and i'd need to find a way to enable that theme over the default via the command line so it could be properly documented in a way that -- if/when i learn bash scripting -- will allow me to make a simple installer for systems with less than 256 mb of RAM.

as far as alternative WM's, i'm not as familiar as some. instead of me picking 500 random WM's from the repos and trying them all, would anyone be willing to look at the high quality options, install a few, run them, and show me "free -m" output, and tell me how they perform on their low-end CPU? i have nothing that old sitting around and dont know how to underclock, so i cannot test myself. :\

> Do you have any plans for the boot process? 

that is beyond the scope of my knowledge at present, to be honest. I think you may be greatly overestimating my linux-fu, friend. enabling/disabling services/daemons and kernel modules in *the-distro-who's-probability-of-being-mentioned-is-approaching-1-as-we-speak* is easy as pie as we all know, but i haven't yet figured out where the hell and how it is done in debian/ubuntu via the command line with its 5 million config files scattered all over the place.

i dont mean to be critical of debian. i am determined to stick to debian/ubuntu base for several dozen outstanding reasons that we dont need to get into here as it would be preaching to the choir. :D

seriously though: i am no guru. check the '[notes to myself]("http://sites.google.com/site/masonux/home/notes-to-myself")'. the tools others have created are thus far making this project incredibly tolerant of my ignorance. as Ubuntu's boot time is decreased, Masonux's boot time will decrease.


edit: also, i did some work on the [web page]("http://sites.google.com/site/masonux/home"). feedback on that would also be appreciated.

---

### Post by TwiceOver on 2009-08-25
I'm thinking about trying this out on my Lenovo S10 netbook and noticed you had it running on a Dell mini 9?  Did you run into any problems?  Any other packages you need to get a laptop/netbook running?

---

### Post by snowpine on 2009-08-25
Hi Earthpigg, I agree with your intention to keep your project closely aligned with "vanilla" Ubuntu. Don't feel like you have to create new artwork or hack the boot scripts if that is not your expertise. Your project is a good "short cut" for users who want a lightweight desktop, but are intimidated by a minimal install.

I am very happy with Fluxbuntu on this old laptop, but if I ever decide to switch, I just might check out Masonux. :)

---

### Post by earthpigg on 2009-08-25
> **TwiceOver said:**
> I'm thinking about trying this out on my Lenovo S10 netbook and noticed you had it running on a Dell mini 9?  Did you run into any problems?  Any other packages you need to get a laptop/netbook running?

i didn't run into any problems on my dell mini 9 or need to install any additional packages to get it up and running. that screenshot was taken in a hotel room, shortly after a fresh install. i dont think that netbook has ever been plugged into a wired internet connection, so wifi obviously hasn't given me problems :)

to the best of my understanding, if ubuntu supports the hardware than this will.

it runs fine with no additional packages added.

the netbook-oriented package that makes programs maximize when launched is 'maximus', if you want that.

the 'additional packages' page at the site also has a list of a few packages you can add to make the GUI a bit more like ubuntu's default interface, if you want that. the gnome panel with applications/places/system, the applications -> add/remove application app, and a few others.

im going to go add maximus to the list at the site right now, as a matter of fact.

edit: updated website to include maximus and lxlauncher - both outstanding tools for netbook ease-of-use.

---

### Post by Mighty_Joe on 2009-08-25
I did a full install (as opposed to a LiveCD type install) to a 1GB flash drive and booted up my laptop (HP/Compaq 8510p).  Typical Ubuntu install is over 2GB.  Wireless works and the GUI's snappy. Very nice.

---

### Post by CJ Master on 2009-08-25
Btw, when it asks you, don't use isolinux. Grub's usually is a better choice unless there's a specific reason you like isolinux.

---

### Post by graabein on 2009-08-26
Hi! I think the web page looks great. Clean simple and stylish. :) 

Regarding a default theme I was just trying to be helpful and make the distro stand out and get more attention. Maybe someone with more linux-fu than you and me both can help out?

Anyway here's a link to openbox themes from the universe repo:

[http://packages.ubuntu.com/jaunty/openbox-themes]("http://packages.ubuntu.com/jaunty/openbox-themes")

---

### Post by XubuRoxMySox on 2009-08-26
It's nice to see people working on "lightweight Ubuntu" that is *truly* lightweight -- what Xubuntu was aiming for at first I think.

There are other LXDE-based "Ubuntu Lite" projects under way as well (U-Lite and the Lubuntu project come to mind right away). It'll be nice to have several to choose from!

-Robin

---

### Post by earthpigg on 2009-08-26
graabein - i was referring to my weak linux-fo when it came to tweaking with the boot process. i'm going to take a look into taking some of the clutter off of the panel and maybe a different openbox theme. i think the default look of the panel hurts LXDE's default look much more than the default theme.

---

### Post by kk0sse54 on 2009-08-26
What does Masonux have to offer over Lubuntu, U-lite, or even Debian Lxde?

---

### Post by vrkalak on 2009-08-26
Ubuntu seems to like:  Gnome, KDE, Xfce and FluxBox . . . there 'is' more.

I have been looking into the 'other' WM ... like LXDE, e17 Environment and JWM, as well as, OpenBox.

I'll definitely checkout your distro ... Masonux

---

### Post by Plumtreed on 2009-08-27
Masonux is very good, fast, clean and tidy. The best part is that I know how to get to everything.

I recently tried PCLXDE, an offshoot of PCLinoxos, but I think I prefer your Ubuntu origins. They used Midori as a browser and everything worked even had all the video access working from the live CD.

I'm looking forward to future developments and thanks:P

---

### Post by verbertus on 2009-08-27
Downloading Masonux is not easy.

The torrent seems no longer available and the download from Dropbox is very slow: I now have 4% downloaded and still 2 hours 50 minutes to go. (speed about 28kb/sec...)

Isn't there any way to offer Christopher (earthpigg) a better host? Any ideas from the experts :) ? Rapidshare??

---

### Post by ungrus on 2009-08-27
Hi!!

earthpigg, masonux is great idea!

I donload it and try to install, but it seems that the iso download with an error and i can't install (burn 3 cd's and try in VBox, same error).
I don't try to download again because i have a very slow connection (5 hours to down the iso), so, i follow you tutorial and made an iso by myself! and it's work great!
The only diference it's that i use an ubuntu alternate install cd that i already have, and include the hardware manager for easy install the driver for the wifi because i don't have wired network, and replace firefox for opera just because it's faster.

Thanxs again eartpigg!!!! and congratulations!!!!!

---

### Post by verbertus on 2009-08-27
Hi ungus,

Same problem here. The iso download is not correct or usable.
I hope earthpigg finds a better host soon!

---

### Post by CJ Master on 2009-08-27
> **verbertus said:**
> Hi ungus,

Same problem here. The iso download is not correct or usable.
I hope earthpigg finds a better host soon!

The mirror isn't working correctly? I'll get to work on it, thanks for telling me.

---

### Post by earthpigg on 2009-08-27
> **CJ Master said:**
> The mirror isn't working correctly? I'll get to work on it, thanks for telling me.

mirror 1 is your dropbox CJ, mirror 2 is mine. 

the guy that runs [this]("http://www.utopiaforums.com/boardroot") small-time niche site on his own personal server (i think) is offering me hosting services for $0... that website usually loads very fast and has good uptime, so my assumption is that a direct download from same will be rather fast and reliable.

the thing is: he is doing me a huge favor for $0, so it would not be polite to be on his case and rush him, etc.

regarding the torrent... it was going *_great_* until TPB went down. we had like 4 seeders and quite a few peers going. even though TPB back up, something still seems to be out of whack with the popular trackers. maybe the workload of the #1 tracker in the world got shifted to other trackers that weren't prepared? not sure.

there are some things about torrents, i think, that i am still kind of iffy on. clients seem to do things automatically, which is annoying. i made a new torrent with 5 trackers, including [linuxtracker]("http://linuxtracker.org/"). vuze seems to be playing nice with it and the trackers, not changing it to "dhc" or whatever.

im going to upload that torrent to the website. its the exact same .iso, so anyone that already has it should be able to help me seed by putting that .iso in the downloads folder and opening the torrent in seed mode.

anyone want to give me a hand, and hopefully we can get a good .torrent swarm going again?

i may not have a chance to work on this stuff to much for the next few days starting tonight, 27 august. girlfriend's father died a few nights ago in a motorcycle accident, so i'll be spending the weekend with her and her family several hours away. 

i may only have access to my netbook with its tiny keyboard for the next 3 days or so, and may not even have net access. ill be bringing a bootable thumb drive with masonux (:D ) installed on it along with the .iso file.

if i do then from there, i should still be able to find time to update the website's direct download a better host than dropbox free account presents itself, and if there is some fundamental thing about torrents that i am missing (never created a torrent before) that someone else can fix by creating a new torrent or whatever, i should be able to update the website to point to that torrent as well.

---

### Post by verbertus on 2009-08-27
Hi CJ Master,

Thanks for looking into this.

After the torrent-way proved impossible, I tried both mirrors. Just now I discovered the download finished at 168MB in stead of 325MB, both times. Maybe Dropbox sets this maximum, after a certain number of downloads?

Thanks earthpigg for your explanation and for your efforts to get the downloading going.
What would be the cost of a quality download site?
I would be willing to donate some money, if that would help.

Best regards

---

### Post by CJ Master on 2009-08-28
All that want to download,

I'm very perplexed, as I just fully downloaded (all of) it, at a speed of 1.5 MB/s to boot! I'm unsure why it's not working for you, but I recommend that you [contact dropbox](mailto:support@getdropbox.com) for support, as I cannot help you any further. If problems persist then I will attempt to find another mirror.

---

### Post by verbertus on 2009-08-28
Hi CJ Master,

It's a known problem. 
The Dropbox forum is full of complaints about uploading/downloading speeds. [*dropbox-forum-search*]("http://forums.getdropbox.com/search.php?search=download+speed")

I installed the Dropbox utility, but that does not speed up the downloading, still hovering around 28kb/sec.

So, either you are lucky, living in a part of the US with a fast connection to Dropbox (I'm in Europe), or the speed you saw was because what you did is syncing instead of real downloading. (Just thinking out loud.)

I can live with the slow download speed, what worries me is that the download stopped after 1.5 hours, when only about half the iso was downloaded.

I would be willing to mirror the iso on a reliable server, but for that I need to have it first :rolleyes:

Thanks again

---

### Post by verbertus on 2009-08-28
I might have spoken too soon,,

Download went perfect now about 114KB/sec 
Writing this from the live CD,
First impressions are good :)

---

### Post by TwiceOver on 2009-08-28
Installed in about 7 minutes!  WOW!  Recognized my wifi right out of the "box".

Running this on my Lenovo s10e netbook with Atom 1.6, 2gb Ram, 32gb Patriot SSD.  Boot time is no faster than Ubuntu, but I really wasn't expecting it to be much better in that arena.  Apps load almost immediately, except for FF3 which has always been slow to load on any Ubuntu system.

Only issue is that I'm missing the battery manager stuff...

---

### Post by earthpigg on 2009-08-28
> **TwiceOver said:**
> 
Only issue is that I'm missing the battery manager stuff...

thanks for giving it a shot, TwiceOver! :D

regarding the battery manager, want to give gnome power manager a try?
```

sudo apt-get install gnome-power-manager
sudo cp /etc/xdg/autostart/gnome-power-manager.desktop /etc/xdg/autostart/gnome-power-manager.desktop.backup
sudo sed -i 's/OnlyShowIn/#OnlyShowIn/g' /etc/xdg/autostart/gnome-power-manager.desktop
```

log out/back in for changes to take effect.

first line installs gnome-power-manager.
2nd backs its .desktop file up.
3rd comments out the line in its .desktop file telling it to only run its applet in gnome and xfce.


question:

should this be included by default, or merely be included in the [additional packages]("http://sites.google.com/site/masonux/home/ease-of-use") page?

---

### Post by CJ Master on 2009-08-28
Ok, I'm hosting another mirror on my server. It may be a bit slow, however (100kbs) [here](http://admin.masonux.cjmaster.operaunite.com/file_sharing/content/masonux-9.04-20090821-i386.iso). I will attempt to keep my computer on at all times, however downtime will happen.

---

### Post by TwiceOver on 2009-08-29
> **earthpigg said:**
> thanks for giving it a shot, TwiceOver! :D

regarding the battery manager, want to give gnome power manager a try?
```

sudo apt-get install gnome-power-manager
sudo cp /etc/xdg/autostart/gnome-power-manager.desktop /etc/xdg/autostart/gnome-power-manager.desktop.backup
sudo sed -i 's/OnlyShowIn/#OnlyShowIn/g' /etc/xdg/autostart/gnome-power-manager.desktop
```

log out/back in for changes to take effect.

first line installs gnome-power-manager.
2nd backs its .desktop file up.
3rd comments out the line in its .desktop file telling it to only run its applet in gnome and xfce.


question:

should this be included by default, or merely be included in the [additional packages]("http://sites.google.com/site/masonux/home/ease-of-use") page?

Might want to double check that.  After running those lines I Gnome-Power-Manager didn't start automatically and I lost nm-applet from running automatically.

I went back and edited the gnome-power-manager.desktop to comment out the "showonlyin" and that got gpm to load automatically.

Unfortunately nm-applet still won't load.  I can run it manually and all is good, but it won't start on boot.

hrm.  Good stuff so far though.

---

### Post by Bölvaður on 2009-08-29
> **earthpigg said:**
> 

should this be included by default, or merely be included in the [additional packages]("http://sites.google.com/site/masonux/home/ease-of-use") page?

It should not be included in default.
But there could be benefits for having special deb metapackage for laptops, but as it is there isn't enough to put in it at the moment.

Just pit it in the additional packages and perhaps have apturl on the packagenames.

---

### Post by Jimleko211 on 2009-08-29
I downloaded the live CD, it downloaded in 2 minutes under mirror 2.  Will try it out once it's finished burning.

---

### Post by earthpigg on 2009-08-29
> Unfortunately nm-applet still won't load. I can run it manually and all is good, but it won't start on boot.

i looked over those commands, and i still dont see any typo! :( 

did you check if nm-applet.desktop still looks right?

bolvador: great idea about the .deb metapackage for laptops. actually, if i do that, it would include links that install each package (i think its just apt://packagename?), and a *netbook* metapackage that includes lxde's netbook launcher thingie.

edit: cj, updated site to add your 2nd mirror.

jimleko: if it downloaded in 2 min, there is a good chance it did not download entirely/correctly :\

---

### Post by CJ Master on 2009-08-29
By the way earthpigg, should I keep my mirror up or do you not need it any more? (The one hosted on my computer, not dropbox.)

---

### Post by Jose Catre-Vandis on 2009-08-29
Just installed in virtualbox

Some thoughts:

1. For a VB install build-essential and headers are required for making VBox additions, but I was surprised they weren't there by default?

2. Sound needs a GUI applet to allow "Mx" to become more accessible to the "masses"

3. Similarly a media player, mplayer from the repos would do for starters (audio and video)

4. Themewise, make it your own, at least some Masonux wallpaper ;). I am a brand hater, but can just about tolerate the default xubuntu background.

Must suggestions may go against your principles, which is fine :) I can cope with getting what is not there there, others might just walk away?

Good work, quick install and setup, easy ubuntu to use :)

---

### Post by Jimleko211 on 2009-08-29
> **earthpigg said:**
> 
jimleko: if it downloaded in 2 min, there is a good chance it did not download entirely/correctly :\
Not so.  It's now installed, working perfectly.

---

### Post by kerry_s on 2009-08-29
alright, i'm testing Masonux now.

my thoughts, it needs work. 
the bootloader, what can i say it needs help. 
wireless tools would have been nice. i have my firmware on usb so its easy to copy over & get on the net, i ended up copying the firmware to the live usb then rebooting just to get internet.
i think you should clean up synaptic a bit, everything shows up as local/obselete, clicking reload fixes that. remastersys you could do a local repo for "deb file:///extra/ /" very easy to do a local repo, google it.
i did have a problem with usb-creator, but thats not your fault, i blame usb-creator for not installing it's dependencies.
i think gparted would be nice on there to, you never know when you might need to format a drive to get your remastered system on.

well times up, jaunty gnomes finished downloading.

---

### Post by Jimleko211 on 2009-08-30
LXDE is a nice DE.  I wish it used something other than Openbox as a WM, but hey, what can you do?  It's functional, it recognizes my wireless card (which Ubuntu itself won't do unless I load the latest drivers from a svn manually), and it functions fast.

---

### Post by earthpigg on 2009-08-30
> **Jimleko211 said:**
> LXDE is a nice DE.  I wish it used something other than Openbox as a WM, but hey, what can you do?  It's functional, it recognizes my wireless card (which Ubuntu itself won't do unless I load the latest drivers from a svn manually), and it functions fast.

your wireless card being detected could have more to do with the official 9.04 .iso being put together several months ago and using an older kernel than masonux 9.04-_20090821_.

if you do a fresh install of ubuntu 9.04 and then immediately update and reboot, is your wireless picked up?

---

### Post by Jimleko211 on 2009-08-30
> **earthpigg said:**
> 
if you do a fresh install of ubuntu 9.04 and then immediately update and reboot, is your wireless picked up?
Maybe?  It's been a while.  I don't think so, since the only time I ever got it working was with the svn of madwifi.  I don't think I ever tried updating and then trying to connect, though.

---

### Post by RyconPayne on 2009-08-31
My wireless isn't recognized here, and it is in vanilla Ubuntu.  This makes me sad, because I really like the speed of this.  I'll see about the madwifi thing, but I think I'm just missing something obvious.

---

### Post by earthpigg on 2009-08-31
> **Jimleko211 said:**
> LXDE is a nice DE.  I wish it used something other than Openbox as a WM, but hey, what can you do?

install a different WM, of course :D

im playing around in compiz at the moment. 

'jockey-gtk' is the package that adds the 'hardware drivers' app that finds non-free drivers for your video card / wireless card / etc.

compizconfig-settings-manager, i am sure, will include all the dependencies required to get compiz up and running -- provided you can ***menu -> run -> 'compiz --replace'*** on your own :D



i see no reason why you couldn't install 'metacity' and then 'metacity --replace' if you wanted to to use metacity as your wm.

---

### Post by Jimleko211 on 2009-08-31
> **earthpigg said:**
> install a different WM, of course :D

im playing around in compiz at the moment. 

'jockey-gtk' is the package that adds the 'hardware drivers' app that finds non-free drivers for your video card / wireless card / etc.

compizconfig-settings-manager, i am sure, will include all the dependencies required to get compiz up and running -- provided you can ***menu -> run -> 'compiz --replace'*** on your own :D



i see no reason why you couldn't install 'metacity' and then 'metacity --replace' if you wanted to to use metacity as your wm.
Mmk, the next time I'm on my laptop with any time for tinkering, I'll look into it.  Thanks for the suggestion.

---

### Post by PolarBear on 2009-09-01
Thank you earthpigg! Masonux gave new life to my 256mb laptop :cool:):P

---

### Post by 1stbyte on 2009-09-03
I switched over to Masonux from CrunchBang#! and never look back! CrunchBang is pretty light distro, but Masonux is much lighter. Indeed, I find Masonux is very light and easy on my old pc and laptop. Everything works out of the box. There are rooms for improvement. 
First, If you want user to see how light it is, I think you should include conky to the desktop. I like CrunchBang because it tells me how memory I'm using now. 
Second, the artwork is sort of dated. I prefer understate elegance of CrunchBang's dark/black theme. It makes me focusing on the tasks at hand and not distracted by all fancy art work.
Last, there are too many text display (on boot and between sessions). Hide those messages.
I cannot wait for your next release.
Thanks!
[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by CJ Master on 2009-09-04
Oh Earth, just wanted to report that I generally have a couple people downloading it at the time, unfortuantly I have a very simple server so I can't tell how many downloads or anything like that.

I agree, please add conky. Conky really sets a distro apart.

---

### Post by XubuRoxMySox on 2009-09-04
You like Conky? *You* add it. No need to fill up the installation CD with software that isn't needed for the basic intended use. It's easy enough to add the extras you want. Masonux is sweet and minimal "as is" without getting bogged down with people's favorite applications.

Add this! 
Add this! 
Put this in!
It should have this too!

C'mon. You want it? Add it yourself. It's just a few mouse clicks for cryin' out loud.

Even the Lubuntu project has been briefly paralyzed by disagreement on what applications to include. It's silly! Let folks add the ones they want without having to remove a bunch of extra stuiff they don't need and don't want and won't use.

-Robin

---

### Post by 1stbyte on 2009-09-04
Of course, I added conky. My point is that if you want to set this gem distro apart, you need to show and convince user on the first impression. Desktop area is like your front yard to your home, you have to set the tone so that user don't have to guess. I do agree that the distro must keep the packages to the minimal.

---

### Post by earthpigg on 2009-09-04
i really appreciate the feedback, and im glad you like it PolarBear and 1syByte and others that havent posted :D

im sorry to dissapoint, but dixie said it better than i could have myself, folks.
> 
No need to fill up the installation CD with software that isn't needed for the basic intended use. It's easy enough to add the extras you want.

recall, folks, that i am not targeting this towards absolute Linux newbies.

the Lubuntu project is attempting to replicate the efforts of Xubuntu and Kubuntu, which is great and i wish them the best.

Unlike the massive teams of developers of L/X/K/Ubuntu, i assume Masonux users know how to install software, and i assume that you the end user know what your fav photo editing app, word processing app, etc -- ergo, i don't need to include it for you.

from the site:
> If you have never installed a GNU/Linux distribution successfully, I do not recommend that you attempt to install Masonux as your first unless it's on a machine you have sitting around currently not doing anything.



here is the direction i am going to take Masonux:
-new desktop background. maybe ill make it myself, but ill probably solicit volunteers and folks that enjoy doing that stuff. ill probably follow LXDE's lead and include three or four different colored backgrounds. blue, pink, green, purple.
-new default theme from among those included with openbox/lxde by default.
-a lot of the stuff on the panels either removed or moved around.
-possibly a netbook edition that comes with lxlauncher and maximus installed.


i may test some of that on my own, but the public next release will likely come with 9.10 (a month or so away). i will also be very interested in feedback regarding upgrading from 9.04 to 9.10 -- i am pretty sure it will work in theory, but we will see.

if there are point releases (9.04.1, 9.04.2, 9.10.1, etc) i may re-release accordingly.

---

### Post by Sporkman on 2009-09-04
> **dixiedancer said:**
> You like Conky? *You* add it. No need to fill up the installation CD with software that isn't needed for the basic intended use. It's easy enough to add the extras you want. Masonux is sweet and minimal "as is" without getting bogged down with people's favorite applications.

Add this! 
Add this! 
Put this in!
It should have this too!

C'mon. You want it? Add it yourself. It's just a few mouse clicks for cryin' out loud.

Even the Lubuntu project has been briefly paralyzed by disagreement on what applications to include. It's silly! Let folks add the ones they want without having to remove a bunch of extra stuiff they don't need and don't want and won't use.

-Robin

Why have distros at all, then?

---

### Post by earthpigg on 2009-09-05
> **Sporkman said:**
> Why have distros at all, then?

let's look at the spectrum of options, within the Ubuntu "meta-distribution", if you dont mind me pulling a word out of thin air and using it with the assumption that you will immediately know what i mean.

On one extreme, we have the Ubuntu CLI install that includes the Kernel, some GNU tools, some Debian package management stuff, and access to some gigantic software repositories available if you wish to use it.

Somewhere in the middle, we have vanilla Ubuntu that includes the above with GNOME and some great UI stuff.

Close to the other extreme, we have Ultimate Edition. All of the above, plus a whole bunch of stuff from the aforementioned gigantic repositories, additional repositories, and non-free software.

Masonux fits in close to the first extreme, no doubt. 

It's a ready-to-roll 'build it yourself' kit that assumes you have used GNU/Linux before but dont feel like mucking around in the command line every time you install a new system.


Would you presume to include a specific car stereo in a build-it-yourself car kit? how would you even know if those do-it-yourself-ers will ever even  use a music CD a single time during the entire lifetime of the car?

some will choose to plug their thumb drive in because they have an old one sitting around.
some will choose to use normal Music CDs because they think they are cool.
some will choose to use a DVD-RW with 50000 MP3 files on it.


do it yourself types clearly have no use of any 'standard' radio -- especially if it increases the cost (in the case of Masonux, 'cost' would be 'system requirements'.).


you want to use GIMP with Masonux? the tools to install it are provided, have at it.
you want to use Tux Paint with Masonux? the tools to install it are provided, have at it.


i am considering a bloated version of Masonux, due to the apparent user demand. the primary version will maintain the philosophy it currently has, and remain the first thing you see at the website.

"Masonux Bloated Edition" would include extra stuff, if i decide to make it. One word processor, one multimedia player, gparted, gnome's add/remove applications, maybe even non-free software such as Opera and ubuntu-restricted-extras.... and, perhaps, a huge sources.list that will give the user access to the latest builds of chrome, skype, opera, and every-damn-thing else under the sun all out of the box.

but does an ubuntu remix that competes with Ultimate Edition need to exist *based on and around **_LXDE_***?

would anyone use it?

---

### Post by 1stbyte on 2009-09-05
I'd not want the "bloat" edition of Masonux. There are bunch of those distro's, just take your pick. 
Instead, I think you should have a page like FAQ pointing people to programs/packages available by interests, like multimedia, graphics, game, servers or programming. 
I find your page for additional software very useful and wish that there are more.
Hey, earthpigg, I think you stick your original idea, "sticks to its roots". Keep it simple, keep it clean and keep it light (really light).

---

### Post by longtom on 2009-09-05
I like your simple and basic approach.  If anybody cannot install LXDE from a basic install, that's the way to go.

So the step from basic install and LXDE to Masonux is not a huge one, I guess.  However, it might get some people going who do not dare to tackle the basic install of Ubuntu.

And so another niche is filled - wonderful.  Keep it going.

---

### Post by earthpigg on 2009-09-05
thanks for the feedback, longtom and 1stbyte. also, your hippo is rad, longtom. i think i mentioned that in another thread weeks ago?

> I find your page for additional software very useful and wish that there are more.

if you where more specific about which 'more' you would like, i could add more to it :D

short of another '50 windows apps and their Free Software equivelants' list, of course.... i'd love to expand on the existing list, but don't know what other basic graphical interface-based operating system functionality and/or control tools user's would like.



is there a website that contains a good (but not awkwardly huge) list of 'mainstream' Linux graphical tools that is ***_not_*** centred around alternatives to Windows apps that i could reference or link to? i dont want to chase tail lights nor look like i am :D .... but i am also not a huge fan of re-inventing the wheel.

---

### Post by longtom on 2009-09-05
> **earthpigg said:**
>  your hippo is rad, longtom. 

**Pigmy**-hippo - please.  Hilda is very specific about this.  She is especially hammering on the weight aspect.  Women....all the same...:P

---

### Post by RealG187 on 2009-09-11
Would it work on Pentium I systems?

---

### Post by earthpigg on 2009-09-12
> **RealG187 said:**
> Would it work on Pentium I systems?

i don't have one around to test on, so i cannot say for certain.

i can say that there aren't to many background services that will be eating up CPU cycles.

i'd love for ***you ***to tell ***me ***if it runs on a P1, though, if you are up to it.

---

### Post by NormanFLinux on 2009-09-12
I think it would run on anything that ran Windows 95/98. LXDE would be a good replacement OS on a Pentium PC.

---

### Post by earthpigg on 2009-09-17
[SIZE="4"]Masonux 9.04-20090917 [released]("http://sites.google.com/site/masonux/news").[/SIZE]

There is no compelling reason to use this version if you already have a previous 9.04 release of Masonux. This is an incremental release that accomplishes two of the items on my To-Do List:

[LIST]
[*]Default lxpanel config - The default panel appearance now looks nice, instead of ugly.
[*]gnome-power-manager included by default
[/LIST]

Screenshot attached shows the new default panel appearance.

Remaining items on my To-Do list that will hopefully be implemented in 9.10:

[LIST]
[*]Desktop Background - Create a desktop background in 3 or 4 colors that includes the URL to this web page and maybe default LXDE keyboard shortcuts.
[*]Screenshots - Create a screenshots page and add to web page. If you have any, please email them to me!
[*]Forum - Keep bothering my associate until he finishes this.
[/LIST]

**If anyone creatively talented would like to create and contribute a desktop background, I would appreciate it and will credit you on the Masonux web page if you like.** I'd like to follow LXDE's precedent: 3 or 4 of essentially the exact same wallpaper, but in several colors... a blue version, red version, purple, green, etc.

---

### Post by Bölvaður on 2009-09-17
> **earthpigg said:**
> [SIZE="4"]gnome-power-manager included by default

I thought I made my self clear a month ago :D when I said having only things that are shared with all computers on the disk, have all the other stuff an option... Perhaps as a .deb metapackage on the desktop.

Btw I have an idea for a desktop background which Im going to do in few minutes when I find the camera. What do you think of having a profile of someones head (possibly with a shining light from 45° angle, which would be kind of above to right/left) and the background is what ever colour you wish.

*added*
never mind, the background looks worse than I thought.

---

### Post by NormanFLinux on 2009-09-17
LXDE is minimalist. There is no GUI utility for configuring the clock and there is no direct way to edit application icons.

---

### Post by RealG187 on 2009-09-17
I have a few questions:

* How do I connect to a Samba server, it seems to not be working out of the box
* How do I install a .deb package, when I double click one it opens it with the archiver program and not tries to install it

---

### Post by CJ Master on 2009-09-18
> **RealG187 said:**
> 
* How do I install a .deb package, when I double click one it opens it with the archiver program and not tries to install it

Right click it.

---

### Post by RealG187 on 2009-09-18
> **CJ Master said:**
> Right click it.Then what, I only see the archiver under the open with menu...

---

### Post by Bölvaður on 2009-09-18
> **RealG187 said:**
> * How do I install a .deb package, when I double click one it opens it with the archiver program and not tries to install it

```
cd /cdrom/hamm/hamm/binary/editors
**dpkg -i** vim_4.5-3**.deb**

```

---

### Post by NormanFLinux on 2009-09-18
Install Gdebi... it will install a deb. package with all needed dependencies taken care of.

---

### Post by earthpigg on 2009-09-18
> **RealG187 said:**
> I have a few questions:

* How do I connect to a Samba server, it seems to not be working out of the box
* How do I install a .deb package, when I double click one it opens it with the archiver program and not tries to install it

for the .deb, [website just updated]("http://sites.google.com/site/masonux/home/ease-of-use#TOC-Double-Click-to-Install-.deb-Files"):

> Double Click to Install .deb Files
After you install this package, you will be able to double click on .deb files to install them, just like vanilla Ubuntu.
package name: gdebi

for samba in Masonux: comparing my vanilla ubuntu sandbox install and my Masonux sandbox install, it appears these two packages that are **not** included in Masonux are included in Ubuntu, and come up when I search synaptic for "samba":

> python-smbc - Python bindings for Samba clients (libsmbclient): A module for using the Samba client API in Python programs.

nautilus-share - Nautilus extension to share folder using Samba: Nautilus Share allows you to quickly share a folder from
the GNOME Nautilus file manager without requiring root access.

from the [lxde wiki pcmanfm article]("http://wiki.lxde.org/en/PCManFM"): 

> What don't have (*sic*):

    * Don't have support for SAMBA, you can't use \\192.168.0.10 \\houselaptop or smb:\\houselaptop 

it looks like you will need to install a file manager other than pcmanfm for GUI samba support.  i'd go with nautilus, since you are already familiar. also add nautilus-share and python-smbc. would you (or someone else) mind testing and confirming this functionality works with those three packages installed?

if you wanted to, you could probably mount the remote filesystem at the command line, and then navigate to it and do the rest in pcmanfm.

---

### Post by earthpigg on 2009-09-18
> **Bölvaður said:**
> I thought I made my self clear a month ago :D when I said having only things that are shared with all computers on the disk, have all the other stuff an option... Perhaps as a .deb metapackage on the desktop.

Btw I have an idea for a desktop background which Im going to do in few minutes when I find the camera. What do you think of having a profile of someones head (possibly with a shining light from 45° angle, which would be kind of above to right/left) and the background is what ever colour you wish.

*added*
never mind, the background looks worse than I thought.

9.10 _***may***_ come in three variants:
**basic/desktop** - same as -20080821 release of Masonux.
**laptop** - add gnome-power-manager.
**netbook** - include the above, maximus and lxlauncher both pre-configured.

will make it clear that any of the above will work on any system.

thanks for giving the wallpaper a shot :D let me know if you come up with anything you are happy with.

---

### Post by NormanFLinux on 2009-09-18
The Lubuntu team is working an optimized LXDE Netbook Remix.

---

### Post by earthpigg on 2009-09-18
> **NormanFLinux said:**
> The Lubuntu team is working an optimized LXDE Netbook Remix.

depending on how truly optimized it ends up being (low level versus high level), that would potentially encourage me not to bother.

[SIZE="5"]So, legal mumbo jumbo time.[/SIZE]

anyone have any opinions on this, before i shoot it off to Canonical?

it pertains to [trademark]("http://www.ubuntu.com/aboutus/trademarkpolicy") and the word "Remix".
> 
To: [http://www.ubuntu.com/contact/trademark](http://www.ubuntu.com/contact/trademark)
From: me :D

Hi,

This is my modest hobbyist spare-time Ubuntu-derived project: [http://sites.google.com/site/masonux/](http://sites.google.com/site/masonux/)

Thread @ ubuntuforums.org: [http://ubuntuforums.org/showthread.php?t=1248322](http://ubuntuforums.org/showthread.php?t=1248322)

I'd like permission to refer to it as some variation of "Masonux: Ubuntu Remix" with "Ubuntu Remix" as the subheading.... if i put Masonux in large letters, for example, I would put "Ubuntu Remix" in slightly not-quite-as-large letters.

Currently, I use terms such as "Ubuntu-derived" and "based on Ubuntu" as allowed by the general Trademark Policy and make it very clear at my website why: [http://sites.google.com/site/masonux/home#TOC-Release-Numbers-and-Naming](http://sites.google.com/site/masonux/home#TOC-Release-Numbers-and-Naming)

I understand that the package selection is far to different from Ubuntu's defaults (see: [http://sites.google.com/site/masonux/home/notes-to-myself](http://sites.google.com/site/masonux/home/notes-to-myself)) to allow me to use the word "Remix" without permission from Canonical Ltd as outlined by the trademark policy here: [http://www.ubuntu.com/aboutus/trademarkpolicy](http://www.ubuntu.com/aboutus/trademarkpolicy) .

Thus, I request permission from Canonical Ltd to use the word "Remix" in conjunction with my project as outlined above under terms similar to those outlined below.

The maximum divergence from Ubuntu I will implement without contacting Canonical Ltd. for permission to continue using the term "Remix" (instead of "Ubuntu-derived" or "Ubuntu based" that i am currently using and will continue to use if no other agreement is reached) is:

-Default package selection will continue to be radically different, but follow the pattern established and continue to be centered around LXDE.

-Default config file modification in line with my established pattern (see: [http://sites.google.com/site/masonux/home/notes-to-myself](http://sites.google.com/site/masonux/home/notes-to-myself)). If i wish to modify any config file not following that established pattern while still using the term "Remix", i will contact Canonical Ltd first.

-Desktop background and other artwork. I plan to use a wallpaper other than one included in the repositories in the next release. It will not be profane, offensive, discriminatory, inappropriate for children, discredit Ubuntu, etc. If I ever plan to replace other artwork while still using the term "Remix", I will contact Canonical Ltd first. If Canonical Ltd desires, I will e-mail a copy of the proposed wallpaper for approval.

-remastersys, which is not in the official repositories, will continue to be installed by default. If I ever wish include other packages not included in the official repositories while using the term "Remix", I will contact Canonical Ltd first.

-I will continue to make it very clear that there is no affiliation between my project and Lubuntu. I will not put "_Buntu" anywhere in the name of the project, except right next to the word "Remix".

-I'd like to use the Ubuntu logo on my web page and hopefully as desktop wallpaper artwork in the Ubuntu-derived project itself.

-I will display whatever trademark sublicense I recieve on the web page.

That is the general outline of the terms I humbly request. 

I understand that Canonical has no obligation - moral or otherwise - to accept my proposal. But hey, it can't hurt to ask, right?

I understand that the actual agreed-upon terms (if my proposal is accepted) will be in written legal mumbo jumbo language that Canonical Ltd will (hopefully) provide.


Thank you for your time,

Christopher Mason
Head Dude of the Masonux Project

[SIZE="4"]TLDR VERSION:[/SIZE]

Using terms like "Ubuntu-based" and "Ubuntu-derived" is always allowed, if it is true. The term "Ubuntu *Remix*" & use of Ubuntu logos are in a class of its own.

one of the terms of the trademark policy of Ubuntu is that it disallows folks from using the term "Ubuntu Remix" & artwork if package selection is significantly different ***or*** includes packages not in the repositories ***without asking and receiving permission.***

as my package selection is significantly different ***and*** it includes a package not in the repositories (remastersys) and i would like to use the term "Ubuntu Remix" along with artwork, i am thus goind to ask permission :D

if they say no, then they say no and i will oblige with no grudge held. I understand and respect their desire to uphold the quality associated with the word and associated artwork of "[COLOR="Sienna"]Ubuntu[/COLOR]". It costs me $0.00 to ask.

---

### Post by NormanFLinux on 2009-09-18
You can use the Ubuntu base and design an entirely different GUI on top of it. That's what the creators of Jolicloud did. And giving it a unique name makes every one happy as Canonical doesn't mind that you build off Ubuntu but they will object if you build on it.

---

### Post by RealG187 on 2009-09-18
> **Bölvaður said:**
> ```
cd /cdrom/hamm/hamm/binary/editors
**dpkg -i** vim_4.5-3**.deb**

```

So cd to the directory and "dpkg -i debname.beb"?

What's Vanilla?

---

### Post by earthpigg on 2009-09-19
> **RealG187 said:**
> What's Vanilla?

[http://en.wikipedia.org/wiki/Vanilla_software](http://en.wikipedia.org/wiki/Vanilla_software)

> Vanilla software is computer software that is not customized from its delivered form - i.e. it is used without any customizations applied to it. Vanilla software can become a widespread de facto industry standard, widely used by businesses and individuals.

the Ubuntu that you get that is *exactly* what you would get from the official Ubuntu website is *vanilla* Ubuntu.

as soon as you apt-get install ubuntu-restricted-extras or move a panel item, you are no longer using vanilla Ubuntu.

---

### Post by RealG187 on 2009-09-20
> **earthpigg said:**
> [http://en.wikipedia.org/wiki/Vanilla_software](http://en.wikipedia.org/wiki/Vanilla_software)



the Ubuntu that you get that is *exactly* what you would get from the official Ubuntu website is *vanilla* Ubuntu.

as soon as you apt-get install ubuntu-restricted-extras or move a panel item, you are no longer using vanilla Ubuntu.That's what I thought it was given the context of it being used in a remix. I just wanted to make sure...

---

### Post by nicefinger on 2009-09-24
I really like this Masonux. 
How fast will there be a 9.10 version?
(Masonux will be perfect for my fathers P3, better than ChrunchBang)

---

### Post by earthpigg on 2009-09-24
> **nicefinger said:**
> I really like this Masonux. 
How fast will there be a 9.10 version?
(Masonux will be perfect for my fathers P3, better than ChrunchBang)

i plan on having it out the week remastersys works with 9.10.

if that is the week that 9.10 comes out, then so be it.

---

### Post by RealG187 on 2009-09-24
> **nicefinger said:**
> I really like this Masonux. 
How fast will there be a 9.10 version?
(Masonux will be perfect for my fathers P3, better than ChrunchBang)Has anyone tried it on a P3? Cuz Ubuntu doesn't perform all to well on mine, atleast not as good as Windows does...

---

### Post by nicefinger on 2009-09-26
> **RealG187 said:**
> Has anyone tried it on a P3? Cuz Ubuntu doesn't perform all to well on mine, atleast not as good as Windows does...

I use #! 8.10 on my fathers p3-1000 now. It works much better than Xubuntu ever did. 
But yes, it is slow sometimes. Flash often take 100% cpu on some webpages (Hotmails welcome f.ex) 
When masonux 9.10 arrives, I will install it on that P3. Maybe with a faster HD too.

---

### Post by HappyFeet on 2009-09-26
> **nicefinger said:**
> I use #! 8.10 on my fathers p3-1000 now. It works much better than Xubuntu ever did. 
But yes, it is slow sometimes. Flash often take 100% cpu on some webpages (Hotmails welcome f.ex) 
When masonux 9.10 arrives, I will install it on that P3. Maybe with a faster HD too.

I understand that some of you *really* want to use ubuntu whenever possible, but sometimes a computer is just too old to run a modern OS efficiently. I would suggest Puppy linux, DSL, Slitaz, or Tiny Core for these old machines. You will have a much better experience.

---

### Post by nicefinger on 2009-09-26
> **HappyFeet said:**
> I understand that some of you *really* want to use ubuntu whenever possible, but sometimes a computer is just too old to run a modern OS efficiently. I would suggest Puppy linux, DSL, Slitaz, or Tiny Core for these old machines. You will have a much better experience.

That is probably true. But Firefox and proprietary driver for graphics is a must. Therefore, to make things easy, Ubuntu-derivatives.

---

### Post by CJ Master on 2009-09-26
> **nicefinger said:**
> I use #! 8.10 on my fathers p3-1000 now. It works much better than Xubuntu ever did. 
But yes, it is slow sometimes. Flash often take 100% cpu on some webpages (Hotmails welcome f.ex) 
When masonux 9.10 arrives, I will install it on that P3. Maybe with a faster HD too.

It's rare when flash is completely needed. If you're concerned about youtube, there's plenty of plugins that substitute.

---

### Post by nicefinger on 2009-09-26
> **CJ Master said:**
> It's rare when flash is completely needed. If you're concerned about youtube, there's plenty of plugins that substitute.

It is a very strange subject for me to understands. Some Flash runs nice, some not. It has nothing to do with how "big" the applications is ...

---

### Post by CJ Master on 2009-09-26
> **nicefinger said:**
> It is a very strange subject for me to understands. Some Flash runs nice, some not. It has nothing to do with how "big" the applications is ...

Even on Windows flash is buggy and a hog. I use it because my system can totally handle it, but for a P3 I would really recommend not using flash and finding substitutes.

---

### Post by earthpigg on 2009-09-26
> **CJ Master said:**
> Even on Windows flash is buggy and a hog. I use it because my system can totally handle it, but for a P3 I would really recommend not using flash and finding substitutes.

could you be more specific about these substitutes, and your experiences with them?

---

### Post by leclerc65 on 2009-09-27
I have Easy Peasy on the SSD of eeePC 701 , now Masonux on an 8G SD - it works fantastic (hope to prolong the life of the SSD ... forever:)).
But how can I have the button for the Speaker Volume Control ?
Thanks.

---

### Post by earthpigg on 2009-09-27
> **leclerc65 said:**
> But how can I have the button for the Speaker Volume Control ?

you don't have the little green speaker applet on the lower right?

---

### Post by CJ Master on 2009-09-27
> **earthpigg said:**
> could you be more specific about these substitutes, and your experiences with them?

I've personally never used any substitutes, but here's one: [https://addons.mozilla.org/en-US/firefox/addon/12027](https://addons.mozilla.org/en-US/firefox/addon/12027)

---

### Post by nicefinger on 2009-09-28
> **earthpigg said:**
> you don't have the little green speaker applet on the lower right?

You have to put it there Yourself. ...
Rigth-click on panel- add/remove panel items - Panel applets - +Add

---

### Post by leclerc65 on 2009-09-28
But I cannot try that now...my eee just quit with a Grub error 17.
I fixed that with Super Grub , but only Easy Peasy works for the moment. I have not a faintest idea why (too newbie).
Will try again later. Thanks all.

---

### Post by RealG187 on 2009-09-28
> **HappyFeet said:**
> I understand that some of you *really* want to use ubuntu whenever possible, but sometimes a computer is just too old to run a modern OS efficiently. I would suggest Puppy linux, DSL, Slitaz, or Tiny Core for these old machines. You will have a much better experience.P3s aren't even that old. P1s and 2s are older.

My P3 runs XP and Server 2003 fine and those are modern OSes.

I have tried Puppy Linux and DSL and they don't provide enough functionality for me. I could either run them and no little functionality, run Ubuntu and have Functionality at the cost of performance, or run Windows and have both.

If I cannot have an Ubuntu derivative on my P3 I will use Windows. If I cannot have one one P1 I would use Windows 2000 (As XP doesn't run well on them)

---

### Post by Eskobar on 2009-10-02
I'm on Crunchbang now, gonna try this out and post back!! I'm just lookin for the most basic system possible, so I can add exactly what "I WANT".  This seems to be it.

Edit

Just installed and its wonderful right out the box!!!  all pre installed apps are lite and I cant began to mention how much faster my cpu is responding.  I'm gonna go through now and nip and tuck somethings.... but I'm loving this Distro.  Thanks a lot Earthpigg

---

### Post by gfe on 2009-10-07
Earlier today I installed Masonux on an old Toshiba laptop (K6-2 processor at 475 MHz with 192 MB of RAM), and I'm pleased so far.

I had been using Puppy Linux on it. I liked Puppy, but there was no easy way for me to upgrade to Opera 10 with Puppy, and there were a few quirks that bugged me, so I thought I'd give Masonux a try. (I had tried Xubuntu before installing Puppy, and it wasn't quite light enough.)

Everything worked fine right out of the box, including the no-brand USB wireless adapter, and Opera is running great. I'll probably add AbiWord and FileZilla, and then I'll have exactly what I need. And if I can get printing to work (I never did get it figured out in Puppy) that would be a bonus.

The only problem that I had is that Synaptic takes forever to rebuild its database on my decrepit system. I couldn't do much of anything for about 20 minutes as the hard drive grinded away.

Thanks, Earthpigg, for your efforts. 

By the way, the installer worked fine with my 192 MB.

---

### Post by RealG187 on 2009-10-07
Does Linux run on a AMD-K6?

My Compia Linux book says if a Linux installation fails possible problems can include an over-clocked or AMD-K6 processor.

---

### Post by ikisham on 2009-10-11
> **RealG187 said:**
> Does Linux run on a AMD-K6?

My Compia Linux book says if a Linux installation fails possible problems can include an over-clocked or AMD-K6 processor.

It wont run if it's a so called i686 version (only works with k7+). This one is i386 so it works. [Absolute Linux]("http://absolutelinux.org/") should work too.

---

### Post by earthpigg on 2009-10-19
hello,

i tossed [this]("http://i109.photobucket.com/albums/n59/earthpiglite/desktop.png") together as a potential default background for the 9.10 release that will be coming soon.

simple, direct, not to flashy, and small (37kb). like Masonux itself.

anyone have any opinions on it they'd like to share?

---

### Post by longtom on 2009-10-20
> **earthpigg said:**
> hello,

i tossed [this]("http://i109.photobucket.com/albums/n59/earthpiglite/desktop.png") together as a potential default background for the 9.10 release that will be coming soon.

simple, direct, not to flashy, and small (37kb). like Masonux itself.

anyone have any opinions on it they'd like to share?

As good as any.  I personally don't like predominantly black backgrounds, so I would probably change it.
But looking at Gnome Arts, dark backgrounds appear to be in high fashion - so you are right on the money.

---

### Post by Plumtreed on 2009-10-20
Sorry, I don't like a black background either. Blue is always good and I was quite happy with the initial setup! 

I prefer computer things to be plain and business like especially for an OS like yours. Don't like the cartoon very much.

It all doesn't matter much because your OS is OK and it is always possible to change  things.

I am not very creative so I am unable to offer an alternative but perhaps someone else will be able to help

---

### Post by earthpigg on 2009-10-20
> **longtom said:**
> As good as any.  I personally don't like predominantly black backgrounds, so I would probably change it.


> Sorry, I don't like a black background either.

the idea rolling around in my head as a possibility was to follow LXDE's example with the backgrounds -- make them available in a few colors.

black
forest green (though a solid color can never really look forest-y)
pink
red
purple
blue
ubuntu brown
smiley-face yellow :)

---

### Post by Plumtreed on 2009-10-20
That sounds good...go for it, but, I still don't like the dorky duck cartoon!

---

### Post by CJ Master on 2009-10-20
Ahh! That jogged my memory, I made some wallpapers for you. They were quick to make, so I won't be offended if you don't want to include them on your distro.

[http://i38.tinypic.com/ajuvig.jpg](http://i38.tinypic.com/ajuvig.jpg)

[http://i36.tinypic.com/1z6rqpz.jpg](http://i36.tinypic.com/1z6rqpz.jpg)

---

### Post by earthpigg on 2009-10-20
> **CJ Master said:**
> Ahh! That jogged my memory, I made some wallpapers for you. They were quick to make, so I won't be offended if you don't want to include them on your distro.

[http://i38.tinypic.com/ajuvig.jpg](http://i38.tinypic.com/ajuvig.jpg)

[http://i36.tinypic.com/1z6rqpz.jpg](http://i36.tinypic.com/1z6rqpz.jpg)

i dig the first one!

---

### Post by CJ Master on 2009-10-20
> **earthpigg said:**
> i dig the first one!

Cool! Sorry it took so long to get back to you on those wallpapers. . . I kept forgetting :S

---

### Post by earthpigg on 2009-10-20
> **CJ Master said:**
> Cool! Sorry it took so long to get back to you on those wallpapers. . . I kept forgetting :S

it happens :D

you are the sole owner of the copyright by default, of course.

want to declare them [WTFPL]("http://en.wikipedia.org/wiki/WTFPL"), or do you want to [pick a creative commons license]("http://creativecommons.org/choose/"), or something else (public domain, one-time-use-no-derivatives, etc)?

---

### Post by CJ Master on 2009-10-21
Ah, I always have loved the WTFPL.

License for my Wallpaper:
[http://creativecommons.org/licenses/by-sa/3.0/us/](http://creativecommons.org/licenses/by-sa/3.0/us/)

---

### Post by Plumtreed on 2009-10-21
Avoid the 'square & compass' of Freemasonry but perhaps a mason's hammer & chisel might be a nice symbol to go with wallpaper #1........darker blue please!:P

---

### Post by earthpigg on 2009-10-21
> **CJ Master said:**
> Ah, I always have loved the WTFPL.

License for my Wallpaper:
[http://creativecommons.org/licenses/by-sa/3.0/us/](http://creativecommons.org/licenses/by-sa/3.0/us/)

> Attribution — You must attribute the work in the manner *specified by the author* or licensor (but not in any way that suggests that they endorse you or your use of the work).

i demand specification, sir!

> Avoid the 'square & compass' of Freemasonry but perhaps a mason's hammer & chisel might be a nice symbol to go with wallpaper #1........darker blue please!

Mason is my last name :D

> The name and logo of "Ubuntu" are trademarked, and the company behind Ubuntu has come down on folks appending -buntu to their project's name.

Linus Torvalds owns the trademark to the name "Linux," and the Linux Mark Institute sub-licenses the name on Linus' behalf. I am to lazy to apply for the right to put "Linux" in the project's name.

Well, it would appear I need a name for this project that does not include "*Buntu" or "Linux." So, I am simply and unimaginatively following the established pattern. Adding -ux to my name is simpler than coming up with a clever recursive acronym and accomplishes the same thing, so I went with that and here we have "Masonux".

---

### Post by Plumtreed on 2009-10-21
I know Mason is your name and that is exactly why Masonux is such a great name for your project! Don't change it. I was suggesting that it could, not essential, perhaps have a logo more distinctively yours rather than the Linux penguin. 

The hammer and chisel are the tools used by a mason.....a design might be easily 'created' so that your project carries a distinctive identification mark.

This is not in the least important, of course, and one of the good things about Masonux is that it works and is easy to use. No clutter or bloat should be added! Any time I suggest Masonux to people they always find it handy for daily use and as a good starting point to add their personal preferences. Haven't had a complaint yet!

---

### Post by CJ Master on 2009-10-21
Ah, I had just assumed no credit necessary. I don't really care if I'm credit or not. Whatever works out. :)

---

### Post by earthpigg on 2009-10-23
Plum: I'm glad it is working well for you!

CJ Master: roger that, thanks again!


Community:


I am experiencing a minor dilemma about which login manager to use in 9.10 due to some upstream changes. Please leave your feedback [here]("http://www.boxcarhosting.net:8080/masonux/boardthread?id=gen&thread=8") or [here]("http://ubuntuforums.org/showthread.php?p=8154007") if you are up to it. Thanks!

---

### Post by RealG187 on 2009-10-28
How do I change keyboard shortcuts and the resolution?

---

### Post by earthpigg on 2009-10-29
> **RealG187 said:**
> How do I change keyboard shortcuts and the resolution?

[http://wiki.lxde.org/en/LXDE:Questions#How_do_I_change_the_hotkeys.3F](http://wiki.lxde.org/en/LXDE:Questions#How_do_I_change_the_hotkeys.3F)

it certainly isn't as easy as in GNOME, but that's the current way to do it in LXDE.

as for the screen rez: menu -> run -> [lxrandr]("http://wiki.lxde.org/en/LXRandr")

in the 9.10 release, there will be a shortcut to it in the menu :D

Speaking of the 9.10 release...

It will be delayed for a while due to under-the-hood changes in Ubuntu 9.10 [not being compatible with remastersys.]("http://geekconnection.org/remastersys/forums/index.php?topic=320.0")

Once that is worked out, I'll cut the 9.10 release of Masonux as soon as possible. The dude behind remastersys has been pretty good about these things in the past, so hopefully it will be resolved soon.

---

### Post by ranch hand on 2009-10-29
If you are wanting to put out your 9.10 version before remastersys is updated to grub2, you could do this and then you wouldn't face that problem;
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)
Read it all before starting (the first post).

---

### Post by earthpigg on 2009-10-30
ranch hand: have you tested a karmic system reverted to grub legacy with remastersys out of curiosity? that is the biggest under the hood change of 9.10, so yeah that is probably it.... 

if you havent i will tomorrow or later this weekend after haloween hangover recovery.

---

### Post by ranch hand on 2009-10-30
No I haven't.  I do know that Stoner Edition is going to be coming out that way.

That is the deal breaker with remastersys, the guys at Zenix have put out a couple betas where they got it to work with grub2 but it is buggy as all get out.

I really like Lxde and want to see how it really works with Kinky Kitty (9.10).  Yours seems a good way to go.

I have a lot of space all the sudden.  I had a lot of OS', mainly Kinky variations, for testing.  With that over I have wiped one 320Gb drive and still have to do my dual 320Gb external enclosure.  I have to put something on them.

I also have a single 320Gb enclosure that I loan to people so they can try Linux on their box at speed rather than the Live CD.  I use Mandriva for KDE, Ubuntu, I think Zenix for Xfce, and it could be Masonux for Ldxe (Mandriva has it an gnome too - select at boot).  I think people need to see some choice.

---

### Post by earthpigg on 2009-11-13
Hello,

*[SIZE="4"][COLOR="Blue"]I'm happy to announce the first (and potentially only) Beta of Masonux 9.10.[/COLOR][/SIZE]*

[http://dl.dropbox.com/u/1832211/masonux-9.10-beta1-i386.iso](http://dl.dropbox.com/u/1832211/masonux-9.10-beta1-i386.iso)

Notes:

-I am calling this a beta. That means do not use this in a production environment. I am asking the community to *do me the favor* of installing it in a VM or on extra non-critical computers and giving me feedback or advice - Especially in terms of hardware support when compared to Ubuntu/Masonux 9.04, and if you find a working solution to 9.10-related regressions, please share them.

-I decided that the "-20090821" method of distinguishing version is a bit... awkward. Now, releases will be numbered as such: "Masonux 9.10.1". I am calling this release "Masonux 9.10 Beta1" in my head. It may or may not be re-released as "Masonux 9.10.1" in the future.

-Masonux has a new look, and a new desktop background thank's to the artistic contribution of a certain ubuntuforums.org community member.

-The .iso does not play nicely with Ubuntu's "USB Startup Disk Creator". It ***does*** work with unetbootin.

-The "Install" icon on the desktop seems not to function. Entering "ubiquity" in a terminal works.

-There is currently no power manager aside from LXDE's native "battery monitor" panel applet.

-The current NetworkManager doesn't seem to like to place nicely outside of GNOME. The workaround I used for previous releases no longer works. [Wicd]("http://en.wikipedia.org/wiki/Wicd_%28Linux_Network_Manager%29"), the most popular alternative to NetworkManager is now being used. If anyone here is able to get NetworkManager to work in this release, please let me know how you did so.

-The hardware support regressions present in Ubuntu 9.10 also exist in this release. In the case of my own Dell Mini 9, I'm having connection problems. The wireless card is recognized as "eth1", and seems to get stuck at "Obtaining IP address..."

-I will periodically try a command line install and sudo apt-get update && sudo apt-get upgrade to see if hardware support of 9.10 improves over time. If it does, a new point-release of Masonux will be released so folks can get that better hardware support OOB. This will be done because I had folks claiming the 9.04 release of Masonux (that came in august) supported hardware out of the box that Ubuntu 9.04 did not support. The only possible reason for this is because Masonux 9.04 came out in August, and thus included four months worth of upstream package updates that Ubuntu 9.04 did not.

-lxmusic is installed by default. There is a very real chance it will not be included in the final release.

-Hard drive and RAM use on my test machine (Dell Mini 9) remain about the same. 1gb and 65mb at first boot.

-Following Ubuntu's lead, empathy has replaced pidgin. Likewise, if Ubuntu where to replace Firefox with Midori - I would replace Firefox with Midori in my release. I have no love or dislike for empathy over pidgin, I am merely following Ubuntu's lead and will likely continue to do so. If you think my decision to follow Ubuntu's lead is mistaken, please share your opinion. If you think pidgin is better than empathy, please direct ***that*** part to the Ubuntu developers.

-The default sources.list (for now) looks like this:
```
deb http://geekconnection.org/remastersys/repository karmic/
deb http://mirrors.us.kernel.org/ubuntu/ karmic main restricted universe multiverse
```
you will need to run sudo apt-get update prior to installing additional packages, and if you want to tailor the menu.list to suit your needs you can use [this tool]("http://repogen.simplylinux.ch/") to do so. I went with mirrors.us.kernel.org to do my part to lighten the load on Ubuntu's main US servers.

---

### Post by ranch hand on 2009-11-13
I am in 10.04testing (yes I am nuts).  My test platform is an external enclusre with a meager capacity of two 320Gb drives.  Right now it has 4 OS' on it.

I think I can find room for some more.

I spend the day on that drive.  I just switched to my night OS.  I will down load in the morning.

---

### Post by RealG187 on 2009-11-13
How did you get a direct link for that ISO? Did you have to pay for hosting?

---

### Post by earthpigg on 2009-11-13
> **RealG187 said:**
> How did you get a direct link for that ISO? Did you have to pay for hosting?

someone earlier in the thread directed me to [dropbox]("https://www.dropbox.com/"). linux-friendly, 2gb free, really smart upload method (it hangs out in your sys tray and syncs local -> cloud when idle) but downloads are sometimes as slow as 100kb/s. right now its 350kb/s, but that is not always the case... i suspect it goes slower as more and more people download over time? 

if someone wants to make a torrent, ill link to it on my site, the first post of this thread, and be grateful.

---

### Post by RealG187 on 2009-11-13
And they give you direct link hosting?

---

### Post by Tibuda on 2009-11-14
> **earthpigg said:**
> Hello,

*[SIZE="4"][COLOR="Blue"]I'm happy to announce the first (and potentially only) Beta of Masonux 9.10.[/COLOR][/SIZE]*


Nice. What are you using as login manager?

---

### Post by earthpigg on 2009-11-14
> **danielrmt said:**
> Nice. What are you using as login manager?

i went with gdm :\

IIRC, SLiM from 9.04 was giving me issues when i tried to make the .iso, and gdm means users can apt-get install ubuntu-desktop with less fuss, if they wish.

the overhead didn't turn out to be significant in the big picture of things, and if you install lxde first gdm pulls less gnome stuff.

---

### Post by ranch hand on 2009-11-14
Well, I am bummed.  Downloaded and burned to CD.

Booted to CD.  Did have some strange things here as the bugger insisted that there should be sdc (there isn't).

Can't get the installer to run at all.  Double click or right click and select "execute".  Nothing happens.

I did not check the md5sum because I did not see where to get that.

---

### Post by earthpigg on 2009-11-14
> **ranch hand said:**
> Booted to CD.  Did have some strange things here as the bugger insisted that there should be sdc (there isn't).

Can't get the installer to run at all.  Double click or right click and select "execute".  Nothing happens.


yeah, annoying and im stumped regarding that. for now. from the notes above:

> -The "Install" icon on the desktop seems not to function. ***Entering "ubiquity" in a terminal works.***


can you provide more details on the bugger insisting there should be sdc?

---

### Post by ranch hand on 2009-11-14
I will have to give the ubiquity a try.  Should have thought of that.

Sdc.  The text rolled about a page of "can not mount sdc"

Entering "check" seemed to satisfy it.

The interesting thing about that is this is going on my test platform.  External dual SATA enclosure.  All internal drives are set to "off" in bios.  So the only drives are sda and sdb.

---

### Post by earthpigg on 2009-11-14
odd.

did this issue present itself using that exact setup/config and vanilla ubuntu 9.10?

---

### Post by ranch hand on 2009-11-14
That was just booting to the live CD.

---

### Post by ranch hand on 2009-11-14
Well, I waited for the end of my "daytime" testing run to install.

Went fine.  Won't boot.  Have a looping GDM on login.  I "knew" that this was because of a /etc/X11/xorg.conf file.  Nope.

I know the bugger knows my user name and password as I used it in terminal when trying to boot through recovery mode.

I am back on my "night" OS (9.04) and rumaging around in Masonux files for a clue.

---

### Post by nicefinger on 2009-11-15
Have downloaded. Will test tomorrow.

---

### Post by nicefinger on 2009-11-16
Running the Livecd now. Enormous 2048x1536 resolution, even in vesa safe mode. X breaks if I try to change it.

---

### Post by earthpigg on 2009-11-16
> **nicefinger said:**
> Running the Livecd now. Enormous 2048x1536 resolution, even in vesa safe mode. X breaks if I try to change it.

tried using lxrandr?
```

lxrandr
```

i need to double check on that being a menu item before i declare anything stable. among other things...

---

### Post by NormanFLinux on 2009-11-16
It should be noted the official Lubuntu was not ready for Karmic. It is still under heavy development before LXDE will become an official part of the Ubuntu family.

---

### Post by coolbrook on 2009-11-16
> **NormanFLinux said:**
> It should be noted the official Lubuntu was not ready for Karmic. It is still under heavy development before LXDE will become an official part of the Ubuntu family.

lubuntu-desktop is a package in the repositories, so it works anyway.

---

### Post by CJ Master on 2009-11-16
> **coolbrook said:**
> lubuntu-desktop is a package in the repositories, so it works anyway.

Yes, but it's terrible.

---

### Post by coolbrook on 2009-11-16
> **CJ Master said:**
> Yes, but it's terrible.
There's also the LXDE package.   It seemed to install less.

---

### Post by nicefinger on 2009-11-17
> **earthpigg said:**
> tried using lxrandr?
```

lxrandr
```

i need to double check on that being a menu item before i declare anything stable. among other things...

I am using that. The menue-item Monitor Settings is lxrandr.

---

### Post by ranch hand on 2009-11-17
I have gotten into the bugger.

Boot to recovery, choose "return to normal boot", get text log in, login, startx.  Takes me to a black screen (no background) but the bugger works.

I have no clue why the GDM does not work.  We had quite a time with it looping during testing but none of the triggers for that  seem to be here.

Beats me.

---

### Post by alphaniner on 2009-11-17
I installed it as a VBox VM.  I didn't get a splash; I assume this is an error because the grub entry has 'quiet splash'.  And I unchecked 'manage desktop and icons' or whatever in the desktop properties and lost me wallpaper. #-o

Not particularly worried about the former, but a solution to the latter would be nice. :)

---

### Post by earthpigg on 2009-11-18
alphaniner:

the latter is just how lxde works :D

the assumtion, i believe, is that if you uncheck that then you have something ***else*** you would rather have manage your desktop and icons besides pcmanfm. like nautalus, for example, or openbox.

you can get it back through pcmanfm's menus.


rest: i am reading all of this, even if i don't comment on every specific aspect. the most common answer would be "well, i suppose i need to look into that..."

---

### Post by LibraMark on 2009-11-18
Hey earthpigg

Don't know if you tried it yet or not, but for WiCD, I had the same trouble (hanging at obtaining IP address) and found that if I changed the dhcp client it would work.  It is set initially at "Automatic - recommended" (don't know why they recommend it when it doesn't work ha ha!) and you can instead set it to try either dhcpcd or dhclient and see which will work for your system.

Enjoying your work on my X40 laptop.  It's very snappy and clean.  I have an idea and if I get a little time I might be able to send you some funky lxde colored desktop backgrounds if you want.  

Mark.

---

### Post by NormanFLinux on 2009-11-18
Its not the same as a stand alone LXDE distro. I played around with Fedora LXDE but some reason it doesn't like my HP Mini 2133. It crashes when the desktop appears.

---

### Post by alphaniner on 2009-11-18
> **earthpigg said:**
> you can get it back through pcmanfm's menus.

Thanks.  I never would have thought to look in the file manager for the solution.

---

### Post by niraj2709 on 2009-11-28
friends try mandriva lxde 2010 V2
its awesome !!

---

### Post by niraj2709 on 2009-12-01
monomaxus lite edition
is also a great lxde distro based on ubuntu.
it works out of the box.

---

### Post by earthpigg on 2009-12-01
hi,

I released [Masonux 9.10 beta2]("http://sites.google.com/site/masonux/news") today. It has some issues, you can read about them there.

Good news, though:

I updated the [Notes to Myself]("http://sites.google.com/site/masonux/home/notes-to-myself") page, so people that want to can now use that as a how-to guide to get a funcitonal LXDE/Ubuntu 9.10 desktop identical to Masonux onto a system with a wired internet connection.

It includes covering how to [make your own metapackage]("http://sites.google.com/site/masonux/home/notes-to-myself/metapackage") so you can remove things listed in the lxde metapackage without putting yourself in a situation wherein 'sudo apt-get autoremove' breaks your system -- this can ***also*** work if you want to get rid of some stuff included in ubuntu-desktop without borking your system... just replace ubuntu-desktop with ***your own ***metapackage. :D Once you've done it the first time, it takes about 5 minutes to create and install one.

As always, the content of the website aside from the software itself is licenced under the [WTFPL]("http://en.wikipedia.org/wiki/WTFPL").

---

### Post by earthpigg on 2009-12-21
curses!

> from: Dropbox
to: Me
subject: Notification from Dropbox

Hi Chris,

This email is an automated notification from Dropbox that your Public links have been temporarily suspended on account of generating excessive traffic. Your Dropbox will continue to function completely normally with the exception of Public links.

If you have any questions, feel free to drop us a line at [email]support@dropbox.com[/email].

- The Dropbox Team


Well, that's annoying. Cursed by success! :D Anyone that would like to offer a more reliable mirror, or any .torrent gurus that would like to set that up for me, please do so and let me know.

Until we resolve this, [these directions]("http://sites.google.com/site/masonux/home/notes-to-myself") will still work.
I'd prefer to find a $0.00 solution, as I don't want to start panhandling you folks for donations.
Suggestions? Please post them.

---

### Post by NoaHall on 2009-12-21
Host a torrent on your own computers for a while(2-3 days), then hope some others will seed it.

---

### Post by XubuRoxMySox on 2009-12-22
I'm sure that it's a hardware issue that makes LXDE on Ubuntu - or any variant of Ubuntu (including Masonux unfortunately) - so darn buggy on my 'puter. But it runs great on non-Ubuntu based distros like Debian. Have no idea why there's a *'buntu barrier* to LXDE. I can only guess it's my hardware, since I haven't seen much documentation for it, just my own experience.

But Masonux looks great! Very smartly put together metapackage that worked much better than my own minimal Ubuntu/LXDE remix. I'm looking forward to trying it again, perhaps on some different hardware.

-Robin

---

### Post by markp1989 on 2009-12-22
thats looks decent mite throw this on my eee pc.

keep us posted will torrent it as soon as its available

---

### Post by prshah on 2009-12-30
> **earthpigg said:**
> any .torrent gurus that would like to set that up for me, please do so and let me know.

I'm already seeding all the ubuntu images I can get my hands on, including k,x,myth etc, alternate, i386, x64, server and all combinations thereof. 

Seeding Masonux will be no hardship, and in fact a privilege. Please point me to an approved torrent file. Or do you mean that you want someone to do the initial seeding and attach a torrent file here (or your site)?

---

### Post by earthpigg on 2009-12-30
> **prshah said:**
> Or do you mean that you want someone to do the initial seeding and attach a torrent file here (or your site)?

that. my connection is over wifi, so me seeding would do nothing. if you do it, please include the [md5sum]("http://sites.google.com/site/masonux/downloads") in the torrent. :D

---

### Post by gsmanners on 2009-12-30
I've been looking over that meta package. I wonder if this basically covers it:

```
- LXDE (trimmed down a bit)

lxde-core (depends on lxde-common, lxpanel, lxsession, and pcmanfm)
lxde-icon-theme
lxappearance (depends on gtk2-engines)
lxinput (depends on lxde-settings-daemon)
lxrandr
lxsession-edit
lxshortcut

(note that lxpanel depends on lxmenu-data)

- file management

xarchiver

- xarchiver recommends (I would add bzip2 to this list)

arj
p7zip-full
rpm (depends on librpm0, librpmbuild0, librpmio0)
unzip
xdg-utils (highly recommended)
zip

- editors:

leafpad

- screensaver

xscreensaver (depends on xscreensaver-data, recommends libjpeg-progs and miscfiles)

- multimedia/graphics (lxmusic depends on the xmms stuff)

xmms2-core
libxmmsclient5
libxmmsclient-glib1
gpicview (recommends xdg-utils)

- development (used for help with strftime)

manpages-dev

- networking (network-manager-gnome?)

dnsmasq-base
libgnome-bluetooth7
mobile-broadband-provider-info
modemmanager
update-notifier-common
```

---

### Post by earthpigg on 2009-12-31
updated the download page of the website to have a .torrent that someone created... i downloaded it and verified the md5sum. [knyslinux001]("http://www.boxcarhosting.net:8080/masonux/boardthread?id=gen&thread=30&time=1262310944796") and i are seeding it, if others want to help i would greatly appreciate it.

i have two offers for direct download hosting, which i will look at after i get back from skiing in Lake Tahoe :P

---

### Post by chris200x9 on 2009-12-31
> **earthpigg said:**
> updated the download page of the website to have a .torrent that someone created... i downloaded it and verified the md5sum. [knyslinux001]("http://www.boxcarhosting.net:8080/masonux/boardthread?id=gen&thread=30&time=1262310944796") and i are seeding it, if others want to help i would greatly appreciate it.

i have two offers for direct download hosting, which i will look at after i get back from skiing in Lake Tahoe :P


Torrenting it now, set to seed regardless of ratio once it finishes, I might be able to mirror it too.

---

### Post by prshah on 2010-01-01
...and, torrenting too... now.

---

### Post by earthpigg on 2010-01-01
[chris200x9]("http://ubuntuforums.org/member.php?u=139215") hosted the .iso as direct download. once i download it and verify the md5sum, ill post the direct link here and on the website. then, off to Tahoe!

edit:
md5sum verified, torrent and that direct download listed on the website, time to pack for skiing (we depart in 24 minutes...)!

if anyone else wishes to host a direct download somewhere... feel free! let me know the link, ill download, verify the md5sum, and link it. Don't blame me if whatever free hosting service you use cuts you off, though!

i also ranted a bit on the little '[news]("http://sites.google.com/site/masonux/news")' section of the website. and i swore i would never become a blogger... whoops.

---

### Post by OxTubu on 2010-01-10
Hi folks! 

I must say that this is sooo much better for my HP NC4200 than xubuntu used to be. I made the switch some hours ago, and the difference is massive. 

Xubuntu used to be great for first 10 minutes, and then become very slow for the rest of the session. I am not experiencing anything similar after several hours with Masonux, and also my de facto internet speed is up on average 50% (I've done 5 measurements over the last few hours). 

Im using chrome, Dropbox and Skype on top of the original software. Im no expert, far from it, and thus Im very thankfull for this 'simple' way to use a lightweight linux system.

---

### Post by kolchak on 2010-01-11
I've been looking for a "build up from" minimal Linux distro for my desktop, which I'll be using as a dev workstation.  I'm running an Opteron 144 w/2 GB of RAM - not current generation, but not resource-constrained, either - and while Xubuntu runs well, I still wanted less stuff on the machine.

Enter Masonux.  I ran across it in a post somewhere about ultra-light distros, and after reading about it, I decided to set up my own 64-bit version.  It took a bit of trial and error, but I've now got a snappy, compact base to work from.  At rest, 162 MB of RAM are used; this is more than earthpigg describes, but may be due to a slight variation in installation, noted below.  Also, I haven't "audited" my system yet to see if there are unnecessary autostart processes running that I can clean up.

Overall, quite happy with [COLOR="Red"]**Masonux64**[/COLOR], and I hope to see LXDE continue to improve, as well.  Thanks!

      ======

1) I had a specific partitioning scheme I wanted to use, so when installing from the 64-bit mini.iso, I selected the "expert" rather than "command line" install.  If you do this, SKIP the "Select and install software" step.  By going into this step, things like OpenJava and OpenOffice were installed, even when I continued with no selection made from the list presented.

2) On my laptop, which already had a complete Ubuntu 9.10 install, I got Network Manager working with LXDE, so I replaced wicd with network-manager when doing the *apt-get install* step from earthpigg's *Notes to Myself*.  To get it to work, the only thing I had to do was add "LXDE;" to the OnlyShowIn line in the file /etc/xdg/autostart/nm-applet.desktop (noted in someone else's post, I believe).

3) During the install, when I selected GRUB for the bootloader, I couldn't get past a fatal error warning.  I selected GRUB 2, instead.

4) I didn't read about the gdm breakage until after I experienced it when I tried to boot my brand new Masonux64 system.  :o   I went with installing slim_1.3.1-4_amd64.deb, as suggested by kagashe in earthpigg's thread [*[COLOR="Blue"]LXDE Users - which login manager in 9.10? GDM now requires GNOME, SLIM vanished....[/COLOR]*]("http://ubuntuforums.org/showthread.php?t=1299214").  Though it's a little funky having this Debian-logo screen displayed when I start my system, it seems to work just fine.

---

### Post by earthpigg on 2010-01-16
A long-term solution to direct download hosting is now in place, thanks to the awesome folks at [geekconnection.org]("http://www.geekconnection.org/") who have given masonux it's own ftp domain/server space. those are the same folks that host remastersys (Masonux would not be possible without that project, due to my own ignorance) and a number of other small community Free Software-related projects. Check them out if you get a chance.

[http://masonux.geekconnection.org/](http://masonux.geekconnection.org/)

now that that particular monkey is off my back, back to 9.10 work... if i give it another shot or two and still can't fix the install icon on the desktop, i'm going to go ahead and release with that bug in place. ill toss some wallpaper together that instructs users to lxmenu -> run -> ubiquity.

@kolchak - glad things are working out well for you. if i here another story or two or demand for a 64-bit edition, ill cut one.

@OxTubu - i've also found chrome to be great on light hardware. better than ff.

---

### Post by CJ Master on 2010-01-16
Oh, did you change the wallpaper to the one in / ? It looks nice.

---

### Post by earthpigg on 2010-01-17
> **CJ Master said:**
> Oh, did you change the wallpaper to the one in / ? It looks nice.

that one may be in 9.10, yes, or i may use something flashier... but masonux still has no form of 'logo' as such. i hadn't noticed this till distro watch just wrote 'masonux' in the same font i use in the little 'logo' cell of their table. :P

---

### Post by earthpigg on 2010-01-21
Hi,

i need testers for the 9.10 RC. if you have time, please give me a hand.

[http://masonux.geekconnection.org/](http://masonux.geekconnection.org/)

notes:

-the install icon on the desktop doesn't work. o well. do what the desktop wallpaper tells you to do to install.

-depending on your install media, you MAY need to manually select 'lxde' at the login screen (@bottom) the first time you boot.

thats all.

QUESTIONS:

1. What install media did you use, and how did you burn/write it? ie: CD-R burned with [software name here], thumb drive with ubuntu's USB Startup Disk Creator, unetbootin, DVD-RW burned with [software name here], etc.

2. Hardware specs on computer?

3. Issues?

4. Is the icon on the bottom panel a real firefox one, or a generic blue one?

---

### Post by TironN on 2010-01-21
Looks great! I hope to give it a try!

---

### Post by mfrazzz on 2010-02-13
Downloaded the RC iso and connected it up to Virtualbox.  Booted in the VM just fine and the Live CD seemed to work.  I then did an install (Ubiquity) on the VM, and the install went fine.  I chose to not login, and found when I rebooted I only had a terminal window with no window manager.  So after trying a few things (all unsuccessful), I deleted and started over doing another install.  Again, the install went fine and this time I chose to use the login.  Rebooted and had the login screen,  But due to the default VM screen size, I wasn't able to click on the Session area to choose LXDE and could find no way to tab or anything else to get to that box (the blue circle icon with the silohette in it was on the session box, and the time ran across it).

So unfortunately, I couldn't test an installed version on Virtualbox.  Anyone have any ideas or work arounds?  Once I get logged in, I'd be able to do the guest cd addons to then get a larger screen resolution and this wouldn't be an issue.

---

### Post by CJ Master on 2010-02-13
> **mfrazzz said:**
> Downloaded the RC iso and connected it up to Virtualbox.  Booted in the VM just fine and the Live CD seemed to work.  I then did an install (Ubiquity) on the VM, and the install went fine.  I chose to not login, and found when I rebooted I only had a terminal window with no window manager.  So after trying a few things (all unsuccessful), I deleted and started over doing another install.  Again, the install went fine and this time I chose to use the login.  Rebooted and had the login screen,  But due to the default VM screen size, I wasn't able to click on the Session area to choose LXDE and could find no way to tab or anything else to get to that box (the blue circle icon with the silohette in it was on the session box, and the time ran across it).

So unfortunately, I couldn't test an installed version on Virtualbox.  Anyone have any ideas or work arounds?  Once I get logged in, I'd be able to do the guest cd addons to then get a larger screen resolution and this wouldn't be an issue.

Does normal Ubuntu work fine in your VM box?

---

### Post by mfrazzz on 2010-02-13
Yes, I have a VM of Xubuntu and Kubuntu that work just fine under Virtualbox.  For that matter, I've had 3 or 4 other distros (including a minimum Ubuntu install with only LXDE added to it) and they've all worked.  The problem for me seems to be that I can't get to the session box to be able to change it to LXDE (it appears to be blank, but hard to tell since other stuff is on top of it).  As I said, the Live CD of Masonux works just fine on my VM setup, its only trying to login (and it was pointed out by earthpig that on the first login after install you may have to set the session, and thats what I can't do).

I may try to use VMplayer and see if I can get it to work with that.

---

### Post by Eskobar on 2010-02-13
I did a clean install when I used it and it worked fine.  I'm about to try and install it on VM and see what happens, Be back later.....

---

### Post by mfrazzz on 2010-02-13
Ok, I just installed it under VMplayer (vmware) and it worked fine, as I could get to the session box to choose LXDE.

I went back to Virtual box, and deleted the VM and redid the install.  I realize now that I had chose to do the install from the initial boot screen, so I think that was the problem. I let it boot the live cd, then did Run -> Ubiquity and installed.  This time the session box (like with vmplayer) had entries and I could click on it and select LXDE...

So it appears my problem was "a short between the keyboard and the chair"...  :D

I'll play around with this tomorrow now and see how it goes.  May look at dumping my Xubuntu install for Masonux on an old 500Mhz pc that I use mainly for a samba server and to run a bzflag server.

---

### Post by Eskobar on 2010-02-13
Glad you got that situated....i'm gonna play with it.  I'm using Karmic Studio right now, but I am getting bored with it, I may switch over.

---

### Post by earthpigg on 2010-02-16
howdy,

I haven't had any luck resolving any of the annoying issues caused by upstream changes not meshing well with LXDE and openbox. Unless that changes, Masonux 9.10 r1 will be the final 9.10-based release. 10.04 will hopefully not be so wonky.

Masonux 9.10 r1 is Beta quality. If must have stuff only available in the Ubuntu 9.10 repositories and are willing to read through the release notes/discussion, it is available for download. However, **if the "Just Works" aspect is important to you, you probably want to use Masonux 9.04-20090821.**

[here is the /]("http://masonux.geekconnection.org/") of the FTP server for all downloads.

i know i should be filing bug reports regarding the wonkiness, but to be honest i don't expect any of the involved parties to make my issues a high enough priority that they will change anything to accomidate my little project - my bugs are relevent to only a very small niche of people, whereas other bugs affect whole bunches of people. maybe if i find time during spring break ill do some interaction with the openbox folks -- i think the problem with the broken 'install' .desktop icon resides there, but i am far from certain. it could have to do with remastersys.

also, i joined the [Open Invention Network]("http://www.openinventionnetwork.com/"). here is the [contract]("http://www.openinventionnetwork.com/pat_license_agreement.php").

I think I am about the 60th licensee - Google, Linux Mint, Canonical, and a few others are above me on that list. I joined as "Christopher Thomas Mason" and not "Masonux" because Masonux isn't registered anywhere as any type of formal organization (non-profit, etc).

It is unfortunate that I live in a nation with such silly software patent laws that a patent pool such as this is needed, but thus is life.

happy ubuntuing and happy masonuxing, and happy valentinesing to all :D

---

### Post by ssj6akshat on 2010-05-16
Now here comes Lubuntu

---

### Post by Shining Arcanine on 2010-05-16
What is the difference between this and Lubuntu?

---

### Post by Shazzam6999 on 2010-05-16
I haven't tried this to be honset... but for the most part the core ubuntu spinnoffs like Kubuntu and Lubuntu are just Ubuntu with a different default DE. They don't really spend a lot of time (at least from my experience) integrating the new DEs with ubuntu which is why kubuntu is a lot bulkier than a Kde install on something like Arch. Just using it as an example, but if you've ever tried Kubuntu and then used a native Kde distro the difference is pretty clear.

I'm guessing that Masonux is simply a better integration of Lxde into Ubuntu than Lubuntu is.

---

### Post by pete_m on 2010-05-16
Thanks for this thread and what looks a very handy distro . .
 I have a dozen old P2 machines . .maybe i'll be able to upgrade these and fix 'em up with Masonux( or something like it ) for use at a local project .

I'm an EEE PC user planning an imminent move to Ubuntu Lucid  .  .in the hope of performance improvements and the benefit of tying in to a fresh LTS release. I'm hoping to be able to upgrade my machine rather than do a fresh install
. 
Ii've put some work into my existing install based on 9.10 karmic nbr2 and am very happy with the results - full credit and thanks to all . .

First screenshots - more soon - of my work in progress at

[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)

I'm still comparitively new to Linux so any observations and guidance will be much appreciated ..

I have already downloaded but not yet tried the LXDE netbook remix . .

am i right in thinking that LXDE is a complete replacement for the gnome desktop ?
what would i need to do to be able to choose to launch LXDE in place of gnome at the login?
how feasible would it be to implement something similar to my present setup in LXDE or other lightweight WMs?

Thanks and Regards to all . .

---

### Post by Shazzam6999 on 2010-05-16
Yes, LXDE is a replacement for Gnome. If you're using gdm there should be a choice at the login screen called "sessions", you simply have to choose LXDE. I'm not too LXDE savvy but as long as you can enable compositing you should be able to get the same look.

---

### Post by earthpigg on 2010-05-16
[COLOR="Red"]**_Announcement relating to Masonux 10.04:_**[/COLOR]

I'm still a college student, for those unaware. One more week of lecture, and then Finals week. Once that is done, my little brother whom I haven't seen in a while is coming out to visit. Once that is done, summer school starts for me... Only taking one class, though.

My Agenda:
-Re-evaluate Lubuntu and the Linux Mint LXDE spin, and see if Masonux still needs to even exist. Compare hard drive, ram, and CPU usage on identical virtual machines.
-If it looks to me like Masonux still needs to exist, I'll get to work in earnest as my schedule allows.

If anyone wants to look at the [notes]("http://sites.google.com/site/masonux/home/notes-to-myself") from the 9.10 cut and start experimenting with 10.04, please let me know about any quirks you discover and if you were able to find workarounds.


> am i right in thinking that LXDE is a complete replacement for the gnome desktop ?

it's 'complete' in that it can replace gnome, yes.

it is not 'complete' in the sense that it comes with alternatives to every single graphical tool that gnome has - for certain tasks, you will either need to learn the command-line way of doing it, or pick a graphical application to install yourself. gnome comes with a cd/dvd burner, for example, but lxde assumes you are able to find your own and install that one.

the 'price' for this is integration. to continue with the example above, there are zillions of choices for cd/dvd burner apps... but, since none are ***integrated*** with lxde, you won't be able to find an iso and [ right click -> burn to cd ] the way you can with gnome. instead, you start the cd/dvd burning app you've selected, and burn from there.

---

### Post by earthpigg on 2010-06-18
[COLOR="Red"]**_Project Ending:_**[/COLOR]
June 18, 2010

The niche once filled by Masonux is no longer a niche, and thus I've decided that Masonux no longer has a need to continue. It's been fun folks, and thank you for your support.

Check out Lubuntu, LXDE Mint, Remastersys LXDE Lite, and Peppermint for some other distros that use LXDE.

---

### Post by K.Mandla on 2010-06-18
> **earthpigg said:**
> [COLOR="Red"]**_Project Ending:_**[/COLOR]
June 18, 2010

The niche once filled by Masonux is no longer a niche, and thus I've decided that Masonux no longer has a need to continue. It's been fun folks, and thank you for your support.

Check out Lubuntu, LXDE Mint, Remastersys LXDE Lite, and Peppermint for some other distros that use LXDE.
Sorry to hear that. Thanks for all your hard work. :)

---

### Post by edcompsci on 2012-04-11
This works great on my Fujitsu Lifebook S6210. I changed from the Jaunty repositories to Lucid and have to be careful to not synaptic out any important packages, but it still runs very nice. I am currently trying to find a VM solution to work on it. I tried kvm/qemu but that removes too many needed packages and I had to rely on my Clonezilla image to get back to where I was. Now I have this problem, trying to install VirtuaBox:

```


progave@Lifebook-S6210:~/Downloads$ sudo dpkg -i virtualbox*
(Reading database ... 60151 files and directories currently installed.)
Preparing to replace virtualbox-4.1 4.1.12-77245~Ubuntu~lucid (using virtualbox-4.1_4.1.12-77245~Ubuntu~lucid_i386.deb) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
Unpacking replacement virtualbox-4.1 ...
Setting up virtualbox-4.1 (4.1.12-77245~Ubuntu~lucid) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  
 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong

Processing triggers for shared-mime-info ...
progave@Lifebook-S6210:~/Downloads$ cat /var/log/vbox-install.log
/usr/share/virtualbox/src/vboxhost/vboxdrv/build_in_tmp: 65: make: not found
progave@Lifebook-S6210:~/Downloads$ sudo deb virtualbox*
sudo: deb: command not found
progave@Lifebook-S6210:~/Downloads$ 


```

---

### Post by sffvba[e0rt on 2012-04-11
> **earthpigg said:**
> [COLOR="Red"]**_Project Ending:_**[/COLOR]
June 18, 2010

The niche once filled by Masonux is no longer a niche, and thus I've decided that Masonux no longer has a need to continue. It's been fun folks, and thank you for your support.

Check out Lubuntu, LXDE Mint, Remastersys LXDE Lite, and Peppermint for some other distros that use LXDE.

Project has ended. - THREAD closed.


404

---

