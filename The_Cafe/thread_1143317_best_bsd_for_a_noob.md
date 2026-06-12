---
title: "best bsd for a noob?"
date: 2009-04-29
forum: The Cafe
---

### Post by mamamia88 on 2009-04-29
i want to try bsd what would be the best one in your opinion to try?

---

### Post by swoll1980 on 2009-04-29
For simplicity, nothing comes close to PC-BSD

---

### Post by mamamia88 on 2009-04-29
cool i'll download that how hard would it be to add to a current dualboot of jaunty and windows 7?

---

### Post by swoll1980 on 2009-04-29
> **mamamia88 said:**
> cool i'll download that how hard would it be to add to a current dualboot of jaunty and windows 7?

Depends. Do you know how to edit Grub?

---

### Post by mamamia88 on 2009-04-29
i know how to add lines to the grub menu i would just have to find the entry for it right?

---

### Post by swoll1980 on 2009-04-29
> **mamamia88 said:**
> i know how to add lines to the grub menu i would just have to find the entry for it right?

You would have to add a line that points to the bsd kernel. There's probably a few tutorials floating around that would make it easy. If you install the bsd boot loader, it doesn't auto add preexisting installations so I wouldn't go that route, or you would have to learn how to manage that loader instead,

---

### Post by mamamia88 on 2009-04-29
thanks i want to give it a go since i installed jaunty my spacebar has stopped working randomly and maybe bsd will work better for m could i install gnome on it?

---

### Post by swoll1980 on 2009-04-29
> **mamamia88 said:**
> thanks i want to give it a go since i installed jaunty my spacebar has stopped working randomly and maybe bsd will work better for m could i install gnome on it?

You can, but you can't uninstall KDE it's tied into the system, or at least it used to be.

---

### Post by mamamia88 on 2009-04-29
is there a bsd with gnome default?

---

### Post by swoll1980 on 2009-04-29
> **mamamia88 said:**
> is there a bsd with gnome default?

All the other bsds I know of are kde, or text based, and have no desktop by default. They have to be manually installed, and configured, and are not for the faint of heart.

---

### Post by mamamia88 on 2009-04-29
dang theres something i just don't like about kde

---

### Post by .Maleficus. on 2009-04-29
> **mamamia88 said:**
> is there a bsd with gnome default?
There are quite a few BSDs with *nothing* as their default...  FreeBSD can be installed with X right away and afterwards all you need to do is install Gnome.  It can be installed with pkg_add or through Ports.

[http://www.freebsd.org/gnome/docs/faq2.html](http://www.freebsd.org/gnome/docs/faq2.html)

---

### Post by swoll1980 on 2009-04-29
> **mamamia88 said:**
> dang theres something i just don't like about kde

Yeah me too. PC-BSD is real nice though if you can get past the KDE4 thing when I used it it was KDE3.5 which imo was way better than 4.2

---

### Post by kk0sse54 on 2009-04-29
You might also want to try out DesktopBSD although the last official release of the project is quite dated however I don't what state their development snapshots are in. In my personal brutally honest opinion PC-BSD is BSD done wrong, you might like such concepts such as PBIs but I've never been a fan of them. If you're willing to read the fantastic documentation available and get dirty doing a little work you might want to also look into trying one of the big three, FreeBSD, OpenBSD, or NetBSD although it can be a struggle for newcomers especially linux users who expect BSD to act like linux.

---

### Post by swoll1980 on 2009-04-29
> **.Maleficus. said:**
> There are quite a few BSDs with *nothing* as their default...  FreeBSD can be installed with X right away and afterwards all you need to do is install Gnome.  It can be installed with pkg_add or through Ports.

[http://www.freebsd.org/gnome/docs/faq2.html](http://www.freebsd.org/gnome/docs/faq2.html)

It's not as easy as just installing gnome. There is a lot of configuring involved in the Gnome installation(at least there used to be). If you have to install Nvidia that's another adventure. I wouldn't call this the  good approach for noobs.

---

### Post by swoll1980 on 2009-04-29
> **C!oud said:**
>  In my personal brutally honest opinion PC-BSD is BSD done wrong, you might like such concepts such as PBIs but I've never been a fan of them. 

Why do you say this? If you don't like pbi why would you have to use it? All PC-BSD is, is FreeBSD with a preinstalled KDE set up, and some tools to make things easier. It's like what Ubuntu is to Debian.

---

### Post by kk0sse54 on 2009-04-29
> **mamamia88 said:**
> is there a bsd with gnome default?

[http://wiki.netbsd.se/Desktop_Project](http://wiki.netbsd.se/Desktop_Project), it's still in the planning early development stage though so it won't be available for a while. Otherwise I'm using Gnome in FreeBSD right now

---

### Post by mamamia88 on 2009-04-29
i know it's not bsd but what about solaris?

---

### Post by .Maleficus. on 2009-04-29
> **swoll1980 said:**
> It's not as easy as just installing gnome. There is a lot of configuring involved in the Gnome installation(at least there used to be). If you have to install Nvidia that's another adventure. I wouldn't call this the  good approach for noobs.
Having only installed Xmonad on FreeBSD this very well good be the case, but really, if you aren't willing to get your hands dirty why use a BSD flavor at all?  Maybe I didn't use it to its full ability but the only advantage it had for me over Linux was the bushier neckbeard that comes with saying you use a BSD.

---

### Post by swoll1980 on 2009-04-29
> **mamamia88 said:**
> i know it's not bsd but what about solaris?

Solaris is nice, but make sure you go in ready to compile some hardware drivers, and that you have a GiB of RAM. Multimedia might still be a problem as well. When I tried it, the mplayer package that gave you multimedia codecs was broken. Might work fine now though.

---

### Post by swoll1980 on 2009-04-29
> **.Maleficus. said:**
> but the only advantage it had for me over Linux was the bushier neckbeard that comes with saying you use a BSD.

So true! But with a distro like PC-BSD floating around it kind of kills some of the geek cred.

---

### Post by kk0sse54 on 2009-04-29
> **swoll1980 said:**
> Why do you say this? If you don't like pbi why would you have to use it? All PC-BSD is, is FreeBSD with a preinstalled KDE set up, and some tools to make things easier. It's like what Ubuntu is to Debian.

Becuase I don't like the concept of Windows like installers in place for package management. Sure ports is available for PC-BSD but I doubt most PC-BSD users use them and in my expierence mixing ports and pbi's has caused problems and it's even recommended to stick with pbi's. I also like DesktopBSD better than PC-BSD since although PC-BSD is described as > customized installation of FreeBSD I find DesktopBSD to be closer under the hood to FreeBSD.

---

### Post by Daisuke_Aramaki on 2009-04-29
My first trial with BSD was with FreeBSD, which i still use. Easy to set it up. And I had a very minimal set up just with fluxbox. But you need to do a lot of post configuration after the first install to load the appropriate modules to recognize most features, or even better compile them in the kernel. BSD's ports concept is something special, and its fantastic in my opinion. i did not try pcbsd, and never will, since i used kde in a very limited fashion. FreeBSD documentation and handbook are all what you need to troubleshoot issues that might crop up. all the answers that i needed when i ran into problems were covered there. 

i concur with the previous posts, that opensolaris needs minimum 1gig RAM. i experimented with opensolaris on my eee, and it was very sluggish. but if you have standard hardware, opensolaris should be great. i experimented with opensolaris, only for one reason, zfs. of course one can do that with freebsd, but i had quite a few kernel panics. but fortunately there was a fantastic post somewhere about installing a minimal opensolaris, without X. that was all i needed, since learning zfs was my priority. let me dig that link for you.

Edit: Here is the link for minimal opensolaris installation howto.

[http://alexeremin.blogspot.com/2008/12/minimum-opensolaris-200811-install.html]("http://alexeremin.blogspot.com/2008/12/minimum-opensolaris-200811-install.html")

---

### Post by swoll1980 on 2009-04-29
> **C!oud said:**
> Becuase I don't like the concept of Windows like installers in place for package management. Sure ports is available for PC-BSD but I doubt most PC-BSD users use them and in my expierence mixing ports and pbi's has caused problems and it's even recommended to stick with pbi's. I also like DesktopBSD better than PC-BSD since although PC-BSD is described as  I find DesktopBSD to be closer under the hood to FreeBSD.

I'll agree that FreeBSD is better if your OK with the bare bones install, simply because I don't like kde, and bare bones is the only way to solve that problem. I never used the pbi when I was using PC-BSD, so I can't comment on how it works.

---

### Post by kk0sse54 on 2009-04-29
> **Daisuke_Aramaki said:**
> 
i concur with the previous posts, that opensolaris needs minimum 1gig RAM. i experimented with opensolaris on my eee, and it was very sluggish. but if you have standard hardware, opensolaris should be great. i experimented with opensolaris, only for one reason, zfs. of course one can do that with freebsd, but i had quite a few kernel panics. but fortunately there was a fantastic post somewhere about installing a minimal opensolaris, without X. that was all i needed, since learning zfs was my priority. let me dig that link for you.

Edit: Here is the link for minimal opensolaris installation howto.

[http://alexeremin.blogspot.com/2008/12/minimum-opensolaris-200811-install.html]("http://alexeremin.blogspot.com/2008/12/minimum-opensolaris-200811-install.html")

@OP as well as doing a minimal OpenSolaris install there a number of OpenSolaris derivatives such as [MilaX]("http://www.milax.org/") that attempt to build a minimal distrobution based off of OpenSolaris

---

### Post by jimi_hendrix on 2009-04-29
> **swoll1980 said:**
> Yeah me too. PC-BSD is real nice though if you can get past the KDE4 thing when I used it it was KDE3.5 which imo was way better than 4.2

i like the shell thing in the background of PC-BSD...too bad it wasnt gnome...the menu in PC-BSD doesnt match the rest of the theme imo

---

### Post by thisllub on 2009-04-29
I prefer OpenSolaris to BSD because VirtualBox works.
Just install a Linux or Windows VM for the software you just can't be without.

It is pretty hard wired to Gnome which annoys me but everything else is pretty good. If I could get OpenBox to compile I would be happy.

Multimedia works fine and it has functioning power management for my Acer laptop. Something that Linux can't do.

---

### Post by kk0sse54 on 2009-04-29
> **mamamia88 said:**
> i want to try bsd what would be the best one in your opinion to try?

I just came across this, might be of interest to you [http://www.virtualbsd.info/](http://www.virtualbsd.info/), of course it requires vmware but it will alow you to play around with FreeBSD a bit.

---

