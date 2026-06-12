---
title: "Does compiling your own kernel actually make the OS faster?"
date: 2010-01-09
forum: The Cafe
---

### Post by sandyd on 2010-01-09
Does compiling my own kernel actually make the OS faster?
i just did that (using linux-source) and everything instantly became snappy.

---

### Post by NoaHall on 2010-01-09
Slightly.

---

### Post by madverb on 2010-01-09
Yes, it can make it faster because you can set it up just for the hardware in your computer, rather than a generic one that is set up for all sorts of hardware.

---

### Post by nothingspecial on 2010-01-09
I tried it once.

Maybe a little bit.

I`ve come to the conclusion that none of that matters.

Arch, gentoo, ----- all that work and not much improvement on ubuntu - a couple of seconds, maybe.

My personal preference is ubuntu-minimal + X + openbox + firefox

I have yet to try slack, but don`t think I`ll bother.

I think Ubuntu minimal, built up, is as minimal as I need.

---

### Post by squilookle on 2010-01-09
Unless you specifically want to learn more about the kernel, is it worth it?

It's a step I haven't ever felt the need to take.

---

### Post by 00ber n00b on 2010-01-09
Never tried it.  How well does it work on laptops?  I know a lot of drivers for laptops are generic, so, is it *easy* for laptops?

---

### Post by schauerlich on 2010-01-09
> **carlee said:**
> i just did that (using linux-source) and everything instantly became snappy.

[http://en.wikipedia.org/wiki/Placebo](http://en.wikipedia.org/wiki/Placebo)

---

### Post by 00ber n00b on 2010-01-09
> **schauerlich said:**
> [http://en.wikipedia.org/wiki/Placebo](http://en.wikipedia.org/wiki/Placebo)

LOL.  A stop watch can put an end to that...

---

### Post by sandyd on 2010-01-09
> **00ber n00b said:**
> Never tried it.  How well does it work on laptops?  I know a lot of drivers for laptops are generic, so, is it *easy* for laptops?
this was done on a laptop.
i actually compiled it a few times cause i accidentally forgot to compile a few modules and built-in stuff for my computer, but it works on a laptop.

the link is in my sig (only for karmic though), and it should be working as i just tested it

---

### Post by nothingspecial on 2010-01-09
I did it on a netbook.

Honestly, don`t bother.

As far as I understand, this may have been advantageous a few years ago, but doesn`t really matter now.

Taking all that into account, it`s fun, so go ahead.

I`m a bit wishy/washy:)

---

### Post by chris200x9 on 2010-01-09
maybe a little, truth be told I think arch ran faster than gentoo on my desktop, at least it seemed like it...

---

### Post by RabbitWho on 2010-01-09
I'd like to learn about the kernel.. but I don't want to change it.. and I want Ubuntu... there should be a Ubuntu learner install where it stops and tells you each thing as it's setting it up, explains to you what that means, and asks you if you think it's a good idea and necessary for your computer or not.. if you've no idea you just click okay..  but you don't have to change anything from the normal Ubuntu, because I really like it... That would be awesome.

---

### Post by Zoot7 on 2010-01-09
The only notable difference I ever got with a kernel I compiled myself was a faster boot time.

---

### Post by gnomeuser on 2010-01-09
That is like asking if building your own house automatically always ensures a superior end result.

If you know how to build a house, understand your specific needs and desires then yes, you will probably build a better house than the person who is hired to slap together prefabricated houses. 

However those prefab houses are also well designed by taking a large number of house owners and seeing how to best address the common requests and doing so cheaply.

If you know exactly which drivers to compile in and which settings fit your system and the way you use it best then yes your kernel will end up being lighter and more highly tailored to your needs. Performance is one indicator of this, the size of the image, the boot time might decrease.

On the other hand if you just flip switches without being informed about the consequences then you are likely going to end  up with non-booting kernel, and as such would be better off with the stock kernel.

Though, all this being said, the stock kernel is very good, I doubt most people would draw any benefits in performance from hand compiling.

---

### Post by nothingspecial on 2010-01-09
> **gnomeuser said:**
> That is like asking if building your own house automatically always ensures a superior end result.

If you know how to build a house, understand your specific needs and desires then yes, you will probably build a better house than the person who is hired to slap together prefabricated houses. 

However those prefab houses are also well designed by taking a large number of house owners and seeing how to best address the common requests and doing so cheaply.

If you know exactly which drivers to compile in and which settings fit your system and the way you use it best then yes your kernel will end up being lighter and more highly tailored to your needs. Performance is one indicator of this, the size of the image, the boot time might decrease.

On the other hand if you just flip switches without being informed about the consequences then you are likely going to end  up with non-booting kernel, and as such would be better off with the stock kernel.

Though, all this being said, the stock kernel is very good, I doubt most people would draw any benefits in performance from hand compiling.

Bloody good answer

---

### Post by dragos240 on 2010-01-09
Yeah. Less time to load, it's configured for your hardware. A generic kernel has support for everything.

---

### Post by Linuxforall on 2010-01-09
During early days of SuSE 8 this used to be standard for me, now having tried self compiled optimized kernel versus the one that comes with Ubuntu, I don't see any perceptible difference. Furthermore, I would rather have the peace of mind of important kernel security patches from team Ubuntu than run my own vanila self compiled vulnerable kernel.

I did enjoy Con Covilas patches in those days of kernel compiling days, they used to make a load of difference.

---

### Post by Regenweald on 2010-01-09
> **carlee said:**
> Does compiling my own kernel actually make the OS faster?
i just did that (using linux-source) and everything instantly became snappy.

Thanks for the link, I'll do it but as far as I know, the only major change is a drop in boot time, unless you change the Hz.

---

### Post by &#32 Greg on 2010-01-09
> **RabbitWho said:**
> I'd like to learn about the kernel.. but I don't want to change it.. and I want Ubuntu... there should be a Ubuntu learner install where it stops and tells you each thing as it's setting it up, explains to you what that means, and asks you if you think it's a good idea and necessary for your computer or not.. if you've no idea you just click okay..  but you don't have to change anything from the normal Ubuntu, because I really like it... That would be awesome.

The normal menuconfig has a great help function for all the features, to at least advise you.

---

### Post by magmon on 2010-01-09
> **gnomeuser said:**
> That is like asking if building your own house automatically always ensures a superior end result.


I was going to use the same analogy.

---

### Post by judge jankum on 2010-01-09
> **magmon said:**
> I was going to use the same analogy.
If you'e a builder and knew the technical specs it would probably be better...But if not standard is usually better..

---

### Post by magmon on 2010-01-09
> **judge jankum said:**
> If you'e a builder and knew the technical specs it would probably be better...But if not standard is usually better..

Precisely.

---

### Post by steveneddy on 2010-01-10
I have custom compiled kernels on the machines at home.

I've tried it on my lappie but don't have the time to mess with it really. I make my living on the road with this laptop.

I do notice that the machine runs better with a custom kernel.

---

### Post by Exodist on 2010-01-10
> Does compiling your own kernel actually make the OS faster?Yes, but only yes if you remove un needed drivers and stuff from the kernel that you will not need. Like ham radio support and old chipsets and stuff that you will not need on your system. This can free up memory and help the OS boot faster.

---

### Post by Khakilang on 2010-01-10
Never try but  day I will.

---

### Post by ~sHyLoCk~ on 2010-01-10
I always compile own kernel. It definitely makes system faster since I remove all the unnecessary stuffs. Also bfs+tunxonice rox! ;-)

---

### Post by Frak on 2010-01-10
Depends on how you look at it. If you mean "does it save X seconds on boot time and makes everything boot 40% faster!", no. If you mean "I can scientifically measure the minute time differences between the default and the customly compiled", then maybe.

There is no definitive "yes", but you cannot technically say "no" either. It doesn't make it noticeably faster (in most cases), but it doesn't not make it faster either (you could shave milliseconds off some processes).

---

### Post by The Toxic Mite on 2010-01-10
> **schauerlich said:**
> [http://en.wikipedia.org/wiki/Placebo](http://en.wikipedia.org/wiki/Placebo)
 
This++
 
/thread

---

### Post by CharlesA on 2010-01-10
Tbh, it wouldn't be worth the time/effort (for me) to compile from source just to shave a few seconds off boot up time.

But yeah, it supposedly makes it faster to start up since you don't have to load all the generic drivers and junk.

---

### Post by handy on 2010-01-10
If the question had of been does compiling your own kernel actually make it smaller?

Then I would have voted yes. :)

---

### Post by sdowney717 on 2010-01-10
I will get a significantly bigger speed boost by spending money on new hardware. With a stock kernel, I can change any and all components and it will boot.

---

### Post by xir_ on 2010-01-10
if you use and ati card an compile the 33 rc3 kernel then there is a good chance that it will. (with the os driver)
If you include bfs then you might notice faster responses.
if you just recompile the stock with mcore=(your arch), then no, not more than 2%

The best thing about compiling your own kernel is that you can include newer patches, these will have more of an effect than adjusting the core options. But my view is that if you recompile anyway you might as well set the kernel to your arch and set the frequency to a desktop friendly setting.

---

### Post by oedipuss on 2010-01-10
Why not just test it?

Boot time is measurable, so is ram usage, and there's a decent benchmarking suite now, phoronix test suite, which can show exactly what the benefits are, if any.

---

### Post by Xbehave on 2010-01-10
I have a slightly faster boot time, (less that ½s), the main benefit i have is being about to get features before they get into mainline ubuntu, e.g kms or BF scheduler. The price I pay is that I spent quite a while configuring the kernel for my hardware. I don't think it was worth it for the performance/features, but I'm glad i did it for the learning experience.

---

