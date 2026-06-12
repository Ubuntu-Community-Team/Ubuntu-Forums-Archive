---
title: "Should desktop-file-utils be a dependency of ubuntu-desktop only?"
date: 2007-12-04
forum: Ubuntu Brainstorm
---

### Post by TheForkOfJustice on 2007-12-04
I'm making a new Ubuntu-based distro and have run into something that's a pain in the butt.

I use different default programs than Ubuntu and therefore I have to alter the file 

> /etc/gnome/defaults.list

located in the package **desktop-file-utils** so the filetypes will play with different programs by default.

Problem is, if I change that file then I will run into problems when nabbing updates, and if I remedy that by changing the package's name I will have to end up altering a lot of packages that include (but are not limited to):

[B]nautilus
openoffice-common
xdg-utils
gnome-control-center[/B]

and you can just imagine the problems that will cause.  I may end up having to remake hundreds of packages!

So I was wondering, is it were possible to only make **desktop-file-utils** a dependency of ubuntu-desktop so it won't cause such a mess for those of us making offshoots of Ubuntu?

Also, for some reason gnome-control-center is mentioned twice in Synaptic as a "dependent package" of desktop-file-utils.

---

### Post by coolen on 2007-12-06
Is it possible to tag it in APT somehow, so its configuration files won't be replaced?

---

### Post by TheForkOfJustice on 2007-12-07
I've been notified of a command called dpkg-divert that can be of some help in this area but I have to research more about it.

What I would really like to know is if there were a way to make all of these 'diversions' by installing a deb with a file/files containing the diversions I wish to make.

---

### Post by coolen on 2007-12-09
Do debs not contain scripts to be run during the installation?
This sounds kind of hacky, but if you have a deb to simply run the appropriate commands to create the diversions you need, it may work.
Of course, I'm sure there's a more elegant way of doing this.

Good luck with your project, by the way. It sounds like you're really trying to do something good :)

---

### Post by TheForkOfJustice on 2007-12-09
> **coolen said:**
> Do debs not contain scripts to be run during the installation?
This sounds kind of hacky, but if you have a deb to simply run the appropriate commands to create the diversions you need, it may work.
Of course, I'm sure there's a more elegant way of doing this.

Good luck with your project, by the way. It sounds like you're really trying to do something good :)

Ah!  I totally forgot about the scripts in the deb.  It is hacky as you said but it just might work.

I also hope for a more elegant way of doing it.

And thanks for the complement :)

---

