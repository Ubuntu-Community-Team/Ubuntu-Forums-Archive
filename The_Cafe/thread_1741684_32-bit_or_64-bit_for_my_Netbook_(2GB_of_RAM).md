---
title: "32-bit or 64-bit for my Netbook (2GB of RAM)?"
date: 2011-04-28
forum: The Cafe
---

### Post by BrokenKingpin on 2011-04-28
I an going to do a fresh install of the new Xubuntu on my netbook, and I am wondering what will be better for my netbook, the 32-bit or the 64-bit version?

My netbook has the Intel Atom N450, 2GB of RAM, and a 60GB SSD. I know the netbook can run the 64-bit version, I am just wondering if it is worth it not having 4+ GB of RAM.

---

### Post by 3Miro on 2011-04-28
2GB is the minimum in my opinion for you to not notice the extra RAM usage and gain some speedup from the CPU. On the other hand, I am not sure how Atoms work, it may be that you get no speedup at all.

I personally would have kept 32-bit on this machine.

---

### Post by fuduntu on 2011-04-28
> **BrokenKingpin said:**
> I an going to do a fresh install of the new Xubuntu on my netbook, and I am wondering what will be better for my netbook, the 32-bit or the 64-bit version?

My netbook has the Intel Atom N450, 2GB of RAM, and a 60GB SSD. I know the netbook can run the 64-bit version, I am just wondering if it is worth it not having 4+ GB of RAM.

32bit.  The binaries are a little thinner, and use less memory.  In addition, with the Atom you probably wouldn't see much of a performance gain (though I could be wrong there).  If your netbook had 4GB of memory or more, you'd want to consider 64bit.

---

### Post by Paqman on 2011-04-28
If your machine is capable of running 64-bit then use it. 2GB of RAM is plenty for Ubuntu, the marginally larger memory footprint of 64-bit won't be noticed at all.

Why throttle your chip down to 32-bit? Running it 64-bit will save battery by not maxing your CPU out for so long on computationally intensive stuff (which on a netbook without a decent graphics chipset is a lot)

---

### Post by _outlawed_ on 2011-04-28
> **Paqman said:**
> If your machine is capable of running 64-bit then use it.


This 100%.

---

### Post by Blasphemist on 2011-04-28
> **Paqman said:**
> If your machine is capable of running 64-bit then use it. 2GB of RAM is plenty for Ubuntu, the marginally larger memory footprint of 64-bit won't be noticed at all.

Why throttle your chip down to 32-bit? Running it 64-bit will save battery by not maxing your CPU out for so long on computationally intensive stuff (which on a netbook without a decent graphics chipset is a lot)

I fully agree with this.

---

### Post by NMFTM on 2011-04-28
> **Paqman said:**
> Why throttle your chip down to 32-bit? Running it 64-bit will save battery by not maxing your CPU out for so long on computationally intensive stuff (which on a netbook without a decent graphics chipset is a lot)
Oh wow, didn't know (some) Atoms even had integrated GPUs integrated into the chip die. But how would the CPU being 32 or 64 bit effect the GPU? Doesn't that just mean it's on the die it's self but is otherwise it's own self contained unit?

---

### Post by Paqman on 2011-04-28
> **NMFTM said:**
> Oh wow, didn't know (some) Atoms even had integrated GPUs integrated into the chip die. But how would the CPU being 32 or 64 bit effect the GPU? Doesn't that just mean it's on the die it's self but is otherwise it's own self contained unit?

I just mean that without a decent GPU, your CPU is going to be doing a lot of work rendering video. A 64-bit chip will do this a *lot* better than a 32-bit one, so won't have to work so hard.

---

### Post by fuduntu on 2011-04-28
> **Paqman said:**
> I just mean that without a decent GPU, your CPU is going to be doing a lot of work rendering video. A 64-bit chip will do this a *lot* better than a 32-bit one, so won't have to work so hard.

Only if the code has been specifically optimized for 64 bit (data types, pointers, etc).

Unlikely.  You also didn't take into account the impact that these larger memory allocations would have on things like cache.

There is generally no visible improvement on battery life between 64 bit and 32 bit Linux.

---

### Post by NMFTM on 2011-04-28
> **Paqman said:**
> I just mean that without a decent GPU, your CPU is going to be doing a lot of work rendering video. A 64-bit chip will do this a *lot* better than a 32-bit one, so won't have to work so hard.
I misread your original post. I saw "with" where you actually said "without". Now it all makes sense.

---

### Post by 3Miro on 2011-04-28
> **Paqman said:**
> I just mean that without a decent GPU, your CPU is going to be doing a lot of work rendering video. A 64-bit chip will do this a *lot* better than a 32-bit one, so won't have to work so hard.

I am not so sure about this. All video cards that I know of are 32-bit. If there is any compatibility issues, that is with 64-bit not 32-bit. My guess would be that 64-bit would use more power then 32-bit.

A test would be interesting to see. BrokenKingpin, if you have enough time to play with it, can you test the battery life and maybe do some basic benchmarks on 32 vs 64 bit Atoms. I am really curious of this, but I don't own an Atom CPU.

---

### Post by PhillyPhil on 2011-04-29
@OP: definitely go 64 bit.  Don't hobble 64 bit hardware with a 32 bit OS. 

> **fuduntu said:**
> Only if the code has been specifically optimized for 64 bit (data types, pointers, etc). The OS code has, and the percentage of other software that has is growing every day. 

> Unlikely.  You also didn't take into account the impact that these larger memory allocations would have on things like cache. You didn't take into account the larger size and number of registers that means with 64 bit software you have less access of the cache in the first place.

Believe it or not, the larger cache entries issue was not forgotten or ignored by 64 bit architects.  64 bit is still faster.  
> There is generally no visible improvement on battery life between 64 bit and 32 bit Linux.> **3Miro said:**
> My guess would be that 64-bit would use more power then 32-bit.
A cpu is likely to draw slightly less power as 32 bit because less of its circuitry is used, but on the other hand 64 bit software (eg the OS) will be running more efficiently. 
I doubt there would be a noticeable difference in battery life between 32 bit and 64 bit, unless you spend the entire life doing something like video encoding or sequencing DNA (64 bit may give you a boost there).

---

### Post by Shining Arcanine on 2011-04-29
Go with 64-bit. Half of your CPU's general purpose registers will be wasted if you use 32-bit.

---

### Post by fuduntu on 2011-04-29
> **PhillyPhil said:**
> @OP: definitely go 64 bit.  Don't hobble 64 bit hardware with a 32 bit OS.

 The OS code has, and the percentage of other software that has is growing every day. 

 You didn't take into account the larger size and number of registers that means with 64 bit software you have less access of the cache in the first place.

Sure I did.  My implication would be that cache would fill faster.

> **PhillyPhil said:**
> Believe it or not, the larger cache entries issue was not forgotten or ignored by 64 bit architects.  64 bit is still faster.  

64bit can be faster, but it isn't always.  Applications compiled on a 64bit platform that aren't optimized for the 64bit platform, etc will perform the same.

> **PhillyPhil said:**
> 
A cpu is likely to draw slightly less power as 32 bit because less of its circuitry is used, but on the other hand 64 bit software (eg the OS) will be running more efficiently. 
I doubt there would be a noticeable difference in battery life between 32 bit and 64 bit, unless you spend the entire life doing something like video encoding or sequencing DNA (64 bit may give you a boost there).

In my testing, it works out to be the same.  There is no benefit or drawback to 64bit over 32bit in regard to battery life with an Atom processor.  In some applications there can be a slight performance gain (video encoding / decoding) with this CPU but it is negligible.

I don't think anyone will be using an Atom 450 to encode video or sequence DNA.

---

### Post by Dragonbite on 2011-04-29
> **Paqman said:**
> If your machine is capable of running 64-bit then use it. 2GB of RAM is plenty for Ubuntu, the marginally larger memory footprint of 64-bit won't be noticed at all.

Why throttle your chip down to 32-bit? Running it 64-bit will save battery by not maxing your CPU out for so long on computationally intensive stuff (which on a netbook without a decent graphics chipset is a lot)

This is good to know!  Thanks!

---

### Post by PhillyPhil on 2011-04-29
> **fuduntu said:**
> Sure I did.  My implication would be that cache would fill faster. That negative is absorbed and exceeded by the positives (eg less cache requests).  > 64bit can be faster, but it isn't always.  Applications compiled on a 64bit platform that aren't optimized for the 64bit platform, etc will perform the same. Of course.  I feel ok about calling something that's faster in some circumstances, and the same speed otherwise, simply 'faster', but apologies if I was unclear. 

> In my testing, it works out to be the same.  There is no benefit or drawback to 64bit over 32bit in regard to battery life with an Atom processor.  In some applications there can be a slight performance gain (video encoding / decoding) with this CPU but it is negligible.

I don't think anyone will be using an Atom 450 to encode video or sequence DNA. It wasn't a serious suggestion...

---

### Post by fuduntu on 2011-04-29
> **PhillyPhil said:**
> That negative is absorbed and exceeded by the positives (eg less cache requests).   Of course.  I feel ok about calling something that's faster in some circumstances, and the same speed otherwise, simply 'faster', but apologies if I was unclear. 

 It wasn't a serious suggestion...

Why not?  Since your comment, I have clustered all of my Atom based systems and begun sequencing my genome using a fork of 64bit Unity.


:lolflag:

---

### Post by oldos2er on 2011-04-29
64-bit works great with 2GB RAM.

---

### Post by stmiller on 2011-04-29
This has some random benchmarks fwiw:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae)

For some things 64bit is faster.

---

### Post by deshotel on 2012-05-18
> **BrokenKingpin said:**
> I an going to do a fresh install of the new Xubuntu on my netbook, and I am wondering what will be better for my netbook, the 32-bit or the 64-bit version?

My netbook has the Intel Atom N450, 2GB of RAM, and a 60GB SSD. I know the netbook can run the 64-bit version, I am just wondering if it is worth it not having 4+ GB of RAM.

I have the same netbook with only 1 GB ram and I really like 64 bits, using ubuntu studio currently...works!

---

### Post by oldos2er on 2012-05-18
Old thread closed.

---

