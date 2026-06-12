---
title: "Ubuntu 16.04 use too much RAM"
date: 2016-08-10
forum: Ubuntu, Linux and OS Chat
---

### Post by dphoenixpl on 2016-08-10
Ubuntu 15.10 was using only about _600 MB of RAM._ Ubuntu 16.04 use _about 900 MB,_ **so 300 MB more than older version**. I have installed Ubuntu 16.04 on my (second) older PC, with only 1,8 GB of RAM. And it's not enough for actual Ubuntu system. A lot of people (as me) want to emigrate **from Windows XP to Ubuntu**, but old PCs wit XP often have **only 1 or 2 GB of RAM**, and **Ubuntu don't work properly,** and better way, is stay on Windows XP. Cannonical, can you better optimize your system? Or maybe there is some other way to reduce RAM usage?

---

### Post by SeijiSensei on 2016-08-10
Try a more "light-weight" version of Ubuntu like [Lubuntu]("http://lubuntu.net/") or [Xubuntu]("http://xubuntu.org/").

---

### Post by pfeiffep on 2016-08-10
> **dphoenixpl said:**
> Ubuntu 15.10 was using only about _600 MB of RAM._ Ubuntu 16.04 use _about 900 MB,_ **so 300 MB more than older version**. I have installed Ubuntu 16.04 on my (second) older PC, with only 1,8 GB of RAM. And it's not enough for actual Ubuntu system. A lot of people (as me) want to emigrate **from Windows XP to Ubuntu**, but old PCs wit XP often have **only 1 or 2 GB of RAM**, and **Ubuntu don't work properly,** and better way, is stay on Windows XP. Cannonical, can you better optimize your system? Or maybe there is some other way to reduce RAM usage?
SeijiSensei provided 2 options to which I'd add Ubuntu MATE

---

### Post by mikodo on 2016-08-10
People have noticed a jump of memory lately for even Lubuntu and Xubuntu as of 16.04. I noticed about 200mg more of RAM being used in Xubuntu 16.04 compared to when I booted into Xubuntu 14.04 that was still installed beside it. I have my suspicians that it is not something caused by Ubuntu. But, I concur, you can try a lighter [Official Ubuntu Flavor]("http://www.ubuntu.com/download/ubuntu-flavours") that will use less RAM than Unity Desktop.

Here is my RAM used in Xubuntu 16.04 with two instances of Firefox open. Firefox itself is using a lot more than it used to in the past too. A lot more, and I am showing it all lumped together here. Not just Xubuntu Desktop.

Addendum: Oh ya, I also use a commercial VPN that when running as I have now, uses about 40MB of Ram. 

```
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3942         620        2205          77        1116        2985
Swap:             0           0           0
```

---

### Post by grahammechanical on 2016-08-10
Windows XP users should have switched to Linux long before Microsoft stopped giving security fixes for XP. Or, they should have scrapped those machines and brought new, expensive Windows machines. As they were advised to do by the Microsoft adverts. 

Canonical does not get any financial gain from anyone installing any flavour of Ubuntu. Therefore, there is absolutely no commercial pressure on Canonical to spend money trying to get XP users to switch to Ubuntu. So, there is no point in trying to panic Ubuntu developers. It is especially pointless trying to panic the developers on a user forum that is not visited by Ubuntu developers.

The problem with XP machines is often the video adapter being incapable of doing hardware accelerated 3D rendering because the GPU does not have the capability to do the rendering and the amount of video memory is too small. I get a good user experience because I have a video adapter with 1GB of video memory. I think that is what makes the difference.

Over the last 4 years I have seen a big improvement in the way the Linux kernel handles memory. I am using Ubuntu on a machine with only 1GB of RAM and right now with  only Firefox open at Ubuntu forums only 600MB of RAM is being used. 

The situation changes completely when I visit the web site of a National newspaper that is filled with adverts which are often embedded video and added into the mix are scripts to report which adverts have been clicked back to some other web site. All this takes up band width and often causes Firefox to freeze. I doubt if more memory would make any difference. Cable broadband, may be.

Here is a more accurate comparison of memory usage between Ubuntu and the other flavours.

[https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared](https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared)

and the comparison run for 14.04.

[https://bryanquigley.com/uncategorized/ubuntu-14-04-livecd-memory-usage-compared](https://bryanquigley.com/uncategorized/ubuntu-14-04-livecd-memory-usage-compared)

It seems to me that there has been improvement all round between 14.04 & 16.04. I thank the Linux developers for that.

Regards

---

### Post by bjoern-ramberg on 2016-08-10
I absolutely second this as a behavior from firefox. I saw this bump in ram usage both on later windows and Linux versions at around q4 2015 / q1 2016.

Not sure this is exactly what op are seeing but both on a "normal" and on a very high end machine there has been a huge increase in ram usage by Firefox.

It becomes really interesting if you start a few tabs with some rotating content (like a news page or som adverts) and leave it for a while (like a day or so). It keeps increasing ram usage steadily on both tested systems.

I think the way that firefox is rendering tabs does seem to be part of this issue.

Cheers, 

B

---

### Post by KBD47 on 2016-08-10
Yes, Firefox has gotten heavy on Ubuntu. Suggest Chromium or Chrome. Also use extensions to block ads, tracking cookies.

---

### Post by mastablasta on 2016-08-11
> **bjoern-ramberg said:**
> I absolutely second this as a behavior from firefox. I saw this bump in ram usage both on later windows and Linux versions at around q4 2015 / q1 2016.



they have some "add-ons" on by default. yeah it's eating RAM. close to 400-500 MB.

ah version 2.x of Firefox worked fine on Windows 95 with 32Mb ram.... what happened with internet and browsers?!

---

### Post by mörgæs on 2016-08-11
Browsers are some of the most memory demanding applications. I suggest that people try the lightweight browser **links2** for browsing news sites and the like.

It displays text and some pictures. No scripts, no ads, no Flash. Fast, secure and uses little bandwidth (sounds like I am selling stuff, doesn't it?)

Admitted, it takes a while to get used to but it's worth the effort.

---

### Post by mikodo on 2016-08-11
> **mörgæs said:**
>  - Snippets - I suggest that people try the lightweight browser **links2** for browsing news sites and the like.

It displays text and some pictures. No scripts, no ads, no Flash. Fast, secure and uses little bandwidth .

It does support older versions of JavaScript ([up to version 2.1pre28]("https://en.wikipedia.org/wiki/Links_(web_browser)")).

Is that assumably older version of JavaScript not a [concern]("http://security.stackexchange.com/questions/110850/what-are-the-exact-security-risks-of-having-javascript-enabled") to worry about anymore?

---

### Post by mörgæs on 2016-08-11
Thanks for posting. I thought it didn't execute scripts at all. 
I am no expert in Javascript and security so I can't give a good answer.

---

