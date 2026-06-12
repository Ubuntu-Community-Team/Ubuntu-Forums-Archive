---
title: "Kernel 6.1 RC (Release Candidate) Series"
date: 2022-10-03
forum: Ubuntu Development Version
---

### Post by zika on 2022-10-03
Looking ahead to new version of kernel that carry nice promises...
[https://www.phoronix.com/news/Linux-6.1-Features-Early-Look](https://www.phoronix.com/news/Linux-6.1-Features-Early-Look)

---

### Post by Doug S on 2022-10-16
[Kernel 6.1-rc1]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1-rc1/") is available in the mainline PPA.

I am compiling it now. It has 102 default kernel configuration changes:

```
doug@s19:~/kernel/linux$ scripts/diffconfig .config-6.0 .config | wc -l
102
doug@s19:~/kernel/linux$
```

---

### Post by zika on 2022-10-17
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1-rc1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1-rc1/)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)
> **@ 2022-10-16 23:01 Linus Torvalds**[B]  2022-10-17  1:53 ` [linux-next: stats for 6.1-rc1 (was: Linux 6.1-rc1)]("https://lore.kernel.org/lkml/CAHk-=wj6y5fipM2A5kEuOO9qm5PBzUY=-m9viEahhtxT09KR_g@mail.gmail.com/T/#me119bfca21774da74531eb8d1649c6b191275a8e") Stephen Rothwell
  2022-10-17  2:58 ` [6.1rc1: NFS memcpy warning on mount]("https://lore.kernel.org/lkml/CAHk-=wj6y5fipM2A5kEuOO9qm5PBzUY=-m9viEahhtxT09KR_g@mail.gmail.com/T/#m48fc1a57563995b750e7dc9532af41bc56ec12ae") Dave Jones
  [0 siblings, 2 replies; 7+ messages in thread]("https://lore.kernel.org/lkml/CAHk-=wj6y5fipM2A5kEuOO9qm5PBzUY=-m9viEahhtxT09KR_g@mail.gmail.com/T/#r57b4391783002641215c01e1d799dbd7916e6f9c")
From: Linus Torvalds @ 2022-10-16 23:01 UTC ([permalink]("https://lore.kernel.org/lkml/CAHk-=wj6y5fipM2A5kEuOO9qm5PBzUY=-m9viEahhtxT09KR_g@mail.gmail.com/") / [raw]("https://lore.kernel.org/lkml/CAHk-=wj6y5fipM2A5kEuOO9qm5PBzUY=-m9viEahhtxT09KR_g@mail.gmail.com/raw"))
  To: Linux Kernel Mailing List

You all know the drill: it's Sunday afternoon, the two weeks of merge
window are over, and now we're supposed to start calming things down.

This isn't actually shaping up to be a particularly large release: we
"only" have 11.5k non-merge commits during this merge window, compared
to 13.5k last time around. So not exactly tiny, but smaller than the
last few releases. At least in number of commits.

That said, we've got a few core things that have been brewing for a
long time, most notably the multi-gen LRU VM series, and the initial
Rust scaffolding (no actual real Rust code in the kernel yet, but the
infrastructure is there).

And hey, this merge window was full of surprises for other reasons too
- my main machine was basically out of action for a couple of days
because it suddenly started showing memory problems, and it took me a
couple of days to get that sorted out (to a large degree because it
was unexpected and I started out blaming a kernel bug for the memory
corruption). All sorted out now, but it caused some frustration.

Talking about frustration, let me just say that after I got my machine
sorted out and caught up with the merge window, I wass somewhat
frustrated with various late pull requests. I've mentioned this
before, but it's _really_ quite annoying to get quite a few pull
requests in the last few days of the merge window.

Yes, the merge window is two weeks, but that's very much to allow me
time to look things over, not "two weeks to hurriedly put together a
branch that you send Linus on Friday of the second week". The whole
"do an all-nighter to get the paper in the day before the dealine" is
something that should have gone out the window after highschool. Not
for kernel development.

The rule is that things that get sent to me should be ready *before*
the merge window opens, not be made ready during the merge window.
With some slack for "life happens", of course, but I really get the
feeling that a few people treat the end of the merge window as a
deadline, missing the whole "it was supposed to be ready before the
merge window".

You know who you are.

Anyway, it's not the first time I've said this, I doubt it will be the
last. But maybe more people could take it to heart, ok?

Enough kvetching, let's get this party calmed down. The merge window
may not be the biggest ever, but it's certainly big enough that the
shortlog is much too big to post, and below is just my usual merge
log. For all the gory details, please refer to the git tree.

Please get the testing started,

                   Linus
[https://www.phoronix.com/news/Linux-6.1-rc1-Released](https://www.phoronix.com/news/Linux-6.1-rc1-Released)
[/B]

---

### Post by zika on 2022-11-22
[https://www.phoronix.com/news/Linux-6.1-rc6-Released](https://www.phoronix.com/news/Linux-6.1-rc6-Released)
Any news what is happening with [https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D) ...?

---

### Post by Doug S on 2022-11-22
> **zika said:**
> [https://www.phoronix.com/news/Linux-6.1-rc6-Released](https://www.phoronix.com/news/Linux-6.1-rc6-Released)
Any news what is happening with [https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D) ...?Hi Zika,
Due to some ongoing testing that needs all things equal, I have been on 6.1-rc3 for a few weeks now and didn't notice the lack of mainline -rc6, or anything since Nov 18th. Suggest we give it a few more days and then chime in on that discourse page or IRC.

---

### Post by Doug S on 2022-11-27
O.K. Mikemecanic posted on [the kernel discourse page]("https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/77") inquiring about the lack of mainline builds. Zika and I have clicked the "like" button, any other readers please so the same.

---

### Post by IanW on 2022-11-29
> **Doug S said:**
> O.K. Mikemecanic posted on [the kernel discourse page]("https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/77") inquiring about the lack of mainline builds. Zika and I have clicked the "like" button, any other readers please so the same.

Done.

There is a reply, posted yesterday:-
[quote=XNOX]On 17th of November a broken config was pushed, which made the build machinery error out even before attempting builds and/or triggering notification of failed builds. I have a patch to unbreak it, and we will try to re-schedule build for it to catch up.[/quote]

---

### Post by IanW on 2022-11-30
UPDATE - Mainline PPA now has a [2022-11-30 folder]("https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2022-11-30/"), but all attempted builds of 6.1-rc7 seem to have failed.

---

### Post by zika on 2022-11-30
> **IanW said:**
> UPDATE - Mainline PPA now has a [2022-11-30 folder]("https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2022-11-30/"), but all attempted builds of 6.1-rc7 seem to have failed.
[https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2022-11-30/amd64/log](https://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2022-11-30/amd64/log)

...

[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1-rc8/log](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1-rc8/log)

---

### Post by Doug S on 2022-12-09
The mainline compiles are still broken. Thanks to those that have chimed in on [the kernel discourse page]("https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664"). I found [this on IRC]("https://irclogs.ubuntu.com/2022/12/02/%23ubuntu-kernel.html"), which was a reply to [a post from the day before]("https://irclogs.ubuntu.com/2022/12/01/%23ubuntu-kernel.html").

---

### Post by cbotmk3 on 2022-12-19
The mainline builds for version 6.1 final also failed: [https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1/)
I really want to use 6.1, any news on this?

---

### Post by zika on 2022-12-19
After this answer:  [https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/88](https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/88) I've got on Discource I would not hold my breath about Mainline, anymore...
You might try *linux-image-generic-wip*, or *linux-lowlatency*,
currently:
```
[COLOR=#000000]:~$ apt policy linux-image-generic-wip
[/COLOR]linux-image-generic-wip:
  Installed: 6.1.0.9.9
  Candidate: 6.1.0.9.9
  Version table:
 *** 6.1.0.9.9 500
        500 https://ppa.launchpadcontent.net/canonical-kernel-team/bootstrap/ubuntu devel/main amd64 Packages
        100 /var/lib/dpkg/status
     6.1.0.3.3 500
        500 https://ppa.launchpadcontent.net/canonical-kernel-team/bootstrap/ubuntu kinetic/main amd64 Packages
```

```
[COLOR=#000000]:~$ apt policy linux-lowlatency
[/COLOR]linux-lowlatency:
  Installed: 6.1.0.1001.1
  Candidate: 6.1.0.1001.1
  Version table:
 *** 6.1.0.1001.1 500
        500 https://ppa.launchpadcontent.net/canonical-kernel-team/bootstrap/ubuntu devel/main amd64 Packages
        100 /var/lib/dpkg/status
     5.19.0.1009.8 100
        100 http://archive.ubuntu.com/ubuntu devel-proposed/main amd64 Packages
        100 http://archive.ubuntu.com/ubuntu lunar-proposed/main amd64 Packages
     5.19.0.1007.7 500
        500 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu lunar/main amd64 Packages
        500 https://ppa.launchpadcontent.net/canonical-kernel-team/bootstrap/ubuntu kinetic/main amd64 Packages
```
I'm, only, a bit, or even byte, scared that these PPA's might disappear after I've mentioned them here and above... ;)

---

### Post by MAFoElffen on 2022-12-19
> **zika said:**
> After this answer:  [https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/88](https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/88) I've got on Discource I would not hold my breath about Mainline, anymore...

I'm, only, a bit, or even byte, scared that these PPA's might disappear after I've mentioned them here and above... ;)
Dang... ](*,)](*,)](*,)

---

### Post by cbotmk3 on 2023-01-08
Seems like the build of 6.1.1 from yesterday succeeded again, but 6.1.2 to 6.1.4 did not:
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1.1/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1.1/)

I'll try starting with 6.1.1 right now.

---

### Post by xyz-t on 2023-01-09
This is up:
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1.4/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1.4/)

or cappelikan ppa::
[https://9to5linux.com/you-can-now-install-linux-kernel-6-1-on-ubuntu-heres-how](https://9to5linux.com/you-can-now-install-linux-kernel-6-1-on-ubuntu-heres-how)

Website:
[https://code.launchpad.net/~cappelikan/+archive/ubuntu/ppa](https://code.launchpad.net/~cappelikan/+archive/ubuntu/ppa)

---

### Post by IanW on 2023-01-13
Mainline updater offered me 6.1.5 last night, but the build process errored out.

EDIT - The kernel installed fine. My error was the dkms build of Nvidia GPU drivers failing, as 6.1.5 is "not supported".
EDIT #2 - The dkms error was because I'd previously installed GPU drivers using Nvidia's *.run file. Switching back to Ubuntu's repo fixed it.

---

### Post by cbotmk3 on 2023-01-19
I switched to xanmod kernel: They always have the newest kernel via repository (plus it's a performance-optimized one).

---

### Post by corradoventu on 2023-02-01
On my Ubuntu Lunar I installed Kernel 6.1 from proposed. It boot successfully but:
Starts with X11 session not allowing to select Wayland
The X11 session shows a wrong monitor resolution
does not see my smartfone hotspot so I can't access the web

---

### Post by IanW on 2023-02-08
Installed 6.1.10 from mainline this morning without issue.

BTW - [6.1 is now the official LTS kernel of 2022]("https://www.phoronix.com/news/Linux-6.1-LTS-Official")

---

### Post by zebra2 on 2023-03-04
Kernel 6.1 in the downstream. Today March 4th 2023 Ubuntu 23.04

---

### Post by jonestruckzs on 2023-08-09
[COLOR=#000000][I] I have a patch to unbreak it, and we will try to re-schedule build for it to catch up.
[/I][/COLOR][SIZE=1][whatsapp mod]("https://waplus.win/")[/SIZE]
[SIZE=1][watch tv series ]("https://projectfreetv.onl/")[/SIZE]

---

