---
title: "speed up RAM"
date: 2011-12-31
forum: The Cafe
---

### Post by Matrix01 on 2011-12-31
how do u speed up RAM?

---

### Post by lolpenguin on 2011-12-31
What????? That does not make _any_ sense! You don't "speed up" RAM.
You can increase the clock in the BIOS (i.e. overclocking) to make it run faster, but it will a) void your warranty b) be more likely to overheat c) be unstable.
If you meant "make computer less laggy" or something similar, then I suggest checking your startup applications, run less programs at once, keep background processes to a minimum or (last resort) buy more.

---

### Post by chipbuster on 2011-12-31
Well what are you trying to do? Do you want to make a RAM overclock? Do you want to try to make a superfast RAMDISK to load the OS into? Do you want to try to get a high benchmark score?

Or do you just want to make your computer perform a little better? If it's this, then speeding up your RAM is not a good place to start.

[http://www.perlmonks.org/?node_id=542341](http://www.perlmonks.org/?node_id=542341)

I'm guilty of this a lot of the time, but it helps if we try to state our initial problem instead asking for a way to do something else that (may or may not) be related.

---

### Post by 2F4U on 2011-12-31
You are posting a lot of snippet questions in the forum that just don't make any sense. Are you trying to increase you post count? If not, I would suggest that you sit down and try to rewrite your questions with more information about what the problem is and what you intend to achieve.

---

### Post by Paqman on 2011-12-31
There are several ways to improve RAM performance:
[LIST=1]
[*]Replace it with faster RAM
[*]Overclock it
[*]Make sure that the RAM sticks are installed in matched pairs or triples, depending on what type of memory controller you have.
[*]Make a blood sacrifice to the RAM gods
[/LIST]

Apart from that, you're stuck with what you've got. Generally speaking RAM is almost never the bottleneck in system performance, so I wouldn't worry about it.

---

### Post by Ms. Daisy on 2011-12-31
> **2F4U said:**
> You are posting a lot of snippet questions in the forum that just don't make any sense. Are you trying to increase you post count? If not, I would suggest that you sit down and try to rewrite your questions with more information about what the problem is and what you intend to achieve.
+1 !!!!
And I'm starting to wonder if you're even reading the responses. 
Or maybe we're all giving advice to a bot :confused:

---

### Post by d3v1150m471c on 2011-12-31
> **Ms. Daisy said:**
> +1 !!!!
And I'm starting to wonder if you're even reading the responses. 
Or maybe we're all giving advice to a bot :confused:

A bot with 500+ posts? While i'm here i should probably add something clever. Uhhhhhh, vm.swappiness, buy more RAM, disable useless services, and theory of relativity.

---

### Post by oldos2er on 2011-12-31
Moved to Community Cafe.

---

### Post by vpharry on 2011-12-31
May be he means running the entire system in ram... Theres a tutorial for that

---

### Post by LowSky on 2011-12-31
> **Matrix01 said:**
> how do u speed up RAM?

BIOS.  increase the FSB to RAM.

---

### Post by del_diablo on 2011-12-31
How to speedup RAM:
Replace HDD with a SSD. Now... instead of that crappy half a megabyte second at random read, your RAM gets feed properly.

---

### Post by forrestcupp on 2011-12-31
This reminds me of those RAM compressor programs that people used to install because it supposedly made it seem like you had more RAM than you really did.

---

### Post by lisati on 2011-12-31
> **forrestcupp said:**
> This reminds me of those RAM compressor programs that people used to install because it supposedly made it seem like you had more RAM than you really did.

I'm reminded of disk utilities to achieve a similar goal.

---

### Post by 3Miro on 2012-01-01
I remember the disk compression utilities, back in the 90's I used one that worked pretty well. It made things slower, but it did give more space.

However, I would be skeptical about doing something like this in RAM. Has anyone tried it? I may seem like you have more RAM, but ultimately I would expect this to slow things way too much.

---

### Post by Paqman on 2012-01-01
> **3Miro said:**
> 
However, I would be skeptical about doing something like this in RAM. Has anyone tried it? I may seem like you have more RAM, but ultimately I would expect this to slow things way too much.

I get the impression that the point was to avoid swapping to disk. A few years back it might have made sense, but these days we've all got enough RAM that it'd be pointless.

---

### Post by del_diablo on 2012-01-01
I think there is some kernel patch that enables you to run a really fast compression algorythm on everything that goes to RAM, which apparently works.
That, or I have heard of people saying that its possible to implent it.

---

### Post by forrestcupp on 2012-01-01
> **3Miro said:**
> I remember the disk compression utilities, back in the 90's I used one that worked pretty well. It made things slower, but it did give more space.

However, I would be skeptical about doing something like this in RAM. Has anyone tried it? I may seem like you have more RAM, but ultimately I would expect this to slow things way too much.

Both types of compression were a disaster, but especially the RAM compressors. It was back when people didn't have much RAM, and it was very expensive. It slowed things down to a halt and did more harm than good. That's why that technology didn't last very long.

Hard drive compressors were horrible, too. I used to use one back in the early Windows 95 days. It made my computer so slow that I think I ended up reinstalling my system because I couldn't get it to uninstall and reset everything properly.

Disk and RAM compressors were horrible ideas that seemed like good ideas.

---

### Post by del_diablo on 2012-01-01
RAM compression is a good idea actually, providing you have a fast enough CPU and a weak enough algorythm(Doesn't use time to overcompress).
I am fairly certain that some form of lmza compression combined with a modern CPU could handle a realtime compressed RAM. Now... the gain would be minimal because the bottleneck is elsewhere in the system, but it could be more feasable on the bottlenecks.

---

### Post by Plumtreed on 2012-01-01
Webupd8 talks about ZRam which is a type of virtual ram that does work...but since the OP has gone I didn't bother with doing a link.

..for more info jus google webupd8 zram:D

---

