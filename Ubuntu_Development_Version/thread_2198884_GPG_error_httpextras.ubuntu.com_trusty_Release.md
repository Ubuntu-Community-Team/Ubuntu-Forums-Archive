---
title: "GPG error: http://extras.ubuntu.com trusty Release"
date: 2014-01-11
forum: Ubuntu Development Version
---

### Post by Bucky Ball on 2014-01-11
Hi all,

Am getting this error at the end of 'sudo apt-get update':

```
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
```

All updates fine and that is the only sign I get of a problem. Install is pretty much faultless apart from that. 14.04 mini install with xfce4.

---

### Post by Elfy on 2014-01-11
Not sure that extra's is up yet. However, try
```

gpg --keyserver keyserver.ubuntu.com --recv 3E5C1192

gpg --export --armor  3E5C1192 | sudo apt-key add -
```

---

### Post by Bucky Ball on 2014-01-11
Yep, worked. ;)

Thanks Elfy. I've marked three of my 14.04 threads solved within about three hours. Must be a record.

14.04 mini is working great after some tweaking. Don't remember if I've asked you this already, but is there an xubuntu-core available for me to try?

---

### Post by Elfy on 2014-01-11
>  Not sure if I've mentioned this, but is there an xubuntu-core available for me to try? Sort of - perhaps - maybe - not quite ;)

We've been fighting a bunch of other stuff, so that's sort of taking a back seat atm from what I can see. I'll try and get a bit more information and let you know.

---

### Post by ajgreeny on 2014-01-11
Xubuntu 14.04 daily iso from 9th Jan is running very well on my system in Virtualbox, so if a xubuntu-core is available I think it would fly on decent hardware.

---

### Post by Bucky Ball on 2014-01-11
I'm running the minimal on an i3 with 4Gb of RAM and loving it.

This time around I've noticed how much dross even setting up a minimal install drags in. Install gdm and it drags in bits of evolution and samba. The list goes on. Still, the install only takes up 3.16Gb, but there's still a few things left to install.

---

### Post by cariboo on 2014-01-11
> **Bucky Ball said:**
> I'm running the minimal on an i3 with 4Gb of RAM and loving it.

This time around I've noticed how much dross even setting up a minimal install drags in. Install gdm and it drags in bits of evolution and samba. The list goes on. Still, the install only takes up 3.16Gb, but there's still a few things left to install.

Wouldn't xdm be a bit better in this case? the list of depends and recommends is much shorter than for gdm.

---

### Post by Bucky Ball on 2014-01-11
I've just purged gdm (but I don't think I needed to?) and swapped to lightdm to try it out. Works fine, too, but can't see anywhere to choose a session ... 

The depends go on forever so I'm thinking of attempting SLiM again. Xdm is pretty ugly, but I guess it can be tarted up. :-k

---

