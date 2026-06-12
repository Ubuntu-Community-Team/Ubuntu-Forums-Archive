---
title: "Why is a package manager not preinstalled?"
date: 2020-01-06
forum: Ubuntu, Linux and OS Chat
---

### Post by theuserbl on 2020-01-06
On every new installed Ubuntu there have to be at minimum the following written in the terminal

```
 sudo add-apt-repository universe
 sudo add-apt-repository multiverse
 sudo apt-get update
 sudo apt-get install synaptic
 sudo synaptic
```

Why isn't a graphical pakage manager not preinstalled in Ubuntu?

If I compare Ubuntu with OpenSUSE: On OpenSUSE it is an installation and then direct working with it. Yast2 is the package manager, which is in the start menu of the installed system. So on OpenSUSE new users need only to install the Operating System and all other things can be figured out by plaing around with the programs in the start menu.
And on Ubuntu? There you can with the programs in the start menu not all do. You have to use ap-get on command line or to install with apt-get the needed helpful tools.

Ok, Ububtu have its snapcraft snap-store. But not all programs existing for it. Programming languages and so on are not there. And to see, what programming langugeas can be installed, is the easiest way, to do it with synaptic, which is not preinstalled...

Greetings
theuserbl

---

### Post by theuserbl on 2020-01-06
Oh, and that some programs existing as snap-package **and** as deb-package makes not much sense.
And why is the preinstalled Firefox from the deb-package, where comes not so often actual updates?

---

### Post by rbmorse on 2020-01-06
Apt is the baseline package manager and is installed by default.  

The repositories you add are not included by default for the reasons listed in the repo description.  This is a explicit decision by the management. 

Synaptic is nice, but it's just a GUI.  If you want to have some real fun with package management on Ubuntu, try aptitude.

---

### Post by crip720 on 2020-01-06
'Software and updates'  take care of the first two.  Synaptic can be installed by the 'software store'.  Usually also install 'gdebi' because sometimes it works best.

---

### Post by crip720 on 2020-01-06
Snap is very new and still in testing phase, still has some bugs.  Deb is the old and well tested, but each version of Ubuntu/Linux needs a new Deb made.  Snap is suppose to not need this.

---

### Post by TheFu on 2020-01-06
There are multiple package managers installed with every Ubuntu flavor.
[LIST]
[*]apt (all)
[*]apt-get (all)
[*]Software & updates (desktops only)
[/LIST]

If you don't like those defaults, you are free to add:
[LIST]
[*]aptitude (all)
[*]synaptic  (desktops only)
[/LIST]

I'm not a GUI person, so apt is normally the package tool used.  apt-get supports globbing, which can be nice when removing multiple, specific, kernels or all of network-manager or all of bluetooth or ... .  aptitude is smarter about dependencies so I like to have it around to get the main dependencies options I desire when the defaults aren't it.

Snaps are not exactly new, just newly forced onto normal ubuntu users.  The Ubuntu Phone project lead the snap design.  There are many issues with snaps and if you have lots of RAM and lots of CPU and lots of HDD, then snaps only have a few huge issues, not many, many huge issues.  Until snaps support local configuration of the confinement, they are next to useless for my needs.  Linux is supposed to be about flexibility.  Snaps are not that.

---

### Post by CatKiller on 2020-01-06
In addition to what everyone else has said, I'll note that Kubuntu comes with Muon (KDE's Synaptic equivalent) already installed.

I do feel, and have said before, that Synaptic should still be installed by default to help new users over the bump of understanding package management.  Software Centre is simple, and does include snaps of things that aren't in the repositories (and things that *are* - grrr). But it hides that calming package resolution progress that helps make things click. 

For your use case it's not as important, since someone that's already experienced already knows that they can just install Synaptic, or aptitude, or whatever. In my case, Gnome's other flaws pushed me to KDE, and that doesn't have the issue.

---

### Post by SeijiSensei on 2020-01-07
Recent versions of Kubuntu call the software manager "Discover." In the menu it appears as "Software Center - Discover".

---

### Post by QIII on 2020-01-07
What it comes down to is this:  Canonical decides what they think is important to include in the default installation for whatever reasons they have to make that decision.  What other distributors choose to include is up to them.

Even among those who maintain the *Buntu official flavors, what to include by default is their decision.

Nobody here works for Canonical, so we can't really speak to the reasons for the fact that there is no GUI package manager included by default.  We can only help users deal with that fact.

Installing Synaptic is a good suggestion if you want a GUI package manager.

---

### Post by howefield on 2020-01-07
> **theuserbl said:**
> Why isn't a graphical pakage manager not preinstalled in Ubuntu?

[https://wiki.ubuntu.com/SoftwareCenter#Rationale](https://wiki.ubuntu.com/SoftwareCenter#Rationale)

Might be different in earlier releases but having just completed an install of 19.10 all repositories are enabled. Even if they weren't as others have said no need to use the terminal to enable them.

> So on OpenSUSE new users need only to install the Operating System and all other things can be figured out by plaing around with the programs in the start menu....

Now, you have to be joking :)

---

