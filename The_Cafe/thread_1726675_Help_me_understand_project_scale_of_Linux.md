---
title: "Help me understand project scale of Linux"
date: 2011-04-11
forum: The Cafe
---

### Post by asifnaz on 2011-04-11
I sometimes think Linux is a vary large scale project . My friend suggest me otherwise . They say Linux is a fairly big project but not as big as I think .

They say a handful group of people are working on similar project <Haiku OS> and they already have a fairly stable and working OS 
  
Kindly help me understand what is scale of Linux ....

what it takes to become a working OS like Linux ...????

and by Linux I mean gun/linux not kernel only .

I hope you will understand my confused question and answer it.

---

### Post by koenn on 2011-04-11
> A similar study was later made of Debian Linux version 2.2 (also known as "Potato"); this version of Linux was originally released in August 2000. This study found that Debian Linux 2.2 included over 55 million lines of source code, and if developed in a conventional proprietary way would have required 14,005 person-years
[http://en.wikipedia.org/wiki/Source_lines_of_code](http://en.wikipedia.org/wiki/Source_lines_of_code)

that should give you an idea

---

### Post by screaminj3sus on 2011-04-11
There are tons of people that develop for linux, but development is very fragmented into a bunch of smaller projects. In a way you are both right.

---

### Post by Seq on 2011-04-11
Your friends are likely underestimating the number of people who contribute.

[The MAINTAINERS file from the Linux 2.6.38.2]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.38.y.git;a=blob;f=MAINTAINERS;h=f1bc3dc6b3699de3c072bfce91b3ec25417e41cb;hb=cf6013b4a767169ca105edec2735ef7ff8d9b403") is 7000 lines long. Granted, there is a bit of formatting in there, but it only lists module maintainers. Many, many more fix issues and pass them along to those maintainers, and will be credited within those files directly.

Slightly older information, but [kernel 2.6.35 had patches from 1145 people]("http://lwn.net/Articles/395961/"). Thats only counting patches applied in the three-month window between 2.6.34 and 2.6.35.

Now, to compare to an all-in-one OS like Haiku, you also need to factor in all of the GNU userspace (bash, etc), and literally thousands of other projects (X11, GNOME, upstart, avahi, firefox, Ubuntu packaging folks etc.), some of which are large, some are small. Also, that's not even factoring in folks who contribute in non-code ways (translators, testers, etc).

Furthermore, there are enough people doing packaging and distribution that it is not only one group doing this work, but many. [Distrowatch lists ten distributions considered "Major"]("http://distrowatch.com/dwres.php?resource=major") (#11 is FreeBSD). [Their popularity chart lists 320 distributions]("http://distrowatch.com/stats.php?section=popularity").

---

