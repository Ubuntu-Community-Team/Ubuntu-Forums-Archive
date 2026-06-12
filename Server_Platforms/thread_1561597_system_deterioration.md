---
title: "system deterioration"
date: 2010-08-26
forum: Server Platforms
---

### Post by ianmorris1960 on 2010-08-26
Hi,

My system is slowing down, I can tie this back to late July, nothing much has changed in terms of useage, similar volumes of web traffic (HAVP), similar amounts of email (postfix, dovecot and fetch mail) no changes to FTP use (ftppro).

So I explored Munin stats and noticed that the swap in/out has increase, and that iowait seems to have gone up, and the periods when the system is almost at a standstill coincide with these hi figures on the daily stats.

The only change made around that time was upgrading software (automatically!). the system now has Ubuntu Linux 8.04.1. 

The system is a little low on memory - webmin tells me there is 204 of 250MB available.

suggestions please

Thanks Ian

---

### Post by CharlesA on 2010-08-26
Are you actually running 8.04.1 or 8.04.4? 8.04.4 is the latest release of 8.04 (Hardy)

If I/O wait is high, then the hard drive cannot keep up with the system. Is it full?

---

### Post by arubislander on 2010-08-26
Low memory will cause more swaps... 10.04 uses much less memory as compared to 8.04... Would it be possible to try that?

---

### Post by CharlesA on 2010-08-26
[s]If the machine has 256MB of RAM, I don't know if Lucid will even run on it. Think the minimum is 512MB.[/s]

Scratch that, per the release notes, the minimum is 256MB of RAM for Lucid.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

### Post by Thelinuxgeek on 2010-08-26
Could you post your specs, please? And by memory, were you refering to HDD space or RAM? If you only have 250 MB of RAM, you definately need more. RAM is really cheap now, anyway. Old or inadequate hardware can really hinder system performance.

---

### Post by TwoEars on 2010-08-26
If you're using a GUI - stop doing that, you'll need more RAM if you want to use a GUI as well as server software.
Check out your system logs. I've seen cases like this where log files are going crazy, causing swap and RAM to be used. Also, could you post the output of ```
ps aux
```? I also suggest a reboot, perhaps after upgrading, 8.04.1 is old.

---

### Post by CharlesA on 2010-08-26
Old RAM isn't cheap, since it's not made any more.

---

### Post by arrrghhh on 2010-08-26
> **TwoEars said:**
> I also suggest a reboot, perhaps after upgrading, 8.04.1 is old.

But, still very much supported on the server platform - and for older hardware, I would recommend 8.04.

8.04 will be supported (on the server platform) until April 2013

[Releases](https://wiki.ubuntu.com/Releases)

---

### Post by TwoEars on 2010-08-26
> **arrrghhh said:**
> But, still very much supported on the server platform - and for older hardware, I would recommend 8.04.

8.04 will be supported (on the server platform) until April 2013

[Releases](https://wiki.ubuntu.com/Releases)

8.04.1 ;)

8.04.4 is the current version of 8.04

---

### Post by arrrghhh on 2010-08-26
> **TwoEars said:**
> 8.04.1 ;)

8.04.4 is the current version of 8.04

Details!  :P  

But, I think 8.04, 8.04.1, 8.04.2, 8.04.3 and 8.04.4 are ALL supported until April 2013.  (Again, only on the server platform.  Desktop support expires on April 2011)

---

### Post by TwoEars on 2010-08-26
> **arrrghhh said:**
> Details!  :P  

But, I think 8.04, 8.04.1, 8.04.2, 8.04.3 and 8.04.4 are ALL supported until April 2013.  (Again, only on the server platform.  Desktop support expires on April 2011)

Yeah, I'm not entirely clear on this matter neither. I keep my Ubuntu running server up to date with the latest maintenance packs. 8.04.x, where x>1, all contain bug fixes(which might solve his problem).

To OP: I think if you're finding 256MB too small in terms of RAM, you've either used a poor configuration(choice of packages, etc), you have a software/hardware problem(which in terms of software, the updating will solve), or you're under attack(DoS etc). I suggest that you might consider changing distribution, if you can't afford the extra RAM/solve the problem.

---

### Post by ianmorris1960 on 2010-08-27
I have version 8.04.1, so I will upgrade this, and see what happens, 

yes the server is getting a little old, and I did get more memory for it, but I think I was unlucky and the chip caused more problems than it solved - it got recycled as jewellery!

will report back.

Ian

---

### Post by CharlesA on 2010-08-27
Hopefully upgrading to 8.04 or 10.04 will help the problems. :)

---

### Post by ianmorris1960 on 2010-09-10
Time to report back,

My server came to a halt a couple of times last week, do drastic action required!

I upgraded the server to 10.04, this left some issues - dovecot would not work, turned out to be the certificate!

I have left the FTP service off, so simply running Mail (fetchmail, dovecot & postfix) and dropped HAVP and replaced with squid. Also running Munin to keep an eye on things.

So all good. Thanks for you guidance.

Now, when I read the munin graphs, everything seems a lot calmer, however the memory useage graph has a solid slab of red (swap) and very little green (free memory).

If I understand correctly from earlier posts this means ADD MORE MEMORY! and I think the amount of memory to add is such that there is headroom above the swap value.. the swap value is peaking at about 150Mb so need to add at least 256Mb

please could someone who knows more than me confirm this please.

Sorry if it is obvious!

thanks Ian

---

### Post by arrrghhh on 2010-09-10
I would add _at least_ 256mb... You can never have too much memory, trust me ;)

---

