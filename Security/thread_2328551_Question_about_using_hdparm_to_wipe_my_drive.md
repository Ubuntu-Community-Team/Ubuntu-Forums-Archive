---
title: "Question about using hdparm to wipe my drive?"
date: 2016-06-22
forum: Security
---

### Post by SpaceManJack on 2016-06-22
Ok first off I have already successfully used DBAN to wipe my drive but just in case it didn't work I want to use another program to wipe my drive, just to be totally sure. Someone told me to check out this post  in another thread, that this post would show me how to use hdparm, here [http://ubuntuforums.org/showthread.php?t=2124829&page=2&p=12555068#post12555068](http://ubuntuforums.org/showthread.php?t=2124829&page=2&p=12555068#post12555068)

If you check out that post you'll see that he entered several commands into the terminal but I'm confused, which ones do I enter in exactly? Do I copy him command for command?

p.s. please dont try and recommend other ways to wipe my drive I wish to understand how to use hdparm thanks.

---

### Post by HermanAB on 2016-06-23
Here you go:

$ ls /dev/sd*
Note the device name and substitute the sdX below.

$ sudo hdparm --security-set-pass user /dev/sdX
$ sudo hdparm --security-erase-enhanced user /dev/sdX

Looooooong wait...

---

