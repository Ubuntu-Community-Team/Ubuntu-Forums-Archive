---
title: "libvirt can't see running Xen guests"
date: 2012-03-14
forum: Virtualisation
---

### Post by PacShady on 2012-03-14
Hey guys,

For some reason, libvirt can't see running Xen guests on my Ubuntu Server 10.04 box. xm list brings up the full list of guests, but virsh and virt-manager can only see guests if they're not running. According to Google I'm the only person who seems to have this problem, and I'm at a loss as to what to look for. Does anyone have any ideas on what I might be able to do to sort this out?

Cheers

---

### Post by PacShady on 2012-04-06
BUMP

Three weeks and no reply :(

---

### Post by Dedoimedo on 2012-04-08
I assume you're running commands as root?
Did you try legacy http access?
Dedoimedo

---

### Post by PacShady on 2012-06-15
For the sake of anyone who Google's this in the future (I HATE it when trying to find a solution and all you find are ancient threads with no solutions):

I found the problem, it's some sort of bug with the version of libvirt that ships with 10.04.

I added ppa:ubuntu-virt/ppa and updated to the latest version available from there, and the problem is solved.

Easy fix :)

---

