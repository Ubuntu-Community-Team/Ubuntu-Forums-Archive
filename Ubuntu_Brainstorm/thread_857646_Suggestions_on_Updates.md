---
title: "Suggestions on Updates"
date: 2008-07-12
forum: Ubuntu Brainstorm
---

### Post by vishnumrao on 2008-07-12
Two suggestions to the development team:

1. Size of updates: Recently a friend of mine installed Hardy Heron on his laptop. He lives in India. Although he has broadband, its a very basic service. Gives him a 120 Kilo bits per second download speed, which is slow compared to North America and Europe, Japan etc. 

Though he is happy about the OS, his major greivence is the size of updates that he needs to download every now and then. Since his internet connection is slow, the automatic download of updates uses his bandwidth. 

I taught him to turn off updates, but that is not very advisable, as he wants to run the latest versions of packages he uses.

My suggestion is that the size of updates should be made really small. And I don't know how he's going to do a dist-upgrade when Intrepid Ibex is released. It will take him days to do a dist-upgrade at 120 kbps download speed. 

2. Some time back, I read about some guy using P2P to apply updates to about 30 machines he administers in a lab or school. I am not sure about the details of story. 

My suggestion: why not use P2P to give updates to Ubuntu machines worldwide. It will put less load on the servers. It will be very very useful when newer versions of the OS are released every 6 months and people start doing dist-upgrade. P2P has been proved to be useful to share very large files in illegal torrent downloading. Time we put it to do legal updates downloading (and hopefully Comcast will not throttle speeds).

By default the share ratio for updates that have been downloaded can be set to 1, and give the user to raise or lower the ratio.

Comments on the merits and downfalls of my suggestion are welcome.

---

### Post by Merk42 on 2008-07-12
Your first suggestion... do you have any idea how they would make it smaller? Or is it one of those things where you just wave your arms and go "I don't care, go do it"

As for the second suggestion it's been brought up a few times, especially for new distribution upgrades, to use torrent.  [It has been been sort of worked on](http://sianka.free.fr/), but brings up issues of having to transfer the repos to it and security issues.

---

### Post by vishnumrao on 2008-07-12
Merk42, 

1. I did not mean to sound like how you put it. I am very enthusiastic about Linux adoption and preach Ubuntu to my friends and family. This was a concern that my friend expressed and I thought I will try querrying at the forum as a suggestion. 

Compressing the updates to a high compression ratio and then putting it out for the folks to grab it could be one possibility. 

Or skipping versions could be one option. Eg. if Ubuntu were to release updates once in two months, and if a package was revised 3 times in two months, the update would be released only once. i.e instead of releasing the package for general public every version, Ubuntu could hold back and release updates in a fixed cycle. Maybe once in a month or once in two months. 

2. Cool! someone's already implemented it. Will the package be available for Ubuntu and supported? Would love to try it while updating to Ibex. But what are the security issues accociated with this?

---

### Post by Merk42 on 2008-07-13
Well if you want to skip versions, then couldn't your friend turn off updates and manually check them every few months?

I don't know if the torrent thing will ever be implemented, honestly.  If you search the forums you can see it brought up every once in a while.  One of the problems is that ISPs limit/block ANY torrent traffic.

---

### Post by zekopeko on 2008-07-13
> **Merk42 said:**
> Your first suggestion... do you have any idea how they would make it smaller? Or is it one of those things where you just wave your arms and go "I don't care, go do it"


he gave a valid suggestion. don't be an ars. anyway they can use delta updates. you basically just download the bytes that have changed not the entire application. the problem is something about stress on the servers + digital signing or something similar.

---

### Post by Merk42 on 2008-07-13
> **zekopeko said:**
> he gave a valid suggestion. don't be an ars.

Simply saying "Make it smaller" is incredibly vague, and verging on idealistic. At least with the latter mention of compression does it get more realistic.

---

### Post by smartboyathome on 2008-07-14
> **zekopeko said:**
> he gave a valid suggestion. don't be an ars. anyway they can use delta updates. you basically just download the bytes that have changed not the entire application. the problem is something about stress on the servers + digital signing or something similar.

Though like has been said about Delta updates, they could theoretically be bigger than a normal update if you have to wait long enough to update, since you have to apply each patch after another in order not to break the source.

---

