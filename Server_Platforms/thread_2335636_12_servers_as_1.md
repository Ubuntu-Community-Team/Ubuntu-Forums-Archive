---
title: "12 servers as 1"
date: 2016-08-30
forum: Server Platforms
---

### Post by nimoria on 2016-08-30
Hello


I have 12 ubuntu servers running different calculation program (math).


We now use the different servers separate but it is not optimal, and we are looking for a solution to run all together.


1: install & update all machines simultaneously


2: add all calculations in a queue and load balancing between machines (all calculations runs through commandline commands)


I've been thinking about writing some scripts that perform the above, but is there any better "standard solution"


I've looked a little on ubuntu MAAS but do not know if that's the way to go. (Overhead)


/Nimoria

---

### Post by Vegan on 2016-08-30
what are you doing that needs 12 boxes? there are servers with tons of cores if you need them

---

### Post by nimoria on 2016-08-31
We do heavy calculations of big GIS data.

Each "box" has four CPUs with 8 cores each, which was the most cost-effective when we bought the hardware.

/Nimoria

---

### Post by coldraven on 2016-08-31
There is "Landscape" but it costs money and may be overkill for your needs.
[https://landscape.canonical.com/](https://landscape.canonical.com/)

---

### Post by SeijiSensei on 2016-08-31
Have you considered "clustering" technologies like [Beowulf]("https://www.linux.com/blog/building-beowulf-cluster-just-13-steps")?  They were designed precisely for the type of application you describe with heavy computational needs.

---

### Post by nimoria on 2016-09-01
Thanks ! I will look at both proposals...

---

### Post by linuxdude1990 on 2016-09-05
Regardless of server distro, I would actually follow advice on Beowulf, it really is exactly what you're looking for.

Otherwise I would invest in the hardware of syncing the four machines as one machine and virtualizing the servers but cost wise, that would not be practical at all.

---

