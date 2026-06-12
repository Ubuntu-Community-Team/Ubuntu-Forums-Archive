---
title: "Download the whole repository"
date: 2009-07-18
forum: Server Platforms
---

### Post by Vegan on 2009-07-18
How big is the whole repository? I was thinking that it might be more expedient to have it on the LAN where things are faster than try to download it over and over.

---

### Post by ktrnka on 2009-07-18
For each release of Ubuntu the repositories are around 40-50GB(remember for EACH). You can use apt-mirror to download the repository and setup your own mirror. 

apt-mirror is in the repos but here is more info.

[http://apt-mirror.sourceforge.net/]("http://apt-mirror.sourceforge.net/")

---

### Post by Vegan on 2009-07-18
Thanks for the reference, I was wondering: could the mirror be incrementally updated easily?

---

### Post by ktrnka on 2009-07-18
Yea you can interrupt it and it will pickup where it left off the next time you run it.

---

### Post by windependence on 2009-07-19
> **Vegan said:**
> Thanks for the reference, I was wondering: could the mirror be incrementally updated easily?

First off, you don't download the entire repository because it's constantly changing. Secondly, hello, MIRROR - that means you are always up to date with what is on the repository server. I can't see much, if any advantage to doing this. The repos are pretty fast these days.  :-s

-Tim

---

### Post by jerrrys on 2009-07-19
maybe a compromise, the DVD...

[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu)

---

### Post by Cheesemill on 2009-07-19
> **jerrrys said:**
> maybe a compromise, the DVD...
 
[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu)
 
The DVD doesn't contain any more packages than the CD, it just has more languages.

---

### Post by ramnarayan on 2009-07-19
> **windependence said:**
> You really are a bit of a nutbag. First off, you don't download the entire repository because it's constantly changing. Secondly, hello, MIRROR - that means you are always up to date with what is on the repository server. I can't see much, if any advantage to doing this. The repos are pretty fast these days.  :-s

-Tim

Am not sure the OP said "mirror"

Regarding having the whole repos, depends on how well one is connected to the net ?? always on big pipe sure good but what if the bandwidth is narrow ??

then it might help because the packages can be installed locally and then maybe only updates need to be applied

I normally try and get the entire set of DVD (repos) 6 for 9.04 from someone who might have them and keep aside a section of my external HD and just install packages that i want from there ?? 

it really helps esp if i have to install for someone else and want them up and running with everything they can dream of.

Added to that my bandwidth is really slow, creaky and unreliable

EDIT - ask around, some one in your neighborhood may already have the repos.

---

### Post by jerrrys on 2009-07-19
> **Cheesemill said:**
> The DVD doesn't contain any more packages than the CD, it just has more languages.

my mistake, but i do find this misleading...

[ATTACH]121653[/ATTACH]

---

### Post by HermanAB on 2009-07-19
Howdy,

I get my distribution repositories from mirrors.kernel.org using wget.  However, be kind to other users and use the random delay feature of wget when you do that.  With random delays, it takes about 3 days to download a repo and the size is around 30GB including all binaries and source code.

---

### Post by Cheesemill on 2009-07-19
> **jerrrys said:**
> my mistake, but i do find this misleading...
 
[ATTACH]121653[/ATTACH]
 
All of the supported software is not the same as the entire repos.

---

### Post by Vegan on 2009-07-19
I was hoping to leverage my server to make fresh installs on other machines a bit more expedient.

In practice the download speeds for updates are slow here in Canada.

---

### Post by cariboo on 2009-07-19
The last week or two the Canadian servers: [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) have been fairly fast, I have been updating at between 180Kb and 200Kb.

---

