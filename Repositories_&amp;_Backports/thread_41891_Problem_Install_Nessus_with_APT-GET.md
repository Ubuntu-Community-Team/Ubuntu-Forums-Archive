---
title: "Problem Install Nessus with APT-GET"
date: 2005-06-15
forum: Repositories &amp; Backports
---

### Post by Nikodemis on 2005-06-15
When I run sudo apt-get install nessus or nessusd I get line after line of the following.

Can't stat source package list (different path are listed here)

Then it says to run

apt-get update to fix the problem

it seams the backport.ubuntuforurms are the ones that fail. Can anyone point me in a direction to fix this problem?

Thanks

---

### Post by FLeiXiuS on 2005-06-15
Yes there is a fix :-P.

Remove all of the backports.ubuntuforums.org repo's in your /etc/apt/sources.list

Replace them with:

```

deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted

```

Then all you need to do is apt-get update, and voila.  Nessus away!

---

### Post by Nikodemis on 2005-06-15
[QUOTE=FLeiXiuS]Yes there is a fix :-P.

Remove all of the backports.ubuntuforums.org repo's in your /etc/apt/sources.list

Replace them with:

```

deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted

```

Then all you need to do is apt-get update, and voila.  Nessus away![/QUOTE]

Thank you I add those lines but I know get

 Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp .nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or director

---

