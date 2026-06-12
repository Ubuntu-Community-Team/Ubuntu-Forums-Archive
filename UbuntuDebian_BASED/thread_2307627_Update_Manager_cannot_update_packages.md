---
title: "Update Manager cannot update packages"
date: 2015-12-26
forum: Ubuntu/Debian BASED
---

### Post by cinead on 2015-12-26
Something is going awry. I am running Enlightment OS/Luna on Ubuntu Precise and I can't get ```
apt-get update
``` or Update Manager to return successful.

My Update Manager says:
```
Failed to download Repository Information

W:Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/luna-getdeb/games/binary-amd64/Packages  404  Not Found [IP: 104.28.25.125 80]
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/luna-getdeb/games/binary-i386/Packages  404  Not Found [IP: 104.28.25.125 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I have tried to remove getdeb from Software Manager and I have tried manually removing the ppas without success. If I try...
```
~# add-apt-repository -r <URL>
Error: <URL> doesn't exist in a sourcelist file.
```

I can confirm this by looking in /etc/apt/sources.list and the <URL>'s are not in there.

I also tried installing y-ppa and removing or purging the offending ppas, but although this says that it works, it doesn't.

So why is it trying to hit these ppas? And why are they non-existent? **And how do I get rid of them?**

I have apt-get, synaptic, software manager, and Update Manager installed.

Thank you for your time.

---

### Post by howefield on 2015-12-26
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by cinead on 2015-12-26
Almost solved...

The only place those ppas were listed was apparently within Update Manager itself.

From Update Manager, I clicked Settings and then the Other Software tab. I then found the offending ppas and high-lighted them, clicking Remove.

After this Update Manager updated.

I still seem to have some issues in apt-get update though...

---

### Post by cinead on 2015-12-26
[RESOLVED]

apt-get update started throwing duplicate entries:

```
W: Duplicate sources.list entry <URL>
```

Using [this page]("http://askubuntu.com/questions/120621/how-to-fix-duplicate-sources-list-entry"), I edited the /etc/apt/sources.list file to comment out the duplicate statements for:
```
deb <URL>
deb-src <URL>
```

Changing them to:
```
## deb <URL>
deb-src <URL>
```

Now apt-get update works.

---

