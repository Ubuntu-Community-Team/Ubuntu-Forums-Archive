---
title: "simplified offline installation of packages"
date: 2008-10-31
forum: Ubuntu Brainstorm
---

### Post by wesmo on 2008-10-31
Not sure if this has been mentioned before but here goes:

For the few connections that exist out there without an internet connection (or without working wireless drivers), getting new packages generally involves looking up the package at packages.ubuntu.com on a different computer, finding the requested package and downloading it and all its dependencies one-by-one, then copying to usb/cd/dvd and individually installing each package on the offline computer.

As you know, manually downloading is a fairly tedious job without apt-get so what I'm thinking is:

1 - a link under each packages that downloads the package and all its dependencies in one go.

2 - a way of generating a record of the offline systems installed package state so that the offline user can use the diff to only download the packages she/he needs. This diff may also contain hardware info so as to allow any required drivers to be downloaded to.

3 - A way of treating the group of packages downloaded as a temporary apt source to resolve any circular dependencies.

4 - The first time update-manager attempts to update and finds no connection a prompt comes up in the update manager asking the user to create a diff for offline installation. This prompt may be toggled off.

I'm not sure if this is currently possible but I think it would take some of the pain out of installing new packages offline.

For updating packages, the simplest way to do this would be to generate a monthly (similar to the daily releases) of the latest stable + all updates or allow users to use the diff generated in 2) to locate and download the latest updates.

---

### Post by smartboyathome on 2008-10-31
This has been mentioned, try searching.

---

