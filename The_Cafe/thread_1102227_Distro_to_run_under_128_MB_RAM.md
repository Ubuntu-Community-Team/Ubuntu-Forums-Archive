---
title: "Distro to run under 128 MB RAM?"
date: 2009-03-21
forum: The Cafe
---

### Post by armageddon08 on 2009-03-21
Any suggestions? Better if the distro is Red Hat/Fedora based?

---

### Post by HermanAB on 2009-03-21
Linux is Linux is Linux...

Deep down they are all the same.

Most RAM is used by X and graphical applications, so while any distribution with any desktop system will work on 128MB RAM, you will have best results with a light weight desktop such as LXDE or XFCE.  So try Xubuntu or install LXDE yourself.

Cheers,

Herman

---

### Post by Twitch6000 on 2009-03-21
Tiny Core Linux is all you need :).

Or possibly Damn Small Linux.

---

### Post by hansdown on 2009-03-21
Hi armageddon08.

Puppy linux should work well.

[http://www.puppylinux.org/](http://www.puppylinux.org/)

Simply mepis is a good distro that works right away without any work.

[http://www.mepis.org/](http://www.mepis.org/)

---

### Post by binbash on 2009-03-21
+1 puppy

---

### Post by sports fan Matt on 2009-03-21
Yeah..dsl or puppy id say

---

### Post by MasterNetra on 2009-03-21
+1 Puppy Linux or DSL

---

### Post by armageddon08 on 2009-03-21
Thanks guys for your quick fire replies. But is there one with Red Hat/Fedora roots?

---

### Post by s.fox on 2009-03-21
another vote for puppy!

---

### Post by hansdown on 2009-03-21
> **armageddon08 said:**
> Thanks guys for your quick fire replies. But is there one with Red Hat/Fedora roots?

You could try fedora.

[http://fedoraproject.org/](http://fedoraproject.org/)

---

### Post by mkvnmtr on 2009-03-21
I have done some minumal installs of Ubuntu. I can get xorg and xfce4 to work on 128Mb but not very well. DSL and Puppy work well. If you want to go with something from fedora why not install the kernel and build just what you need. I would assume they have a command line install. Then adding the lightest of what they offer in there repositories should give you something that would work.

---

### Post by cardinals_fan on 2009-03-21
Most light distros are either independent or Slackware-based.  I haven't found a good Red Hat derivative for light use.

I'm going to recommend either [SliTaz]("http://slitaz.org/en/") or [Vector Light]("http://vectorlinux.com/").  Here's a quick overview of each:
[B]
SliTaz[/B]: a newcomer to the distro scene, this little system has already gathered a small following.  At first glance, this distro is just a nice, light system with LXDE and some light defaults.  A peek under the hood, however, reveals an innovative package manager and a light init system.  To admit some personal bias, SliTaz is my favorite *Linux* distro (I still prefer NetBSD) and has dazzled me.  Unlike most live CDs, SliTaz works well as an installed system and has a really solid development and packaging push between releases.  My personal SliTaz and evilwm system uses just **28 MB** of RAM, but an average LXDE desktop will probably need about** 50 MB**.  By the way, be sure to either download the latest Cooking image or wait for version 2.0 in a month or so - 1.0 is dated and limited.

**Vector Light**: Vector Linux is a well-established Slackware derivative with a small but loyal following.  Last year, the Vector team came out with a special Light version, designed for machines too old to handle the normal Xfce desktop or those who want a more minimal system.  Vector Light comes with LXDE and Fluxbox for window managers and taps into the Vector repos for other software.  Vector is also fully compatible with any Slackware packages you might find.  Using about **60 MB** of RAM in my tests, the standard LXDE desktop balances quick setup and light resource usage elegantly.

I recommend **against** both Puppy and DSL.  Don't get me wrong; these two distros have many uses.  But they were both designed as live CDs, and in my tests both feel cumbersome for installed use.  The lack of maintenance between releases, irregular repos, and slightly cumbersome system designs are no issue with live usage.  However, I haven't found anyone yet who would use Puppy on newer hardware, and only one who would use DSL.  Compared to SliTaz, both of these just seem a bit less complete.

I firmly believe that TinyCore will be a great project and will give SliTaz a run for its money.  However, this distro is just too new for me to recommend right now.  You will be severely limited if you take this route at this time.

---

### Post by armageddon08 on 2009-03-21
> **cardinals_fan said:**
> Most light distros are either independent or Slackware-based.  I haven't found a good Red Hat derivative for light use.

I'm going to recommend either [SliTaz]("http://slitaz.org/en/") or [Vector Light]("http://vectorlinux.com/").  Here's a quick overview of each:
[B]
SliTaz[/B]: a newcomer to the distro scene, this little system has already gathered a small following.  At first glance, this distro is just a nice, light system with LXDE and some light defaults.  A peek under the hood, however, reveals an innovative package manager and a light init system.  To admit some personal bias, SliTaz is my favorite *Linux* distro (I still prefer NetBSD) and has dazzled me.  Unlike most live CDs, SliTaz works well as an installed system and has a really solid development and packaging push between releases.  My personal SliTaz and evilwm system uses just **28 MB** of RAM, but an average LXDE desktop will probably need about** 50 MB**.  By the way, be sure to either download the latest Cooking image or wait for version 2.0 in a month or so - 1.0 is dated and limited.

**Vector Light**: Vector Linux is a well-established Slackware derivative with a small but loyal following.  Last year, the Vector team came out with a special Light version, designed for machines too old to handle the normal Xfce desktop or those who want a more minimal system.  Vector Light comes with LXDE and Fluxbox for window managers and taps into the Vector repos for other software.  Vector is also fully compatible with any Slackware packages you might find.  Using about **60 MB** of RAM in my tests, the standard LXDE desktop balances quick setup and light resource usage elegantly.

I recommend **against** both Puppy and DSL.  Don't get me wrong; these two distros have many uses.  But they were both designed as live CDs, and in my tests both feel cumbersome for installed use.  The lack of maintenance between releases, irregular repos, and slightly cumbersome system designs are no issue with live usage.  However, I haven't found anyone yet who would use Puppy on newer hardware, and only one who would use DSL.  Compared to SliTaz, both of these just seem a bit less complete.

I firmly believe that TinyCore will be a great project and will give SliTaz a run for its money.  However, this distro is just too new for me to recommend right now.  You will be severely limited if you take this route at this time.

Thanks. I think its time I tried Slackware. May be I should begin with Vector Light.

---

### Post by cardinals_fan on 2009-03-21
> **armageddon08 said:**
> Thanks. I think its time I tried Slackware. May be I should begin with Vector Light.
Vector (Light) is a good intro to Slackware.  It has lots of autoconfiguration and slapt-get for out-of-the-box package mangement, but is still Slackware under the hood.  **I would recommend starting with this.**

You should also know about SLAX.  SLAX is a pure Slackware system as a live CD.  It can also provide a quick (albeit dirty) way of installing Slackware.  This is a bit more hackish, but it does offer an up-to-date Slack system with little effort.  If you feel adventurous, let me know and I can post more detailed instructions.  Otherwise, just enjoy SLAX as a live CD and Slackware demo.

I personally love Slackware for its simplicity and stability.  It takes a bit more work up front, but the stability and control will pay off over time.

---

### Post by gn2 on 2009-03-21
Zenwalk might be worth a try?

---

### Post by cardinals_fan on 2009-03-21
> **gn2 said:**
> Zenwalk might be worth a try?
I'm sad to say that I can no longer recommend Zenwalk for old machines.  It's just getting too big... :(

---

### Post by adamlau on 2009-03-21
Any distro with the right DE/WM combo and the judicious use of lightweight apps and some minor tweaking will run fine with 128 MB. That includes Ubuntu and Fedora. Any distro.

---

### Post by kerry_s on 2009-03-21
archlinux+jwm+opera, i have it on 700mhz 128mb ram minus some for vid, it's perfectly usable. uses around 64mb with opera tweaked for low resource, adblock list, etc...
i went a day without even dipping into swap.

---

