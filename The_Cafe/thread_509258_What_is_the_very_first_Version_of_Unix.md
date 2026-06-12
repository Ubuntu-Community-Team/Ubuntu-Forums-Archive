---
title: "What is the very first Version of Unix?"
date: 2007-07-25
forum: The Cafe
---

### Post by benzies on 2007-07-25
You hear it all the time.


Linux is based of the Unix, blah blah blah.

But is there an official Unix that started everything?

Same with Linux.  What is the actual very first Linux to ever hit the streets?

Somebody please explain to me how it all began, how all the distributions are based off whatever etc.

Its very confusing, i would just like to know how it all began :(


Thanks.

---

### Post by handy on 2007-07-25
***_[http://en.wikipedia.org/wiki/Unix](http://en.wikipedia.org/wiki/Unix)_***

[I]**[Edit:]**  The wiki has a great image that lays it all out, really easy to who did what when.
Does not show all the Linux distro's though.[/I]

---

### Post by Pobega on 2007-07-25
I believe AT&T's Unix was the first...It was originally called Unics and it was based off of the Multics operating system, but that's as far as my knowledge goes. It was either the late 60s or early 70s, it's definitely somewhere in that Wikipedia article but I'm too lazy to look.

---

### Post by bonzodog on 2007-07-25
The very first distribution of Linux was called 'MCC Interim', which was shortly followed by Soft Landing Systems (SLS), which later developed in to Slackware. So, the oldest current distribution still in full development today is Slackware.

A Linux distro timeline:

[http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png](http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png)

---

### Post by tcpip4lyfe on 2007-07-25
> **bonzodog said:**
> The very first distribution of Linux was called 'MCC Interim', which was shortly followed by Soft Landing Systems (SLS), which later developed in to Slackware. So, the oldest current distribution still in full development today is Slackware.

A Linux distro timeline:

[http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png](http://upload.wikimedia.org/wikipedia/commons/e/ed/LinuxDistroTimeline.png)

Didn't know that.  Probably why slackware is so rock solid.

---

### Post by benzies on 2007-07-26
Dear God THANKYOU

My Brain can now rest, until further questioning!! Mwuahaha

:)

Cheers.

---

### Post by bogolisk on 2007-07-26
From comp.os.linux.announce
> 
Newsgroups: comp.os.linux, comp.os.linux.announce
From: sanjuan!pmacd...@sol.UVic.CA (Peter MacDonald)
Date: Tue, 15 Dec 1992 03:00:53 GMT
Local: Mon, Dec 14 1992 11:00 pm
Subject: SLS update: .99 kernel

I was so impressed with the .99 kernel, that I have already upgraded
SLS to it.  Just get SLS/a2 and "sysinstall -install /user/image.taz" it.
It may take Ted a bit to get the .99 source and change the symlink.
Be patient (don't you get tired of hearing that: give it ALL to me
right NOW!).

I am not upgrading the boot disk as yet, but let me know if the old
one causes problems (SCSI?).   The kernel has grown another 30K or so
so until/if loadable devices show up, I may have to be a little conservative
on the boot disk upgrades.  Maybe I could try rebuilding the kernel
without FP-EMU.  Do bash/tar/compress et al need FP?  

Peter
pmacd...@sanjuan.uvic.ca



For those who might be curiousr about FP-EMU: the 80386 doesn't have a floating point unit so the linux kernel (used to?) provide 80387 emulation transparently to applications.

more about SLS.
> 
Newsgroups: comp.os.linux.announce, comp.os.linux
Followup-To: poster
From: wirze...@cc.helsinki.fi (Lars Wirzenius)
Date: Tue, 8 Dec 1992 14:51:25 GMT
Local: Tues, Dec 8 1992 10:51 am
Subject: Linux INFO-SHEET

LINUX INFORMATION SHEET
by Lars Wirzenius (lars.wirzen...@helsinki.fi),
earlier versions done by other people 

.....

Other methods of obtaining Linux

        There are several BBS's that have Linux files.  A list of them
        is maintained by Zane Healy; he posts it to the comp.os.linux
        newsgroup around the beginning and middle of the month, please
        see that post for more information.

        There is also at least one organization that distributes Linux
        on floppies, for a fee.  Contact

                Softlanding Software
                910 Lodge Ave.
                Victoria, B.C., Canada
                V8X-3A8
                (608) 360-0188

        The price is US$3.25 per disk ($4.00 Canadian) in **5.25" format**
        (add $1/disk for 3.5").  Add GST (7%) and PST/SST as
        applicable, plus $10.00 for S&H (outside North America, add
        $10.00).  (Prices may change without notice.)  [b]There are 13
        disk in a base system, 21 if you want X.[/b]

        Also, don't forget about friends and user's groups, who are
        usually glad to let you make a copy.

...


---

