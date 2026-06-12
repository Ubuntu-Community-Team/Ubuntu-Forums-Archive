---
title: "How do I get dirvish to install?"
date: 2006-07-27
forum: Server Platforms
---

### Post by Maddog Battie on 2006-07-27
(I'm a noob at ubuntu so please state the obvious and hold my hand a bit please)

I've just installed Dapper server on to a new machine and it went surprisingly easy. It took me a while to get samba going correctly but alls well now.

My problem is I would like to use dirvish to create some rolling backups but I'm unsure as to how to go about it.

aptitude does not seem to list the package and

[FONT="Fixedsys"]$ sudo apt-get install dirvish
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package dirvish
[/FONT]
doesn't seem to work either.

I guess I could install it by hand but I'm loath to do this as I'm bound to put something in the wrong place.

dirvish is listed as a package in ubuntu [http://packages.ubuntu.com/dapper/admin/dirvish](http://packages.ubuntu.com/dapper/admin/dirvish) so I would have thought it was easy to install.

What am I missing?

Cheers, MdB

---

### Post by Kurt` on 2006-07-27
# apt-cache search dirvish

displays:

dirvish - Filesystem based backup system using rsync

Chances are it's in a repository you need to enable.

Please follow this guide:

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

Basically just uncomment everything in the file. Then run # sudo apt-get update

After that, you should be able to simple # sudo apt-get install dirvish

---

### Post by Maddog Battie on 2006-07-27
That solved it! Thanks for your help. :KS

---

