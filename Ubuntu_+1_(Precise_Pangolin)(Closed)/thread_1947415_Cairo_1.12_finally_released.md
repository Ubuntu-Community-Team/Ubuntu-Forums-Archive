---
title: "Cairo 1.12 finally released"
date: 2012-03-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by t1497f35 on 2012-03-26
It's been over a year since last release [with]("http://www.phoronix.com/scan.php?page=news_item&px=MTA3NzE") [lots of improvements]("http://cairographics.org/news/cairo-1.12.0/"), anyone knows if it makes it into Ubuntu 12.04?

---

### Post by screaminj3sus on 2012-03-26
Its probably unlikely this lately in the cycle for an lts, but it would be nice.

---

### Post by ScislaC on 2012-03-27
I got confirmation today, it will not be making it in 12.04. Apparently the Debian maintainer is seeing some regressions in exa (plus it's a year and a half of development and really risky anyway).

---

### Post by neu5eeCh on 2012-03-27
I was just using it, just before reading this. Cairo crashed. Hard.

---

### Post by t1497f35 on 2012-03-27
> **VTPoet said:**
> I was just using it, just before reading this. Cairo crashed. Hard.
How do you know that cairo crashed? And what video hw are you using?

---

### Post by neu5eeCh on 2012-03-27
> **t1497f35 said:**
> How do you know that cairo crashed?

Because Cairo crashed hard?

Is that the right answer?

Here's what happened. I was noodling around with the dock, getting it all gussied up. That done, I clicked on the FF "window button" to close FF. The instant I clicked on that button, the desktop went darkish, Cairo dock disappeared and the desktop essentially locked up. Two "undocked" cairo apps remained on the desktop. They were unclickable though. I had to TTY to reboot.   



 > **t1497f35 said:**
> And what video hw are you using?

Vanilla Intel:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by t1497f35 on 2012-03-27
I see, sometimes people decide what crashed based on logs, eg. when Java crashes it leaves a trace log in your home dir. If so you could have created a bug report and attach the log so the devs could fix it.

---

### Post by Azrael84 on 2012-03-28
Could someone give me some guidance installing this. I downloaded and unzipped the tar ball, then in the unzipped dir did ./configure however upon attempting 'make' I get the error that no makefile found.

Am I doing something wrong?

---

### Post by neu5eeCh on 2012-03-28
> **Azrael84 said:**
> Could someone give me some guidance installing this. I downloaded and unzipped the tar ball, then in the unzipped dir did ./configure however upon attempting 'make' I get the error that no makefile found.

Am I doing something wrong?

Why are you compiling it? -- as opposed to installing it via the software manager?

---

### Post by Azrael84 on 2012-03-28
> **VTPoet said:**
> Why are you compiling it? -- as opposed to installing it via the software manager?

is it available via the software manager? or is there a repository I could add etc? I could only see a tarball on their website but I'd glady do it the other way if someone could point me to a PPA or whatever..

---

### Post by neu5eeCh on 2012-03-28
> **Azrael84 said:**
> is it available via the software manager? or is there a repository I could add etc? I could only see a tarball on their website but I'd glady do it the other way if someone could point me to a PPA or whatever..

Sure. It's in the software manager. Just search for Cairo and install it (it will install the Cairo Session as part of the package).

If you want to be sure you have the latest stable version, go [here]("https://launchpad.net/%7Ecairo-dock-team/+archive/ppa").
If you want to live on the edge, go to the weekly unstable version [here]("https://launchpad.net/%7Ecairo-dock-team/+archive/weekly").

**Note:** Cairo Dock hasn't created a directory for 12.04. I installed the PPA myself to test it, but apt-get update gave me the following:

W: Failed to fetch [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

Double checked the website and nothing is there for precise. Just install the version in software manager.

---

### Post by gradinaruvasile on 2012-03-28
Ummm.. The OP was talking about libcairo? Not cairo-dock...

---

### Post by neu5eeCh on 2012-03-28
> **gradinaruvasile said:**
> Ummm.. The OP was talking about libcairo? Not cairo-dock...

Oops... my bad then. #-o

---

### Post by Azrael84 on 2012-03-28
> **gradinaruvasile said:**
> Ummm.. The OP was talking about libcairo? Not cairo-dock...

hehe, yeah libcairo..so I'm guessing I'm stuck with the tar then? if so does anyone know why after I run ./configure, then  do make, a makefile is not found? thanks

---

### Post by Harry33 on 2012-03-29
> **Azrael84 said:**
> is it available via the software manager? or is there a repository I could add etc? I could only see a tarball on their website but I'd glady do it the other way if someone could point me to a PPA or whatever..

There is a repository (xorg-edgers) where you can find cairo 1.12.
Here:
[https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise](https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise)

The version is 1.12 plus changes up to 25th March (git version).

---

### Post by Azrael84 on 2012-03-29
> **Harry33 said:**
> There is a repository (xorg-edgers) where you can find cairo 1.12.
Here:
[https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise")

The version is 1.12 plus changes up to 25th March (git version).

Thanks, I added the PPA as described on the website and did apt-get-update, but still when I search in software manager for libcairo the version displayed is 1.10 not 1.12; is there something I'm missing? sorry to be a pain..

---

### Post by ricotz on 2012-03-29
> **Azrael84 said:**
> Thanks, I added the PPA as described on the website and did apt-get-update, but still when I search in software manager for libcairo the version displayed is 1.10 not 1.12; is there something I'm missing? sorry to be a pain..

I think you might want to go with ppa:ricotz/testing while I am not sure you want to go with xserver 1.12 what a simple "apt-get upgrade" will give you with ppa:xorg-edgers/ppa!

---

### Post by Azrael84 on 2012-03-29
> **ricotz said:**
> I think you might want to go with ppa:ricotz/testing while I am not sure you want to go with xserver 1.12 what a simple "apt-get upgrade" will give you with ppa:xorg-edgers/ppa!

thanks this worked

EDIT: although of on rebooting all my menus have gone a funny faded out grey, as has the calander etc (like the faded grey you might expect if items were unusable) arghh!

EDIT 2: also my system logs me out at some random points during browsing! are these issues something to with xserver? can I revert?

---

### Post by Azrael84 on 2012-03-30
I've purged the PPA and everything working again. Is there a way I can just get cairo from one of the PPAs without changing anything else?

---

### Post by ScislaC on 2012-03-30
You can get just cairo from the xorg-edgers ppa. Add the ppa to your sources and in synaptic you can reload/update the package list and explicity only choose cairo to upgrade.

You can also snag the same cairo packages (possibly outdated by a few days) from my ppa [https://launchpad.net/~scislac/+archive/gfx](https://launchpad.net/~scislac/+archive/gfx) (note, you probably don't want that version of Inkscape though unless you're looking to do testing of a pretty incomplete feature)

---

