---
title: "best development practices?"
date: 2010-11-22
forum: Security
---

### Post by minsf on 2010-11-22
Hi all,

I recently joined an open source project, so I was wondering if other developers here could  recommend some security practices they use.

_Motivation: _ It is a small project (3 developers) and I kind of trust them, but you know how they say trust no one... Plus, I consider this as a jump board to bigger projects, so I wonder what one does when they do not know all the other developers...

_More Details: _ the project is mainly written in java, which means I need to run _ant_ in order to build my code, but the build.xml file is so long, so I am not yet sure what it really does... Then, I need to run the jar file (_java -jar blahblah.jar_) to test it. I am using git for revision control, even though the repository is svn, but I doubt that source code management creates any big security risk, so it's probably just the ant and the jar.
 
_Some Ideas:_ Should I run "ant" and "java -jar" as a different user? something like 
```
su -c "java -jar blahblah.jar" differentUser
```
or should I chroot?
or maybe some other (better) idea?

I usually google this stuff online, but this time I have no clue what to search for, so I guess I just need some direction.

---

