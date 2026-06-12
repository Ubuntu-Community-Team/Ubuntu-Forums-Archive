---
title: "Why are the liveCD and &quot;alternate&quot; CD not merged?"
date: 2011-04-12
forum: The Cafe
---

### Post by youbuntu on 2011-04-12
Okay, pardon my lack of knowledge as to what is required to master GNU/Linux distros, but I recall, years ago, that there were separate liveCD and Install CD discs. 

Why are the liveCD and Alternate CD not merged? In fact, why is there not one single "universal binary" disc, that caters for ALL platforms/variants, in a DVD ISO?

Please answer the questions separately, if you decide to reply.

:?

thx

---

### Post by uRock on 2011-04-12
Because you can't fit them onto one CD.

Not a support question. Moved to Cafe.

---

### Post by youbuntu on 2011-04-12
> **uRock said:**
> Because you can't fit them onto one CD.

Not a support question. Moved to Cafe.

Granted, but how about a cross-platform DVD ISO?

Side note: It would be **amazing** to have, by default, an SSH/Remote Desktop install option as part of the setup. You could tell the installer to leave SSH open, so that after the install had completed, you could re-login and run updates etc.

No? :D

---

### Post by earthpigg on 2011-04-12
It wouldn't be very difficult for you to implement all of what you desire on a LiveDVD, if you wished for such a thing to exist. Once you got the routine down, it would take you a few hours every six months to provide and maintain this for the Ubuntu community. Deep technical knowledge would not be required, only that you read the documentation associated with a few projects that already exist. Two come to mind....

-There is a thread in the cafe somewhere about a shell script that lets you put multiple .isos onto a single cd/dvd. I cannot remember what the thread/script is called. Multi-ISO.sh or something?

-[remastersys]("http://en.wikipedia.org/wiki/Remastersys"). The creator/maintainer of that project is a very nice fellow, and he helped me out a great deal with a [project]("http://sites.google.com/site/masonux/") I formerly did. Once it was clear that I had read all of the documentation he provided and still needed help, he was very willing to do so. He even put me in touch with someone that hosted my project's direct download for free (well, not free... [someone]("http://geekconnection.org/home/") paid hard-earned money for that [bandwidth]("http://masonux.geekconnection.org/"), just not me). He also wasn't at all upset or put off when I declined his offer to host the official forums for my project as a subforum of his remastersys forums.

Once you start doing research for your project (assuming you want it badly enough to devote time/energy to its creation), let us know if you hit any brick walls.

---

### Post by youbuntu on 2011-04-12
> **earthpigg said:**
> It wouldn't be very difficult for you to implement all of what you desire on a LiveDVD, if you wished for such a thing to exist. Once you got the routine down, it would take you a few hours every six months to provide and maintain this for the Ubuntu community. Deep technical knowledge would not be required, only that you read the documentation associated with a few projects that already exist. Two come to mind....

-There is a thread in the cafe somewhere about a shell script that lets you put multiple .isos onto a single cd/dvd. I cannot remember what the thread/script is called. Multi-ISO.sh or something?

-There is also remastersys.

Once you start doing research for your project (assuming you want it badly enough to devote time/energy to its creation), let us know if you hit any brick walls.

I'm not talking about a multi ISO disc - that's not solving the problem. I mean ONE ISO that is live **and** install, for ALL platforms. Surely it should have been implemented by now?

I'm in no position to do this, sorry. It sure would save Canonical bandwith, too.

---

### Post by tgm4883 on 2011-04-12
> **youbuntu said:**
> I'm not talking about a multi ISO disc - that's not solving the problem. I mean ONE ISO that is live **and** install, for ALL platforms. Surely it should have been implemented by now?

I'm in no position to do this, sorry. It sure would save Canonical bandwith, too.

Actually, it would cost Canonical bandwidth, not save bandwidth. I have 64-bit machines, why would I need to download all the 32-bit binaries?

---

### Post by tgm4883 on 2011-04-12
I would also point out that

1) [There already is a DVD ISO]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#dvd")

2) You can install from the Live CD.

---

### Post by uRock on 2011-04-12
> **youbuntu said:**
> I'm not talking about a multi ISO disc - that's not solving the problem. I mean ONE ISO that is live **and** install, for ALL platforms. Surely it should have been implemented by now?

I'm in no position to do this, sorry. It sure would save Canonical bandwith, too.
How would hosting a 4.* GB image that everyone downloads be more efficient than someone downloading a 700MB image, twice? 

We know already that if they were to use the DVD as their main image, then they will most likely fill the ISO to its fullest capacity.

I am sure there is a brainstorm listing for this subject. Have you looked for it, so that you can vote?

Cheers,
uRock

---

### Post by earthpigg on 2011-04-12
> I'm not talking about a multi ISO disc - that's not solving the problem. I mean ONE ISO that is live **and** install, for ALL platforms. Surely it should have been implemented by now?

erm - that is the point. you can modify sshd as you describe, include that on your various custom .isos. then, you could use the multi iso script to create a single .iso.

> I'm in no position to do this, sorry. It sure would save Canonical bandwith, too.

you are in the perfect position, sir. you want it to exist, and you have access to the tools to make it exist. Canonical has adopted unofficial projects as official in the past, this could be one more example of that.

---

### Post by youbuntu on 2011-04-12
I feel the point is being missed, here. It would not necessarily need to be the full 4.7Gb ISO size, surely?

As regards the existing DVD ISO; yes, I know that - but what about older hardware that **cannot** install in liveCD mode? That's the *point* of the alternate disc, and *my* point is that it would be easier (for the users) to merge them into one, no?

Do you see my viewpoint now? :)

---

### Post by earthpigg on 2011-04-12
hardware so old that it requires the alternate install cd is ***also*** possibly so old that it would need to be a cd, and ***not*** a dvd.

the old re-purposed corporate machine's i've worked with that get donated to charities very rarely have dvd drives, and very often require the use of the alternate install cd. the volunteers know/expect this, and generally don't even bother with the graphical install CDs and certainly wouldn't carry a DVD around with them. generally speaking, we're talking about a custom install cd (***never*** dvd) that is ncurses or text based, not graphical.

---

### Post by youbuntu on 2011-04-12
> **earthpigg said:**
> hardware so old that it requires the alternate install cd is ***also*** likely so old that it would need to be a cd, and ***not*** a dvd.

I was about to reply with that, yes. Okay, well I am asking why this has not (yet) come to pass - one universal *CD* and one universal *DVD*, which both include *alternate* text-based installers for older machines. Is it *that* hard? I'm not being snotty, I am asking, genuinely, if it IS that hard or not? :)

[EDIT]

If the data size of the ISO was less than 4.XGb, don't they zero-pad the image? It could be compressed as ZIP, and surely it would shrink to the pre-padded size?

---

### Post by earthpigg on 2011-04-12
> **youbuntu said:**
> one universal *CD* and one universal *DVD*, which both include *alternate* text-based installers for older machines.

the dvd would be easy, but cost money in the form of bandwidth.

the cd, though, not so much. canonical has already crammed as much into 700mb as humanly possible (edit: and it is already compressed using methods superior to .zip, iirc). if you want to put a 2nd text-based installer, you've got to ditch an app or two that currently comes pre-installed in ubuntu. 

and if you wanted the universal CD to include both 32 *and* 64 bit, then you need to axe over half of the programs ubuntu comes preinstalled with.

edit2:

it wouldn't be good business, either way. ditching a few apps to get the text-installer included would make ubuntu more appealing to hobbyists with older computers, but these aren't Canonicals source of revenue. Businesses that are willing/able to purchase support contracts are Canonical's source of revenue, and businesses willing/able to purchase support contracts are already past the point of being willing/able to purchase modern computer hardware. 

it has never been about making ubuntu the best operating system possible. it has, and shall remain, always been about making it the best revenue generator possible given the initial business model and founding principles/promises outlined by Mark. ***coincidentally***, that means making Ubuntu great - but we shouldn't confuse ourselves by saying that "the point" has ever been to make it great. it is incidental. 

So, let me ask a question: how would following your proposal generate more revenue for Canonical? keeping in mind that charities and hobbyists are a minuscule and trivial source of income.

---

### Post by youbuntu on 2011-04-12
> **earthpigg said:**
> the dvd would be easy, but cost money in the form of bandwidth.

the cd, though, not so much. canonical has already crammed as much into 700mb as humanly possible (edit: and it is already compressed using methods superior to .zip, iirc). if you want to put a 2nd text-based installer, you've got to ditch an app or two that currently comes pre-installed in ubuntu. 

and if you wanted the universal CD to include both 32 *and* 64 bit, then you need to axe over half of the programs ubuntu comes preinstalled with.


Right. So let's say the i386+amd64 merge idea is put to one side; how much does it take to implement a text-based install option into the normal "Desktop" ISO? Surely not *that* much? It just seems a little clunky to have to have **two** CDs, when one would suffice? You'd have the option whether to run in liveCD mode, or go straight to text-based installer. Makes far more sense, doesn't it?...

---

### Post by earthpigg on 2011-04-12
please re-read my post, i edited it substantially.

> It just seems a little clunky to have to have two CDs, when one would suffice?

most of us hard-core hobbiest nerds have long since moved from having more than one CD.

[LIST]
[*]alternate 32-bit install cd, ***only*** for older systems that cannot boot usb.
[*]liveusb for everything else. the best guess .iso hangs out on the thumb drive, and unetbootin can be put on any win/mac/linux computer for on-the-spot live installer creation. in the past, i've gone so far as to include unetbootin.exe on the liveusb itself.
[/LIST]

with those two things, im pretty much set for any computer you put in front of me. linux or no linux, i'd be carrying that thumb drive with me anyways - so it isn't extra weight. it usually has some movies or other stuff hanging out on it in addition to ubuntu 32 bit desktop.

---

### Post by earthpigg on 2011-04-12
and, i believe i was specific in answering your question of;

> how much does it take to implement a text-based install option into the normal "Desktop" ISO? Surely not that much?

but, just in case...

how much will it take: exactly one or two apps. talking in terms of megabytes is irrelevant, because business users don't see megabyes - they see apps.

---

### Post by youbuntu on 2011-04-12
My points have been missed. I am not debating the business side of things. If you want to carry on downloading TWO ISOs, be my guest. I'm leaving this thread for a while, to see if anyone else has any comments. 

Bye :)

---

### Post by uRock on 2011-04-12
> **youbuntu said:**
> If you want to carry on downloading TWO ISOs, be my guest.

I would much rather download 700MB instead of 4.7GB. We know the current images wouldn't take up that much, but we also know that the devs would fill the image to its limit.

An all-in one disk would be great for many people. One day it may happen. 

> I am sure there is a brainstorm listing for this subject. Have you looked for it, so that you can vote?

---

### Post by tgm4883 on 2011-04-12
> **youbuntu said:**
> My points have been missed. I am not debating the business side of things. If you want to carry on downloading TWO ISOs, be my guest. I'm leaving this thread for a while, to see if anyone else has any comments. 

Bye :)

I'm in a good mood, so I'm going to say this as nicely as I can. 

On a hunch, I downloaded the Ubuntu Natty Beta DVD from the Ubuntu website. I opened VirtualBox, attached it to an existing virtual machine and booted it up. Guess what it has both Live mode and text installer mode.

So I'll wait now for you to apologize for coming here and making accusations about how nobody understands your great ideas. It took me less than 1 hour to download the 4GB ISO and verify that you don't know what you are talking about.

---

### Post by youbuntu on 2011-04-12
> **tgm4883 said:**
> I'm in a good mood, so I'm going to say this as nicely as I can. 

On a hunch, I downloaded the Ubuntu Natty Beta DVD from the Ubuntu website. I opened VirtualBox, attached it to an existing virtual machine and booted it up. Guess what it has both Live mode and text installer mode.

So I'll wait now for you to apologize for coming here and making accusations about how nobody understands your great ideas. It took me less than 1 hour to download the 4GB ISO and verify that you don't know what you are talking about.

There are so many gracious and polite ways that you could have worded that reply... so why did you choose the accusational, rude & apology seeking one?

I have not yet downloaded the DVD iso, but obviously you HAVE - well done for you. Ironically, none of the OTHER members on this thread had filled in the "missing pieces of the puzzle", so to speak - not one single person, **staff included**, mentioned it.

You'll get no apology, as I don't think one is needed.

---

### Post by earthpigg on 2011-04-12
tgm4883 - does the dvd include both 32 and 64 bit? 700mb+700mb = 1.4gb. any idea what is filling up that last 2.6gb? all language packs?

> **youbuntu said:**
> Ironically, none of the OTHER members on this thread had filled in the "missing pieces of the puzzle", so to speak - not one single person, **staff included**, mentioned it.

probably cuz none of us realized that Canonical is doing this with the latest release. interesting. maybe i was wrong.

Anyways, it is likely that the 'staff' also haven't done this. they aren't Canonical employees, and the vast majority aren't Ubuntu programmers or beta testers. They are random dudes and dudettes on the internet that were asked to help moderate a discussion forum relevant to their interests.

There is no conspiracy :P.

---

### Post by youbuntu on 2011-04-12
> **earthpigg said:**
> probably cuz none of us realized that Canonical is doing this with the latest release. interesting. guess i was wrong.

Anyways, it is likely that the 'staff' also haven't done this. they aren't Canonical employees, and the vast majority aren't Ubuntu programmers or beta testers. They are random dudes and dudettes on the internet that were asked to help moderate a discussion forum relevant to their interests.

There is no conspiracy :P.

I don't think their is a "conspiracy" even for a second - conspiracy theories are ridiculous. I made that point, to illustrate that I am **not** trying to accuse anyone of not understanding the "idea", at all. Shame some folk seem to feel the need to pick holes in your debate, no matter WHAT it takes, to bolster their ego.


Thanks for the reply :)

---

### Post by tgm4883 on 2011-04-12
> **youbuntu said:**
> There are so many gracious and polite ways that you could have worded that reply... so why did you choose the accusational, rude & apology seeking one?

I have not yet downloaded the DVD iso, but obviously you HAVE - well done for you. Ironically, none of the OTHER members on this thread had filled in the "missing pieces of the puzzle", so to speak - not one single person, **staff included**, mentioned it.

You'll get no apology, as I don't think one is needed.

Don't worry I wasn't really waiting for an appology, you don't seem like the type of person that would ever admit they were wrong. With statements like this one

> **youbuntu said:**
> I was about to reply with that, yes. **Okay, well I am asking why this has not (yet) come to pass - one universal *CD* and one universal *DVD*, which both include *alternate* text-based installers for older machines.** Is it *that* hard? I'm not being snotty, I am asking, genuinely, if it IS that hard or not? :)

[EDIT]

If the data size of the ISO was less than 4.XGb, don't they zero-pad the image? It could be compressed as ZIP, and surely it would shrink to the pre-padded size?

why would anyone question whether you had actually checked it. You sound off with a wave of knowledge there.

Don't make assumptions. You are being borderline nefarious in your statements regarding Ubuntu, which you obviously haven't fact checked. 

My point here is check your facts before you spout off nonsense. You won't come be accused of trolling if you actually bring some good discussion.

---

### Post by KiwiNZ on 2011-04-12
"Any topic or discussion that causes problems or drama will be closed."

Thread Closed

---

