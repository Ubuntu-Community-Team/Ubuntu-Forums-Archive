---
title: "nautilus search doesn't search hidden folders"
date: 2012-06-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-06-27
Is this a "feature" or a known issue? I can't say I've run across this before, but suffice to say nautilus search doesn't find things that exist in "hidden" folders. Looking for all the *.iso files today in nautilus failed a couple times; first searching *.iso gives nothing, you must search for .iso to find anything? Secondly several isos were missing it seemed to me. I used ```
find -name *.iso
``` and boom, up came the missing results. Am I crazy?

---

### Post by mc4man on 2012-06-27
Probably a limitation, though it will search a 'hidden' folder or a folder inside a hidden folder if the folder is bookmarked

Does not appear to search for hidden (.) files

Almost never use here, prefer gnome-search-tool

*no reason edit*

---

### Post by cariboo on 2012-06-27
Does nautilus search for hidden files/folders when Ctrl-h is used? Personally I use mc to search.

---

### Post by philinux on 2012-06-28
> **cariboo907 said:**
> Does nautilus search for hidden files/folders when Ctrl-h is used? Personally I use mc to search.

Unfortunately not.

---

### Post by mc4man on 2012-06-28
As far as files I think the only thing that can be searched after a .(dot) is filetype (extensions
hidden folders can be searched if they are specified in location, by default the available locations are what's in the sidebar under bookmarks & computer plus pixmaps

---

### Post by ventrical on 2012-06-28
I had always noticed that wildcards do not work in nautilus, but just the "." and then file extension.

  I think it is a bug of omission.

---

### Post by philinux on 2012-06-28
> **ventrical said:**
> I had always noticed that wildcards do not work in nautilus, but just the "." and then file extension.

  I think it is a bug of omission.

These didn't look to be in a hidden folder.

---

### Post by ventrical on 2012-06-28
:) Sorry.

---

### Post by ventrical on 2012-06-28
> **guitara said:**
> Is this a "feature" or a known issue? I can't say I've run across this before, but suffice to say nautilus search doesn't find things that exist in "hidden" folders. Looking for all the *.iso files today in nautilus failed a couple times; first searching *.iso gives nothing, you must search for .iso to find anything? Secondly several isos were missing it seemed to me. I used ```
find -name *.iso
``` and boom, up came the missing results. Am I crazy?


Definitely a bug.

Even with 'show hidden folders' enabled...

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018981](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018981)

---

### Post by philinux on 2012-06-28
Confirmed.

---

### Post by ventrical on 2012-06-29
One of the users left a message with this link at launchpad.

[https://wiki.ubuntu.com/Bugs/Upstream/GNOME](https://wiki.ubuntu.com/Bugs/Upstream/GNOME)

---

### Post by jbicha on 2012-06-29
> **ventrical said:**
> One of the users left a message with this link at launchpad.

[https://wiki.ubuntu.com/Bugs/Upstream/GNOME](https://wiki.ubuntu.com/Bugs/Upstream/GNOME)

Seb's not just a user, he's the lead of the Canonical Desktop Team! ;-)

But yeah, the bug needs to be reported to the Nautilus developers at bugzilla.gnome.org.

---

### Post by mc4man on 2012-06-29
> **ventrical said:**
> One of the users left a message with this link at launchpad.

[https://wiki.ubuntu.com/Bugs/Upstream/GNOME](https://wiki.ubuntu.com/Bugs/Upstream/GNOME)

Well then you should file a gnome(component nautilus) bug, though It seems like 2 bugs - 
It will not search .name (hidden file 
It will only in .directory if .directory is an available search location

Possibly the 1st would fix the 2nd though maybe not

---

### Post by ventrical on 2012-06-29
> **jbicha said:**
> Seb's not just a user, he's the lead of the Canonical Desktop Team! ;-)

But yeah, the bug needs to be reported to the Nautilus developers at bugzilla.gnome.org.

Pardon my ignorance but I do not fully understand this two tiered bug reporting system. I realize it is a convenience for devs but the process then becomes more complex.  I am just making a side note on this topic - to elucidate  that some who are not familiar with this process may feel deterred to take it to the next step.

---

