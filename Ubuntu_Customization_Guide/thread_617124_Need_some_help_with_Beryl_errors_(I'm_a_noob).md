---
title: "Need some help with Beryl errors (I'm a noob)"
date: 2007-11-19
forum: Ubuntu Customization Guide
---

### Post by Th0r4z1n3 on 2007-11-19
OK, I just switched back to Ubuntu and am trying to install Beryl. I used [this guide]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") to do it. All is good up until it comes time to actually install  Beryl, i typed:

[INDENT]sudo apt-get install beryl beryl-manager emerald-themes
[/INDENT]
in the terminal and got this this message;

[INDENT]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl: Depends: beryl-settings but it is not going to be installed
E: Broken packages[/INDENT]

I've also tried to load it using synaptic, and when I do I get this message:
[INDENT]
Could not mark all packages for installation or upgrade.

The following packages have unresolvable dependencies. Make sure that all the required repositories are added and enabled in the preferences.

beryl:
 Depends: beryl-settings but it is not going to be installed
 Depends: beryl-manager but it is not going to be installed[/INDENT]

I've also added the following repositories:
[INDENT]
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn[/INDENT]

ala [this guide]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html") for Dapper Drake, but... no luck. Any help would be greatly appreciated, thanks.

---

### Post by Sef on 2007-11-19
Beryl is no longer being supported.  Instead compiz-fusion is what to download. It is available in the repositories.   If you system can run it, it should have asked you if you wanted it downloaded.

---

### Post by seniorciz on 2008-01-09
Why was beryl eliminated? I worked for five hours to get everything right and i am still having problems. Is The Compiz-fusion the same basic idea that beryl is? and where can i pick that up?

---

### Post by Lvcoyote on 2008-01-09
There is a guide to installing Compiz-Fusion at the same place you got your Beryl guide.

---

