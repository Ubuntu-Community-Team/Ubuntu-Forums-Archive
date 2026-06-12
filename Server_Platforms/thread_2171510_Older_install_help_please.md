---
title: "Older install help please"
date: 2013-08-31
forum: Server Platforms
---

### Post by david-oldcolo on 2013-08-31
I am attempting to install an older version of Ubuntu to gain a LAMP server, specifically to install PHP4 as am trying to resurrect a web site that uses php4 in its environment.

I've been mucking through trying to install everything from Ubuntu 6.06LTS to Ubuntu 7 and now Ubuntu 8, but I am having difficulty in getting the old repositories to work in upgrading applications and such from these older versions.

I've tried a myriad of settings indie /etc/apt/sources.list, specially changing the repositories to "old-releases.archive.ubuntu.com" and for instance in 8.04, using 'intrepid' as the build name.  No joy.

Rather than list everything that has not worked... can I ask, anyone help point me to a HOW-TO that would help me install an older version of Ubuntu, and install php4 as well?  And... have the dependencies bind together with Apache2 and MySql which I know has to blend together as well?

Any guidance would be much appreciated.  Am running in circles and would sure appreciate any pointers.

tx

---

### Post by SeijiSensei on 2013-08-31
Have you tried running the site on PHP5?  I have sites that date back PHP4 and still work correctly on PHP5.  I'd start by trying to get it to run on 12.04.  You won't find active repositories for versions of Ubuntu that have passed their "[sell-by]("https://wiki.ubuntu.com/Releases")" dates, nor are you likely to find much support for PHP4.

---

### Post by houstonbofh on 2013-08-31
As said, the only repositories of the old versions are the ones on the CDs.  You may need to use a different distrubution that puts more on the CD, like Susi or Red Hat.

---

