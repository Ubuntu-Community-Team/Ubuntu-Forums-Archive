---
title: "More Format Wars"
date: 2022-05-13
forum: The Cafe
---

### Post by Shibblet on 2022-05-13
What is the vested interest Canonical has in Snaps?  I mean, why not just support FlatPak?

I know Sony had a lot of money into Blu-Ray, and therefore had to fight with HD-DVD.
Same with Beta / VHS.  There were monetary interests at stake.

But, it doesn't seem this way with Snaps and FlatPak (or even AppImage).

So, why push Snaps so much?  Why not do what the Beatles sang about, and Come Together?

---

### Post by GhX6GZMB on 2022-05-13
Who cares? People vote with their feet.
The very few applications that are only available as snaps or flatpack can be counted on one hand.
Everything else is still there as .deb.
If you don't like Canonical, MS is still in business.

---

### Post by Tadaen_Sylvermane on 2022-05-14
[COLOR=#000000]> What is the vested interest Canonical has in Snaps? I mean, why not just support FlatPak?

Same reason they tried to use Upstart. Gave it up after awhile and went with the new standard. They came up with it so they decided to try to use it.
Then there was Unity. Customized version of Gnome. That's gone now to. (open sourced but not pushed by Ubuntu rather)
Snap is next in the list. 

I think the idea is they came up with something and don't intend to abandon it unless it becomes blatantly obvious that it's inferior. Companies are usually proud of their product. Until one becomes dominant for a decent reason they will all coexist. I also believe their vision is for software to be irrespective of distro or package manager. Noble of course but it also goes against some of the things that make linux stuff great. I wish one could come out on top, don't much care which though. I dislike multiple "app stores" concept so to speak. I would love to get everything in one spot and be done.

One could easily ask that question about why so many distros themselves. If they all came together we might see something truly incredible. But philosophy rules the world apparently. And then the age old question "who decides what we want". The biggest irony is linux's biggest strength (to me) is also it's biggest weakness. The way things currently are it is extremely efficient and easy to mold. However it also is difficult to get the "big name" software because every distro has some little difference and the devs refuse to bother. Who can blame them? They can't possibly figure every niche case. All distros use stuff in /usr/bin except distro x which puts it all in /bin... stuff like that. Not sure if that's a good example but the point is these minor minor MINOR differences are part of the problem for big software. Consistency is necessary.
[/COLOR]

---

### Post by TheFu on 2022-05-14
Flatpak - NIH (Not Invented Here). Created by RedHat.

Snaps - came from Canonical's years working on Ubuntu Phone. They want our computers to be single-user phones that aren't really network connected on a LAN with centralized user and storage management (except via their snap store).  

AppImages are very different from snaps or flatpaks. AppImages don't bring any constraints or extra security.  They don't auto-update either and there isn't a command built-in that will autoupdate.  

Snaps autoupdate - even when we don't want those updates. It is the Windows10 method. You get it when we say. The default updates are checked 4 times a day. It is possible to change that. To check only on Saturdays:
```
$ sudo snap set system refresh.timer=sat 
```
Sadly, the manpage for snap doesn't have these things documented. Boooo. [https://snapcraft.io/docs/keeping-snaps-up-to-date](https://snapcraft.io/docs/keeping-snaps-up-to-date) says it is possible to hold all snaps, thus preventing updates. refresh.hold can delay updates for up to 90 days. Actually, I think that is very reasonable.  I can see a need to prevent updates for a few weeks, say while on travel, but forcing an update eventually **is** an excellent idea.

Flatpaks auto update a few minutes after a reboot. There are flatpak tools which can update all the flatpaks installed. I haven't looked into flatpaks too much, as the main mandated package of this type that I'm forced to use is only  lxd and it is only shipped as a snap - not available in any other manner.  Boooo.

Ubuntu Core is a step in this snap-only direction. Only snaps can be installed and only through a registered account connected to the internet.  This is good and bad.  Good for centralized IoT device makers who want/need to maintain their systems remotely installed. Bad for home users or locations that don't have internet.

The main problem I have with using snaps is this:
> The snap daemon (snapd) requires a user’s home directory ($HOME) to be located under /home on the local filesystem. This requirement cannot currently be changed.
Effectively, they expect enterprises with thousands of users and network home directory mounts all to be moved to local disks and placed under /home/.  That isn't the real world.

---

### Post by QIII on 2022-05-14
Ii wonder if /home/user on the local machine can be a symbolic link to some remote directory elsewhere in the enterprise with snaps.  Or is that the exact problem?

---

### Post by grahammechanical on 2022-05-14
> [COLOR=#000000]Same reason they tried to use Upstart. Gave it up  after awhile and went with the new standard. They came up with it so  they decided to try to use it.
Then there was Unity. Customized version of Gnome. That's gone now to. (open sourced but not pushed by Ubuntu rather)
Snap is next in the list. [/COLOR]

Upstart was code that started tasks and services during boot time. Debian used it. RedHat came up with SystemD and RedHat employees working on Debian pushed for SystemD to replace Upstart. There was an almighty argument among Debian developers. Canonical employees who were Debian developers were told by Mark Shuttleworth to keep out of the dispute. Those Debian developers who lost the argument left Debian and forked the code to produce Devuan which uses Upstart and not SystemD

When Debian switched to SystemD then Canonical also switched to SystemD because Ubuntu is based upon Debian. It was cheaper to go with the flow. Unity was not a customized version of Gnome. It was a completely new user interface that run on a new display server called Mir. The intention, or hope as you would call it, was for Mir and Unity to not only be a phone OS but part of a system where a Ubuntu phone could be turned into a Ubuntu desktop computer with the addition of monitor, keyboard and mouse.

Oh, by the way, you forgot to mention Ubuntu TV that was to be the OS on smart TVs. Yes, Ubuntu TV used Mir and Unity. Snap packaging started out as Click packing. It was a method of packaging that would have made phone apps very secure. No data mining of users personal information.

I do not see anything wrong with Canonical being innovative or disruptive as Mark Shuttleworth used to call it. Up to the present time all versions of Ubuntu are still available to download, install and distribute without charge to the user no matter how many machines the user installs Ubuntu on. We get a very good deal from Canonical. There are other distributors of Linux who make far greater profits than Canonical does. 

Regards

---

### Post by DuckHook on 2022-05-14
> **QIII said:**
> Ii wonder if /home/user on the local machine can be a symbolic link to some remote directory elsewhere in the enterprise with snaps.  Or is that the exact problem?
I've tried in a slightly different capacity and symlinks don't work. But a bind mount does—well, kinda sorta.

Something to do with the sandboxing. It's all way over my head, but to my understanding, one of the benefits of snaps is its sandboxing. However, the way that some forms of malware try to fool the system is through a process similar to symlinking. So, the snap devs designed snaps to effectively disallow symlinks. This is true even if you enable remote disk access, which is in turn only possible if the app dev had the foresight to build such access into the snap in the first place. Some devs insufficiently familiar with snaps or who haven't foreseen such a need don't allow remote disk access, so such apps are broken until patched. This last is probably just a teething pain though.

But aren't bind mounts limited to only physically connected disks? I've never tried them on a network directory, so wouldn't know. If only physical disks, then that would be another limitation.

---

### Post by DuckHook on 2022-05-16
> **grahammechanical said:**
> …I do not see anything wrong with Canonical being innovative or disruptive as Mark Shuttleworth used to call it. Up to the present time all versions of Ubuntu are still available to download, install and distribute without charge to the user no matter how many machines the user installs Ubuntu on. We get a very good deal from Canonical. There are other distributors of Linux who make far greater profits than Canonical does…
Excellent sentiments.

I've always said that Canonical should be applauded for at least trying to tackle HW platforms that other distros don't even look at.

I for one am saddened that Ubuntu couldn't successfully transition to phones and tablets. As I close in on my objective of de-Gogglefication, I am painfully reminded every day of how much I miss such an alternative.

---

### Post by GhX6GZMB on 2022-05-16
> **DuckHook said:**
> Excellent sentiments.
I've always said that Canonical should be applauded for at least trying to tackle HW platforms that other distros don't even look at.

That's the smallest thing that Canonical has done. And that's done more by the developers.

Canonical's made the effort to offer a comprehensive, consumer-friendly OS collected/comprised from open-source software. In this case (x)ubuntu.
The work of the open-source community has been immense, and the results are mind-boggling.
But trying to find consensus on a distribution is like hearding cats... it just won't work. Personal animosities, differing views, different priorities etc. makes it hopeless.

The value of Canonical is putting together a distribution that is viable for a consumer. And you need a commercial mindset for that.
This has been very successful, and I'm grateful to Canonical for it. It will not make them billionaires like M$, but the idea of making money of consulting for other companis using Linux and having (x)ubuntu as a basis for that makes sense.
It's a symbiosis.

Red Hat tried the same thing, but weren't really succesful. Too early, perhaps.

---

### Post by grahammechanical on 2022-05-16
I am reminding myself of the foundation principle of Free and Open Source Software.

> **the users have the freedom to run, copy, distribute, study, change and improve the software**.

[https://www.gnu.org/philosophy/free-sw.en.html](https://www.gnu.org/philosophy/free-sw.en.html)

The result is fragmentation or increased choice. Look at it anyway you want. I count 45 discontinued Linux distributions as listed by Wikipedia. Not all FOSS projects survive the march of time.

[https://en.wikipedia.org/wiki/Category:Discontinued_Linux_distributions](https://en.wikipedia.org/wiki/Category:Discontinued_Linux_distributions)

It is still possible for a few programmers to produce a Linux distribution that meets their own choice of what a Linux distribution should be. Check out Ubuntu unity. It only has 5 programmers.

[https://ubuntuunity.org/](https://ubuntuunity.org/)

All these kind of independent programmers are heavily dependent on the work of others just as Canonical is dependent on other software projects for Ubuntu. This situation may not have been in the mind of Richard Stallman when he developed the idea of F.O.S.S but it is the harvest of the seed he sowed all those years ago. And those of us who try to think for ourselves are benefiting from FOSS.

Regards

---

### Post by DuckHook on 2022-05-17
> **grahammechanical said:**
> …This situation may not have been in the mind of Richard Stallman when he developed the idea of F.O.S.S but it is the harvest of the seed he sowed all those years ago. And those of us who try to think for ourselves are benefiting from FOSS.
Not only such as those of us who try to think for ourselves.

It is simultaneously gratifying, inspiring, humbling and maddening that FOSS has also benefited the entire human race: from trillion dollar tech&#8209;giants like Apple, Google and Facebook to their billionaire owners to appreciative geeks like us to the masses who are oblivious to its very existence to even the malevolent trolls who sneer at what they neither understand nor have the sense to value.

On these forums, we frequently enumerate to newcomers, naysayers and the ill&#8209;informed the various ways in which FOSS in general and Linux in particular have conquered the IT space. But even we sometimes underestimate the debt we owe to RMS for the seed he sowed. Think what you like of him—and he has certainly courted controversy—but his legacy has been massive.

---

### Post by Shibblet on 2022-05-17
> **DuckHook said:**
> Not only such as those of us who try to think for ourselves.
Beautifully stated.

If it would only stay that way.  If true free-choice were allowed, it would be a beautiful system.  Unfortunately, I am starting to see how choice is slowly being chipped away at, one program at a time... one piece of hardware at a time... one EULA at a time.

---

### Post by Tadaen_Sylvermane on 2022-05-17
One of my favorite movies, [https://www.imdb.com/title/tt0128278/](https://www.imdb.com/title/tt0128278/) (Instinct 1999) deals with a general concept that fits the idea of a free society and life and the software world in this case. It's all an illusion. The illusion of control. The illusion of power. The illusion of choices. At the end of the day they can all disappear instantly through no fault of our own.

We think we're free. We aren't.

---

