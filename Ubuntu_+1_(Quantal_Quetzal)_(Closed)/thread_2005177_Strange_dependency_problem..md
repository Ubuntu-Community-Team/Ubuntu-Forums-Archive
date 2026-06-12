---
title: "Strange dependency problem."
date: 2012-06-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Gregory Lee on 2012-06-17
I tried to install gnome, both using the Ubuntu Software Center and with "aptitude install gnome".  And I get this message:
> gnome: Depends: gnome-core (= 1:3.0+6ubuntu3) but 1:3.0+6ubuntu3 is to be installed
What does it mean?  ("aptitude install gnome-core" does nothing -- apparently gnome-core is installed.)

---

### Post by dino99 on 2012-06-17
gnome-core is a meta package, so you can ignore it.

it should be easier to install & use synaptic instead of all other alternatives.

---

### Post by hailholyghost on 2012-06-21
Hello,

I am getting this same error.  Has a solution been found?

Last night I updated to Precise Pangolin... or so I thought

```
%lsb_release -rd
Description:	Ubuntu quantal (development branch)
Release:	12.10
```

I must empatically state I did NOT do this purposefully.  All I want is to get back to Gnome and get the functionality back that Unity took away.  "Downgrading" to Precise Pangolin would be *great*.

When I attempt to get GNOME back from the Software Center I get 

```
"gnome: Depends: gnome-core (= 1:3.0+6ubuntu3) but 1:3.0+6ubuntu3 is to be installed"
```

So then I attempt to install "gnome-core" from Synaptic

```
The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences
gnome-core:
 Depends: evolution-data-server but it is not going to be installed
 Depends: gnome-contacts but it is not going to be installed
 Depends: gnome-panel but it is not going to be installed
 Depends: gnome-session but it is not going to be installed
 Depends: gnome-session-fallback but it is not going to be installed
```

So I attempt to use Synaptic to fix install evolution-data-server, but 

evolution-data-server:
```
  Depends: evolution-data-server-common (=3.2.3-0ubuntu7) but 3.4.3-1 is to be installed
```

This is what other Ubuntu people have referred to as "Dependency Hell".

How can I get GNOME back?](*,)

NB: I also posted this in launchpad (is my desperation showing? haha) but is that unethical?

Anyway I appreciate any help that can be offered.

---

### Post by dino99 on 2012-06-21
not sure to understand what exactly you want to do, but downgrading to Precise is a no way.
if you think to the gnome-classic desktop, then install gnome-session-fallback and logout.
then select "gnome-classic while logging with lightdm (hit the little icon into the right corner)

---

### Post by jbicha on 2012-06-21
Well one particular problem is that libreoffice needs to be rebuilt  against the newest evolution-data-server; until that happens,  libreoffice-gnome is uninstallable and the "gnome" metapackage depends  on libreoffice-gnome. Ubuntu's LibreOffice maintainer is working to get  LibreOffice 3.6 Beta to build in quantal so you'll just have to wait a  bit longer until that gets sorted.

A second problem is that epiphany-extensions was uninstallable too but I  just uploaded a new version so that problem should be fixed within a  few hours.

On the other hand, you don't really need to install "gnome" as that's actually a special metapackage for Debian. As dino99 said, just install gnome-session-fallback to get the GNOME 2 style desktop.

---

### Post by hailholyghost on 2012-06-22
To dino99 and Gregory Lee,

I tried installing gnome-fallback, but there were more issues.  I restarted the computer and then the GUI was gone.  The only solution I could think of was to back everything up and wipe out Quantal with 12.04, which worked just fine.

Now I have a functioning Ubuntu install back :KS

thanks so much for your help!

---

### Post by Gregory Lee on 2012-06-22
Well, my question was not how to fix the Gnome interface (I gave up on that), but just what the strange error message meant.  That was my question -- What does it mean?  Apparently, no one here knows.

Several weeks before Precise became final, both the Gnome and Ubuntu desktops (all versions) stopped working for me.  They crashed every time I tried to use one.  Quantal is no different from Precise, in this regard.  I mentioned it here, spent a lot of time making bug reports, but nothing good happened.

However, I discovered that the KDE "plasma" desktop still worked (and also XFCE).  This is one of the optional application extras that showed up in the Software Center for the Gnome desktop.  So, that's what I've been using.

I'm keeping Ubuntu and Gnome desktops updated, as best I can, along with the rest of my Ubuntu Quantal system, thinking that some day, they may start working again.  Never can tell.

---

### Post by vidtek on 2012-06-22
Gregorylee-

I had some strange errors too with QQ, Everything went well until I tried the additional drivers.  After installing the Nvidia recommended drivers the system had a dkpg error which basically broke the system.
Installing the nvidia driver from the nvidia site works ok, but there were strange messages about the nuveau driver being in-kernel and might not be removable, requiring a blacklist type entry (can't remember exactly old fart memory).
It worked allright after that.
The trick to install the driver is to from a terminal use ```
/etc/init.d/lightdm stop
```
This kills the x-server enabling the install from a command-prompt.

The unity interface worked okay, but I prefer KDE so installed that and so far so good.  The only thing that gives me grief is the MCEUSB remote drivers are now in the kernel, wish I could just easily delete them, I don't want to build a non-standard kernel, just get rid of these pesky "events".

Tony.

---

