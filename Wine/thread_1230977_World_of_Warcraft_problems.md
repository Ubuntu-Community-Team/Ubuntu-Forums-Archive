---
title: "World of Warcraft problems?"
date: 2009-08-04
forum: Wine
---

### Post by [&#1048;.E.W.T] on 2009-08-04
Posted this in general along with my hardware problems, got directed here? or Wine? I'm not sure where to post this so PLEASE bare with me.
> 
 The original reason I got ubuntu was becuase I thot that it would take up the least amount of room on my HD, since, well, I have an incredibly small HD (35gb) and need to run WoW. 
 
 On XP it ran great but I wanted to have some more room on my HD just incase. With ubuntu I have gone through WINE, CrossOver,and Cedega to get WoW to play best and yet all them have flaws including, Super low frames per second, Mouse is laggy in the games window, and I also have a problem with it messing up when i use the W key to move forward and it takes it like im pushing it over and over again really fast so my in game character is moving all weird(Yes, I went to System>Preferences>Keyboard> and uncheck repeat keys which got it working but, I cant hold down backspace to get remove stuff anymore and have to click it over and over and over until every letter is gone which is BS imo...)Sound is cracking and horrible. and the game seems to be blurry.

---

### Post by hikaricore on 2009-08-04
You probably should provide more info, such as what kind of video card do you have?  nvidia or ati?
How much ram you have, processor, etc.  Be sure 3d desktop effects are disabled and such before running anything with WINE.

---

### Post by [&#1048;.E.W.T] on 2009-08-04
> **hikaricore said:**
> You probably should provide more info, such as what kind of video card do you have?  nvidia or ati?
How much ram you have, processor, etc.  Be sure 3d desktop effects are disabled and such before running anything with WINE.

Alright,
My card is a Nividia 9500 GT
2gb ram,
not sure of my processor,
What I can tell you, is that when I had xp on the computer I was able to run WoW on top setting with 30 fps.
Now when I'm playing,  the game runs OK, not the best but, playable, except in, "raids" where you get in a group with 25 ppl, when I'm doing this its ok until we start actaully attacking something ingame and people start using stuff, the colors start flying and the game drops to 1-2 fps :(

---

### Post by dardack on 2009-08-04
run nvidia-settings make sure your using the restricted drivers.  Also if that runs go to the OpenGL and slide the bar to performance over quality.

---

### Post by khelben1979 on 2009-08-04
> **'[&#1048 said:**
> ;7730635']not sure of my processor

You really should check this. Also, if you can create a screen dump of your graphic settings in WoW, this would help understanding how it looks like.

Was playing in RAID slow when doing it with Windows XP as well?

---

### Post by [&#1048;.E.W.T] on 2009-08-04
> **khelben1979 said:**
> You really should check this. Also, if you can create a screen dump of your graphic settings in WoW, this would help understanding how it looks like.

Was playing in RAID slow when doing it with Windows XP as well?

Any commands on finding the processor?
cant log onto WoW right now, servers are getting the new patch :D (Good news :))
BUT
All the setting are on the lowest when using WINE:(

Raids were competely  fine on xp, maby a bit of lagg from all the ppl over the world computers shooting spells, colours and stuff but now its literally 1-2 fps..

---

### Post by decoherence on 2009-08-04
You do know that running WoW in wine will always be slower than doing it in native XP? Just making sure you aren't expecting similar performance between the two. It could be that you can squeeze some more performance out of it, but if you just want a basic "Wow-station" your best bet is do to a stripped down Windows XP install.

---

### Post by khelben1979 on 2009-08-04
> **decoherence said:**
> if you just want a basic "Wow-station" your best bet is do to a stripped down Windows XP install.

Or getting better hardware.

```
cat /proc/cpuinfo
```
displays information about your cpu.

---

### Post by decoherence on 2009-08-04
> **khelben1979 said:**
> Or getting better hardware.

That's always a solution, of course! 

You buying? ;)

---

### Post by khelben1979 on 2009-08-04
> **decoherence said:**
> That's always a solution, of course! 

You buying? ;)

Not a chance! :D

---

### Post by [&#1048;.E.W.T] on 2009-08-04
> **khelben1979 said:**
> Or getting better hardware.

```
cat /proc/cpuinfo
```displays information about your cpu.

But isnt this just more... I dont know seems stupid that you need to buy more stuff to get it to work where as it works fine on windows?

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) 4 CPU 2.93GHz
stepping    : 1
cpu MHz        : 2925.790
cache size    : 1024 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid xtpr
bogomips    : 5851.58
clflush size    : 64

```

---

### Post by khelben1979 on 2009-08-04
From looking at that output I see that your cpu is holding back the power which that graphic card can give.

At the present, getting better hardware is probably the only thing which can give you better performance in Linux. And if you won't, it's back to Windows, at least for WoW.

As time moves on the performance will probably get better because of better graphic drivers and because of Wine updates, but for now it don't look good.

---

### Post by [&#1048;.E.W.T] on 2009-08-04
> **khelben1979 said:**
> From looking at that output I see that your cpu is holding back the power which that graphic card can give.

At the present, getting better hardware is probably the only thing which can give you better performance in Linux. And if you won't, it's back to Windows, at least for WoW.

As time moves on the performance will probably get better because of better graphic drivers and because of Wine updates, but for now it don't look good.

Alright, well ,we will see how it goes soon. Can you give me some help on CPU? if I'm upgrading, what should I be looking for? Something that's going to run the game again and is affordable?

*EDIT*

Will this work?
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16819103681](http://www.newegg.ca/Product/Product.aspx?Item=N82E16819103681)

---

### Post by khelben1979 on 2009-08-05
> **'[&#1048 said:**
> ;7733568']Alright, well ,we will see how it goes soon. Can you give me some help on CPU? if I'm upgrading, what should I be looking for? Something that's going to run the game again and is affordable?

*EDIT*

Will this work?
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16819103681](http://www.newegg.ca/Product/Product.aspx?Item=N82E16819103681)

I think it's a bad choice. Go for a motherboard which can handle dual cores from Intel and has a pretty high clock rate on it. From a price point I believe this is the best choice.

If it were myself, I would rather go for a motherboard which is compatible with processors from AMD and uses AM3. I don't think it's the best choice for you if the computer is mainly going to be used for World of Warcraft.

From what I've heard you will not need more RAM than 2GB for World of Warcraft, but 4GB is nice.

Are your present video card attached through pci express?

Motherboard reviews at Legion Hardware is a nice place to start reading if you're into analyzing motherboards. [Look here]("http://www.legionhardware.com/list.php?category=02").

---

