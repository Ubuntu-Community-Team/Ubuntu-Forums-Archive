---
title: "Is it possible to make a Linux distro with no GNU tools?"
date: 2007-08-12
forum: The Cafe
---

### Post by Ultra Magnus on 2007-08-12
Just wondering - With opensolaris and BSD around, would it be theoretically possible to make a linux distribution with No GNU tools or anything?

---

### Post by original_jamingrit on 2007-08-12
One of the main things you would need to worry about replacing is th gcc compiler, but I think there should be one or two other compilers that suit Linux's needs, maybe the Borland compiler(proprietary, you need to buy it I think).

Although, if you do successfully make a distro with no GNU tools, you should expect to get flamed for a little while.  Theoretically, of course.  =-P

EDIT:  Oh yeah, pretty much every administrative command in the terminal has a GNU copyleft on their manpages.  If you really wanted to replace them, you'll have a lot of writing to do, or moving stuff from other version of Unix/BSD/etc..

---

### Post by prizrak on 2007-08-12
It is possible to have Linux without GNU it would be fairly difficult though. You would basically have to find a substitute for each GNU tool or write your own.

---

### Post by starcraft.man on 2007-08-12
> **Ultra Magnus said:**
> Just wondering - With opensolaris and BSD around, would it be theoretically possible to make a linux distribution with No GNU tools or anything?

Adding to the just wondering, why would anyone want to gut all the GNU out of Linux?

---

### Post by ThinkBuntu on 2007-08-12
For a more concise distro name, e.g. "Debian Linux"?

---

### Post by Lord Illidan on 2007-08-12
Perhaps someone anti GPL or anti GNU might want to do it..perhaps MS? :P

---

### Post by kellemes on 2007-08-12
> **Lord Illidan said:**
> Perhaps someone anti GPL or anti GNU might want to do it..perhaps MS? :P

Cannot imagine this will happen, I **can** imagine MS coming with there own GNU/Linux distribution some day..

Recoding the hole GNU tool set is possible of course, but since the hole GNU-environment is very modular anyway it's much easier to gradually recode certain tools over time. And this is what happens anyway.

Edit: typo's

---

### Post by 23meg on 2007-08-12
Of course you can, theoretically. In the sense that you can also change the Earth's orbit with the existing technologoies, theoretically.

---

### Post by kellemes on 2007-08-12
> **23meg said:**
> Of course you can, theoretically. In the sense that you can also change the Earth's orbit with the existing technologoies, theoretically.

Looking at the weather the last couple of years it seems to be already happening.:)

---

### Post by Hex_Mandos on 2007-08-12
I don't think it's impossible. DeLi Linux uses very few GNU tools. The most important packages can be replaced:

* BASH: Some other shell you like
* coreutils: busybox
* gcc: tcc (Tiny C Compiler, not necessarily the best, but still a C compiler)
* libc: uClibc

---

### Post by bruce89 on 2007-08-12
AFAIK, Linux (the kernel that is) needs gcc in order to compile. No other complier can do it (mabye it is possible others can do it now).

Unless you want to write your own kernel, I doubt it is possible (or useful).

---

### Post by jfinkels on 2007-08-12
Better get cracking on that C compiler if you want a non-GNU distribution...

But isn't it called GNU/Linux because Linus's original kernel incorporated the GNU Hurd kernel or something like that? So wouldn't you have to rewrite the kernel (essentially stripping the operating system of its 'Linux' status)?

> **23meg said:**
> Of course you can, theoretically. In the sense that you can also change the Earth's orbit with the existing technologoies, theoretically.

Haha :D

---

### Post by bruce89 on 2007-08-12
> **jfinkels said:**
> But isn't it called GNU/Linux because Linus's original kernel incorporated the GNU Hurd kernel or something like that?

Certainly not, Linux was spawned from Minux. Hurd's completely seperate.

---

### Post by WishingWell on 2007-08-12
> **bruce89 said:**
> Certainly not, Linux was spawned from Minux. Hurd's completely seperate.

Actually, both the Hurd and the Linux kernel share more aspects with the NT kernel than they do with each other.

The Hurd = micro kernel
Linux = monolithic kernel
NT = Hybrid (a combination of a micro and monolithic kernel)

---

### Post by jfinkels on 2007-08-12
> **bruce89 said:**
> Certainly not, Linux was spawned from Minux. Hurd's completely seperate.

Okay I remember now, you're right. Linus used Minix + GNU tools to make Linux.

---

### Post by WishingWell on 2007-08-12
> **23meg said:**
> Of course you can, theoretically. In the sense that you can also change the Earth's orbit with the existing technologoies, theoretically.

It has already been done with [Mastodon.]("http://www.pell.portland.or.us/~ftp/pub/freeware/mastodon/")

Mastodon is based on Linux kernel 2.6, libc 4, a.out, and a BSD userspace.

---

### Post by 23meg on 2007-08-12
It still seems to have a bunch of GNU stuff inside. But that's not the point; what I was getting to was that unless you're in a deep disagreement with the GPL or just want to build a proof-of-concept system (which Mastodon looks like), it's kind of shooting yourself in the foot.

---

### Post by WishingWell on 2007-08-12
> **23meg said:**
> It still seems to have a bunch of GNU stuff inside. But that's not the point; what I was getting to was that unless you're in a deep disagreement with the GPL or just want to build a proof-of-concept system (which Mastodon looks like), it's kind of shooting yourself in the foot.

That would depend on if you can build a better system using other tools than GNU or not.

And Mastondon was primarily built because David Parson is an old Unix guru who wanted a system that used the Linux kernel but with a Unix libc and userland.

(the last version had to be removed because it had SCO patented Unix tools in it but the earlier version were just as free of GNU and used BSD code to replace it)

I guess i misunderstood you when you said it was possible *theoretically* in the same way moving the earth out of orbit with todays technology is also possible theoretically. To me that would mean that you were saying they are equally possible and since one of them is not then neither should the other one be possible.

---

### Post by perce on 2007-08-12
> **23meg said:**
> 
 unless you're in a deep disagreement with the GPL 


Linux itself is distributed under GPL.

I do find the fight over the name a bit childish, but we shouldn't forget that the FSF has done and is still doing a tremendous job to make GNU/Linux possible, and their ideas about freedom, although a bit  extreme, do make a lot of sense. So, what's the point of removing GNU software from your favourite distribution?

---

### Post by cobrn1 on 2007-08-12
I think that it's called GNU/Linux out of respect for the fact that without the inordinate amount of GNU code that goes into a linux distro, the linux kernel itself would be pretty much useless (atleast for most people's uses).

Technically I guess you could rewrite all the commands yourself, one at a time, but it would be a pain and be very difficult as the code would need to be substantially different not to incur GLP wrath, but would need to do the same thing.

Basically, the 'changing the orbit of the planet with current tech' was right on the nail, technically possible, but no... if you see what I mean.

---

### Post by WishingWell on 2007-08-12
> **cobrn1 said:**
> I think that it's called GNU/Linux out of respect for the fact that without the inordinate amount of GNU code that goes into a linux distro, the linux kernel itself would be pretty much useless (atleast for most people's uses).

Technically I guess you could rewrite all the commands yourself, one at a time, but it would be a pain and be very difficult as the code would need to be substantially different not to incur GLP wrath, but would need to do the same thing.

Basically, the 'changing the orbit of the planet with current tech' was right on the nail, technically possible, but no... if you see what I mean.

You should read the whole thread before you reply, not only is it possible, it's already been done at least once. (you can download the iso from the link i posted in my previous post and try it out for yourself if you'd like)

---

### Post by tbroderick on 2007-08-12
> **WishingWell said:**
> You should read the whole thread before you reply, not only is it possible, it's already been done at least once. (you can download the iso from the link i posted in my previous post and try it out for yourself if you'd like)

Mastodon clearly uses gcc.

---

### Post by hanzomon4 on 2007-08-12
The bsd's don't use GNU code right?

---

### Post by Anthem on 2007-08-12
How much of this software makes it into an Ubuntu Linux install?

[http://directory.fsf.org/](http://directory.fsf.org/)

Doesn't look like much (other than GCC, obviously).

---

### Post by WishingWell on 2007-08-12
> **tbroderick said:**
> Mastodon clearly uses gcc.

It does? Can you provide a link to where you got that information from?

---

### Post by tbroderick on 2007-08-12
> **WishingWell said:**
> It does? Can you provide a link to where you got that information from?

Read the page you linked to. 

"INST0063 is also available. This version still uses **gcc 2.7.2.3 **for everything."

"INST0064 is also available. This version had, among other things, **gcc updated to 2.95.2**, which means that a lot of things just stopped working."

Here's the tricky one,

"BETA0066 is now available. This no longer has **gcc 2.95.2**, but libc 5 is still dead and some packages have been updated to newer versions of the code"

If you click on the link to 'BETA0066' you can see the package list. You'll notice they went back to **gcc-2.7.2.3**.

---

### Post by WishingWell on 2007-08-12
> **tbroderick said:**
> Read the page you linked to. 

"INST0063 is also available. This version still uses **gcc 2.7.2.3 **for everything."

"INST0064 is also available. This version had, among other things, **gcc updated to 2.95.2**, which means that a lot of things just stopped working."

Here's the tricky one,

"BETA0066 is now available. This no longer has **gcc 2.95.2**, but libc 5 is still dead and some packages have been updated to newer versions of the code"

If you click on the link to 'BETA0066' you can see the package list. You'll notice they went back to **gcc-2.7.2.3**.

You're quite right, my apologies for not bothering to read closer what compiler was used.

---

### Post by init1 on 2007-08-12
> **Hex_Mandos said:**
> I don't think it's impossible. DeLi Linux uses very few GNU tools. The most important packages can be replaced: * BASH: Some other shell you like * coreutils: busybox * gcc: tcc (Tiny C Compiler, not necessarily the best, but still a C compiler) * libc: uClibc Right. But bash *is* my favorite shell; sh isn't as good, and zsh is weird. And you can still have GNU apps in Busybox, or at least I think you can. I thought Busybox was just a way to fit lots of commands into one, so that the source of each of the commands doesn't have to change much, if at all. But I don't know for sure. I have never looked the Busybox source before.

---

### Post by tbroderick on 2007-08-12
> **WishingWell said:**
> You're quite right, my apologies for not bothering to read closer what compiler was used.

You should apologize to cobrn1.

---

### Post by 23meg on 2007-08-12
> **WishingWell]That would depend on if you can build a better system using other tools than GNU or not.[/QUOTE]

Sure said:**
> I guess i misunderstood you when you said it was possible *theoretically* in the same way moving the earth out of orbit with todays technology is also possible theoretically. To me that would mean that you were saying they are equally possible and since one of them is not then neither should the other one be possible.

Both are possible, as well as not being practical for modern common purposes.

[QUOTE=perce]Linux itself is distributed under GPL.

I do find the fight over the name a bit childish, but we shouldn't forget that the FSF has done and is still doing a tremendous job to make GNU/Linux possible, and their ideas about freedom, although a bit extreme, do make a lot of sense. So, what's the point of removing GNU software from your favourite distribution?[/QUOTE]

I don't see a point; that was pretty much my point actually.

---

### Post by Hex_Mandos on 2007-08-12
> **init1 said:**
> Right. But bash *is* my favorite shell; sh isn't as good, and zsh is weird. And you can still have GNU apps in Busybox, or at least I think you can. I thought Busybox was just a way to fit lots of commands into one, so that the source of each of the commands doesn't have to change much, if at all. But I don't know for sure. I have never looked the Busybox source before.

AFAIK, Busybox replaces the coreutils, but doesn't include them.

---

### Post by init1 on 2007-08-12
> **Hex_Mandos said:**
> AFAIK, Busybox replaces the coreutils, but doesn't include them.
OK, I wasn't sure. How different are the busybox apps from coreutils?

---

### Post by hanzomon4 on 2007-08-13
zsh is cool, you just need a good zshrc, profile, whatever config files and you will only notice the enhancements

---

### Post by init1 on 2007-08-13
> **hanzomon4 said:**
> zsh is cool, you just need a good zshrc, profile, whatever config files and you will only notice the enhancements
Maybe I'll try that. But the zsh in GRML is annoying. Bash does what I need and expect, but I haven't explored the features of zsh yet.

---

### Post by WishingWell on 2007-08-13
> **tbroderick said:**
> You should apologize to cobrn1.

My apology was general, it wasn't directed to you and i see no reason to make a separate apology to cobrn1.

Fact is that GCC can be replaced so using the other packages from the distro with another compiler would create a new completely GNU free system, granted, it wouldn't be Mastodon but it's perfectly doable and as such, not beyond reach for anyone who knows how to code.

---

### Post by Oki on 2007-08-13
Debian is working on the Hurd Kernel - as I understand it the works goes slowly. Remember reading Richard S. saying they had a working but unstable kernel in 2002. 
So I guess they will sooner(but not likely) remove Linux before GNU. Got the fealing GNU dont like that all the credit gos to Liunx - since GNU came before Linux, and contains a lot more work then Linux.

---

### Post by WishingWell on 2007-08-13
> **Oki said:**
> Debian is working on the Hurd Kernel - as I understand it the works goes slowly. Remember reading Richard S. saying they had a working but unstable kernel in 2002. 
So I guess they will sooner(but not likely) remove Linux before GNU. Got the fealing GNU dont like that all the credit gos to Liunx - since GNU came before Linux, and contains a lot more work then Linux.

Well there is also Belenix, Nexenta and Shillix that are using a different kernel successfully (OpenSolaris) and then there is DebianBSD whis uses the FreeBSD kernel.

However, "they" don't really have anything close to being done with the Hurd, it would take other programmers less time to build the GNU used tools in Ubuntu than it has taken for the Hurd to come to this unusable state.

For some reason people think that GNU rules the FOSS world, and it's just not true, RMS wants to be the second coming of Jesus but he's not, he's just an old hippie who talks a lot more than he thinks these days. I'll have to give him credit for many years of excellent work though, love his work, hate his ideology which is the opposite of freedom.

BSD, that's real freedom, no restrictions.

---

### Post by cobrn1 on 2007-08-13
> **WishingWell said:**
> My apology was general, it wasn't directed to you and i see no reason to make a separate apology to cobrn1.

Fact is that GCC can be replaced so using the other packages from the distro with another compiler would create a new completely GNU free system, granted, it wouldn't be Mastodon but it's perfectly doable and as such, not beyond reach for anyone who knows how to code.

I think the point is that there's a difference between apologising for posting incorrect imformation, and apologising for being outright rude to someone - particularly when you were in the wrong...

However, I'm not one to gloat and I don't particularly care if you apologise (though it would be the manly thing to do), I ask only that you hold your tongue in future, least you upset someone less thick-skinned... ;)

---

### Post by WishingWell on 2007-08-13
> **cobrn1 said:**
> I think the point is that there's a difference between apologising for posting incorrect imformation, and apologising for being outright rude to someone - particularly when you were in the wrong...

However, I'm not one to gloat and I don't particularly care if you apologise (though it would be the manly thing to do), I ask only that you hold your tongue in future, least you upset someone less thick-skinned... ;)

Well you should be glad that he caught the gcc thing because you didn't, did you, honestly? 

Did you honestly read the entire thread, went through the link i posted and without even mentioning it conclude that it contained one GNU package?

If so, i sincerely apologise but it would have been better and more believable if you had just posted it right there and then.

And the point i was arguing against was that it's as possible as moving the earth out of orbit with existing technology (which isn't possible even with all the nukes we have centered in one place, it would just blow the planet up) and you could just use another compiler instead of gcc to make the distro work (the tricky thing here would be choosing the correct compiler, i know icc can compile the linux kernel but i don't know about the rest, maybe it'd have to be a two compiler version, one for the kernel and one for the rest?).

It would not be Mastodon since it uses gcc, but it would be Mastodon with a non gnu compiler/set of compilers.

So was it really rude of me to state that you haven't read the thread or had you read the thread and researched Mastodon to find one GNU package?

---

### Post by cobrn1 on 2007-08-13
> So was it really rude of me to state that you haven't read the thread or had you read the thread and researched Mastodon to find one GNU package?Well:

> **WishingWell said:**
> You should read the whole thread before you reply, not only is it possible, it's already been done at least once. (you can download the iso from the link i posted in my previous post and try it out for yourself if you'd like)


Translation: Idiot! Retard! He can't even f*ing read!!! RTFM, etc...

> **WishingWell said:**
> My apology was general, it wasn't directed to you and i see no reason to make a separate apology to cobrn1.

Translation: WHAT!!! And make me look like the idiot... no thank you!

> **WishingWell said:**
> Well you should be glad that he caught the gcc thing because you didn't, did you, honestly? 

 Did you honestly read the entire thread, went through the link i posted and without even mentioning it conclude that it contained one GNU package?

honestly, no - I didn't catch it myself. What i did do though is reason that linux is called GNU/Linux for a reason, ie, linux without GNU is not easy, and I would have heard about it (given that I keep up with the new in the linux world). I doubted that your link would have any substance to it in reality.

Lo and behold, I was right, but in future I'll be caseful to look at *ALL* links in the thread so that I may vindicate myself should the need arise again...


> If so, i sincerely apologise but it would have been better and more believable if you had just posted it right there and then.thanks for your advice on posting - however, i haven't the time to read all links in a forum and reasoned that you were wrong. Simple as that (and quite correct it would seem). If you still mean your apology then accepted, but try to be more tactful with you posting - there are nicer ways you could have put it which don't make people look like idiots...

> And the point i was arguing against was that it's as possible as moving the earth out of orbit with existing technology (which isn't possible even with all the nukes we have centered in one place, it would just blow the planet up) and you could just use another compiler instead of gcc to make the distro work (the tricky thing here would be choosing the correct compiler, i know icc can compile the linux kernel but i don't know about the rest, maybe it'd have to be a two compiler version, one for the kernel and one for the rest?).I' surprised you type sucj sweeping statements with no backup. How do you know that we couldn't change the orbit? how do you know we'd just blow up the earth? THere's a very good chance we could do it (but we'd probably kill ourselves in the process - however, that's not equal to estroying the planet and is just an assumption on my part 0 it may well be possible without destruction). Point is, you have no idea if it is possible, but you go ahead and assume it is - please be more careful before you post information that is wrong.

In anycase, at the moment it would seem that it is impossible to have linux without *a* GNU tool being involved, however, it would seem that we're not a million miles off being able to.

EDIT: a more interesting question perhaps - if wishingwell is right and it's just a matter of using a few compilers, would this new distro be any use - are all the GNU tools replicated at the moment... if not then we are a long, long way off... but it's atleast possible. Which is interesting to know.

---

### Post by Anthem on 2007-08-13
> **Oki said:**
> Got the fealing GNU dont like that all the credit gos to Liunx - since GNU came before Linux, **and contains a lot more work then Linux**.
That's certainly not true.

---

### Post by WishingWell on 2007-08-13
> **cobrn1 said:**
> Well:




Translation: Idiot! Retard! He can't even f*ing read!!! RTFM, etc...



Translation: WHAT!!! And make me look like the idiot... no thank you!



honestly, no - I didn't catch it myself. What i did do though is reason that linux is called GNU/Linux for a reason, ie, linux without GNU is not easy, and I would have heard about it (given that I keep up with the new in the linux world). I doubted that your link would have any substance to it in reality.

Lo and behold, I was right, but in future I'll be caseful to look at *ALL* links in the thread so that I may vindicate myself should the need arise again...


thanks for your advice on posting - however, i haven't the time to read all links in a forum and reasoned that you were wrong. Simple as that (and quite correct it would seem). If you still mean your apology then accepted, but try to be more tactful with you posting - there are nicer ways you could have put it which don't make people look like idiots...

I' surprised you type sucj sweeping statements with no backup. How do you know that we couldn't change the orbit? how do you know we'd just blow up the earth? THere's a very good chance we could do it (but we'd probably kill ourselves in the process - however, that's not equal to estroying the planet and is just an assumption on my part 0 it may well be possible without destruction). Point is, you have no idea if it is possible, but you go ahead and assume it is - please be more careful before you post information that is wrong.

In anycase, at the moment it would seem that it is impossible to have linux without *a* GNU tool being involved, however, it would seem that we're not a million miles off being able to.

EDIT: a more interesting question perhaps - if wishingwell is right and it's just a matter of using a few compilers, would this new distro be any use - are all the GNU tools replicated at the moment... if not then we are a long, long way off... but it's atleast possible. Which is interesting to know.

At least it has now been established that i owe you no apology and that it was rather rude of you to say that it would be manly of me to give you a such since i was right all along, you had not read the thread and that is all i stated, your interpretations stand for you and not for me.

icc can compile the kernel, that is known to be true (actually it has been tried, search for it) and the rest is BSD so it uses the BSD compiler supplied by the FreeBSD project. 

I'm not sure if one can compile all but i am sure that a combination can.

Would it be of any use? Well the BSD's are doing what linux is doing and so is OpenSolaris so i'd say that yes, it would be of use as a server, desktop and everything in between.

How do i know that we cannot change the orbit? It's simple physics, the suns gravity is much greater than the earths, to move it out of orbit would take a force stronger than the suns gravity and the earth could not stand that, it would literally crack if we tried. 

Remember, this is with todays technology which was what meg123 said and what you quoted.

---

### Post by cobrn1 on 2007-08-13
> **WishingWell said:**
> At least it has now been established that i owe you no apology and that it was rather rude of you to say that it would be manly of me to give you a such since i was right all along

Actually, we established that you were wrong all along, and I managed to work out that you were wrong without having to look at your link. I never claimed to know that your link uses 1 GNU package (I actually never claimed anything other than the two apologies are very different), however, as you ask, that's not something I 'knew', but as I said above, I worked out an equivalent truth, the link would not lead to a GNU separate linux distro. Instead of pointing this out, and being outright rude by saying that you were almost certainly wrong (thereby making you look bad) I decided to say that I doubted it would be possible (I was right) and used a nice little comment quoted from someone else in the thread.

> you had not read the thread and that is all i stated, your interpretations stand for you and not for me.Actually, I did read the thread (just not your link), and I think it is incredibly impertinent that you are giving me lectures since it was you who have been proven wrong (and were told to apologise for it).

You could have just said - 'fair enough - sorry cobrn1, you were right' (whether I came to the correct conclusion by reading the link in your post or by rationed reasoning is irrelavent), and that would have been fine. Instead you decided to try to save face and post that no apology was owed, and still maintain that... that stands you, not me.

However, as I have said, I care not for you apology (one that incidentally you still maintain you do not owe, and obviously have no intention to give), I'd just like you to be more considerate next time incase you're rude to someone who does care.

Anyway - back to the thread topic - I fear that we have imposed on it too much already.

> icc can compile the kernel, that is known to be true (actually it has been tried, search for it) and the rest is BSD so it uses the BSD compiler supplied by the FreeBSD project. 

I'm not sure if one can compile all but i am sure that a combination can.interesting...

> Would it be of any use? Well the BSD's are doing what linux is doing and so is OpenSolaris so i'd say that yes, it would be of use as a server, desktop and everything in between.So BSD has a copy of every tool that a linux distro requires, but without GNU code? Then it might be possible... and useful.

> It's simple physics, the suns gravity is much greater than the earths, to move it out of orbit would take a force stronger than the suns gravity and the earth could not stand that, it would literally crack if we tried. 

Remember, this is with todays technology which was what meg123 said and what you quoted.There you go with the assumptions again - you assumed (erroneously) that I want to move the earth's orbit outwards - maybe I want to move it closer to the Sun. It wouldn't be too hard *relatively speaking* given that the Sun's gravity would be quite happy to let the Earth move closer. Outwards would be much, much harder, but not necessarily impossible. In any event, the Earth's gravity is irrelevant here - no bearing on the situation at all.

---

### Post by WishingWell on 2007-08-13
> **cobrn1 said:**
> Anyway - back to the thread topic - I fear that we have imposed on it too much already.

interesting...

So BSD has a copy of every tool that a linux distro requires, but without GNU code? Then it might be possible... and useful.

There you go with the assumptions again - you assumed (erroneously) that I want to move the earth's orbit outwards - maybe I want to move it closer to the Sun. It wouldn't be too hard *relatively speaking* given that the Sun's gravity would be quite happy to let the Earth move closer. Outwards would be much, much harder, but not necessarily impossible. In any event, the Earth's gravity is irrelevant here - no bearing on the situation at all.

I skipped your intro since we are never going to agree on how it all happened, if i did insult you or was rude then i apologize for that with no strings attatched.

BSD predates Linux so yes.

And you don't understand how gravity and centrifugal force works, it's like a slingshot, you could do a load bad enough to crack the earth in half and it still wouldn't move it out of orbit.
In fact, it would be harder to get closer to the sun because the centrifugal power is as strong as the gravity of the sun, it needs to be or we would just go straight into the sun.

It would take an equal amount of force as our globe spinning to change the orbit and that would disintegrate both globes.

Earths gravity is most certainly relevant in either case.

The universe is fascinating, one less gram of gravity to earth and we would not be here, not you and not me.

---

### Post by cobrn1 on 2007-08-13
> **WishingWell said:**
> I skipped your intro since we are never going to agree on how it all happened, if i did insult you or was rude then i apologize for that with no strings attatched.

While I just *love* to be ignored, I think that's fair enough - apology accepted, and we'll speak no more about this...

> BSD predates Linux so yes.So BSD has the tools that linux uses. Is that what you mean (and therefore we have all the non-GNU tools we need)? If so, arent the BSD tools going to be descended from the GNU code then?

> And you don't understand how gravity and centrifugal force works, it's like a slingshot, you could do a load bad enough to crack the earth in half and it still wouldn't move it out of orbit.
In fact, it would be harder to get closer to the sun because the centrifugal power is as strong as the gravity of the sun, it needs to be or we would just go straight into the sun.

It would take an equal amount of force as our globe spinning to change the orbit and that would disintegrate both globes.

Earths gravity is most certainly relevant in either case.

The universe is fascinating, one less gram of gravity to earth and we would not be here, not you and not me.I'd thank you not to lecture me on physics I already know - particularly when you are wrong - centrifugal force is non-existant -its the result of centripetal force which we perceive as 'cetrifugal' force (but it's not really). This is simple physics...

However, the analogy of the slingshot is reasonably good. Basically the earth is trying to move forwards (on a tangent to it's orbit), but the gravity of the sun acts like a centripetal force, pulling the earth towards it. The way the forces balance, you end up with a circular orbit (circular motion + satellites 101). If you were able to push the earth a bit closer you would also need to increase it's (orbiting) speed to stop the earth from being sucked into the sun (if you don't increase the speed, the sun's gravity will be strong enough to overcome the Earth's tendance to move away at a tangent (which is what it would do if the sun's gravity wasn't present) which would lead to the earth falling into a decaying orbit of the sun, leading to our untimely destruction - notice though that we have managed our goal of changing the orbit - it just wasn't as stable as we'ed like if we don't increase speed accordingly). This would be easy to do - all you do is place you explosives at an angle (remember that we can resolve the force into two separate once acting at right angles (mechanics 101)) so you increase the speed and move the earth closer. Of course, you'd need to stop it, but if you can do one the other should be *relatively* managable.

To widen the earths orbit you just place the explosives on the otherside of the earth (ie, reflected in the tangent to the earth's orbit, and both sets would (i'd guess, if you were using this method) be placed behind the earth's orbit.

I hope that all makes sense to you, but that is the scientific truth of the matter.

Earth's gravity really has little bearing on this - it will be affecting the centripetal force slightly, but for the purposes of moving the earth's orbit it is not so important.

And yes, it is incredible how fragile our existances are - and number of factors changes and we wouldn't be here - at least not it this form (galaxies, earth, humans + other earth life)... that's the best we can really say, for who really knows how things would pan out otherwise?

---

### Post by GNUix on 2007-09-11
> **jfinkels said:**
> Better get cracking on that C compiler if you want a non-GNU distribution...

But isn't it called GNU/Linux because Linus's original kernel incorporated the GNU Hurd kernel or something like that? So wouldn't you have to rewrite the kernel (essentially stripping the operating system of its 'Linux' status)?



Haha :D

Just came across this thread and I have not read the entire thing, so this may have been properly answered, but in case it has not....

GNU/Linux is called GNU/Linux because its the fair thing to do.  Long before Linus was writing his kernel the Free Software guys were busy writing the GNU System, of which the only thing they lacked was a kernel.  People started using the "Linux" kernel and looked for other software to use with it, what do you know? there was all this Free Software from the GNU system.  So they put it together and called it Linux (when it should have been called GNU).

Anyways its important, because the purpose of the GNU system was not so people could have reliable kick butt software (that was of course a side effect). It was so people could enjoy Freedom with there software, and stripping GNU out takes the Freedom message out too.
[http://www.gnu.org](http://www.gnu.org) give it a read sometime, its all there.

Just so there is not any confusion (because there usualy is) I will add the opening quote from the GNU homepage.
> 
The GNU Project was launched in 1984 to develop a complete Unix-like operating system which is [free software](http://www.gnu.org/philosophy/free-sw.html): the GNU system. Variants of the GNU operating system, which use the kernel called Linux, are now widely used; though these systems are often referred to as &#8220;Linux&#8221;, they are more accurately called [GNU/Linux](http://www.gnu.org/gnu/linux-and-gnu.html) systems. 

GNU is a recursive acronym for &#8220;GNU's Not Unix&#8221;; it is pronounced guh-noo, approximately like canoe.



---

### Post by WishingWell on 2007-09-11
> **cobrn1 said:**
> While I just *love* to be ignored, I think that's fair enough - apology accepted, and we'll speak no more about this...

So BSD has the tools that linux uses. Is that what you mean (and therefore we have all the non-GNU tools we need)? If so, arent the BSD tools going to be descended from the GNU code then?

OpenSSH. 

> I'd thank you not to lecture me on physics I already know - particularly when you are wrong - centrifugal force is non-existant -its the result of centripetal force which we perceive as 'cetrifugal' force (but it's not really). This is simple physics...

However, the analogy of the slingshot is reasonably good. Basically the earth is trying to move forwards (on a tangent to it's orbit), but the gravity of the sun acts like a centripetal force, pulling the earth towards it. The way the forces balance, you end up with a circular orbit (circular motion + satellites 101). If you were able to push the earth a bit closer you would also need to increase it's (orbiting) speed to stop the earth from being sucked into the sun (if you don't increase the speed, the sun's gravity will be strong enough to overcome the Earth's tendance to move away at a tangent (which is what it would do if the sun's gravity wasn't present) which would lead to the earth falling into a decaying orbit of the sun, leading to our untimely destruction - notice though that we have managed our goal of changing the orbit - it just wasn't as stable as we'ed like if we don't increase speed accordingly). This would be easy to do - all you do is place you explosives at an angle (remember that we can resolve the force into two separate once acting at right angles (mechanics 101)) so you increase the speed and move the earth closer. Of course, you'd need to stop it, but if you can do one the other should be *relatively* managable.

To widen the earths orbit you just place the explosives on the otherside of the earth (ie, reflected in the tangent to the earth's orbit, and both sets would (i'd guess, if you were using this method) be placed behind the earth's orbit.

I hope that all makes sense to you, but that is the scientific truth of the matter.

Earth's gravity really has little bearing on this - it will be affecting the centripetal force slightly, but for the purposes of moving the earth's orbit it is not so important.

And yes, it is incredible how fragile our existances are - and number of factors changes and we wouldn't be here - at least not it this form (galaxies, earth, humans + other earth life)... that's the best we can really say, for who really knows how things would pan out otherwise?

Actually earths gravity has a LARGE bearing on it,do you need me to explain to you why that is or can you figure this one out on your own without me "needing to lecture you" which is what you state that i don't have to do everytime i remark on an error you do and your errors are not small, they are enormous, if anyone was to run the Universe according to your way of figuring it out it would be dead before it even started.

So, not so humbly i request that you use at least qualified science or back up your suppositions before making your claims.

Ok?

---

