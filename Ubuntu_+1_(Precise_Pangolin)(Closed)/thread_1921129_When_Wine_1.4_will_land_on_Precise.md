---
title: "When Wine 1.4 will land on Precise?"
date: 2012-02-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sonnet on 2012-02-06
I installed precise with Kde and added wine ppa.
But when I update the repositories , I get this kind of error message at the end:
*Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found*

*W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found*

Is tehre a way I can install latest wine on precise (1.4rc2)

---

### Post by dino99 on 2012-02-06
search wine1.4 in ppa, you will find portis25/test :)

---

### Post by jfernyhough on 2012-02-06
You can also manually change the PPA source from precise to oneiric (e.g. in Software Sources, Other Software).

---

### Post by dino99 on 2012-02-06
> **jfernyhough said:**
> You can also manually change the PPA source from precise to oneiric (e.g. in Software Sources, Other Software).

no, 1.4 rc2 is still not there

---

### Post by portis on 2012-02-06
That's my ppa :)
wine1.4 is already in precise upload queue.
I will delete it from my test ppa as soon as it enters precise.

> **dino99 said:**
> search wine1.4 in ppa, you will find portis25/test :)

---

### Post by dino99 on 2012-02-06
> **portis said:**
> That's my ppa :)
wine1.4 is already in precise upload queue.
I will delete it from my test ppa as soon as it enters precise.

Thanks man :) it works smootly indeed , but synaptic sort these packages as "removable", not a big deal anyway :)

Good job.

---

### Post by jfernyhough on 2012-02-06
Ah, it's rc1... fair enough. :)

```
$ apt-cache policy wine1.3
wine1.3:
  Installed: 1.4~rc1-0ubuntu1~ppa1~oneiric1
  Candidate: 1.4~rc1-0ubuntu1~ppa1~oneiric1
  Version table:
 *** 1.4~rc1-0ubuntu1~ppa1~oneiric1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
     1.3.28-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
```

---

### Post by dino99 on 2012-02-06
> **jfernyhough said:**
> ah, it's rc1... Fair enough. :)

```
$ apt-cache policy wine1.3
wine1.3:
  Installed: 1.4~rc1-0ubuntu1~ppa1~oneiric1
  candidate: 1.4~rc1-0ubuntu1~ppa1~oneiric1
  version table:
 *** 1.4~rc1-0ubuntu1~ppa1~oneiric1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ oneiric/main amd64 packages
        100 /var/lib/dpkg/status
     1.3.28-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 packages
```

we talk about rc2 :(

---

### Post by marin123 on 2012-02-08
When is release of 1.4 planned?

---

### Post by dino99 on 2012-02-08
> **marin123 said:**
> When is release of 1.4 planned?

not sure, now its code freezing, so only bugs fixing; the wine team heavily work on it and have produced RC2 a week later after RC1, so the final release should land rapidly. Its already quite usable & stable, way better than 1.3/1.2

---

### Post by marin123 on 2012-02-09
> **dino99 said:**
> not sure, now its code freezing, so only bugs fixing; the wine team heavily work on it and have produced RC2 a week later after RC1, so the final release should land rapidly. Its already quite usable & stable, way better than 1.3/1.2

Thanks!
Do you know if they have fixed USB bug? Can Wine app access mass storage devices as mass storage? (example iTunes)

---

