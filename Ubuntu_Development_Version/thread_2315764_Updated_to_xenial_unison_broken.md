---
title: "Updated to xenial: unison broken"
date: 2016-03-02
forum: Ubuntu Development Version
---

### Post by wgarcia on 2016-03-02
Just upgraded to xenial this Monday. Except for some errors related to installing the new kernel 4.4, that didn't stop the upgrade, the main problem I found is that the unison syncronization tool is broken. This is the bug report:

[https://bugs.launchpad.net/ubuntu/+source/unison/+bug/1421184](https://bugs.launchpad.net/ubuntu/+source/unison/+bug/1421184)

and 

[https://bugs.launchpad.net/ubuntu/+source/unison/+bug/1548840](https://bugs.launchpad.net/ubuntu/+source/unison/+bug/1548840)

---

### Post by dino99 on 2016-03-02
the xenial's unison use now ncurses6; so your issue might be related i suppose.

---

### Post by sudodus on 2016-03-02
I can confirm that the synchronizing data must be re-configured after updating to xenial - but after that is done, unison works.

---

### Post by wgarcia on 2016-03-02
Which version do you see, sudodus? May be there is an update to 2.48 (2.40 is the one that is broken) and it hasn't arrived to me. And yes, dino99, according to the bug reports linked above, ncurses6 is the culprit, 2.40 cannot run against it, but 2.48 can.

---

### Post by sudodus on 2016-03-02
unison version 2.40.102

---

### Post by wgarcia on 2016-03-02
That's strange, 2.40.102 dumps core as soon as I call it, and according to the linked bug reports above I'm not the only one seeing this.

---

### Post by sudodus on 2016-03-02
I think it dumped a core feb 28 for me too, but I have used it several times, and it seems to work for me. I'll check again, what happens today ... it works.

I think my kernel was recompiled recently because I installed VirtualBox. Maybe that made it updated, so that it can manage Unison.

I've had a number of 'kernel oops' too, which were automatically prompting bug reports, but it seems to work today (without core dumps and kernel oops).

---

### Post by sudodus on 2016-03-02
Maybe I should mention that I'm running a 32-bit version:

```
$ uname -a
Linux xenial32 4.4.0-8-generic #23-Ubuntu SMP Wed Feb 24 20:44:33 UTC 2016 i686 i686 i686 GNU/Linux
```

---

### Post by wgarcia on 2016-03-03
Still broken here on a xenial completely updated, it must be the 64bit architecture then.

```
$ uname -a 
Linux xenial 4.4.0-9-generic #24-Ubuntu SMP Mon Feb 29 19:33:19 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
$ dpkg -l unison
ii  unison         2.40.102-2ub amd64        file-synchronization tool for Uni
$ unison
&#65533;'r&#65533;.rSegmentation fault (core dumped)

```

---

### Post by sudodus on 2016-03-03
Yes, probably the 64-bit Unison is buggy. (But when I dist-upgrade to the same kernel number as you have (4.4.0-8-generic #23-Ubuntu --> 4.4.0-9-generic #24-Ubuntu), I will test if that makes a difference.)

---

### Post by sudodus on 2016-03-04
I upgraded the kernel today: 4.4.0-8-generic #23-Ubuntu --> 4.4.0-9-generic #24-Ubuntu to

```
$ uname -a
Linux xenial32 4.4.0-9-generic #24-Ubuntu SMP Mon Feb 29 19:30:41 UTC 2016 i686 i686 i686 GNU/Linux
```

and Unison is still working for me, so the 32-bit version works for me, while the 64-bit version does not work for you.

---

### Post by Irihapeti on 2016-03-13
Unison works if the remote folder is mounted on the local machine.

When I try and sync using a ssh:// url, it crashes. I prefer the ssh:// option because it's (a lot) quicker to calculate which files need to be synced.

---

### Post by sudodus on 2016-03-14
I think you found something important, *irihapeti*. I use unison only with local drives (internal and external, but not via any network).

---

### Post by wgarcia on 2016-03-14
Thanks irihapeti. Unison still broken here, and the bug report hasn't progressed. Anybody affected, it would be good to click the "I'm affected" button. 

The bug report:
[https://bugs.launchpad.net/ubuntu/+source/unison/+bug/1421184](https://bugs.launchpad.net/ubuntu/+source/unison/+bug/1421184)

---

### Post by Irihapeti on 2016-03-14
I tried to run Unison again this evening. It being the second time I'd tried to sync the two machines, I thought it might be quicker than the first time. No such luck. It was like wading through molasses in winter. I got totally fed up with it and went back to just using rsync from the command line.

It's a bit more fiddly, but *so* much faster.

---

### Post by sudodus on 2016-03-14
Once Unison is set up with two almost identical drives, it can manage the diffs very nicely. But it seems the version in Xenial is new, and needs to get set up again with whatever it uses to decide if the files are still matching.

But I agree, rsync is faster, and often rsync provides good enough control.

---

### Post by wgarcia on 2016-03-15
Irihapeti, unless it has changed or is broken, unison is slow the first time it creates all the catalogues, especially if it is synching large volumes. After a couple of synchronizations it gets faster. 

But of course I haven't been able to use it yet as it is still broken over ssh, so I'm also using rsync. It is not the same, if there is any conflict between the two volumes being synched it may imply a loss of information.

---

### Post by Irihapeti on 2016-03-15
I expected Unison to be slow the first time it created the catalogue. I didn't expect it to be slow the second time, after only a few changes. By "slow", I mean something like 30-40 minutes.

I know that one needs to be careful with rsync. I make a point of running rsync -n (dry run) before I do it for real.

---

### Post by Irihapeti on 2016-03-19
Good news here is that the latest update has made unison usable over ssh again. *Sooooo* much faster. YAY!

---

### Post by wgarcia on 2016-03-20
Confirmed, this issue has been solved.

---

