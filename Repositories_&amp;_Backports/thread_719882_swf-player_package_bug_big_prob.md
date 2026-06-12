---
title: "swf-player package bug? big prob?"
date: 2008-03-09
forum: Repositories &amp; Backports
---

### Post by -random on 2008-03-09
when i go to synaptic and click on the install option for
swf-player

it wants to remove almost all other packages installed on my system!?

what's up with this??

---

### Post by NightwishFan on 2008-03-10
I believe there is a conflict with the ubuntu desktop meta package. One moment ill check it out.

---

### Post by NightwishFan on 2008-03-10
are you installing flashplugin-nonfree?

i do not even have swf-player in the repos, possible since I am using amd64

---

### Post by -random on 2008-03-10
yes, i'm using flashplugin-nonfree, but i think this occured even before i tried to install flash/gnash/or anything of the sorts, meaning i think it'll happen also from a clean install.

I'm using 32bit ubuntu 7.10, don't know if this happens in my 64bit aswell... i'll check it out....

---

### Post by NightwishFan on 2008-03-10
I am sorry I do not have a free partition for 32bit os, so I cannot investigate myself. :(

---

### Post by -random on 2008-03-11
yep, exactly the same happens in my 64bit.

It's not a big problem per say, i'm only afraid that a noobie might install the package and apply before thinking/reading.

should i report this to a MOTU or something? (i'm still very nooob myself! )

---

### Post by NightwishFan on 2008-03-12
kazuma@kazuma-desktop:~$ sudo apt-get install swf-player
[sudo] password for kazuma:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  swf-player: Depends: libgtk2.0-0 (>= 2.10.3) but it is not going to be installed
E: Broken packages
kazuma@kazuma-desktop:~$

edit: this is on gutsy, perhaps file one.

---

### Post by -random on 2008-03-12
phew cool so you won't be able to install it accidently. That's a releif!!

---

