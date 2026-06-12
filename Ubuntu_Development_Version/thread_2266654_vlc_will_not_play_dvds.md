---
title: "vlc will not play dvds"
date: 2015-02-24
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-02-24
15.04 ,14.04.2 will not play DVDs with vlc. Tried several different combos of dvd player. Get a scrabled 'not in this region' msg.

---

### Post by raptir on 2015-02-24
Did you install libdvdcss? It is not installed when you install ubuntu-restricted-extras due to issues with the legality of it in some jurisdictions.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by ventrical on 2015-02-24
..and get this .. but I think I got it ...

```

ventrical@ventrical-MS-7798:~$ sudo apt-get install libdvdcss
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss' has no installation candidate
ventrical@ventrical-MS-7798:~$ 



```

---

### Post by ventrical on 2015-02-24
> **raptir said:**
> Did you install libdvdcss? It is not installed when you install ubuntu-restricted-extras due to issues with the legality of it in some jurisdictions.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)


Thanks again... Working great. I want to try it on the new 4.0 kernel. mac4man helped me with this a while back but I haven't used a dvd in so long I just totally forgot :)

Regards..

edit:

```

sudo apt-get install libdvdread4


then


sudo /usr/share/doc/libdvdread4/install-css.sh

```

---

