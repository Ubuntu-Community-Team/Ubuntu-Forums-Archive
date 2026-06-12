---
title: "Cannot install VirtualBox"
date: 2013-05-01
forum: Virtualisation
---

### Post by garnold on 2013-05-01
I'm a new guy around Ubuntu. A long time ago I tried it and liked it but because of work really never got the chance to use it. My new job offers much more freedom and I'm again jumping on the Ubuntu band wagon :) When I did use this operating system I installed Virtualbox to host other operating systems. I can't seem to get it installed now? I'm using the Software Center and getting some kernal errors. So there seems to be some kind of bug on this but I'm just not savy enough to work around this. Can I please get some help installed VB please? [https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1016165](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1016165)

---

### Post by ibjsb4 on 2013-05-01
For the work environment wouldn't you want something with long term support.  I recommend 12.04 LTS and download vBox from the site and not the software center.  It just seems to work better.  Also don't forget to install dkms and build-essential to whatever version you use.

```
sudo apt-get install dkms build-essential
```

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

[https://www.virtualbox.org/manual/ch02.html#idp11807728](https://www.virtualbox.org/manual/ch02.html#idp11807728)

---

### Post by garnold on 2013-05-01
Yes I'm using 12.04 LTS for that reason plus because being so new I wanted to use the version that's the most stable for me :)

*Also don't forget to install dkms and build-essential to whatever version you use.*

What do you mean by, "Whatever version you use"

---

### Post by ibjsb4 on 2013-05-01
Your version is 12.04.  Your bug report pointed to 12.10, so I just thought your using 12.10

---

### Post by garnold on 2013-05-01
Ah sorry about that, good snag. OK I did the following...

Ran this and terminal said that it was already installed

sudo apt-get install dkms

Ran this and a bunch of stuff installed so I guess thats good right?
sudo apt-get install dkms build-essential

So now I'm thinking I should install the product now correct?

---

### Post by garnold on 2013-05-01
That seemed to do it :) Thank you very much!

---

### Post by ibjsb4 on 2013-05-01
Looks like you got it :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

