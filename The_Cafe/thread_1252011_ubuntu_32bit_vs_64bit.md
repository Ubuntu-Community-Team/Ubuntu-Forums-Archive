---
title: "ubuntu 32bit vs 64bit"
date: 2009-08-28
forum: The Cafe
---

### Post by joe2012 on 2009-08-28
What kind of performance increase is there if I install ubuntu 64bit on a 64bit process as opposed to installing the 32bit?

---

### Post by lackhand on 2009-08-28
I have an 64 bit processor, so I tried out the 64 bit version of Ubuntu and didn't notice any increase in performance.  But I did have a few problems with compatibility.  So I switched back to 32 bit.

---

### Post by joe2012 on 2009-08-28
> **lackhand said:**
> I have an 64 bit processor, so I tried out the 64 bit version of Ubuntu and didn't notice any increase in performance.  But I did have a few problems with compatibility.  So I switched back to 32 bit.

what kind of problems did you have?

---

### Post by Sxeptomaniac on 2009-08-28
I ran into a few problems, such as Google Gears only working on 32-bit systems without a bit of tweaking.  Overall, not a big performance difference, but I think it will come into play more as people tend to increase their RAM to 4gb and up, which requires a 64-bit OS to take advantage of it (if I remember correctly).

---

### Post by joe2012 on 2009-08-28
> **Sxeptomaniac said:**
> I ran into a few problems, such as Google Gears only working on 32-bit systems without a bit of tweaking.  Overall, not a big performance difference, but I think it will come into play more as people tend to increase their RAM to 4gb and up, which requires a 64-bit OS to take advantage of it (if I remember correctly).

did you have any problems with wine? or open office?

---

### Post by steeleyuk on 2009-08-28
I run 64-bit. OpenOffice is fine, same with wine for the most part.

I noticed an improvement when converting video formats and DVD copying to hard disk... as much as a 50% speed boost on some. All in all, 64-bit on my machine is that bit smoother.

---

### Post by lackhand on 2009-09-01
> **joe2012 said:**
> what kind of problems did you have?

It's been over a year and I can't remember all of them really.  But they were software compatibility problems.  Some stuff just wasn't available for 64 bit, and trying to hack to get it to install was just too much for me.  I don't recall having issues with OpenOffice and I didn't try WINE, but I seem to remember flash not working.  

Might be worth trying again as there's been a few new releases of Ubuntu since then.

---

### Post by hanzomon4 on 2009-09-01
I haven't had any problems. Skype, flash, java... everything is 64 bit native, I have no 32bit apps. It's great knowing that I've got an OS that's fully 64bit. Performance is great.

---

### Post by lackhand on 2009-09-01
I'll have to try 64 bit when Karmic is out then.  Looking forward to that.

---

### Post by FuturePilot on 2009-09-01
I've been using 64bit for a while now. No problems at all. Everything works great.

> **hanzomon4 said:**
> I haven't had any problems. Skype, flash, java... everything is 64 bit native, I have no 32bit apps. It's great knowing that I've got an OS that's fully 64bit. Performance is great.

Skype is only 32bit.

> **lackhand said:**
> It's been over a year and I can't remember all of them really.  But they were software compatibility problems.  Some stuff just wasn't available for 64 bit, and trying to hack to get it to install was just too much for me.  I don't recall having issues with OpenOffice and I didn't try WINE, but I seem to remember flash not working.  

Might be worth trying again as there's been a few new releases of Ubuntu since then.

Definitely give it another shot. 64bit Ubuntu has come a long way in a year.

---

### Post by hanzomon4 on 2009-09-01
> **FuturePilot said:**
> I've been using 64bit for a while now. No problems at all. Everything works great.



Skype is only 32bit.



Definitely give it another shot. 64bit Ubuntu has come a long way in a year.

I'm pretty sure the beta I'm using is 64bit 2.1

---

### Post by NCLI on 2009-09-01
Wine 64-bit is very unstable, so I'm sticking with 32-bit for now.

---

### Post by joe2012 on 2009-09-01
> **NCLI said:**
> Wine 64-bit is very unstable, so I'm sticking with 32-bit for now.

What version of ubuntu and wine are you using?

---

### Post by gn2 on 2009-09-01
For the most part there is no appreciable difference.
CPU intensive tasks like encoding video can complete much faster with 64-bit.

---

### Post by Tibuda on 2009-09-01
> **FuturePilot said:**
> Skype is only 32bit.
They have released a 64bit version for the latest beta.

[http://www.skype.com/go/getskype-linux-beta-ubuntu-64](http://www.skype.com/go/getskype-linux-beta-ubuntu-64)

---

### Post by FuturePilot on 2009-09-01
> **danielrmt said:**
> They have released a 64bit version for the latest beta.

[http://www.skype.com/go/getskype-linux-beta-ubuntu-64](http://www.skype.com/go/getskype-linux-beta-ubuntu-64)

It's not a native 64bit binary.

```
$ uname -a
Linux Dream 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```

```
$ apt-cache policy skype
skype:
  Installed: 2.1.0.47-1
  Candidate: 2.1.0.47-1
  Version table:
 *** 2.1.0.47-1 0
        100 /var/lib/dpkg/status
     2.0.0.72-0medibuntu4 0
        500 http://packages.medibuntu.org jaunty/non-free Packages

```

```
$ apt-cache show skype
...
Depends: lib32stdc++6 (>= 4.1.1-21), lib32asound2 (>> 1.0.14), ia32-libs (>= 1.6), libc6-i386 (>= 2.7-1), lib32gcc1 (>= 1:4.1.1-21+ia32.libs.1.19)

```

```
$ file /usr/bin/skype
/usr/bin/skype: ELF **32-bit** LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped
```

---

### Post by toupeiro on 2009-09-01
I'm baffled.  Wine, skype, reports of high unstableness.  I've been running 64-bit for a few years...  *really people?!?*  You really still have this many issues on 64-bit @ 9.04???  Because I use all these things and have had to do no major, or minor modifications to my system which I can recall to make them work.  in fact, the ONLY thing I still have any major issues with is the Citrix client...

:confused:

---

### Post by Tibuda on 2009-09-01
> **FuturePilot said:**
> It's not a native 64bit binary.

I stand corrected. At least they have added ia32-libs as a dependency.

---

### Post by 3rdalbum on 2009-09-01
I've got no problems on 64-bit. If you try and install a 32-bit Debian package it won't install, and you need to use Getlibs to install 32-bit libraries for some 32-bit programs, but most of what you use on Linux is available for 64-bit, or works on 64-bit with just the standard ia32-libs package.

I'm not sure about performance, but there should theoretically be a slight increase in performance, and a reasonable increase in mathematics-intensive code (video encoding).

---

### Post by tuxxy on 2009-09-01
Most native 64-bit applications are going to outperform their 32-bit equivalent.  You will see greatest increases in performance in video, photo manipulation and number crunching.

---

### Post by doorknob60 on 2009-09-01
Always use 64 bit if your CPU can support it. No reason not to. Flash and Java work (natively), and Wine and Skype work with 32 bit libs installed (which get pulled in automatically in Ubuntu anyways). Everything else I use has 64 bit native versions, aside form a few old Linux games (Unreal Tournament GOTY, etc.), which also work fine with the right 32 bit libraries installed.

---

### Post by hanzomon4 on 2009-09-02
> **FuturePilot said:**
> It's not a native 64bit binary.

```
$ uname -a
Linux Dream 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```

```
$ apt-cache policy skype
skype:
  Installed: 2.1.0.47-1
  Candidate: 2.1.0.47-1
  Version table:
 *** 2.1.0.47-1 0
        100 /var/lib/dpkg/status
     2.0.0.72-0medibuntu4 0
        500 http://packages.medibuntu.org jaunty/non-free Packages

```

```
$ apt-cache show skype
...
Depends: lib32stdc++6 (>= 4.1.1-21), lib32asound2 (>> 1.0.14), ia32-libs (>= 1.6), libc6-i386 (>= 2.7-1), lib32gcc1 (>= 1:4.1.1-21+ia32.libs.1.19)

```

```
$ file /usr/bin/skype
/usr/bin/skype: ELF **32-bit** LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped
```

Stand Corrected

---

### Post by Cenotaph on 2009-09-02
I don't even need any 32bit libraries nowadays. I definitely think ubuntu 64bit is worth it.

---

