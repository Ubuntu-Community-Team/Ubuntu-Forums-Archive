---
title: "Same Song Twice"
date: 2010-05-09
forum: Ubuntu One (CLOSED)
---

### Post by MidChaos on 2010-05-09
I purchased the soundtrack for the movie Fireproof, when I first bought it it downloaded all but 1 track, which is track 17, While I'm Waiting (Fireproof Edition). I noticed that there were a few people who had tracks that didn't download so I waited a few days to see if it would, now it finally said it did and it turns out that it ended up downloaded track 10 twice (has a (2) at the end, tracks have same name, just different versions and the difference in name is what is in the () after the name) and when I listen to both of them they are the exact same. So now I'm wondering how I'm going to get track 17 from my purchased soundtrack?

So if anyone has any ideas what I should do or knows a way for me to get the track I'm missing please let me know.

Thanks!

---

### Post by duanedesign on 2010-05-09
The 7digital api provides very basic info about song names and does not allow to identify songs uniquely. That's why the download daemon was downloading Song.mp3 and when request for _another_ Song.mp3 arrived it was not possible to find out whether this is the one is still required to be downloaded or this is the existing one. The programmers are working with 7d now to find out what to do in this case.


See this bug for more info. You can subscribe to it for the latest on the issue. [http://launchpad.net/bugs/547074](http://launchpad.net/bugs/547074)

---

### Post by samortan on 2010-10-12
Well, it would be easy and nice if you download it again. Or you can check it from some where else which track is missing. You will find number of websites doing the same.

---

