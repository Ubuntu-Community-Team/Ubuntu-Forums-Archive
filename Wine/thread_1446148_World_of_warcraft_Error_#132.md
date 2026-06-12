---
title: "World of warcraft/ Error #132"
date: 2010-04-03
forum: Wine
---

### Post by Cloudkookoo on 2010-04-03
Hi all, I've been trying for a while now to get world of warcraft running on another PC I've got.

I've tried several linux distros on this PC and after many failed attempts to get it running, I'm coming here for help.

I get the same error every time I try to start the game. Error #132. I've read that this error can mean many things, yet I can't pinpoint exactly what is causing it in my case. There have been a couple times where I was able to log in, thinking it was fixed. But once I've entered my realm, most, if not all the action bar icons appear to be corrupt. 

I've even tried installing WoW on a somewhat new laptop, which is totally capable of running WoW, and get still get Error #132. This laptop is running Ubuntu 9.10

I am installing WoW by dragging the folder from an external hard drive I've got. And I don't think there is anything wrong with the files on the external, because this is the method I've used several times to install WoW on my main PC, which is also running Ubuntu.

SO, I'm really hoping that someone here can help me to fix this and get WoW running.

Thank you to anyone who can help, and I can post an error log if needed.

---

### Post by asdfoo on 2010-04-05
> **Cloudkookoo said:**
> Hi all, I've been trying for a while now to get world of warcraft running on another PC I've got.

I've tried several linux distros on this PC and after many failed attempts to get it running, I'm coming here for help.

I get the same error every time I try to start the game. Error #132. I've read that this error can mean many things, yet I can't pinpoint exactly what is causing it in my case. There have been a couple times where I was able to log in, thinking it was fixed. But once I've entered my realm, most, if not all the action bar icons appear to be corrupt. 

I've even tried installing WoW on a somewhat new laptop, which is totally capable of running WoW, and get still get Error #132. This laptop is running Ubuntu 9.10

I am installing WoW by dragging the folder from an external hard drive I've got. And I don't think there is anything wrong with the files on the external, because this is the method I've used several times to install WoW on my main PC, which is also running Ubuntu.

SO, I'm really hoping that someone here can help me to fix this and get WoW running.

Thank you to anyone who can help, and I can post an error log if needed.


which video card do you have? are you using the most recent drivers?

---

### Post by Toffeeapple on 2010-04-06
Have you read this..

QUOTE..
The 132 problem is 99% unique to WoW. The exception being 1 or 2 people who simply had bad sticks of RAM that caused the same error in one of the new top of the line offline games.

It isnt a software problem. Reinstalling WoW wont fix it, removing mods or having clean savedvariables wont fix it (thats Blizzards default cop out first answer for most problems), etc.

I have read page after page on the WoW boards and argued with the official tech board representatives over it. The occurance of the error is really pretty random. There doesnt seem to be an identifyable set of game circumstances that cause it reliably. I ran the game for nearly a year without ever having an error. Then 3 months after playing on a new machine, I started getting them. Well that machine went to hell and I had to gut it. New HD, PSU, & MB. Same CPU&RAM. After all the clean installs, new hardware, etc... I got one the very first day I booted it up. I still get them occasionally, but with no real frequency.

Also sadly the std memory testors will not identify any problems in the RAM unless the RAM is just simply bad. WoW techs admit that unless the RAM is just bad the std testors most likely will not reveal any problems with RAM getting the 132 erros.

OK. So what exactly is my point? After about 3 months of arguing over this, I think it really is 1 of 2 problems.

1) overheating of ram, cpu, or mb chipsets
2) the RAM that people are using is not of the *quality* that will run WoW as it was ment to be.

This is my opinions on the matter of RAM: All RAM is not created equal. A stick of RAM may not be *bad* in that it can preform all or 99% of the normal functions required by general computing with few enough errors that the system can ignore or compensate for them.

But the fact is that all RAM contains some degree of *badness*. Its just part of the manufacturing process. I call them deficiencies. In normal computing, there doesnt seem to be much of a difference in using *performance RAM* vs *budget* RAM.

BUT, WoW and similar MMOs are not normal computing. If you dig through all the WoW tech forum discussions, their stance boils down to a statement that WoW is a very demanding cutting edge piece of software that tends to bring out deficiencies in normal hardware. Sounds like a big cop out right? *shrugs* I gave up arguing with them over it.

So, make sure your RAM, CPU, MB chipsets are not overheating. If the error happens enough to make game play intolerable, and you have the cash... invest in some performance RAM. This is not the answer I want to hear either, but its the ones I have come to conclude.

If you have a cheap motherboard that is known to have some performance problems that could definitely affect things especially if you overclock. There are several threads where people fixed thier 132 problem by underclocking the FSB by 1 mghz or changed RAM CAS slightly and fixed thier problems. Even though they did not mention overclocking, I think they probably were which made thier system a bit unstable.

If I had the money, I would buy a pair of Kingston performance RAM myself. But right now my 132 are infrequent enough to not worry about it.
QUOTE.

I found it [here]("http://forums.techguy.org/games/428190-solved-wow-error-132-a.html").

---

### Post by peteraugusts on 2010-04-07
Error 132 for wow is usually related to a RAM issue. I have received both 132 and 134 error messages while playing. The problem isn't with your computer, it's the game itself not processing info fast enough sometimes.

The fix I use...while a pain in the but is to simply reboot the computer! That will clear your temporary cache, and allow the game to reload.

Hope this helps!

---

### Post by dahli.llama on 2010-04-07
> **asdfoo said:**
> which video card do you have? are you using the most recent drivers?

Seconding this question.

I was getting 132 errors every time I started up with my ATI card and the open source drivers.  Once I installed the restricted drivers and added the "SET gxApi opengl" line to my config.txt, then the problem went away.

---

### Post by Cloudkookoo on 2010-04-07
I've heard that it could be bad RAM before, and I'm hoping that isn't the problem. I've got an ATI Radeon x300 (I know, it's old) and the driver manager isn't finding any drivers for the card. I've also tried EnvyNG (I think that's what it's called) and it finds 3 drivers, 2 Nvidia, and 1 ATI. All of which are marked as incompatible.

---

