---
title: "Xfce development"
date: 2013-12-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Andrew_Lucas on 2013-12-06
Hi all,

Having no tabs in Thunar (on 12.04 LTS) was doing my head in, so I updated Xfce using [this]("http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu") PPA.

Recently, I started wondering...was it really such a good thing to have added that 4.10 PPA to update the whole desktop environment (perhaps I would have been better of just manually pulling a thunar .deb from the Saucy repo?).

The problem: being attached to a PPA with a specific version number *implies* that my desktop will be attached to that specific version number, ad infinitum. Obviously, this is something I'd like to avoid - because it would mean my desktop would never be updated past 4.10.X.

A bit of digging led me to search out the Xfce website and see how far behind I was. This revealed that 4.10 was released as stable **28/4/2012**. Development on 4.12 seems to be pretty stagnant...the [roadmap]("http://wiki.xfce.org/releng/4.12/roadmap") shows that the cycle was frozen on **27/5/2012** and hasn't been kick started since. Even the members of the release team are fixed as 'tbd'. The only ray of hope is that the 4.10 PPA still seems to be building packages reguarly (and presumably pulling them from upstream?).

So, in summary:

1) Is being stuck on this 4.10 PPA as bad as it sounds? The handy thing about package management on Linux (as compared to Windoze) is that the process is nearly entirely automated. A command, a password, a y/n, and my system feels shiny and new again. On Windoze, the only way to get the same effect is with a reformatting. Having to regularly see if my 4.10 install is out of date yet would seriously spoil the fun (perhaps not enough to force me back onto Windows 8, but...eugh :mad:!)

2) Is my favourite desktop a zombie that is kept rolling by incorporation into new releases of distros (i.e. Saucy), rather than being having its own vitality upstream? Does anyone have any development news to clear my woes?

Apologies for waxing lyrical. This 'revelation' does call for a bit of melanchology, dramatic violins and all I'm afraid! :P

PS - yes, I do know about [this]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12") PPA. I'm unwilling to apply it without hearing some good news first about 4.12, however.

---

### Post by Bashing-om on 2013-12-06
Andrew_Lucas; Hi !

Somewhat confused by your post. Why add xfce4 from a PPA (testing) when version 4.10.0 is available from the software repository ?
> 
sysop@1304mini:~$ apt-cache show xfce4
Package: xfce4
Priority: optional
Section: universe/x11
Installed-Size: 31
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Xfce Maintainers <pkg-xfce-devel@lists.alioth.debian.org>
Architecture: all
Version: 4.10.0
<snip>


The conservative path is always remaining within the repository.

[INDENT][INDENT]just so we are all on the same page
[/INDENT][/INDENT]

---

### Post by vasa1 on 2013-12-06
> **Andrew_Lucas said:**
> ...

Apologies for waxing lyrical. This 'revelation' does call for a bit of melanchology, dramatic violins and all I'm afraid! :P
...
Does it?
Xfce could use intelligent people like you to speed things up; [Get involved]("http://www.xfce.org/getinvolved") :)
The Xubuntu team is also looking for [contributors]("http://xubuntu.org/contribute/").

---

### Post by vasa1 on 2013-12-06
> **Bashing-om said:**
> ... Why add xfce4 from a PPA (testing) when version 4.10.0 is available from the software repository ?

Maybe it's because OP is on 12.04? Maybe 4.10 (in the software center) is available for later versions and not for 12.04?

---

### Post by Frogs Hair on 2013-12-06
I use the 4.12 ppa and there hasn't been much noticeable cosmetic change with the exception of a new desktop settings GUI. XFCE is not my main desktop and I don't mind experimenting with the ppa . I have had no problems, but I am not using XFCE as a daily workhorse meaning I do little with it other than web browsing  listening to music, and experimenting with the settings . I also only use the XFCE session as an add-on to Ubuntu and not Xubuntu.

---

### Post by Bashing-om on 2013-12-06
[quote=vasa1]Maybe it's because OP is on 12.04? Maybe 4.10 (in the software center) is available for later versions and not for 12.04?[/quote]

That is true !
To add to your above:
"Please help testing Ricardo F. Teixeira's patched builds from this PPA:"
```

sudo apt-add-repository ppa:ricardo.teixas/xfce4-session
sudo apt-get update
sudo apt-get install xfce4-session=4.10.0-2ubuntu2~raring1 ppa-purge

```
[https://code.launchpad.net/~ricardo.teixas/ubuntu/raring/xfce4-session/fix-for-1104435/+merge/161735](https://code.launchpad.net/~ricardo.teixas/ubuntu/raring/xfce4-session/fix-for-1104435/+merge/161735)
Please be sure to test thoroughly.

It has been a bit, but I would think it is an ongoing effort.

[INDENT][INDENT]try'n to keep up[/INDENT][/INDENT]

---

### Post by Toz on 2013-12-06
> A bit of digging led me to search out the Xfce website and see how far behind I was. This revealed that 4.10 was released as stable 28/4/2012. Development on 4.12 seems to be pretty stagnant...the roadmap shows that the cycle was frozen on 27/5/2012 and hasn't been kick started since. Even the members of the release team are fixed as 'tbd'. 
Yes, the roadmap has been delayed, but work is not stagnant (see: [http://git.xfce.org/?s=idle]("http://git.xfce.org/?s=idle")). Granted, much of the work is translation-based, but there are enhancements, bug fixes, etc trickling in.

---

### Post by Andrew_Lucas on 2013-12-07
> **Bashing-om said:**
> Andrew_Lucas; Hi !

Somewhat confused by your post. Why add xfce4 from a PPA (testing) when version 4.10.0 is available from the software repository ?


The conservative path is always remaining within the repository.[INDENT][INDENT]just so we are all on the same page
[/INDENT]
[/INDENT]

Just to emphasise - my install is **_12.04_**. I think someone references this further on, does that solve any confusion? In any case, the 4.10 PPA was recommended by a blog/forum post (I don't remember which/where; I'll have found it via Google) - it *may* have well been outdated (if 4.10 has been moved to the 12.04 repos now?).

> **vasa1 said:**
> Does it?
Xfce could use intelligent people like you to speed things up; [Get involved]("http://www.xfce.org/getinvolved") :)
The Xubuntu team is also looking for [contributors]("http://xubuntu.org/contribute/").

Yeah, I did look into this - and is definitely something I'd like to get into in the future (quite busy atm with University/exams). I did a brief stint on the IRC, and as far as I can recall, they were only interested in coding skills - something I could probably pick up, but don't currently have. Nor do I speak a foreign language (e.g. for translation) - though if there were a demand for English -> British English, I could do that (though I can't imagine this is the most in-demand skill :P). Testing I'm not really able to do during term time, since I can't risk the potential time lost filing bug reports and/or (worst case scenario) having to do a full re-install. My work laptop (which would be the one I'd use for most installations) has got to have Windows on it to, and since I have no disc, I'd be scared of messing up the drive partitioning (i.e. if I was doing a clean install more than once per year).

> **vasa1 said:**
> Maybe it's because OP is on 12.04? Maybe 4.10 (in the software center) is available for later versions and not for 12.04?

Ta for pointing this out. ;)

> **Frogs Hair said:**
> I use the 4.12 ppa and there hasn't been much noticeable cosmetic change with the exception of a new desktop settings GUI. XFCE is not my main desktop and I don't mind experimenting with the ppa . I have had no problems, but I am not using XFCE as a daily workhorse meaning I do little with it other than web browsing  listening to music, and experimenting with the settings . I also only use the XFCE session as an add-on to Ubuntu and not Xubuntu.

Yeah, the whole thing about the scopes was the bullet to the head of me *ever* using straight Ubuntu. Even before that, Unity was (IMHO) ugly - I mean, orange and purple? They don't (quite) clash, but they're hardly the most appealing colours. :p KDE with it's overly smooth greys are marginally better, but I think Xfce is genuinely gorgeous! I never get why you'd want a back up desktop (I mean, the programs are what provide functionality, and they don't change!), anyway, and my install is a daily workhorse (hence use of Precise).

> **Bashing-om said:**
> That is true !
To add to your above:
"Please help testing Ricardo F. Teixeira's patched builds from this PPA:"
```

sudo apt-add-repository ppa:ricardo.teixas/xfce4-session
sudo apt-get update
sudo apt-get install xfce4-session=4.10.0-2ubuntu2~raring1 ppa-purge

```
[https://code.launchpad.net/~ricardo.teixas/ubuntu/raring/xfce4-session/fix-for-1104435/+merge/161735](https://code.launchpad.net/~ricardo.teixas/ubuntu/raring/xfce4-session/fix-for-1104435/+merge/161735)
Please be sure to test thoroughly.

It has been a bit, but I would think it is an ongoing effort.[INDENT][INDENT]try'n to keep up[/INDENT]
[/INDENT]


Uhm, what would the advantage of adding this be? As far as I can see, the patches seem to have been merged anyway ("Approve on 2013-05-27"). Plus, as mentioned, my current use needs a relatively stable installation, so I can't be testing. I wouldn't have updated to 4.10 in the first place if it wasn't for Thunar's lack of tabs *really* beginning to annoy me.

> **Toz said:**
> Yes, the roadmap has been delayed, but work is not stagnant (see: [http://git.xfce.org/?s=idle](http://git.xfce.org/?s=idle)). Granted, much of the work is translation-based, but there are enhancements, bug fixes, etc trickling in.

Thanks for this! It's good to see something is going on. However, scrolling back - I do noticed there seem to be large periods with no development:

> 
[TABLE="class: list nowrap"]
[TR]
[TD="class: toplevel-repo"][xfc]("http://git.xfce.org/bindings/xfc/")[/TD]
[TD][C++ Gtk+ and Xfce binding]("http://git.xfce.org/bindings/xfc/")[/TD]
[TD]Bo Lorentsen[/TD]
[TD]13 months[/TD]
[/TR]
[TR]
[TD="class: toplevel-repo"][xfce4-sample-plugin]("http://git.xfce.org/panel-plugins/xfce4-sample-plugin/")[/TD]
[TD][Sample plugin developers can use as a base for new panel-plugins]("http://git.xfce.org/panel-plugins/xfce4-sample-plugin/")[/TD]
[TD]Nick Schermer[/TD]
[TD]19 months[/TD]
[/TR]
[/TABLE]


The fact that the website has only (seemingly) been neglected is a little worrying about the long term viability? Doubts a little eased, but not completely assuaged.

If anyone could take the time to help out with another fix I need (for the slowwwww loading desktop, see [this]("http://ubuntuforums.org/showthread.php?t=2191388") thread), and can post over there, I'd be very grateful :D

---

### Post by vasa1 on 2013-12-07
> **Andrew_Lucas said:**
> 
... Thunar's lack of tabs *really* beginning to annoy me.
... I do noticed there seem to be large periods with no development:
... The fact that the website has only (seemingly) been neglected is a little worrying 
...
If anyone could take the time to help out ...
I'm not sure people have pointed this out or not, but much of the work done on Linux and Xfce and Xubuntu is by people volunteering their time and without expecting remuneration.

I personally feel more comfortable helping, when I can, someone who shows an understanding of these limitations.

---

### Post by Morbius1 on 2013-12-07
One of the greatest assets that XFCE has is that it changes so slowly. Small incremental changes to fix bugs and maybe add a new feature or two. It's the WinXP of Linux. 

I don't want it to change rapidly for fear that I will have to finally learn how to spell paradime ... paradym ... paradigm?  whatever..... and be forced to interface with my operating system using interpretive dance.

---

### Post by Frogs Hair on 2013-12-07
> I never get why you'd want a back up desktop I install different desktops to learn how to navigate and use them. I'm not all that picky about how I access applications. ;)   Unity dash or Synapse on XFCE  both get the job done quite well .   

> I mean, orange and purple? There are plenty themes icons and some nice customization tools for Unity that are not available on 12.04. Unity has come a long way since 12.04, but that doesn't keep me from trying different window managers. XFCE has been one of my favorites on the last three Ubuntu versions. PPA's all have potential problems and are use at your own risk ! Even if a PPA works great for me it may not for another person with different hardware.

---

### Post by Toz on 2013-12-07
> **Andrew_Lucas said:**
> 
Thanks for this! It's good to see something is going on. However, scrolling back - I do noticed there seem to be large periods with no development:



The fact that the website has only (seemingly) been neglected is a little worrying about the long term viability? Doubts a little eased, but not completely assuaged.

The Xfc component was deprecated pre-4.8 - hence the no work part. The core components of Xfce are:
- libxfce4util
- xfconf
- libxfce4ui
- garcon
- libxfcegui4
- exo
- xfce4-panel
- thunar
- xfce4-settings
- xfce4-session
- xfwm4
- xfdesktop
- xfce4-appfinder
- xfce-utils
- gtk-xfce-engine-2
- tumbler
+ whatever plugins are still being maintained. See: [http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building).

---

### Post by Andrew_Lucas on 2013-12-07
> **vasa1 said:**
> I'm not sure people have pointed this out or not, but much of the work done on Linux and Xfce and Xubuntu is by people volunteering their time and without expecting remuneration.

I personally feel more comfortable helping, when I can, someone who shows an understanding of these limitations.

Yeah, of course I understand this. But *six months* is a long time for development to completely come to a standstill, right? Even if the community using Xfce isn't huge, I imagine it **is** internationally distributed (i.e. I'm assuming someone in India, or any other majority non-Christian country isn't going to have the same slow down the western world has around Christmas/Easter). Plus, regardless of the reason, development apparently (and I do stress apparently - it could just be gaps in the logs or particular bugs being particularly difficult to work out - so updates aren't posted, so it appears as if there was something of a 'development drought') stopping is still development (apparently) stopping. Think of how many distros have gone dead? Who ever hears about [these]("http://distrowatch.com/dwres.php?resource=discontinued") anymore? I'm not saying it *will* happen, I'm saying it *could* happen, and given that, any indication that makes death look more likely (or Xfce being merged with other projects, or being superceded etc.) worry me! Projects go out the window all the time, but unlike a particular package dying, it'd be much more difficult to find a like-for-like replacement of Xfce, I'd definitely miss it's 'feel'.

> **Morbius1 said:**
> One of the greatest assets that XFCE has is that it changes so slowly. Small incremental changes to fix bugs and maybe add a new feature or two. It's the WinXP of Linux. 

I don't want it to change rapidly for fear that I will have to finally learn how to spell paradime ... paradym ... paradigm?  whatever..... and be forced to interface with my operating system using interpretive dance.

I suppose you're looking at this from the other end of the telescope to me. I'm an educated amateur rather than guru, and so for me, how the software updates isn't really that much of a big deal - providing it does actually update once in a while! I do use the Aurora builds of Firefox, and was using Earlybird (now I have to use Outlook, since my Uni uses Exchange rather than an IMAP server), and enjoying seeing tweaks and new features, but it isn't that much of a big deal. I don't do much (read: any) active bug reporting - I'm using those builds because they generally are as stable (at least in practice) as final releases and enable me to see any changes pushed through ahead of the curve. As soon as they stopped being stable and/or offering any advantage, I'd stop using them. Likewise...Xfce offers the best user experierence (look, simplicity, bugginess, GTK rather than Qt - so none of the mess of requiring GTK dependancies on a Qt desktop) out of the DEs I've tried, so I stick with it. If this changed, and I did start worrying about things like release cycles, I'd probably move back to KDE - for the simple reason that it's got a larger community and is more configurable than Cinnamon (GNOME3 would be out of the question!).

---

### Post by Andrew_Lucas on 2013-12-07
> **Frogs Hair said:**
> I install different desktops to learn how to navigate and use them. I'm not all that picky about how I access applications. ;)   Unity dash or Synapse on XFCE  both get the job done quite well .   

 There are plenty themes icons and some nice customization tools for Unity that are not available on 12.04. Unity has come a long way since 12.04, but that doesn't keep me from trying different window managers. XFCE has been one of my favorites on the last three Ubuntu versions. PPA's all have potential problems and are use at your own risk ! Even if a PPA works great for me it may not for another person with different hardware.

Yeah, I know the issues (the biggest one for me is security - particularly if the PPA has a smallish user base). Regarding Unity, colour is probably more the nail in the coffin than anything else - a minor issue that confirms all the other problems I have with it :P.

> **Toz said:**
> The Xfc component was deprecated pre-4.8 - hence the no work part. The core components of Xfce are:
- libxfce4util
- xfconf
- libxfce4ui
- garcon
- libxfcegui4
- exo
- xfce4-panel
- thunar
- xfce4-settings
- xfce4-session
- xfwm4
- xfdesktop
- xfce4-appfinder
- xfce-utils
- gtk-xfce-engine-2
- tumbler
+ whatever plugins are still being maintained. See: [http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building).

Could you expand on this? 'Deprecated'?

---

### Post by Toz on 2013-12-07
> **Andrew_Lucas said:**
> Could you expand on this? 'Deprecated'?
By deprecated I mean no longer being used. Outdated code. Functionality retired or merged into other modules.

---

### Post by vasa1 on 2013-12-07
> **Morbius1 said:**
> ...
I don't want it to change rapidly for fear that I will have to finally learn how to spell paradime ... paradym ... paradigm?  whatever..... and be forced to interface with my operating system using interpretive dance.

You left out *intuitive*. I wonder what that really translates to.

---

### Post by Andrew_Lucas on 2013-12-09
> **Toz said:**
> By deprecated I mean no longer being used. Outdated code. Functionality retired or merged into other modules.
So let's get this in black and white: prior to 4.8, certain components of the DE were deprecated (i.e. more or less written off). That doesn't explain the current dry periods though, does it? :s The components you mentioned would largely form a DE on their own, presumably.

---

### Post by Toz on 2013-12-09
> **Andrew_Lucas said:**
> So let's get this in black and white: prior to 4.8, certain components of the DE were deprecated (i.e. more or less written off). That doesn't explain the current dry periods though, does it? :s The components you mentioned would largely form a DE on their own, presumably.
Personally, I'm happy with the speed of development. To me, Xfce is a complete DE. However, I know that others feel differently. Perhaps it would be best to ask your question to the Xfce maintainers and developers themselves - maybe they can provide the answers you are looking for. You can try the #xfce IRC channel. 

*Since this isn't really a support thread, I'm going to move it to Linux/OS Chat.*

---

