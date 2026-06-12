---
title: "Has anyone noticed this on 10.10?"
date: 2011-01-14
forum: The Cafe
---

### Post by v8skittles on 2011-01-14
Here's link [http://i.imgur.com/rofVI.png](http://i.imgur.com/rofVI.png) . Just noticed after an install of Ubuntu as well as updates.

---

### Post by ikt on 2011-01-14
> **v8skittles said:**
> Here's link [http://i.imgur.com/rofVI.png](http://i.imgur.com/rofVI.png) . Just noticed after an install of Ubuntu as well as updates.

Nope,

[http://ikt.id.au/wp-content/uploads/2011/01/linuxforhumans.png](http://ikt.id.au/wp-content/uploads/2011/01/linuxforhumans.png)

---

### Post by yetiman64 on 2011-01-14
I read on a thread here recently (sorry don't know where it was, as it was a couple of weeks back now) about this situation. If I recall correctly someone mentioned that a bug report on launchpad has been listed for it. May pay for you to check out recent bug reports.

Aha, just found the bug report on launchpad, thanks Google :D.

Here it is. [[COLOR=Blue]--Link--[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248") (apparently there may be multiple bugs reported for this from reading the details)

---

### Post by Primefalcon on 2011-01-14
The error is in this file: /usr/share/gnome/help/libs/global.ent

just open it up like so....

```
gksudo gedit /usr/share/gnome/help/libs/global.ent
```

just update the version bit like so....
```
<!-- VERSIONS -->
<!ENTITY distro-version 'Maverick Meerkat'>
<!ENTITY distro-rev '10.10'>
<!ENTITY distro-rev-short '10.10'>
<!-- the distro-rev-short entity should not include the "LTS" in a long term release and can be used for url links --> 
<!ENTITY distro-release-date "October 2010">
<!ENTITY distro-support-date "April 2012">
<!ENTITY distro-short-codename "maverick">
<!ENTITY distro-apt-cd-name "Ubuntu 10.10_Maverick_Meerkat">
<!ENTITY linux-kernel-version "2.6.35">
```

and voila.... I fixed this on my own machine a few weeks back after a few grep searches

---

