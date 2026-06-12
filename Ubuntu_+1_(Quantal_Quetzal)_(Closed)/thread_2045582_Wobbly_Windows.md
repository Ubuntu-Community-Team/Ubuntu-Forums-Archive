---
title: "Wobbly Windows"
date: 2012-08-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Aenima99x on 2012-08-21
Just installed the daily version and I've noticed that wobbly windows are not available....is this something planned or just not implemented yet? Thanks.

---

### Post by stinkeye on 2012-08-21
I think the package , **compiz-plugins** that contains a lot of the extra plugins needs to be installed.

---

### Post by Aenima99x on 2012-08-21
> **stinkeye said:**
> I think the package , **compiz-plugins** that contains a lot of the extra plugins needs to be installed.

Ohh man I feel dumb now....thanks!

---

### Post by stinkeye on 2012-08-21
> **Aenima99x said:**
> Ohh man I feel dumb now....thanks!
Nahh, these plugins were included in the default compiz before.
Hope it's just for testing purposes.
Got a feeling that they might become neglected.

---

### Post by philinux on 2012-08-21
> **stinkeye said:**
> Nahh, these plugins were included in the default compiz before.
Hope it's just for testing purposes.
Got a feeling that they might become neglected.

I get the feeling this is about making sure Ubuntu runs out the box. I'm betting they'll stay in the repo just not part of the default install.

---

### Post by EgoGratis on 2012-08-21
I hope "Wobbly Windows" don't get remove just "because". If user wants "Wobbly Windows" let him have "Wobbly Windows". ;)

---

### Post by edujose on 2012-08-22
Yeah, don't remove them. They are also a great way to show what Linux is capable of doing.

(I usually use wobbly to get all kinds of "ooohh" and "aaahh" around :p).

---

### Post by mc4man on 2012-08-22
All the plugins in "compiz-plugins" are no longer "supported" (officially
Have seen it come up in a couple of bug reports where it now Can be said
'We don't support <whatever> anyway'

---

### Post by NikTh on 2012-08-22
> **EgoGratis said:**
> I hope "Wobbly Windows" don't get remove just "because". 

Hi , 
I don't think that is "just because" . If "Wobbly Windows" crashing out the system , them must be removed for a stable version of Ubuntu to take place. Then it is user's hand to install or enable any effect he wants , but its his risk to crash the system. 
Thanks

---

### Post by rg4w on 2012-08-22
> **NikTh said:**
> Hi , 
I don't think that is "just because" . If "Wobbly Windows" crashing out the system , them must be removed for a stable version of Ubuntu to take place. Then it is user's hand to install or enable any effect he wants , but its his risk to crash the system. 
Many of the Compiz crashers began only when Unity was introduced.  So is Compiz the source of the problem?

---

### Post by zombifier25 on 2012-08-22
Compiz never crashed unless I turn on something in CCSM. So I hope Wobbly Windows (and associates) are not removed, simply not installed by default

---

### Post by philinux on 2012-08-22
> **zombifier25 said:**
> Compiz never crashed unless I turn on something in CCSM. So I hope Wobbly Windows (and associates) are not removed, simply not installed by default

Precisely. That was the point of my previous post. :p

---

### Post by kerneloftruth on 2012-08-22
I hope that certain features won't be removed in the foreseeable future

especially the exposé-like feature and the negative (invert screen) feature are very useful and I use them on a consistent basis - at least on my Gentoo system

I still need to figure out how to enable it in 12.04LTS which I just installed - probably via ccsm & installing the other plugins

thanks :)

---

### Post by NikTh on 2012-08-22
> **rg4w said:**
> Many of the Compiz crashers began only when Unity was introduced.  So is Compiz the source of the problem?

Hi , 
you have right  , but what developers should do ? 

Logical,  remove these features from standard install until a solution occurs . Until then I agree with @philinux's and @zombiefier25's posts.

---

### Post by EgoGratis on 2012-08-22
Or Ubuntu grows and has enough resources and "Wobbly Windows" don't get remove just "because". If user wants "Wobbly Windows" let him have "Wobbly Windows". :wink:

---

### Post by effenberg0x0 on 2012-08-22
While I can't really say I depend on them to use Ubuntu, the removal of some plugins would make my daily usage of the PC a lot more difficult. I've been working with plugins like Commands, OBS, Place Windows and Shift Switcher for years and they really help me.  

Examples: Having some specific applications being launched exactly in the monitor, viewport & X/Y coordinates I need them to be, in specific states (maximized, non-resizable, not-movable, sticky/all-desktops, always on top, etc) in a complex multimonitor setup. Having console's launched by eclipse always use a pre-determined position in screen and a certain degree of transparency, so I can step through breakpoints and see the effects in the programs in one screen and watch system logs being tailed in another monitor. Having a dashboard that shows me details of a certain system in an specific monitor (which is not in front of me but in another room). I can do all of that without compiz plugins, but would take me a lot of scripting.

I hope they leave the plugins alone and available in repos but, to be honest, even if they survive the QQ cycle, I do not believe that will be the case in the future (considering what we have been seeing since the beginning of Unity and the overall trend of standardization/simplification of UX/UI, removal of customization options).

That's just my opinion/perception and I might be completely wrong about this anyway.

Regards,
Effenberg

---

### Post by mc4man on 2012-08-22
The plugins for the most part will remain - when or if they break on changes that will then present the issue, unsupported plugins may not be fixed, at least in typical fashion (LP bug, ect.

The best hope there is a 'break' also affects a supported plugin.

2 recent examples - 
Here I use commands & dbus, one is initiated thru an edge binding. Currently user set edge bindings won't survive a restart, fortunately it affects supported plugins like wall so the bug has been accepted. (there is a workaround that is fairly effective

The whole deal with flashing on rotate - if that hadn't also affected wall & expo it would never have been fixed (even though at the time  it broke rotate was 'supported'

(the current gsettings test build of unity has no working support for the commands plugin - will be interesting to see what happens on next unity/compiz upgrade

---

### Post by Carbs70 on 2012-09-10
Funny isn't it.... I mean, things like Wobbly Windows and the Desktop Cube are (to me) key features of my Ubuntu experience. If these sorts of customisations are removed, then the system creeps one step closer to a Windows environment (bite my tongue!)

For me as a web developer, there's plenty of tools available in other OS's that I could be using... but I forego all of those because I like the "relaxed" feel of an Ubuntu environment. I *was* excited at the prospect of upgrading to 12.04, and I do like the HUD... but if silly features  like those found in CCSM that really "cement" the Ubuntu experience start to disappear, then it may well start to make sense to return to M$....

---

### Post by grahammechanical on 2012-09-10
They should have deactivated the Compiz plugins when they first brought out Unity. That was when things like Wobbly windows were breaking the Unity desktop and not only in the development branch. And making all our lives difficult. They should have re-instated each plugin as it was proved (tested) to work as it should.

Wobbly windows was fixed. I have been using it in the development branch for more than a year until it was recently removed from CCSM in a recent update to 12.10.

What does the poem say? "Ours not to reason why." Ours to do and break the installation.

Regards.

P.S. Check this out for an example of the left hand not knowing what the right hand is doing:

[http://www.omgubuntu.co.uk/2012/09/so-long-magic-lamp-ubuntu-12-10-reverts-unminimize-animation]("http://www.omgubuntu.co.uk/2012/09/so-long-magic-lamp-ubuntu-12-10-reverts-unminimize-animation")

And people ask us if we know what is intended and not intended!

---

### Post by EgoGratis on 2012-09-11
[http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/](http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/)

Looks like Wobbly won't make it after all.

---

