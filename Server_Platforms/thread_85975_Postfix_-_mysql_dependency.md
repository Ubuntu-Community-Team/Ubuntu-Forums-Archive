---
title: "Postfix - mysql dependency"
date: 2005-11-03
forum: Server Platforms
---

### Post by hostile on 2005-11-03
Okay,

I'm trying to install mysql-server, and apt is insisting that it depends on postfix & mailx. I do not believe this for one second.

Why the hell should I have to install a mail daemon beside my db daemon?

I left the RH world b/c of dependency crap like this.

Is there any way to force the install of mysql w/o all the postfix garbage?

---

### Post by LordHunter317 on 2005-11-04
No, it does, and here's why:  It depends on mailx, which requires an MTA in order to function.  Incidentally, mailx is required for some of the init scripts, IIRC.  Anyway, mailx requires an MTA and postfix is the default MTA, so it's installed.

As a practical MTA installed nix systems sohuld always have an MTA installed, though the Ubuntu team is trying to make that unnecessary for a desktop.  Server OTOH.

And this isn't dependency crap.  This is what depenencies are meant for: to ensure your system functions.  The mailx requirement is very real, as it's it's requirement for an MTA.

If you really don't want postfix, you could install nullmailer, I suppose.

---

### Post by hostile on 2005-11-04
Thanks for the info.

I'm not against postfix per se (at least it's not installing sendmail!), I just want this system to be as lean as possible, with a few services/daemons running as possible. Be it Windows or Linux, I make sure I dont install anything which is superfluous... if mysql truly needs an MTA, so be it.

As far as dependency goes, I understand the theory behind it, naturally. It just happens to be a double-edged sword more often than not. For example, there are certain desktop packages that if one tries to remove them, it removes the whole desktop - utterly ridiculous. It's things like this which make me want to scream over package managers like RPM/DPKG.

Anyhow, thanks for the help!

:D

---

### Post by heimo on 2005-11-04
[quote=hostile] For example, there are certain desktop packages that if one tries to remove them, it removes the whole desktop - utterly ridiculous. 
[/quote]

There are metapackages like ubuntu-desktop and kubuntu-desktop which install no files (or not anything important at least), but depend on bunch of packages. If you remove one of those dependencies, this metapackage will be removed too, but not all of its dependencies. For example, removing firefox would reomove at least ubuntu-desktop (probably some other applications too which depend on firefox, like yelp), but nothing additional is removed. It's exactly how it should work, but admitted, may look scary / stupid at a first glance.

---

### Post by hostile on 2005-11-04
So a meta-package is a package which basically has one way dependencies?

---

### Post by heimo on 2005-11-04
[quote=hostile]So a meta-package is a package which basically has one way dependencies?[/quote]

Dependencies, as I understand them, are one way. And other metapackages may depend on other metapackages. Metapackages are kind of collections of other packages, you may have all those dependent packages installed and "parent" metapackage not installed, but you can't have metapackage installed unless you also have all its dependencies installed. I'm not too good at explaining things like this in English :)

Metapackages are used so that you can easily install set of packages - like whole desktop environment (X/some window manager/applications). It's very convenient, but if you prefer not to install some of the "required" stuff you don't have to. As long as there are no real dependencies between the software packages, you can uninstall those independently. However, of couse, if you find some dependencies which are unneccessary, it's a bug. No one wants to have bloated system and I'm pretty sure Debian and Ubuntu developers share your opinion and IMHO they're doing fantastic job with package management. 

Some examples of metapackages:
[http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential)
[http://packages.ubuntu.com/breezy/base/ubuntu-desktop](http://packages.ubuntu.com/breezy/base/ubuntu-desktop)
[http://packages.ubuntu.com/breezy/x11/x-window-system-core](http://packages.ubuntu.com/breezy/x11/x-window-system-core)

---

### Post by LordHunter317 on 2005-11-04
[QUOTE=hostile]Be it Windows or Linux, I make sure I dont install anything which is superfluous... if mysql truly needs an MTA, so be it.[/quote]Your system generally needs a MTA even if no services really do (or ought to have one).  Cron for example, really expects one.  It's also a trivial way to do monitoring.

> For example, there are certain desktop packages that if one tries to remove them, it removes the whole desktop - utterly ridiculous.Such as?  Unless you're referring to aptitude/synpatic being "helpful", I can think of no such packages.  

And if you are, that's really a flaw of a feature in both of those programs, where it tries to remove automatically installed packages you no longer need.  Only, sometimes it gets it wrong.

---

### Post by hostile on 2005-11-04
> Unless you're referring to aptitude/synpatic being "helpful", I can think of no such packages.

"Helpful" is exactly what I mean.  ;)

---

