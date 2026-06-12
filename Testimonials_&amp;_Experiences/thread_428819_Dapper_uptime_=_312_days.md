---
title: "Dapper uptime = 312 days"
date: 2007-04-30
forum: Testimonials &amp; Experiences
---

### Post by thk on 2007-04-30
Moving my server from dapper to edgy today. Its been up for 312 days strait. Not bad.

---

### Post by loserboy on 2007-04-30
nice, let me know how it goes with edgy, bout to setup a file server for my business and I was gonna just stick with dapper till the next lts

---

### Post by thk on 2007-05-02
Oh so burned... :( 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62308](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62308)

---

### Post by loserboy on 2007-05-03
*         < that problem


:)        < my head

---

### Post by stokedfish on 2007-05-03
why would you update a dapper server anyway?

I won't, things run great!   :)

---

### Post by thk on 2007-05-04
> why would you update a dapper server anyway?

I'm (evidently) a masochist :)

---

### Post by thk on 2007-05-04
The irony of this bus is that I had upgraded a dapper server to edgy many months ago and it went flawlessly. (The reason was needing some package version updates for technical work.)  That machine has been up continuously ever since and I got lulled into thinking moving my other server would be equally painless. Only, the previous server upgraded did not export home directories (just data files) and the NFS bug only effects files with a leading "." which foo bars config files in home directories.

I can only blame myself for upgrading a LTS version. Still, I have to say its rather appalling that a system critical bug like this has never been fixed in Edgy 6+ months later. It would seem that there are no Ubuntu devs mounting their home directories over NFS or this would have been caught and fixed. I see this as a huge problem: devs it appears work on standalone machines and not in shared network environments and so these sorts of applications get very little attention.

---

### Post by loserboy on 2007-05-04
edgy for the desktop has alot of bugs that you would think were serious enough to take care but for some reason they never did, I hear feisty is an overall a better release though. maybe it would be worth trying feisty... couldnt hurt.

---

