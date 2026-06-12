---
title: "KDE and stability?"
date: 2010-03-26
forum: The Cafe
---

### Post by GepettoBR on 2010-03-26
This thread brought to you by a long-time GNOME user determined to be lured in by the sirens of KDE's eye-candy. Disclaimer, lest this post become flamebait: Any reference I make to A being "better", "faster", "more stable" or any other comparative to B is based on my own experience and not meant as a broad or general comparison. Your mileage certainly varies.

Ever since I first started using Linux three years ago, I've been a GNOME user. My first Linux OS was Ubuntu Feisty. Currently I'm on Ubuntu Karmic for my PC and Crunchbang (lightspeed, BTW) on my laptop. KDE 3 never appealed to me, but KDE4 did - largely Amarok 2 and Kopete's fault, but also the fact that the whole desktop seemed to me better integrated, and especially because GNOME apps behaved better in KDE than KDE apps in GNOME. I tend to mix and match a lot, so this was really important to me.  Thus, it's been a while since I've wanted to switch, but I haven't been able to just yet. Until I tried Gentoo, KDE would always crash, freeze, slow down to a crawl, kill X or generally bully my processor somehow.

On every new *ubuntu release, I always check out Kubuntu, but it's never even half as stable on my machine as GNOME Ubuntu. I once read somewhere (in a rather unkind tone) that the Ubuntu devs are just really bad at managing the KDE packages, that Kubuntu is an afterthought. The general message of the article was "if you want KDE, steer clear from Ubuntu". I wanted to test that theory, so I began distro-hopping (I always keep a small partition free for testing new-to-me distros). I tried Arch Linux to see what KDE was like on a KDE-centric distro (since it's at least true that Ubuntu focuses a lot more on GNOME) but I hated the package manager and the community seemed to me a bit stuck up - though hopefully I just had a bad sampling. Sabayon Linux was awfully flaky. openSUSE seemed determined to drag me into dep hell at every package upgrade. Until last month, I had never known what a stable and friendly KDE4 system was like.

I went ahead and did a stage 3 installation of Gentoo (a project I had given up on twice in the past) and emerged the KDE SC 4.4.1. I was amazed at how fast and stable it was, and was extremely impressed with the power and straightforwardness of portage. "Finally", I thought, "this is what *proper* KDE4 feels like!"

All through the distro hops, I always came back to Kubuntu when a new release was out. It was always either slow or unstable, or both.

I'm determined to switch to KDE and while portage has its (overwhelming) advantages, it is time-consuming to manage Gentoo and on that front you can't beat the simplicity of dpkg and apt. There are other reasons I'd rather stick with *ubuntu as well. This leads me to these questions:

I heard there's a KDE PPA for *ubuntu. Are the packages there a bit more reliable than those in the main repos? Alternatively, are the packages in the main repos more stable now than when Karmic was released? Is it possible to get a fast and stable Kubuntu without building it all myself (in which case I should just stick with Gentoo anyway) or sticking with an older version?

On a slightly unrelated note, I intend to try sidux in the near future as well: it seems to bring the best of both worlds: dpkg and a rolling-release schedule, but I'm concerned with just how stable it would be, since it pulls its packages from Sid. Would anyone care to share their experiences with sidux?

---

### Post by macogw on 2010-03-26
Generally, the people who focus on the Ubuntu GNOME desktop do not focus on the Kubuntu KDE desktop, and vice versa.  But yes, there are fewer Kubuntu-specific people.

You may want [https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports) for new releases of KDE on stable versions of Kubuntu.  All other Kubuntu PPAs are for testing new packages.  We do try to make sure these are in good shape.

---

### Post by TetsuoD on 2010-03-26
Apart from Konqueror & Kopete, Kubuntu is actually pretty good now. 

Default fonts are still ugly tho.

---

### Post by lykwydchykyn on 2010-03-26
I haven't done the rounds to get a full sampling of all the KDE distros out there, but in my own experiences with Kubuntu, most of my stability problems come from one of the following:
 - weird cruft in my config files
 - using dodgy plasmoids from kde-look (some of which I'm responsible for)
 - Using kde components from different sources that were compiled against different versions of KDE or Qt libraries.

I don't know, but I'd assume nothing is going to run better or more stable than software that was all compiled on the same machine against the same libraries.  But as far as binary distributions with Debian package management go, Kubuntu is about the best I've seen if you want the newest versions of KDE when they're released.  Don't know what Sidux has, but Debian sid is still at 4.3 last time I checked.

If you find a better solution, let me know!

---

### Post by GepettoBR on 2010-03-28
Thanks for your replies.

> **macogw said:**
> Generally, the people who focus on the Ubuntu GNOME desktop do not focus on the Kubuntu KDE desktop, and vice versa.  But yes, there are fewer Kubuntu-specific people.Sorry, I didn't mean to imply that they do. When I said that "Ubuntu" focuses more on GNOME I meant that in general more man-hours are put into it. It wasn't criticism either, just a comment. GNOME is a great DE and the work that's been put into projects like NotifyOSD (much better than Knotify, IMO), Empathy and more recently Gwibber by the Ubuntu devs is really something - then again, why choose to invest in GNOME-specific apps? That's what I meant.

> **macogw said:**
> You may want [https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports) for new releases of KDE on stable versions of Kubuntu.  All other Kubuntu PPAs are for testing new packages.  We do try to make sure these are in good shape. Thanks! =D So this PPA is more or less suitable for use in a production environment?

> **lykwydchykyn said:**
> I haven't done the rounds to get a full sampling of all the KDE distros out there, but in my own experiences with Kubuntu, most of my stability problems come from one of the following:
 - weird cruft in my config files
 - using dodgy plasmoids from kde-look (some of which I'm responsible for)
 - Using kde components from different sources that were compiled against different versions of KDE or Qt libraries. The cruft was put in there somehow... that's the part that might be the release managers' fault. As for the other two, the problems I've experienced were all present in fresh installs as well. Maybe I'm just unlucky.

---

### Post by Xbehave on 2010-03-28
> **GepettoBR said:**
> The cruft was put in there somehow... that's the part that might be the release managers' fault. 
There are so many settings, in so many apps that change and I'm yet to find a list of changes for 4.3->4.4 so while i think the kubuntu devs should fix this, without help from upstream I don't see it happening any time soon.

I've been running 4.4 since the first beta (using kubuntu ppas) and I've rarely come across any kubntu specific problems, in fact generally the only problems I've had are those lykwydchykyn describe. Perhaps i'm lucky but I've found kubuntu to be very stable in 4.3/4.4 (i stuck with kde3 and debian before then)

---

### Post by snowpine on 2010-03-28
sidux is definitely worth checking out a live CD. It is by definition unstable (based on Sid) but in Debian-talk "unstable" means "constantly updated rolling release," not "beta software that will crash all the time." Ubuntu is based on Sid after all. :) Plus the sidux community posts update warnings that you can read before updating your system, usually if there is a major issue you just hold off on updating for a couple of days, wait for the "all clear" from the forums. Really this is good advice for any distro, especially rolling release. :)

The current sidux live CD (2009-4) uses KDE 4.3 but I think they will have a new release soon with 4.4. 

I have not tried Kubuntu personally. I've read some good things about KDE in OpenSUSE: [http://www.tuxradar.com/content/get-best-kde-linux-distro](http://www.tuxradar.com/content/get-best-kde-linux-distro)

---

### Post by kaldor on 2010-03-28
If you want the best KDE experience learn how to use OpenSUSE, Slackware, Arch, Chakra, Mint KDE CE, Mandriva or PCLinuxOS. 

OpenSUSE has the best presentation of KDE by far, but the problem is that OpenSUSE is a total pain and aggrevation to work with. Mandriva follows close behind, but I feel like Mandriva isn't a good choice. I didn't really enjoy it.

Slackware/Arch/Chakra are other distros you may try, but they are a lot harder to set up than your average OS. But, the KDE provided with Slackware is the default, so you get to see KDE's intended software and layout. Arch has its own "KDEmod" I think it's called. Chakra is based on Arch, is easier to use, BUT it's free (liberty) so proprietary drivers aren't there.



I used KDE on and off for the last few years I have used Linux. I loved KDE 3.5, but I hated the cartoony, non-serious feeling I got whenever I used it. KDE4 is amazing, but in some aspects it just isn't ready. When KDE4 apps stop crashing, I'll use it. I was using KDE4 on a few distros since January, but had to go back to GNOME because I kept having stability problems. 


Here's how most people usually look at it.

GNOME: Simple, idiot-friendly, new-age Linux GUI.
KDE: The more traditional "UNIX" GUI with the users usually being more advanced, though it's not really that hard to use.


Good luck :)

---

### Post by GepettoBR on 2010-03-28
> **snowpine said:**
> The current sidux live CD (2009-4) uses KDE 4.3 but I think they will have a new release soon with 4.4. Thanks, I'll keep an eye on it!

> **kaldor said:**
> If you want the best KDE experience learn how to use OpenSUSE, Slackware, Arch, Chakra, Mint KDE CE, Mandriva or PCLinuxOS. 
From that list, the only one I haven't tried is PCLinuxOS. Arch and Chakra have an awful package management system (though it loses to openSUSE's Yast, which seems incapable of doing what it was designed to do). Mint has the same problems as Kubuntu (From what I've seen, it's Kubuntu with a dedicated artwork team - a great artwork team). Mandriva was one of the first I tried... I can't even remember why I didn't like it. =D You didn't mention sidux! I'm really interested in it. I'll probably take it for a test drive next weekend.

But If I end up leaving the safe haven of the Debian family, it'll be in favor of Gentoo. KDE on Gentoo is slick and fast - it actually uses less RAM and is less CPU-intensive on my PC than GNOME in Ubuntu. Needless to say it runs laps around Windows 7. After a week to get it properly installed and configured, it has been the best Linux experience I've ever had, right up there next to Ubuntu GNOME (since Jaunty, anyway).

---

