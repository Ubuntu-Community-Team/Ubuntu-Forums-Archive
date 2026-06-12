---
title: "possible to network a dvd burner with virtualbox?"
date: 2008-09-23
forum: Virtualisation
---

### Post by tjwoosta on 2008-09-23
i have setup a virtualbox running XP as a guest

so i have learned that you cannot burn dvd's from virtualbox
(which sucks because the only reason i still use windows is because of Alcohol 120)

i have also learned that i can share files with my virtualbox guest (in the virtualbox settings) and map the "virtualbox shared files" as a network drive in XP


so my question is..

knowing that it's possible to share dvd drives over a home network

is it possible to share my dvd drive with the virtualbox in this way?

---

### Post by tjwoosta on 2008-09-27
bump..

---

### Post by lazyart on 2008-09-30
My guess it that it would only show up as a folder, so you wouldn't be able to burn to it.  Why not give it a try and tell us?

---

### Post by MystaMax on 2008-09-30
[quote=tjwoosta]
so i have learned that you cannot burn dvd's from virtualbox
[/quote]

The VirtualBox manual states:
[I]
Using the host drive normally provides a read-only drive to the guest. As an ex-perimental feature (which currently works for data only, audio is not supported), it is possible to give the guest access to the CD/DVD writing features of the host drive (if available).[/I]

If you look at the individual VM properties, you'll see "Enable Passthrough". Try enabling it, and burning a DVD. I know the passthrough option allowed me to rip DVDs using DVDFab HD Decrypter. Before, my DVD drive only showed up as a CD-ROM drive.It doesn't hurt to try.

---

