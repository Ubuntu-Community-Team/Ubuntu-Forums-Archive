---
title: "What is popularity-contest?"
date: 2007-03-16
forum: The Cafe
---

### Post by barney_1 on 2007-03-16
I was just doing a dist-upgrade to feisty on one of my boxes and saw the package "popularity-contest" go by.  I did a search hear and [ran across a thread]("http://www.ubuntuforums.org/showthread.php?t=342638&highlight=popularity-contest") stating that several people think this package is unfair.

What is it?

---

### Post by kevinlyfellow on 2007-03-16
Debian (for which Ubuntu is based on) can come on a large multitude of disks.  To make installation as easy as possible, the most used software is on the first disk, then lesser on the second, then the third...

In order for devs to determine which cd to put a particular package on, they let you opt into a program that tells how much you use a particular package (which one is most popular).

---

### Post by Polygon on 2007-03-17
i think its installed by default anyway.

basically it sets up a cron job that tells a server what packages are installed on your computer. Thats all. It uses this info to determine which packages are more popular then others, hence the name

---

### Post by kevinlyfellow on 2007-03-17
>  The popularity contest project is an attempt to map the usage of Debian packages. This site publishes the statistics gathered from report sent by users of the popularity-contest  package. This package sends every week the list of packages installed and the access time of relevant files to the server via email. Every day the server anonymizes the result and publishes this survey. For more information, read the README and the FAQ.

It also sees which are used most often (by access time).  I

---

### Post by ssam on 2007-03-17
it is installed by default, but **disabled by default**

to enable it go to

System -> Administration -> Software sources and then click on the statistics tab.

the data is publicly available at [http://popcon.ubuntu.com/](http://popcon.ubuntu.com/)

the data is also used for the star ratings in Applications -> Add/Remove. this is what the accusation of unfairness stems from. The default applications all get very high ratings. Not enough people add extra software for it to get such a high rating.

For example, inkscape is a very good program, and fairly popular. but it only has 1 star. Floppy formatter can be used very often, but it is installed by default so it has 4 stars.

---

### Post by Polygon on 2007-03-17
> **ssam said:**
> it is installed by default, but **disabled by default**

to enable it go to

System -> Administration -> Software sources and then click on the statistics tab.

the data is publicly available at [http://popcon.ubuntu.com/](http://popcon.ubuntu.com/)

the data is also used for the star ratings in Applications -> Add/Remove. this is what the accusation of unfairness stems from. The default applications all get very high ratings. Not enough people add extra software for it to get such a high rating.

For example, inkscape is a very good program, and fairly popular. but it only has 1 star. Floppy formatter can be used very often, but it is installed by default so it has 4 stars.

thanks for that, i did not know it was disabled by default.

---

### Post by diskotek on 2007-03-26
thank you for the info, i've already made an upgrade and saw it. i thought it's a kind of contest that  should be in, hehe. anyway, i realised that i'm already in it ;)

most of the people install from the ubuntu cd, and the default applications are installed. so they have extra stars for that. maybe that's why inkscape don't have many stars... that was my horrible opinion on that.

---

### Post by Paqman on 2007-05-20
> **Polygon said:**
> thanks for that, i did not know it was disabled by default.

There's actually now an option in the Feisty install process to turn it on.

---

