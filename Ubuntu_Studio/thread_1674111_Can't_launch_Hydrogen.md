---
title: "Can't launch Hydrogen"
date: 2011-01-23
forum: Ubuntu Studio
---

### Post by maghoxfr on 2011-01-23
I get the following message when trying to launch hydrogen:


```
$ hydrogen
hydrogen: error while loading shared libraries: liblash.so.2: cannot open shared object file: No such file or directory 
```

I tryed unistalling and reinstalling its package but didn't work and I don't want to mess anything up by looking for that "liblash"...

Any ideas?
Thanks

---

### Post by sgx on 2011-01-24
Hi, you should install liblash2, and possibly lashd,
without causing trouble

If they are not in synaptic repos, try these links, and choose
the version for your hardware.

[http://packages.debian.org/sid/liblash2](http://packages.debian.org/sid/liblash2)

[http://packages.debian.org/unstable/sound/lashd](http://packages.debian.org/unstable/sound/lashd)

L inux
A udio
S ession
H andler

Lashd can be used by a few apps to save sessions consisting of them.

Info here:  [http://www.nongnu.org/lash/lash-manual.html](http://www.nongnu.org/lash/lash-manual.html)

Cheers

---

### Post by AutoStatic on 2011-01-24
This is caused by upgrading using falkTX's PPA. From the LAU mailinglist:
> I have such issue after upgrading from liblash2 0.5.4-0ubuntu5 to
liblash2 1:0.3~rc20110102-0ubuntu1~lucid1(falkt) where is no
liblash.so.2 . You have 2 ways:

1. force previous version 0.5.4 instead 1:0.3 by falkt
2. ln -s /usr/lib/liblash.so.1.1.1 /usr/lib/liblash.so.2 (I did this
and hydrogen runs successfully)

More here: [http://linuxmusicians.com/viewtopic.php?f=24&t=2410&start=75](http://linuxmusicians.com/viewtopic.php?f=24&t=2410&start=75)

Best,

Jeremy

---

### Post by maghoxfr on 2011-01-24
> **AutoStatic said:**
> This is caused by upgrading using falkTX's PPA. From the LAU mailinglist:


More here: [http://linuxmusicians.com/viewtopic.php?f=24&t=2410&start=75](http://linuxmusicians.com/viewtopic.php?f=24&t=2410&start=75)

Best,

Jeremy

Thanks Jeremy, I didn't do much research:oops: but I'm very short on time...

I've read that falkTX did upgrade his packages and some conflicts could arise but I didn't tied the knots! I used solution #1 and everything runs allright now. 

Thanks a lot man!

---

### Post by sgx on 2011-01-24
Out of curiosity, I checked my /usr/lib folder,
and found 3 links to liblash.so.1.1.1
Hydrogen works OK, but I don't know which apps placed
the links :-k have to read up on such things.
Cheers

---

### Post by maghoxfr on 2011-01-24
I was just going to use PHASEX but it didn't launch, it gave an error similar to the hydrogen one  but with liblash.so.1, I think (sorry I'm not at my pc now). So I forced it to download from Autostatic's PPA.

It worked, so thanks again Jeremy!

---

### Post by maghoxfr on 2011-02-06
> **AutoStatic said:**
> This is caused by upgrading using falkTX's PPA. From the LAU mailinglist:


More here: [http://linuxmusicians.com/viewtopic.php?f=24&t=2410&start=75](http://linuxmusicians.com/viewtopic.php?f=24&t=2410&start=75)

Best,

Jeremy

I ended up doing this solution.

---

