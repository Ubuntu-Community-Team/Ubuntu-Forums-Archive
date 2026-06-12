---
title: "Distro with stable core and latest apps?"
date: 2009-10-25
forum: The Cafe
---

### Post by cdekter on 2009-10-25
(Dear Lazyweb)

Does anyone have experience with or know of a Linux distro out there that specialises in having a stable core (kernel, drivers, etc) with up-to-date applications (Gnome, Firefox, etc etc)? Similar to the Windows model in fact - core stays fairly constant for several years, applications updated more frequently.

Debian's stability is good but being stuck with Firefox 3.0 isn't...

---

### Post by Warpnow on 2009-10-25
Have you considered just adding PPAs?

IF you want daily releases of Firefox, add the daily PPA. Most projects seem to have one.

---

### Post by cdekter on 2009-10-25
Yes I have tried that in the past... but often the PPAs contain unreleased versions of the software (particularly the Firefox one).

---

### Post by kk0sse54 on 2009-10-25
Debian Testing perhaps

---

### Post by dragos240 on 2009-10-25
Hmm.... stable core... latest apps. Archlinux is for you. If it's not in the repository, it's in the AUR.

---

### Post by kk0sse54 on 2009-10-25
...

---

### Post by Skripka on 2009-10-25
> **dragos240 said:**
> Hmm.... stable core... latest apps. Archlinux is for you. If it's not in the repository, it's in the AUR.

I'll warn you, a whole crowd of UFers are going to yell at you for mentioning the "A Word"

---

### Post by dragos240 on 2009-10-25
> **Skripka said:**
> I'll warn you, a whole crowd of UFers are going to yell at you for mentioning the "A Word"

Well. That's pretty funny considering you have it mentioned 2 times in your signature.

---

### Post by Crunchy the Headcrab on 2009-10-25
I would use Arch if I wasn't such a n00b.  I got it running once and even had DE and my graphics driver running but I couldn't get networking to work.

---

### Post by Dharmachakra on 2009-10-25
You may find that you need to update certain 'core' packages to install the lastest versions of your applications. 

When I updated to Gnome 2.28, I had to upgrade some forty other packages.

---

### Post by cariboo on 2009-10-25
There is no way you can have a distro with a stable core and the latest apps, newer apps mean newer dependencies. Another thing to keep in mind is there are kernel updates to fix bugs and security problems.

---

### Post by dragos240 on 2009-10-25
> **Crunchy the Headcrab said:**
> I would use Arch if I wasn't such a n00b.  I got it running once and even had DE and my graphics driver running but I couldn't get networking to work.

Networking didn't work? You can easily do:
dhcpcd

for an ethernet connection, and follow the instructions for wireless. I got a netbook running archlinux. Speaking of which, I am using this riht now. It's running archlinux, and has everything set up. GNOME, and everything I need for my server.

---

### Post by Skripka on 2009-10-25
> **dragos240 said:**
> Well. That's pretty funny considering you have it mentioned 2 times in your signature.

Post hoc ergo propter hoc.  I know that of which I speak :)

---

### Post by mivo on 2009-10-25
The closest to what you seem to want is a rolling release distro, though you cannot have both an old kernel and old libs and also the latest software. I would also recommend a look at Arch Linux or the Chakra spin-off ([http://chakra-project.org/](http://chakra-project.org/)).

---

### Post by Xbehave on 2009-10-25
No, the problem is that as soon as you start keeping firefox up to date, you start keeping libxulrunner, then libxml and eventually you've got most of the distro running as a rolling release. Your best bet is something like fedora but tbh if its just a few apps you may be better off adding thier repos or installing/maintaining them manually (e.g unpack mozilla's firefox tar in opt and keep it uptodate). One thing to note is quite a few people are asking for something like this so perhaps one of them will put together a PPA with a few programs and their dependencies (AFAIK this hasn't happened and i wouldn't hold my breath)


> **Skripka said:**
> I'll warn you, a whole crowd of UFers are going to yell at you for mentioning the "A Word"
Yes because this isn't a thread about Arch, FFS guys, arch is not stable in the sense that OP was asking, it's rolling release you can't get any less stable. Bringing Arch into unrelated discussions is why you get flamed, not  because its arch.

Note constructive comments like mivo's don't get attacked it's just the stupid ones like "your looking for arch" followed by the inevitable arch support thread (seriously how much support does one distro need)

---

### Post by Bachstelze on 2009-10-25
> **dragos240 said:**
> Hmm.... stable core... latest apps. Archlinux is for you. If it's not in the repository, it's in the AUR.

Since when does Arch have a stable core? Actually, I can't think of any Linux distro that would fit. FreeBSD would, since it clearly separates the core of the system of third-party apps.

---

### Post by Skripka on 2009-10-25
> **Xbehave said:**
> 

Yes because this isn't a thread about Arch, FFS guys, arch is not stable in the sense that OP was asking, it's rolling release you can't get any less stable. Bringing Arch into unrelated discussions is why you get flamed, not  because its arch.

Note constructive comments like mivo's don't get attacked it's just the stupid ones like "your looking for arch" followed by the inevitable arch support thread (seriously how much support does one distro need)

I *knew* you'd drop in sooner or later

*smooch*

---

### Post by mivo on 2009-10-25
> **Bachstelze said:**
> Since when does Arch have a stable core?

He wants something like Windows that keeps updating itself without any need for reinstalls or major upgrades (which rarely work flawlessly), while also having access to the latest software versions. A stable core and latest software isn't a realistic expectation, but Arch still seems the closest to what he seems to have in mind.

---

### Post by cdekter on 2009-10-25
> **mivo said:**
> He wants something like Windows that keeps updating itself without any need for reinstalls or major upgrades (which rarely work flawlessly), while also having access to the latest software versions. A stable core and latest software isn't a realistic expectation, but Arch still seems the closest to what he seems to have in mind.

What I am mainly after is not having core parts of the OS broken on a regular basis (c.f. Intel video problems, X server regressions, etc etc). Once my hardware is working, I expect it to STAY working if I update. Otherwise, there must be a way for me to avoid installing updates that would cause hardware problems, while still updating the applications. 

With OS core I particularly mean kernel, drivers and ACPI stuff - these are the things that seem to be very fragile. I have no problem with updating Gnome, Glibs, gcc libs etc etc.

---

### Post by Xbehave on 2009-10-25
tl;dr read [this link]("http://jaqque.sbih.org/kplug/apt-pinning.html"), for how to run debian stable with the latest apps from testing/unstable
edit: you could do something similar for ubuntu( or any apt based distro), but i don't **think** the rolling release repos are as stable(in the crash sense) as debian's

> **cdekter said:**
> With OS core I particularly mean kernel, drivers and ACPI stuff - these are the things that seem to be very fragile. I have no problem with updating Gnome, Glibs, gcc libs etc etc.
I'm not 100% sure on this but I think something like debian testing + [pinning]("http://jaqque.sbih.org/kplug/apt-pinning.html") xorg+pulseaudio+kernel will do what you want, unfortunately debian testing isn't 100% current its usually about 10w* behind (for reference freeBSD is 13w), AFAIK pacman doesn't do pinning. I think overlays in gentoo do the opposite and would allow you to add the latest stable version of an app over a stable base, but i never spent much time with gentoo (too much compiling for my taste)

*these numbers are from [http://oswatershed.org/]("http://oswatershed.org/") and arent that accurate, but an ok guide.

> **Skripka said:**
> I *knew* you'd drop in sooner or later
I new this thread would be full of stupid "use arch" posts (exception made for mivo that justifies his points, even if i think hes wrong), that's why i dropped by to give an answer to the question asked not just "use $MY_DISTRO"

---

### Post by -grubby on 2009-10-25
> **c!oud said:**
> debian testing perhaps

+1

---

### Post by keiichidono on 2009-10-26
> **Bachstelze said:**
> Since when does Arch have a stable core? Actually, I can't think of any Linux distro that would fit. FreeBSD would, since it clearly separates the core of the system of third-party apps.

FreeBSD would be pretty much it, but it's a female dog to setup.

---

### Post by Hallvor on 2009-10-26
> **cdekter said:**
> (Dear Lazyweb)

Does anyone have experience with or know of a Linux distro out there that specialises in having a stable core (kernel, drivers, etc) with up-to-date applications (Gnome, Firefox, etc etc)? Similar to the Windows model in fact - core stays fairly constant for several years, applications updated more frequently.

Debian's stability is good but being stuck with Firefox 3.0 isn't...

I don`t think there is a distro that meets those requirements, but I assume you want an OS with the latest applications that still is reasonably problem free. I think PCLinuxOS is a good candidate. It has the latest applications and it is a rolling release where everything is upgraded through Synaptic (and not just the applications). Anyway, I have never had a serious problem with it (in a period of two years).

The Gnome version features the latest Gnome desktop, the latest Firefox, etc. There is also a KDE, XFCE and an LXDE version.

---

### Post by 3rdalbum on 2009-10-26
> **CalvinB said:**
> FreeBSD would be pretty much it, but it's a female dog to setup.

I've got two words to say to you: PC-BSD. It's FreeBSD but friendlier.

In fact... I might try it in a dual-boot. Wish me luck!

---

### Post by RichardLinx on 2009-10-26
I'll also recommend you give FreeBSD or OpenSolaris a try. You have to use them to understand, but there's just something about them that makes you think "Stable". If you want to actually get something done, *BSD and Solaris seem like the way to go. If you view a lot of Flash content though, you might have to do some tinkering.

You could also give Debian testing a try. I've heard good things. Getting proprietry hardware working might be a hassle if you don't know what you're doing or can't be bothered tinkering a little bit.

---

