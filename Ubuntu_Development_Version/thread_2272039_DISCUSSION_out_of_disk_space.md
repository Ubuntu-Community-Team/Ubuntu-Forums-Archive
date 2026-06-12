---
title: "DISCUSSION: out of disk space"
date: 2015-04-03
forum: Ubuntu Development Version
---

### Post by bardo2 on 2015-04-03
Hi,

while browsing through the forums, i stumbled into this kind of error quite a lot. And then users tend to have problems to get even the most basic things to work, to get that situation fixed. I know, this is not really a difficult situation to remedy, but the problem seems to be a frequent one.

If i was responsible for the distro, i would try to make things easier. My background:

I am using ZFS as the base filesystem, which, since it is a COW filesystem that tends to slow down with less than 20% of free space and can easily bring the system to a halt, once space runs out, i am reserving 20% from being used. If any problem related to disk space would ever occur, i could temporarily remove that reservation and fix the underlying problem before i set the reservation back.

Ok, ext4 is different, but i suggest a similar approach: why not create a file of adequate size while installing, thus having the OS bark earlier than usual, so that in case of a problem, just removing that file would render the system stable once again, so that any problem resolution would be way easier? - Well, i guess, there are downsides to that approach as well, just saying: i think, the distrubutor should prevent so many users from running out of space and having dire straits at getting their systems up and running comfortably again.

What is your opinion, and where to put this suggestion forward to?

---

### Post by mikewhatever on 2015-04-03
Not sure reserving 20% of space is a good idea. We get occasional complaints over the 5% reserved by default, if it's 20%, every second post would be "Hey. where is my space?". Besides, it doesn't occur too frequently, and most of the really problematic ones are about a boot partition being too small, when it shouldn't be there in the first place.

---

### Post by Elfy on 2015-04-03
> most of the really problematic ones are about a boot partition being too small, when it shouldn't be there in the first place.

This.

Though from what I can see it should be there, /boot partition for encrypted installs.

The issue appears to be /boot size with old kernels not being removed prior to install of newer ones and/or people ignoring warnings.

---

