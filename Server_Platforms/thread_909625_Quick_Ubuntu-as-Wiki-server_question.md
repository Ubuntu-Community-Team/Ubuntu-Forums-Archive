---
title: "Quick Ubuntu-as-Wiki-server question"
date: 2008-09-03
forum: Server Platforms
---

### Post by MNA_Novice on 2008-09-03
System: 

I'm running Hardy Heron w/ gnome GUI 2.22.3 - base install was LAMP server (apt-getted the desktop environment on top for terminal weenies like myself) and runs great; this is on an old Dell Optiplex GX 240.

Org Background: 
(to avoid the inevitable cries of "GUI on a SERVER? Aarrg!!") 

This is the *first* non-MS Winduhs machine in our firm of any kind, as we have a managing partner who fears anything non-MS - I want this to be flawless and smooth and seem *easy* so that we can consider running Ubuntu for some of the workstations too - or Mac OS X - some unix-like and stable OS.

This Linux Box is our Wiki Server (MediaWiki) and so far it's been a roaring success... took me a while to get everything installed and configged to everyone's satisfaction, but as a whole we're just tickety-boo now... 

What I want to know is whether there is a simple way to check on connected users prior to restarting once an OS update has been installed?

In the MS Winduhs world, you go to Manage>Shares>Sessions and you can see all open sessions (complete w/ number of open files for each user) and if Winduhs can do it, I *know* Ubuntu has to be not just one but three better - so how do I do this?

Thanks,

MNA Novice

---

### Post by windependence on 2008-09-04
In the Linux/Unix world you NEVER have to reboot a machine unless you update the kernel, which is rare.

To find out who is logged on in a Linux machine, open a command prompt and type who or even just "w".

-Tim

---

