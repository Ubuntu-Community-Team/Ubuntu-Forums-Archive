---
title: "Why is Ubuntu Debian rather than Gentoo based?"
date: 2007-11-27
forum: The Cafe
---

### Post by yeehi on 2007-11-27
What would the problem be of using the Gentoo Portage system, rather than taking Ubuntu's Debian route?

---

### Post by dptxp on 2007-11-27
I would not use Ubuntu then. I would go for Debian.

---

### Post by PmDematagoda on 2007-11-27
Ubuntu went Debian's way since Debian is rather stable and is also easy to use. And if you prefer a Gentoo based system why don't you use an OS like Sabayon?

P.S. You can get all the information you want simply by googling for it, so would you please try and google the information you want before you look to the forums?

---

### Post by jordanmthomas on 2007-11-27
> **yeehi said:**
> What would the problem be of using the Gentoo Portage system, rather than taking Ubuntu's Debian route?
Technically, there wouldn't be any problems that Gentoo didn't already have.  Same goes for Debian.  Why not choose Slackware?  Why not go with RedHat?
To answer your other question...they chose it over Gentoo because the people who made it liked Debian better?

---

### Post by Cochise on 2007-11-27
> **jordanmthomas said:**
> Technically, there wouldn't be any problems that Gentoo didn't already have.  Same goes for Debian.  Why not choose Slackware?  Why not go with RedHat?
To answer your other question...they chose it over Gentoo because the people who made it liked Debian better?

and Mark Shuttleworth was a Debian developer in the 1990's. Personally if Ubuntu changed base i would use either Debian itself (which I'm considering anyway) or openSuSE.

---

### Post by yeehi on 2007-11-27
WHy are you thinking of going to Debian?

I had never heard of Sabayon. I just checked it out. From what I can gather, it is a preconfigured version of Gentoo. 

I wouldn't use Slackware, as it does nothing to help noobers - i would have to sort out dependencies etc manually. It is not aimed at beginners.

Fedora and OpenSuse are RPM dependency hell.

---

### Post by PmDematagoda on 2007-11-27
I feel that Debian is rather good itself, especially considering that it is the pioneer of the .deb package system which is very easy to use. I personally am thinking of giving Debian a try myself since I heard a good deal about it's stability.

---

### Post by mellowd on 2007-11-27
Mark Suttleworth has a full explanation on his page explaining why they chose Debian

---

### Post by jordanmthomas on 2007-11-27
> **yeehi said:**
> I wouldn't use Slackware, as it does nothing to help noobers - i would have to sort out dependencies etc manually. It is not aimed at beginners.

Fedora and OpenSuse are RPM dependency hell.

Couple of things real quick:  I wasn't suggesting you use Slackware or anything else.  I was just wondering why you asked why Ubuntu is Gentoo based.  It could have just as easily been based on any of the others.  Also, there's ways to get dependency management in Slackware as well I believe.

I'd like to say that while the package management is a lot slower for me in RPM distros, dependencies are handled much better than they used to be.

---

### Post by rsambuca on 2007-11-27
> **yeehi said:**
> I wouldn't use Slackware, as it does nothing to help noobers - i would have to sort out dependencies etc manually. It is not aimed at beginners.

Fedora and OpenSuse are RPM dependency hell.

Did you just crawl out from under a rock or something?  Your comments are outdated FUD.

---

### Post by igknighted on 2007-11-27
> **yeehi said:**
> Fedora and OpenSuse are RPM dependency hell.

*sigh*

Gentoo gets your nod for a "helpful to newbs" distro, while OpenSuse and Fedora do not?  There is **_absolutely nothing_** wrong with RPM packages.  This "rpm dependency hell" is an old complaint that originated from the time when RPM was the ONLY package manager (in other words, before .deb existed).  Modern RPM packages are just as good as debian based systems at package management... in some cases debian does a hair better, and in other rpm does.  But overall they are very similar.

If you think Gentoo is that great (don't get me wrong, I love portage... but if you can't handle rpm, you can't handle portage), go play around with use flags, blacked/masked packages and poorly written ebuilds and come back and tell me how it was.

It's blatantly obvious that you have never used an RPM based distro.  Trust me, don't believe everything you hear.  Go try one out.  I'm not going to promise that you will like it, but it is just as capable at handling dependencies as any.deb system.  So try it out with an open mind... you might actually prefer it.

/rant

---

### Post by igknighted on 2007-11-27
> **jordanmthomas said:**
> I'd like to say that while the package management is a lot slower for me in RPM distros, dependencies are handled much better than they used to be.

Yum (Fedora) using fastest mirror and presto (deltarpm) plugins is at least as fast as apt.  If you want a GUI, download and use yumex instead of pirut (add/remove)... its a much better yum frontend, both layout and in how it works.

Zypper (opensuse) (aside from its slow repo-cache checking) uses deltarpms as well, and does its work quite quickly.  The repository system is top notch, the one-click install from the suse website is awesome, but the Yast package install module can be really slow and annoying at times.

Urpmi (mandriva) is a little more awkward to learn on the CLI (urpmi installs, urpme removes, etc.), but has the best GUI frontend and isn't slow by any stretch either.

Sry for the dp.

---

### Post by Seti on 2007-11-27
IIRC, from using gentoo once, package-management uses portage, which is actually some kind of port of the BSD ports system. This means that it actually builds all your programs right from the source-code, rather than using pre-compiled binaries like apt uses. 
To put it in perspective for you, installing the popular chat client aMSN took something like 5 minutes to install; *considerably* longer than the same operation using apt on debian. Now I don' t know if that was a big factor in ubuntu's popularity over gentoo, but to those of us for whom installing from binaries is not a problem, it might be. 
Regardless, even before there was ubuntu, debian was considerably more popular. I'd say package-management is a BIG factor in deciding a distro's popularity.

---

### Post by jrusso2 on 2007-11-27
I was using Fedora just before coming to use Ubuntu and I had a lot of dependency issues I am not blaming it on .rpm though just poor repository.

---

### Post by jordanmthomas on 2007-11-27
> **igknighted said:**
> Yum (Fedora) using fastest mirror and presto (deltarpm) plugins is at least as fast as apt.  If you want a GUI, download and use yumex instead of pirut (add/remove)... its a much better yum frontend, both layout and in how it works.

Zypper (opensuse) (aside from its slow repo-cache checking) uses deltarpms as well, and does its work quite quickly.  The repository system is top notch, the one-click install from the suse website is awesome, but the Yast package install module can be really slow and annoying at times.

Urpmi (mandriva) is a little more awkward to learn on the CLI (urpmi installs, urpme removes, etc.), but has the best GUI frontend and isn't slow by any stretch either.

Sry for the dp.

I know there's decent front-ends but the actual dependency-checking takes a while for me.  I'm not going to lie, though, I haven't used an RPM distro in about a year (since I found Arch -- pacman rocks pretty hard) so it's entirely possible that this has even been fixed.  I was just trying to say that dependency checking IS there.  In particular, I understand that yast has got a LOT better since I last used it.  Another front-end (sort of, it's almost a replacement I think) you didn't mention that's the fastest I've tried for rpms is smart (in case anyone cares :) )

---

### Post by jordanmthomas on 2007-11-27
> I'd say package-management is a BIG factor in deciding a distro's popularity.
I agree.  It's probably the first thing you have to deal with when trying a new distro (well, after its install) and for me at least it makes or breaks a distro.

Also, sorry for double post, but this one wasn't here when I made the first one.

---

