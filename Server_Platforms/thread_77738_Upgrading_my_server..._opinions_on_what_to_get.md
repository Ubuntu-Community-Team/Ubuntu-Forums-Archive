---
title: "Upgrading my server... opinions on what to get?"
date: 2005-10-17
forum: Server Platforms
---

### Post by mcewen98 on 2005-10-17
Since my upgrade from hoary to breezy didn't go exactly as I had hoped, I've taken it as an opportunity to dump some money into new hardware.  Right now I use an old Athlon 1ghz with 512mb's of ram for my home file server/web server, mythtv backend, etc.

I only want to spend a few hundred.. and it looks like I can achieve this by getting a 2.8ghz celeron, 1 gb of ram, new psu, and motherboard.  

My question is if I should  get the newer 2.53ghz 64bit celeron and run the 64bit version of ubuntu?  The price is essentially the same as the 32bit 2.8ghz chip.

Does anybody else have a set up like this?  If for some reason I had problems, like with a video card driver with the 64bit verison, could the 32bit verison of ubuntu run the same on it?

Does anybody know of any other incompatibilities with applications such as apache, mysql, mythtv?  If  64 bit is still too immature, I don't have a problem going with the 32bit celeron, since anything new will be a big improvement over what I already have.  And are there seperate repositories for 64 bit applications?

Thanks

---

### Post by LordHunter317 on 2005-10-17
I wouldn't be shocked if that Celery was a step-backwards, not forwards in terms of overall performance.

And no, going 64-bit isn't worth it unless you actually need 64-bit applications.

---

### Post by mcewen98 on 2005-10-17
After doing some research I agree with you about 64bit versus 32bit.  However, according to the cpu charts at tomshardware.com, the 2.8ghz Celeron D is significantly faster than the Athlon 1ghz.  I sense some animosity towards celerons....

In several of the tests I looked at the celeron is up there with most of the other P4's in that ghz range, and is about even most of the time with the Athlon XP 2800+ that I have in my primary pc.

Here's the comparison for a large winrar archive, the two processors are the red bars: [http://www23.tomshardware.com/index.html?modelx=33&model1=105&model2=42&chart=20](http://www23.tomshardware.com/index.html?modelx=33&model1=105&model2=42&chart=20)

The only difference between the 2.8ghz Celeron D and the 2.8 P4 (they both have the same prescott core) is that the celeron only has 256kb of cache and does not have hyperthreading.  The cerlon has a 533mhb fsb, the Athlon has 133mhz with 512kb cache (i think).

So I think this cpu paired with a better video card (an nvidia 128mb FX5200 because it's only $35....instead of a 32mb nvidia 440mx) will at least make gnome feel smoother for whatever desktop stuff I end up doing.

Or am I missing something about Ubuntu or Linux in general where the speed gains do not coincide proportionatly with as cpu speed increases?

---

### Post by Glut on 2005-10-17
The Celeron should be faster than the 1ghz athlon. The video card will not make much difference to your experience of the desktop. It's only 2D graphics and your choice of card will not affect that. 64bit is still substancially less mature than 32 bit, if only because of development time. You questions regarding compatibility would be best directed to the 64 bit forum.

In regards to your last comment, very few computing applications speed up proportionally to cpu speed. There are too many other factors involved.

---

### Post by bluck on 2005-10-17
[QUOTE=Glut]
In regards to your last comment, very few computing applications speed up proportionally to cpu speed. There are too many other factors involved.[/QUOTE]

agreed.  when looking at upgrading your CPU, the clock/bus speed ratio is an important factor.  the closer the bus speed is to your clock speed the better.

second to that would be cache size, as this is where the CPU actually does its business.

---

### Post by LordHunter317 on 2005-10-18
[QUOTE=mcewen98] However, according to the cpu charts at tomshardware.com, the 2.8ghz Celeron D is significantly faster than the Athlon 1ghz.  I sense some animosity towards celerons....[/quote]No, I missed the D part.  

Though you have to be careful when reading tests from Tom's, because more than 50% of them are bunk.

The real gains come from having much faster RAM and FSB, not from the processor itself, especially for what you're doing.

---

