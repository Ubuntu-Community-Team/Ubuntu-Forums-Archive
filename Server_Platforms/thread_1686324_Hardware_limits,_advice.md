---
title: "Hardware limits, advice"
date: 2011-02-12
forum: Server Platforms
---

### Post by cosine_omerta on 2011-02-12
I've been reading around and was wondering if there is any reason to not go big on a server I am building.  I was thinking of running ubuntu server 10.10 on this hardware:

AMD Athlon or Phenom II quad core processor
Motherboard with hardware RAID built in
8gb+ RAM ddr3
at least 4 HDDs for RAID

This server is going to be a multi-purpose server, web, file, game (nothing big), mail etc. Any reason that 10.10 couldn't use all of this or is this overkill? Also is software RAID better on 10.10, or should I stick with the hardware?

I have a couple of servers running 10.10, but no hardware this ambitious.  Any advice would be appreciated.

---

### Post by elico on 2011-02-12
very nice hardware and ubuntu will do the most of it (AMD64 version)

---

### Post by CharlesA on 2011-02-12
Keep in mind that "hardware RAID" on the mobo more then likely just [fakeraid]("http://serverfault.com/questions/9244/how-do-i-differentiate-fake-raid-from-real-raid").

---

### Post by cariboo on 2011-02-12
The hardware will work well running the server version, the thng to keep in mind when building a server, is what is it going to do. Are you going to server web pages? Files? Stream audio/video?

My server runs an Intel E5400 cpu and 2Gb ram with 8 hard drives ranging from 120Gb to 1Tb, totalling 4Tb . It runs a couple of internal web sites, one in a vm, plus it servers media files to the other 9 systems on my internal network. Here are the current stats from mtod:

```
System information as of Sat Feb 12 13:47:19 PST 2011

  System load:    0.33               Processes:           169
  Usage of /home: 36.3% of 90.70GB   Users logged in:     0
  Memory usage:   16%                IP address for eth0: 192.168.1.250
  Swap usage:     0%
```

The only thing running currently besides vboxheadless is an rsync backup.

I would suggest staying away from fakeraid as far as possible, I had nothing but problems with file corruption with it on an other server. I would suggest that instead of setting up a raid array, invest the money in large enough drives to backup your complete system, and keep the backup current. It's geeky to have a raid array, but if your data is important back it up.

---

### Post by cosine_omerta on 2011-02-13
Ok, so the RAID support that the mobo boasts is generally fake raid? meaning that it uses system resources such as the cpu to manage the raid?  Even though it's "fake" some sources say that it would work fine, so I'm a little confused.  If its a corruption issue then I certainly wouldn't want to go that route.

So which would be a better idea then, to use software raid, or get a RAID card? With the RAID cards is there something specific I should be looking for, specifically do I need to worry about there being ubuntu server drivers or support?

And yes, I'm just trying to be geeky.  The server won't be doing anything massive, I basically just want to play with RAID.

Thanks for the advice!

---

### Post by CharlesA on 2011-02-13
I guess it really depends. I've only used a RAID card (albiet a low end one) but I haven't noticed a performance hit. I just prefer the management utilities that come with the card I am using.

If you wanted to use software RAID, go with mdadm, instead of using the onboard RAID controller.

---

