---
title: "libapache-mod-security issue"
date: 2009-05-15
forum: Server Platforms
---

### Post by wattaman on 2009-05-15
Situation:
I wanted to make some updates using the *Virtualmin Package Updates* from within the webmin>system (I have webmin+virtualmin installed), however it fails and displays this:
> 
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libapache-mod-security: Depends: mod-security-common (= 2.5.9-1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

.. install failed!
So I followed the instructions and run the _apt-get -f install_, as root, and I got also this thing:
> The following packages will be REMOVED:
  libapache-mod-security

... I haven't confirmed the command because I don't want to *libapache-mod-security* to be removed; and it appears that it wants to remove the *libapache-mod-security* with every update I'm trying to make.
Is there a solution to fix this? Like I've said, I want to keep the libapache-mod-security.
Thank you!

---

