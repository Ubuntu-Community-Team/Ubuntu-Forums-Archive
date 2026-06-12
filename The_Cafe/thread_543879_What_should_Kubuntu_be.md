---
title: "What should Kubuntu be?"
date: 2007-09-05
forum: The Cafe
---

### Post by maybeway36 on 2007-09-05
Compared to other distributions that use KDE as their default (PCLinuxOS, Freespire, PC-BSD, etc.), Kubuntu is a lot closer to "pure KDE". Also, it is more KDE-centric than Ubuntu is GNOME-centric. This is probably because the main focus is going into regular Ubuntu, so Kubuntu can concentrate on its specialties. This poses the question:
**Is Kubuntu "Ubuntu with KDE," or a "KDE distro based on Ubuntu"?**
I think this is something that should be decided on. Kubuntu uses OpenOffice.org rather than KOffice, but there's no Restricted Drivers Manager and no GIMP or Firefox.
(On a related note, why does Ubuntu 7.04 come with GNOME Games, but Kubuntu not come with KDE Games? I always found this strange.)

---

### Post by LowSky on 2007-09-05
> **maybeway36 said:**
> ...I think this is something that should be decided on....

i disagree... (K)Ubuntu is a community and the community should decide what programs are preloaded

dont forget you can Kustomize (lol) it to look any way you want

---

### Post by happysmileman on 2007-09-05
I think OpenOffice is used because it's "Ubuntu with KDE", adn KDEGames aren't included because of space restrictions (probably same for Beryl), but if you used KOffice instead of OpenOffice I think this may be negated..

/me wants KDEGames by default

---

### Post by LowSky on 2007-09-05
beryl isn't included because it was never a stable release

the games was most likely an oversite

i dont get why firefox isn't included though?

---

### Post by misfitpierce on 2007-09-05
> **LowSky said:**
> beryl isn't included because it was never a stable release

the games was most likely an oversite

i dont get why firefox isn't included though?

That' a good point... only konqueror from start like KDE straight up. I think firefox should have been preloaded for new users looking to use it. I installed manually which did not take more than 10 seconds but it should be packed in like ubuntu :)

---

### Post by happysmileman on 2007-09-05
> **LowSky said:**
> beryl isn't included because it was never a stable release

Isn't Beryl or COmpiz included in Ubuntu, just not enabled by default?

---

### Post by lzfy on 2007-09-05
> **misfitpierce said:**
> That' a good point... only konqueror from start like KDE straight up. I think firefox should have been preloaded for new users looking to use it. I installed manually which did not take more than 10 seconds but it should be packed in like ubuntu :)

I hope not. Firefox on KDE sucks. I love the fact that Kubuntu comes only with qt apps. If you don't like konqueror use Opera instead, it integrates better with the K Desktop.

---

### Post by happysmileman on 2007-09-05
> **lzfy said:**
> I hope not. Firefox on KDE sucks. I love the fact that Kubuntu comes only with qt apps. If you don't like konqueror use Opera instead, it integrates better with the K Desktop.

I agree... i went into appearance, click get new themes, first one there was KDE theme :P

Also it's done in QT which is better than mixing GTK and QT apps (though sometimes it's inevitable)

---

### Post by Foxmike on 2007-09-05
IMHO, at least Restricted Package Manager should be included by default.  But because it has been built for Ubuntu, it has synaptic as dependency, hence a bloat of gnome libraries/dependencies, I think that's the main reason why it is not included.  Maybe a pyqt counterpart that relied on adept would be nice?

---

### Post by qazwsx on 2007-09-05
> **Foxmike said:**
> IMHO, at least Restricted Package Manager should be included by default.  But because it has been built for Ubuntu, it has synaptic as dependency, hence a bloat of gnome libraries/dependencies, I think that's the main reason why it is not included.  Maybe a pyqt counterpart that relied on adept would be nice?
[https://wiki.kubuntu.org/GutsyGibbon/Tribe4/Kubuntu#head-0efdc1f98d7fd27716478be21036c0ed5d10d778](https://wiki.kubuntu.org/GutsyGibbon/Tribe4/Kubuntu#head-0efdc1f98d7fd27716478be21036c0ed5d10d778)

---

### Post by igknighted on 2007-09-05
> **Foxmike said:**
> IMHO, at least Restricted Package Manager should be included by default.  But because it has been built for Ubuntu, it has synaptic as dependency, hence a bloat of gnome libraries/dependencies, I think that's the main reason why it is not included.  Maybe a pyqt counterpart that relied on adept would be nice?

But adept cannot handle sun java, because it doesn't open the window for you to accept the license.  Therefor they would need to do it in a totally different way... perhaps leading to the holdup?  I am assuming, of course, that sun-java is something that restricted-package manager would be capable of "managing".

---

### Post by lzfy on 2007-09-05
> **igknighted said:**
> But adept cannot handle sun java, because it doesn't open the window for you to accept the license.  Therefor they would need to do it in a totally different way... perhaps leading to the holdup?  I am assuming, of course, that sun-java is something that restricted-package manager would be capable of "managing".


Click on details next time when installing a package ;)

---

### Post by maybeway36 on 2007-09-05
> **LowSky said:**
> i disagree... (K)Ubuntu is a community and the community should decide what programs are preloaded

dont forget you can Kustomize (lol) it to look any way you want

I didn't say the community shouldn't decide...

My reasoning for asking is this: If Kubuntu emphasizes the Ubuntu part more, they should ship it with Firefox, GIMP, etc. If they emphasize the KDE part more, they should use KDE and Qt apps only.

---

### Post by stmiller on 2007-09-05
I agree with a lot of what maybeway36 says. After installing Kubuntu right from the disk I thought the default package choices were interesting. Not quite what I expected, but I guess you can always install what you like.

---

### Post by maybeway36 on 2007-09-05
On my main machine I used Adept Manager to get rid of all the packages starting with openoffice.org, then installed the koffice metapackage. Maybe this will help someone who wants to have an all-KDE system.

---

### Post by Jucato on 2007-09-05
1. It has already been decided long ago:[https://help.ubuntu.com/6.10/kubuntu/about-kubuntu/C/index.html](https://help.ubuntu.com/6.10/kubuntu/about-kubuntu/C/index.html)

Kubuntu is an operating system based on KDE. It is part of the larger Ubuntu project and uses Ubuntu as its base. But what you should note here is how Kubuntu uses Ubuntu as the base, or rather, what parts of Ubuntu are being used as base. Technically, everything from X down to the kernel is shared by Ubuntu and Kubuntu. Above that they diverge almost completely, except for a few other common packages.

Also, being derived from Ubuntu does not mean we need to follow Ubuntu's choice of apps. So

> My reasoning for asking is this: If Kubuntu emphasizes the Ubuntu part more, they should ship it with Firefox, GIMP, etc. If they emphasize the KDE part more, they should use KDE and Qt apps only.

Isn't true, for any distro derived from any distro.

Short answer: Kubuntu is more than just "Ubuntu with KDE".

2. OpenOffice.org vs. KOffice

OO.o was chosen over KOffice a long time ago, because at that time, the developers believed that KOffice wasn't good enough to be used as the default office suite, not because of any desire to imitate what's on Ubuntu. But KOffice has come a long way since then, so we're waiting for the time that [https://wiki.kubuntu.org/KubuntuKofficeByDefault](https://wiki.kubuntu.org/KubuntuKofficeByDefault) can come into effect, most probably by KOffice 2.0.

3. Konqueror vs. Firefox

This alone can spark many wars, so suffice it to say that the lead developers of Kubuntu want to show KDE as much as possible, whether in branding (the K Menu, the welcome pages, etc.) or in app selection (with the exception of OO.o). So Konqueror is there.

4. Restricted Manager, Restricted Extras, etc.

These will all be in Kubuntu 7.10 Gutsy Gibbon. Yes, sometimes new features come 1 release later than Ubuntu. The reason is that these features are mostly built on the Ubuntu side alone, with very specific GTK dependencies. It takes time to port them to Qt/KDE. And we usually don't get a chance to work on that until after the feature has been released. The good side is that it gets to be tested on Ubuntu users and probably become stable before it enters into Kubuntu.

5. Java and Adept

This bug has been fixed since Feisty. A dialog box will popup for anything that requires a license agreement.

Anything else I missed? :)

---

### Post by Foxmike on 2007-09-05
> **qazwsx said:**
> [https://wiki.kubuntu.org/GutsyGibbon/Tribe4/Kubuntu#head-0efdc1f98d7fd27716478be21036c0ed5d10d778](https://wiki.kubuntu.org/GutsyGibbon/Tribe4/Kubuntu#head-0efdc1f98d7fd27716478be21036c0ed5d10d778)
Ok, well, I should search before to speak :oops:
 
That's quite nice, tho!:)

---

### Post by Fbot1 on 2007-09-05
I think it should be the average KDE install.

---

### Post by maybeway36 on 2007-09-06
Thanks for clearing that all up. I suppose they had to include Konqueror anyway as the file manager, so that makes sense. You can pretty much install anything open-source from the repos, one of the reasons I love (K)ubuntu so much :)

---

### Post by awakatanka on 2007-09-06
For me i hope kubuntu will be a QT thing from start, so i hope koffice 2  will be the standard. One thing i don't like is that Dolphin will be default in gutsy, but i can easily change it with 3 clicks. 

I don't like the system settings because it back back and forward thing and like kcontrol more but thats also easily solved. But if they want something like that they better take a look at control center from mandriva because its better. 

For the future i hope all things will go the right way with KDE 4 and integrate LinuxMCE with KDE 4. [http://dot.kde.org/1187201437/](http://dot.kde.org/1187201437/)

---

### Post by DigitalDuality on 2007-09-06
d

---

### Post by happysmileman on 2007-09-06
> **DigitalDuality said:**
> kubuntu team should just stop.  seriously.  it's awful.  and i love kde compared to all other DEs.

Ubuntu + KDE is far superior to Kubuntu in everyway.

In the same way that development should stop on every single distro and piece of software that you don't like

---

### Post by pelle.k on 2007-09-06
> In the same way that development should stop on every single distro and piece of software that you don't like
LOL. Good one! :D

Serisouly though, i agree that "ubuntu core + KDE" is in some ways superior to "kubuntu-desktop"...
Kubuntu is the best kde distro i know of, and at the same time it's the worst! Some moves just amazes me like the dumbed down "control center" and the exclusion of the "window" menu in konqueror. Why would you make software stupid? i.e. removing features that people actually find useful?
That and small things like why you can't add a "link to storage device" if it's already mounted from fstab. It will fail if you click on it.

---

### Post by Xanatos Craven on 2007-09-06
> **pelle.k said:**
> LOL. Good one! :D

Serisouly though, i agree that "ubuntu core + KDE" is in some ways superior to "kubuntu-desktop"...
Kubuntu is the best kde distro i know of, and at the same time it's the worst! Some moves just amazes me like the dumbed down "control center" and the exclusion of the "window" menu in konqueror. Why would you make software stupid? i.e. removing features that people actually find useful?
That and small things like why you can't add a "link to storage device" if it's already mounted from fstab. It will fail if you click on it.
Ubuntu's a GNOME-centric distro. Of course they're going to remove features and make software stupid on KDE too, it's a habit that can't be broken. :P

Don't know what their problem is with kcontrol, though. If anything, it should at least be displayed by default in the menu as an alternate power-user control panel, if they're that bent on pushing system-settings on us.

---

