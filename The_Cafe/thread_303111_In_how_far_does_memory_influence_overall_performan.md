---
title: "In how far does memory influence overall performance?"
date: 2006-11-19
forum: The Cafe
---

### Post by chaosgeisterchen on 2006-11-19
Good night,

I once read that Linux needs a fast FSB and fast memory to run fast overall. Sticking to that I desperately wanted to get DDR2-800 RAM for my newly built system. But they are expensive as hell.

So, here's the question. If I, for instance, buy DDR2-667 instead of DDR2-800, will that hurt my performance a lot. Or even better: As a mere desktop user, will I feel the performance loss significantly?

Thanks for answers in advance, I am quite confused after having read at silentpcreview.com that I would merely suffer a 5% perfmance loss when decreasing from DDR2-800 to DDR2-533.

cg

---

### Post by deanlinkous on 2006-11-19
basic desktop user?
I cannot imagine "feeling" any difference int he two. How fast do you want a system to be or what do you want to be fast? I haven't noticed my systems dragging *** or anythign and they are cheapo barebone kits from tigerdirect!

---

### Post by cantormath on 2006-11-19
Memory is almost EVERYTHING....  I would rather have a slower processor and double the ram, then half the ram and double the processor.  Another important, and sometimes more important then the above, is the cache, you want a full pipeline for a processor, ie L2 cache share, then half the cache with a faster processor.  lots of ram and lots of cache is my vote.

---

### Post by chaosgeisterchen on 2006-11-19
> **cantormath said:**
> Memory is almost EVERYTHING....  I would rather have a slower processor and double the ram, then half the ram and double the processor.  Another important, and sometimes more important then the above, is the cache, you want a full pipeline for a processor, ie L2 cache share, then half the cache with a faster processor.  lots of ram and lots of cache is my vote.

I know that. But the question was not about the amount of RAM but about the influence of the speed of the RAM.


@deanlinkous:

I am a basic desktop user. Beryl should run smooth in future times and I want to develop software sometimes as well as check the mail, surf the internet. Things like that, apart from Beryl pure 2D.

---

### Post by loell on 2006-11-19
speaking of ram, iv'e never heard of ubuntu loaded entirely in ram , like knoppix,dsl or mcnlive 

 i wanna know how fast it can go, provided the system has huge amount of ram

 since the os is already floating, i'd imagine it would fly ;)

---

### Post by deanlinkous on 2006-11-19
I think a lot of the "speed" numbers are just over-hyped especially memory speed. As I said, I cannot imagine "feeling" the difference unless you had 2gigs of memory and was compiling your kernel while SETI was running and you were debuggin a million lines of code or something. :)

but as I said, I am a cheapo tiger direct barebone kit kind of guy... :D

---

### Post by cantormath on 2006-11-19
> **chaosgeisterchen said:**
> I know that. But the question was not about the amount of RAM but about the influence of the speed of the RAM.


@deanlinkous:

I am a basic desktop user. Beryl should run smooth in future times and I want to develop software sometimes as well as check the mail, surf the internet. Things like that, apart from Beryl pure 2D.

faster ram that runs cooler will work better then slower ram that get hot.  If ram is more important, then I would go with the better ram.:KS

---

### Post by cantormath on 2006-11-19
> **loell said:**
> speaking of ram, iv'e never heard of ubuntu loaded entirely in ram , like knoppix,dsl or mcnlive 

 i wanna know how fast it can go, provided the system has huge amount of ram

 since the os is already floating, i'd imagine it would fly ;)

You know, I have also had good experiences with ReiserFS (vs ext3) file systems.  The fastest machine in my house is ReiserFS, and it really flys with only a gig of ram.

---

### Post by slimdog360 on 2006-11-19
you can always over clock the RAM. I wouldnt bother with the DDR800 unless your going for a complete mean machine to run vista and all the very latest games. I couldnt imaging you noticing the difference otherwise.

---

### Post by loell on 2006-11-19
> **cantormath said:**
> You know, I have also had good experiences with ReiserFS (vs ext3) file systems.  The fastest machine in my house is ReiserFS, and it really flys with only a gig of ram.
nice,
is it ubuntu/reiserfs or other distro/rierfs?
what is the desktop environment?

---

### Post by chaosgeisterchen on 2006-11-19
I used ReiserFS under SuSE 10.0 a year ago and it was very fast and reliable as far as I can remember. 

Concerning RAM: It really seems as if I would not harm myself buying DDR2-533 instead of DDR2-800. It's about 40% the money.

---

### Post by kuja on 2006-11-19
I don't know. Especially in the case of recent AMD processors you can see some really good performance out of slower, low latency RAM. Also, I would rather have a ton of somewhat slower RAM, than have a small amount of really fast RAM, generally. Save a few bucks this route too.

---

### Post by chaosgeisterchen on 2006-11-19
I just checked the prices...

2048 MB DDR2-667 RAM at about 200 Euro.
2048 MB DDR2-800 RAM at about 290 Euro.

Would it really be worth the extra price?

---

### Post by jdong on 2006-11-19
Fast FSB? Say what?

One of my favorite Linux boxes was a 1GHz-ish system with 2.5GB of RAM. Its day-to-day performance seriously contends with my Core Duo laptop especially in the IO department. That is, to everything but CPU-intensive work and gaming :)


In the end, I'd much much rather spend my money towards more RAM than faster RAM, for day-to-day computer usage. Adding more RAM to a Linux system is never wasteful -- the added caching abilities will enhance your disk performance very noticeably.

---

### Post by chaosgeisterchen on 2006-11-19
Oh, thanks. I saw 512 MB RAM performing very lousy - as the swap was almost permanently active.

---

### Post by kuja on 2006-11-19
> **chaosgeisterchen said:**
> I just checked the prices...

2048 MB DDR2-667 RAM at about 200 Euro.
2048 MB DDR2-800 RAM at about 290 Euro.

Would it really be worth the extra price?
I'd say the biggest advantage of the faster RAM is that it allows for more overclocking headroom (at the expense of latency though). Unless you're interested in overclocking you're probably better saving your money and spending it on something you'll notice/appreciate more.

---

### Post by Velotix on 2006-11-19
OK. Let's put it like this - my PC has 2GB of RAM. **I have never seen my 6GB swap partition get used. Not *once*.**

Today's a bad day and yet only 50% of my RAM has actually been used since I booted - and the extra RAM usage comes from the fact that fsck ran automatically on boot today.

I have no performance issues except with graphics, but that's because the driver is poor, which is hardly Ubuntu's fault. ;)

**EDIT:** As to RAM speed, I'm not sure of the benefits specifically. What I will tell you is to be VERY careful - not all motherboards support the higher-speed RAM modules - for example, 1000MHz modules exist but have limited support at present. Check your motherboard can actually cope with the big guns before forking out the extra cash. BTW, I *think* I have 800MHz memory modules, but I can't confirm this. They are definitely DDR2 standard, though.

---

### Post by chaosgeisterchen on 2006-11-19
I am convinced now that 2048 MB DDR2-667 RAM will do the job just fine. Thanks for all replys here and I hope that it helped other users to get information too.

---

### Post by jdong on 2006-11-19
Good luck man and enjoy your RAM... I strongly believe that there is just no such thing as too much RAM these days... If there's one component you should really invest in, it's RAM :)

---

### Post by hardyn on 2006-11-19
this might be considered a boring statement, but i really cringe at the idea of people avocating the purchasing of a slower component and recommending overclocking.  yes it can be done, but most people don't have good luck with it... which usually results in a huge loss in stability for a small improvement in performance.  spend the money and get the right speed stuff, although i hear the tests between 533-667 are negligable. i imagine it would be the same from 667 - 800.

---

### Post by jdong on 2006-11-19
Agreed, hardyn.... I wouldn't condone buying slower-speed components and trying to push them up to higher speeds.... they're slower-speed in the first place for a reason, and it's not a conspiracy plot :)

But I do condone buying more slower-speed RAM over less high-speed RAM :)

---

### Post by chaosgeisterchen on 2006-11-19
I won't overclock it, just to clarify that. It's too much of a risk for me. It's not the same as if I would, for instance, overclock a Core2Duo E6300, which is an overclocking beast (can go for double the speed it is sold).

---

### Post by Velotix on 2006-11-19
(Off-topic, but: )

> I won't overclock it, just to clarify that. It's too much of a risk for me. It's not the same as if I would, for instance, overclock a Core2Duo E6300, which is an overclocking beast (can go for double the speed it is sold).

However, it only has half the L2 cache. 'Tis why I bought the E6600 even though the E6400 and E6600 are similarly priced. (I imagine the E6600 models have even more powerful overclocking abilities. ^^)

---

### Post by jdong on 2006-11-19
> **Velotix said:**
> (Off-topic, but: )



However, it only has half the L2 cache. 'Tis why I bought the E6600 even though the E6400 and E6600 are similarly priced. (I imagine the E6600 models have even more powerful overclocking abilities. ^^)

Yes, though the E6400/E6600 is quite a price bump from the 6300... I'm glad I'm not getting a new PC right now, as that'd be a very very tough decision that'd leave me awake for many nights :)

---

### Post by chaosgeisterchen on 2006-11-19
Yay... please do stop trying to convince me to buy an E6600.. they are so good but too expensive for me.

---

### Post by jdong on 2006-11-19
Speaking of Xeon Woodcrests ;-)

---

