---
title: "Ubuntu memory usage from feisty to hardy"
date: 2008-02-12
forum: The Cafe
---

### Post by swistakers on 2008-02-12
A few days ago I upgraded my Ubuntu to Hardy alpha. I instantly noticed that gnome is loading much longer and it eats up more memory. 
I decided to compare memory usage of different Ubuntu versions. I downloaded Feisty, Gutsy and Hardy alpha 4. The test was pretty simple. Every version was installed inside VirtualBox OSE and given 512 MB of RAM. After booting and logging in to gnome I opened a terminal and ran: free -m. Here are the results:

Feisty:

```

             total       used       free     shared    buffers     cached
Mem:           503        299        204          0          7        202
-/+ buffers/cache:         89        414
Swap:          196          0        196
```

Gutsy:
```
             total       used       free     shared    buffers     cached
Mem:           503        331        172          0          7        210
-/+ buffers/cache:        113        390
Swap:          196          0        196
```

Hardy alpha 4

```
             total       used       free     shared    buffers     cached
Mem:           503        405         98          0          9        209
-/+ buffers/cache:        185        317
Swap:          196          0        196
```

Conclusion?
Sadly I must admit that Ubuntu may become as slow and resources hungry as Vista. It doubled its memory footprint in one year! I know that there is plenty of new features, but the cost of having them is to high, at least for users of not-so-modern computers. 
My suggestion would be to allow users to choose between a simple desktop using as little as 90MB of memory (like in Feisty) and full-blown environment with tracker and compiz.

Greetings!
swistakers

---

### Post by Scarath on 2008-02-12
> **swistakers said:**
> 
My suggestion would be to allow users to choose between a simple desktop using as little as 90MB of memory (like in Feisty) and full-blown environment with tracker and compiz.


You can already do that, no one is forcing you to use compiz or even gnome, if your paranoid about memory use one of the *Box environments.

I do agree that 7.04 used less memory that 7.10 (for me anyway) but you can just mess with the settings and get the memory use back down.
Like everyone on these forums usually says, "thats the great thing about linux", its all your choice.

---

### Post by billgoldberg on 2008-02-12
Since hardy is still in alpha, things could change.

Like the previous poster said, nobody is forcing you to use gnome/tracker/compiz.

---

### Post by swazidoughman on 2008-02-12
RAM is insanely cheap nowadays
so i suggest that you buy more

&

If you want low ram usage then i would use DOS or any text
based version of linux

---

### Post by SunnyRabbiera on 2008-02-12
I am hoping this will only be in the alphas as really ubuntu doesnt need to become a memory hog.

---

### Post by GeneralZod on 2008-02-12
> **SunnyRabbiera said:**
> I am hoping this will only be in the alphas as really ubuntu doesnt need to become a memory hog.

Alpha software is usually much less efficient than release software.  "Make it Work - Make it Work Well - Make it Work Fast", as the saying goes :)

---

### Post by gn2 on 2008-02-12
RAM usage came up on another forum I use, so I looked at it on my Xubuntu 7.04 laptop and found it's 70mb at idle.

---

### Post by rune0077 on 2008-02-12
Well, it's virtually impossible to buy a computer today that doesn't ship with 2 gigs of RAM. Naturally, a new, modern OS that tries to appeal to modern users needs to exploit all this memory, otherwise it will quickly look stale and boring to new users.

---

### Post by koleoptero on 2008-02-12
I found that gutsy without the tracker and compiz used exactly the same amount of ram as feisty. But of course an evolving OS will gradually have more requirements. It's only natural.

---

### Post by swistakers on 2008-02-12
> **Scarath said:**
> You can already do that, no one is forcing you to use compiz or even gnome, if your paranoid about memory use one of the *Box environments.

I don't use tracker and compiz and I know how to customize my desktop. I am aware of other environments. I've got 1GB of memory.

My point is to give a choice to an inexperienced user. That could be an appropriate dialog window shown before first login. 
Please don't tell me that you can use Xubuntu, Bashubuntu etc. Ubuntu should consume less than 180-190MB of memory by default. I hope hardy final will consume less.

---

### Post by forrestcupp on 2008-02-12
> **rune0077 said:**
> Well, it's virtually impossible to buy a computer today that doesn't ship with 2 gigs of RAM. Naturally, a new, modern OS that tries to appeal to modern users needs to exploit all this memory, otherwise it will quickly look stale and boring to new users.

> **koleoptero said:**
> I found that gutsy without the tracker and compiz used exactly the same amount of ram as feisty. But of course an evolving OS will gradually have more requirements. It's only natural.

+1

20 years ago, I was using a C64 with 64K of RAM, and 32K of that was shared with the Kernel and OS, which you didn't really want to overwrite. 10 years ago I had 64 MB of RAM.  That's 1000 times more in 10 years.  Now I have 1.5 GB of RAM, which is becoming low-end in modern computers.  That's 23.4 times more than 10 years ago.

It's a natural part of the process of the evolution of computers that more processing power and memory would be required with time.  I remember wondering why anyone would need more than 2.5 GB of hard drive space.  Now, I wouldn't mind having a 1 TB drive.

If you can't or don't want to have more requirements, don't upgrade.  Either that, or use a DE that doesn't have a lot of requirements.  Personally, I want to exploit the hardware that I've spent a lot of money on.

---

### Post by KillerSponge on 2008-02-12
Interesting to see that it is ok for Ubuntu to use a lot of resources, but not for Vista ;)

I don't really mind if it uses 'a lot' of memory. I have 1.5GB of ram, and it's almost impossible to fill that up under normal use (watch a movie, listen to music, browse the web, all that simultaniously), so if they make improvements that consume a little more RAM, I don't mind. Under one condition: everything still has to run smooth, no hickups.

My three year old system (although I have to admit, I upgraded the RAM from 512 to 1.5) still runs everything perfectly fine without a sweat, so I don't see the big deal :)

---

### Post by rune0077 on 2008-02-12
> **KillerSponge said:**
> Interesting to see that it is ok for Ubuntu to use a lot of resources, but not for Vista ;)


I never minded Vista using a lot of memory. I had a system that could pull it, and every time I ran it I was thinking "so this is why I bought all that RAM" - I can understand why people with less resources are frustrated at Vista, but it ran great and really fast for me (faster than Ubuntu for sure), and it felt great.

---

### Post by swistakers on 2008-02-12
> **forrestcupp said:**
> It's a natural part of the process of the evolution of computers that more processing power and memory would be required with time.  I remember wondering why anyone would need more than 2.5 GB of hard drive space.  Now, I wouldn't mind having a 1 TB drive.

If you can't or don't want to have more requirements, don't upgrade.  Either that, or use a DE that doesn't have a lot of requirements.  Personally, I want to exploit the hardware that I've spent a lot of money on.

I agree with all those statements. 

It's a pity that nobody understands what I mean.
As somebody mentioned disabling features added in Gutsy lowers memory usage to Feisty level. I want Hardy to ask an user if he wants eye candy, tracker etc. If so, he gets these features and 100MB more of used memory. If not, he gets a faster system supported for 3 years.

Sticking to Feisty or resorting to *Box environments is clearly a bad solution.

---

### Post by rune0077 on 2008-02-12
> **swistakers said:**
> I agree with all those statements. 

It's a pity that nobody understands what I mean.
As somebody mentioned disabling features added in Gutsy lowers memory usage to Feisty level. I want Hardy to ask an user if he wants eye candy, tracker etc. If so, he gets these features and 100MB more of used memory. If not, he gets a faster system supported for 3 years.

Sticking to Feisty or resorting to *Box environments is clearly a bad solution.

I get what you're saying. Like, when you run Vista for the first time, it tests your system to see if you're able to run the Aero theme. If your specs is good enough, it loads Aero Glass, and if the test fails, it loads Aero basic and no fancy 3d shifter. And I agree, that would be ideal for Ubuntu, since it would appeal to both low end and high end users. But it would also demand a little more work from the developers. It would be a great feature, though.

---

### Post by macogw on 2008-02-12
Nobody has yet figured out why [Bug #128803](https://bugs.launchpad.net/bugs/128803) exists.  GNOME takes around a full minute to login on Gutsy.  Ugh.  I'm using Fluxbox to avoid it, even though it means I can't use Compiz.

---

### Post by forrestcupp on 2008-02-12
> **rune0077 said:**
> I get what you're saying. Like, when you run Vista for the first time, it tests your system to see if you're able to run the Aero theme. If your specs is good enough, it loads Aero Glass, and if the test fails, it loads Aero basic and no fancy 3d shifter. And I agree, that would be ideal for Ubuntu, since it would appeal to both low end and high end users. But it would also demand a little more work from the developers. It would be a great feature, though.

To an extent, it's already like that.  If you don't have hardware that will run Compiz, Ubuntu will detect that and not turn it on by default.  Even in Vista, you don't have a choice during installation.  With both Vista and Ubuntu, it's not that hard to go to the settings and turn it off if you don't want it.  System->Preferences->Appearance in the Visual Effects tab.  I have an ATI card that doesn't support Compiz without tweaking, and Compiz wasn't turned on when I installed Gutsy.

If every choice possible were given to people during installation, it would take days to install Ubuntu.  Different things are important to different people.  And whether you like it or not, Ubuntu isn't meant to be minimalistic.  That's what Xubuntu is for.

---

### Post by Black Mage on 2008-02-12
Keep in mind that hardware for computers is getting cheaper as computers become more powerful. Today, 2 gigs of RAM isn't that much and as OS become 64-bit, 4 gig may become standard or above.

Not to mention larger hard drives which are faster and enable better swapping are now available.

300 megs is not that much memory if you look at it that way.

---

### Post by swistakers on 2008-02-12
> **rune0077 said:**
> I get what you're saying. Like, when you run Vista for the first time, it tests your system to see if you're able to run the Aero theme. If your specs is good enough, it loads Aero Glass, and if the test fails, it loads Aero basic and no fancy 3d shifter. And I agree, that would be ideal for Ubuntu, since it would appeal to both low end and high end users. But it would also demand a little more work from the developers. It would be a great feature, though.

Automated detection is hard and complicated. I believe a simple dialog can be done before hardy release.

---

### Post by gn2 on 2008-02-12
> **forrestcupp said:**
> Ubuntu isn't meant to be minimalistic.  That's what Xubuntu is for.

And Xubuntu works beautifully.

---

