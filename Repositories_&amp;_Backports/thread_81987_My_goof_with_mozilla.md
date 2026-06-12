---
title: "My goof with mozilla"
date: 2005-10-25
forum: Repositories &amp; Backports
---

### Post by kylenewton on 2005-10-25
Heyall. I've done something wrong, and now apt-get/kynaptic doesn't want to work with me.

I simply ran apt-get update and apt-get upgrade (after one of the repositories - backports maybe, I forget - went down) and it said mozilla needed to be upgraded. So I tried installing through apt-get and it hangs up. Here's some of the output.

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  firefox: Depends: mozilla-firefox but it is not installed
  mozilla-mplayer: Depends: mozilla-browser but it is not installed or
                            mozilla-firefox but it is not installed
E: Unmet dependencies. Try using -f.


And running apt-get -f install results in

sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mozilla-firefox
Suggested packages:
  mozilla-firefox-gnome-support latex-xft-fonts xprt-xprintorg
The following NEW packages will be installed:
  mozilla-firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8802kB of archives.
After unpacking 24.7MB of additional disk space will be used.


Do you want to continue [Y/n]? y

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 19522 package `mozilla-firefox':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)


And no matter how I try to remove and install or re-install I get errors. I'm hoping this is something that is easy enough to fix. Help please?! Thanks.

---

### Post by kylenewton on 2005-10-26
I've still not been able to fix the error. Are other people having the same problem?

---

