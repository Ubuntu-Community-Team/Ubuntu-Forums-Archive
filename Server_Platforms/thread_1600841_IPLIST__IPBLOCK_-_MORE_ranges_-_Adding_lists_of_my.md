---
title: "IPLIST / IPBLOCK - MORE ranges - Adding lists of my own"
date: 2010-10-19
forum: Server Platforms
---

### Post by mistypotato on 2010-10-19
Hi,

I have added quite a few custom lists that I have created and use with ipblock.
Usually I create a TXT file and use the ADD FILE function from the GUI interface.

They all seem to work fine....but the situation is that as I add lists, the loaded ranges seem to DECREASE :confused:

I'm thinking this is a bug in the4 program.

**For example....**

I had 273642 ranges loaded and then created and loaded a NEW blocklist.
After the file finishes loading, Ipblock now reports I have 256285 ranges loaded :confused:

I'm still trying to verify that ALL lists are being used but it seems they are.
   **[COLOR="Red"]Anyone have any idea why ipblock would show fewer ranges loaded as I add MORE ranges?[/COLOR]**

---

### Post by mistypotato on 2010-11-03
This has not been resolved.

Weeks later, the displayed number of IP ranges has gotten even smaller as the number of actual ranges I have added has gone up quite a bit.

Noone else?

---

### Post by s1nch4n on 2010-11-04
I think u should be more specify what do u mean...

are u trying to block some IP or ports?

---

### Post by uljanow on 2010-11-04
The latest version of IPblock shows the number of IPs. Previous versions showed the number of IP ranges, but IPblock *merges* overlapping ranges which can reduce the number of ranges.

---

### Post by mistypotato on 2010-11-04
> **uljanow said:**
> The latest version of IPblock shows the number of IPs. Previous versions showed the number of IP ranges, but IPblock *merges* overlapping ranges which can reduce the number of ranges.

:KS:KS:KS:KS:KS

Very useful
THX!

---

### Post by VcDeveloper on 2010-11-18
How do you create your own list, what is the format?  I looked into the level2.gz and wanted to make sure this is how I can make my own and, would only one IP range worked properly?  Like so:

some name:123.12.123.12-123.12.123.12

I wanted to add one IP at a time, because I just found out one or more of this files are blocking my friends from connecting.  So will I be doing this correctly?

---

### Post by VcDeveloper on 2010-11-19
Cancel that! Did a test and my file is working!

---

### Post by mistypotato on 2010-11-19
> **VcDeveloper said:**
> How do you create your own list, what is the format?  I looked into the level2.gz and wanted to make sure this is how I can make my own and, would only one IP range worked properly?  Like so:

some name:123.12.123.12-123.12.123.12

I wanted to add one IP at a time, because I just found out one or more of this files are blocking my friends from connecting.  So will I be doing this correctly?

I know you answered your own question but.....

SomeNameplusanyotherinfo:123.xxx.xxx.xxx-123.xxx.xxx.xxx

is correct!

I just create a Plain Text file and it loads it just fine.

Also, for anyone new to ipblock, you can put an incredible number of ranges in there like **all** of ANY COUNTRIES plus tons more and ipblock can handle it (depending on your computer of course).

---

### Post by VcDeveloper on 2010-11-20
Thanks [mistypotato]("http://ubuntuforums.org/member.php?u=213821")!...

---

### Post by mistypotato on 2010-11-21
> **VcDeveloper said:**
> Thanks [mistypotato]("http://ubuntuforums.org/member.php?u=213821")!...

ok,

I just remember when I first started using ipblock and I wasn't sure about using plain TEXT (textfile.txt) files but they load and work fine.  At first I thought it HAD to be a gzip file.

I also (as a noobie to ipblocks) wasn't sure how many IP's or Ranges of IP's it could handle.   After experimenting with it, I found it

So, I wasn't specifically trying to "educate" you, it was just for others who may be newer to ipblock.

---

