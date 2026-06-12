---
title: "32-bit or 64-bit?"
date: 2010-04-28
forum: Ubuntu Studio
---

### Post by seagullplayer77 on 2010-04-28
I'm planning on doing a fresh install of 10.04 in a few weeks, but I'm not sure if I want to use the i386 version or the AMD64 version. I'm currently using Ubuntu Studio Hardy (64-bit) on my HP desktop replacement and Ubuntu 9.04 (32-bit) on my ThinkPad. I've found that the ThinkPad is much more stable and a lot less "quirky" then my desktop replacement, and I can't help but wonder if that's due to the fact that I've got a 64-bit OS on my HP.

Here's the thing: I've only got 3GB of RAM and I'm not planning on upgrading to 4GB, so 64-bit capabilities won't do me any good in that respect. It seems like a lot of apps run better on my ThinkPad (which is a 64-bit machine, btw) than they do on my HP, and if there's no tangible benefits for using the 10.04 AMD64, I'll just stick with the i386 version.

Any thoughts :confused:?

---

### Post by carl4926 on 2010-04-28
It sounds like you already figured it out.

Many will argue you use _64, but it doesn't sound a real advantage in your care. I use 32 and 64 side by side and see no difference in the way you describe.

---

### Post by seagullplayer77 on 2010-04-29
> **carl4926 said:**
> It sounds like you already figured it out.

Many will argue you use _64, but it doesn't sound a real advantage in your care. I use 32 and 64 side by side and see no difference in the way you describe.

Yeah. I guess I was just wondering if (other than the ability to use more than 3GB of RAM) there were any benefits of using the AMD64 version. If there are, I might put some more thought into the issue. 

If not, i386 it is :).

---

### Post by carl4926 on 2010-04-29
If you use the PAE kernel in 32 bit it will address more than 3GB RAM

---

### Post by zipperback on 2010-04-29
If you have an AMD 64 bit processor why not use the 64bit version of the operating system?

Unless there is an application which is only available for 32 bit systems that wont run under 64bit Linux why not use the operating system which was intended for your processor?

- zipperback
:popcorn:

---

### Post by trulan on 2010-04-29
Why use 64 bit?   I don't know.

Why stick with 32 bit?  I don't know.

Nobody else seems to know either.  I usually end up keeping at least one 64 bit install around, just so the extra 32 bits on my processor don't feel left out.  Maybe I don't get out much, but I've honestly never ran into anything at all where I could tell that it made even a slight difference which one I was using.

Except for one thing:  The Ubuntu Live CD that you carry with you everywhere you go should really be 32 bit.  It's really annoying to offer to demonstrate Ubuntu for somebody and then realize your CD won't boot on their system.

Does that help?

---

### Post by seagullplayer77 on 2010-04-29
> **trulan said:**
> Why use 64 bit?   I don't know.

Why stick with 32 bit?  I don't know.

Nobody else seems to know either.  I usually end up keeping at least one 64 bit install around, just so the extra 32 bits on my processor don't feel left out.  Maybe I don't get out much, but I've honestly never ran into anything at all where I could tell that it made even a slight difference which one I was using.

Except for one thing:  The Ubuntu Live CD that you carry with you everywhere you go should really be 32 bit.  It's really annoying to offer to demonstrate Ubuntu for somebody and then realize your CD won't boot on their system.

Does that help?

Not really :p.

But it's the thought that counts, right?

It doesn't seem like there's a good argument for either option. Use the AMD64 version because you can. That's kind of weak. Use the i386 version because you want to. That's kind of weak too.

I've noticed that with driver issues and plugin problems, the solution is always easier with a 32-bit Ubuntu install. It's always like, "If you're using 32-bit, type this command and you're done. And if you're using 64-bit . . .  boy. Here's a link to a twenty page tutorial that works about half the time. Good luck!"

To me, it seems like things "just work" better with a 32-bit install. If I feel so inclined, I've got a 64Studio install disk and a 64-bit Ubuntu Studio 8.04 install disk I can use to do a 64-bit install. If 32 bits aren't getting used, I guess that's just too bad. I've never really been able to figure out why 64-bit OSs are so beneficial anyway. Maybe I'm dumb or something, but it seems like the only reasons they get used are a) because you can use more RAM and b) because you can. If I'm being ignorant, feel free to enlighten me.

---

### Post by fedexnman on 2010-04-29
another thing to ask  ? are you gonna use  wine 32bit vst/vsti ? can you use these on a 64 bit system with ardourvst ? ive been using 64-bit, but im wondering bout using ardourvst and wether i should use 32bit or 64 bit ubuntu(studio) ?

---

### Post by sgx on 2010-04-29
> **fedexnman said:**
> another thing to ask  ? are you gonna use  wine 32bit vst/vsti ? can you use these on a 64 bit system with ardourvst ? ive been using 64-bit, but im wondering bout using ardourvst and wether i should use 32bit or 64 bit ubuntu(studio) ?
Hi, most windows vsts will work fine with 32bit wine/Reaper/winesaio (ones without dongles, pace or ilok style copy-protection) and some will work
with lmms, fst, dssi-vst, I have never heard of them working in ardour, it would be nice, but the last post I saw in a non-linux
forum from the ardour author, some months ago, he indicated his efforts are far more focused on excellent audio, much less on midi and vst support, so for now at least, no windows style ardour DAW is planned.
Cheers

---

### Post by seeker5528 on 2010-04-29
> **seagullplayer77 said:**
> Here's the thing: I've only got 3GB of RAM and I'm not planning on upgrading to 4GB, so 64-bit capabilities won't do me any good in that respect. It seems like a lot of apps run better on my ThinkPad (which is a 64-bit machine, btw) than they do on my HP, and if there's no tangible benefits for using the 10.04 AMD64, I'll just stick with the i386 version.

If you have a 64 bit machine, you shouldn't be asking if there is a benefit for using the AMD 64 version of Ubuntu. You should be asking what reason there is to stick with 32 bit.

Flash seems to have it's issues no matter whether the OS and Flash are both 64 bit, 32 bit, or you use the 32 bit Flash on 64 bit Ubuntu. Other than a little less performance and maybe a little more memory usage when using 32 bit Flash on 64 bit Ubuntu due to the wrapper that allows you to mix the 32 bit flash with 64 bit firefox, I have not seen evidence that any combination of these has more problems than any other. 

If you do stuff with Java, on-line stuff in particular, that could be a reason to stick with 32 bit. Doesn't seem to be an issue for most people.

Generally speaking I would say if you are doing a new install, go with the 64 bit, unless you have some specific reason not to.

As 64 bit becomes more dominant, the software will start to become more tuned to that, there is not much reason to stick with 32 bit, and if you want to preserve the option to upgrade later on, there is no easy way to upgrade from 32 bit to 64 bit.

Later, Seeker

---

### Post by Stochastic on 2010-04-30
One MAJOR reason to choose 64bit is that in 10.04 (and probably all future releases) the Preempt kernel that comes packed with the ubuntustudio-audio meta to enable reliable low latency audio use only comes in a 64bit version.  There are PPA kernels with 32bit versions of other low latency kernels, but the security paranoid among us may not want to go that route.

---

