---
title: "Something about Adept (do we really need it?)"
date: 2006-02-25
forum: The Cafe
---

### Post by z-vet on 2006-02-25
Hi all.
There are reports from users whose systems were screwed up by Adept. One is [here](http://ubuntuforums.org/showthread.php?t=134614) on forums, another one is on [kubuntuforums.net](http://kubuntuforums.net/forums/index.php?topic=3738.0). I think there was another one (can't remember where it is) but two reports in two days are enough, imho, to show that Adept is not usable and not newbie-friendly as Ubuntu (Kubuntu) aims to be. I talking about Adept's way to handle dependencies: to see the changes user needs to click on some button on toolbar and if one did not remember (or didn't know) about it? KDE or whole system (or some parts of it) will be uninstalled without any confirmation.  Let's compare it to Synaptic: you mark a package for installation and if there are dependencies or conflicts, it opens an alert window with list of all changes it goes to perform and that's what i call usable app: one that help you to see what is going on, one that interacts with user and tries to be helpful. 
Once again, we talking about newbie-friendly distro and an app that runs as root...and about two folks who just started with Kubuntu: one switched from windoze XP one month ago and second uses Kubuntu for five days only. Things like these will make people to go back to Windows, you know...

---

### Post by Stormy Eyes on 2006-02-25
Why are you telling *us*? We don't work on Adept. File a bug report.

---

### Post by sapo on 2006-02-25
wth is adept?

---

### Post by aysiu on 2006-02-25
Those two posts with catastrophic results are rare exceptions.

Nevertheless, Adept does, in fact, stink. Synaptic is far more user-friendly and *faster*. All this filtering of packages takes a *long* time, especially for people with slower computers.

---

### Post by aysiu on 2006-02-25
[QUOTE=Stormy Eyes]Why are you telling *us*? We don't work on Adept. File a bug report.[/QUOTE] My guess is that z-vet wants to see if it's something that other forum members feel is worth taking away and doesn't want to file a bug report straightaway otherwise... just my guess.

---

### Post by Adrian on 2006-02-25
First of all, let me say that I don't use Adept, so I don't really know what I'm talking about :) . Anyway, I guess it works as **aptitude**, i.e. it can remember meta-package data, and that's why entire desktops can be removed. I think this is a nice thing, but it requires carefull packaging of programs (with Adept in mind, not apt-get!) and you should not mix it with **apt-get** or Synaptic.

---

### Post by z-vet on 2006-02-25
[QUOTE=aysiu]My guess is that z-vet wants to see if it's something that other forum members feel is worth taking away and doesn't want to file a bug report straightaway otherwise... just my guess.[/QUOTE]
Yes, exactly. :)

---

### Post by GeneralZod on 2006-02-25
Adept is still a very young project and is still under heavy development.  I agree that in its current form it's fairly poor and really should have a 0.x.y version number rather than a 1.0 to reflect its immaturity, but it's grossly premature to talk of ditching it completely just because it currently works poorly.

Edit:

I also don't think it should have been the *default* package manager for Kubuntu 5.10.  Hopefully, it will be signifcantly  improved for Dapper :)

---

### Post by z-vet on 2006-02-25
[QUOTE=GeneralZod]Adept is still a very young project and is still under heavy development.  I agree that in its current form it's fairly poor and really should have a 0.x.y version number rather than a 1.0 to reflect its immaturity, but it's grossly premature to talk of ditching it completely just because it currently works poorly.

Edit:

I also don't think it should have been the *default* package manager for Kubuntu 5.10.  Hopefully, it will be signifcantly  improved for Dapper :)[/QUOTE]
Well, i don't say "ditching it completely"...your edit says it all: Adept is far from being used as default package manager in Kubuntu. Let's wait and see what will be Adept in Dapper.

---

### Post by engla on 2006-02-25
[QUOTE=z-vet]Well, i don't say "ditching it completely"...your edit says it all: Adept is far from being used as default package manager in Kubuntu. Let's wait and see what will be Adept in Dapper.[/QUOTE]
I don't use kubuntu and I haven't tested dapper, but according to packages.ubuntu.com, the version of Adept in dapper (right now) is 1.90.

---

### Post by Jucato on 2006-02-25
I've run the Dapper Flight-3 Live CD of Kubuntu, and let me say that interface-wise Adept is even less user-friendly and a bit confusing. There are some things that Adept misses out, some of which are very important.

1. A prompt/confirmation for making changes, allowing the user to plainly see what changes will take place. As it stands, the only way Adept informs you is either through its status bar or by pressing "Preview Changes", both of which is not good.
2. A download-only feature, or "test" feature (where nothing is really installed)

I understand Adept is still young. But that's the point. Why is it the default Kubunt package manager, while not informing users of its youth. It's like it is still in a beta stage. 

IMHO, Kubuntu should also install another package manager as an alternative but still retain Adept as the default.

---

