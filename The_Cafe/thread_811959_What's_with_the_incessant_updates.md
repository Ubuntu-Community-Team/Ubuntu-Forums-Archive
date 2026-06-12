---
title: "What's with the incessant updates?"
date: 2008-05-29
forum: The Cafe
---

### Post by vav on 2008-05-29
Since Gutsy, Hardy beta and now into the full LTS Hardy, I get update notifications every day, and quite often there are 20+ updates. I mean it's great to have a fully patched system, but this is unprecedented!
 
Why are there so many updates? Is it because I'm using medibuntu? Is it because I'm using beta software like compiz? It's a time sink that I'd like to avoid...

---

### Post by _DD_ on 2008-05-29
If you enter the update manager preferences you can do various things such as change the period between update checks (default is daily) and whether it should get on and download them in the background without alerting you. All settings which should help relieve your frustrations :D!

---

### Post by mmb1 on 2008-05-29
When using beta software and new versions of distros, its important to remember that the developers need to fix bugs, add features, and patch the system.

You're not required to install any updates, sometimes I wait a few weeks, before updating, unless its important.

---

### Post by wkulecz on 2008-05-29
I agree that the update rate is too high for an LTS release.  Should have held it longer (like with 6.06) and/or left out pulse audio.

OTOH, one of the updates silently fixed an issue where my system would lockup (no mouse, no keyboard, no numlock LED toggle) randomly if multiple users were active using the fast user switching tool.

On balance 8.04 has been a fairly smooth transition with real benefits over 6.06 and 7.04 for us.  However if audio was crutial I can understand how one might be less than thrilled with it.

--wally.

---

### Post by Nepherte on 2008-05-29
It depends on what repositories you have enabled. Packages that have yet to be proved very stable will hit the hardy-proposed repositories before going to somewhere else. If you enable all the repositories, you will get very recent versions of the software you installed, but yet have to be proved stable in combination with your ubuntu version. These packages typically require more updates, fixes etc. so you'll get more updates for it as well.

A complete description on the repositories can be found at:
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by chrisccoulson on 2008-05-29
> **wkulecz said:**
> I agree that the update rate is too high for an LTS release.  Should have held it longer (like with 6.06) and/or left out pulse audio.

Every new release sees a lot of updates for a few weeks. And why would leaving Pulse Audio out make any difference? Out of all the updates we've seen for Hardy since final, how many of those have been for Pulse Audio? The answer is a big fat **zero**

---

### Post by jimv on 2008-05-29
Odd.  I went about a week with almost no updates, and then today I had about 15.  And I run apt-get update/upgrade pretty much everyday.

---

### Post by swoll1980 on 2008-05-29
> **wkulecz said:**
> I agree that the update rate is too high for an LTS release.  Should have held it longer (like with 6.06) and/or left out pulse audio.



Yeah your probably right. Those updates are annoying. Why can't they just leave the stuff unpatched for a couple of years or so like Microsoft does. Stupid Ubuntu developers when will they learn?

---

### Post by justin whitaker on 2008-05-29
How are updates bad again? :confused:

---

### Post by wkulecz on 2008-05-29
> And why would leaving Pulse Audio out make any difference? Out of all the updates we've seen for Hardy since final, how many of those have been for Pulse Audio? The answer is a big fat zero

Very many of the problems without solution and cries for help are about sound issues, these are mostly problems that didn't happen with older versions.  Read the multimedia fourm if you want perspective.

Sound works well enough for me for the default user set up by the installer, but for a user I added post install using the user and group tool with all settings matching the default user I get no sound if logged in as the added user!  

What is weird is I discovered by accident that switching to my added usere while leaving the default user logged in via the user switch tool the added usr had sound!  But wait, this caused the system to randomly lockup.  While testing it one of the many updated eventually fixed the lockup issue and now both users can stay active to workaround my sound problem.

These are the kind of issues I'm talking about.


If you want to hide behind the arguement that the problems are not with pulse audio but with applications not modified for it, I'd claim this is exactly the kind of system change that *doesn't* belong in an LTS release -- pushing changes onto the apps is for the six month throwaway releases.

--wally.

---

### Post by dnairb on 2008-05-29
> **wkulecz said:**
> I agree that the update rate is too high for an LTS release.

As has been said before on other posts, LTS means **L**ong **T**erm **S**upport, nothing else. It has nothing to do with the system's stability, when updates are released, or anything other than long-term support.

More applications installed = more updates as *everything* listed in Synaptic can and will be updated by the system. (Remember having to run Windows Update, and then updating all other applications individually in Windows? I *really* don't miss doing that)

Also, if you have proposed updates (hardy-proposed) and unsupported updates (hardy-backports) ticked in Update Manager you will, of course, get more updates more frequently.

---

### Post by wkulecz on 2008-05-29
> **swoll1980 said:**
> Yeah your probably right. Those updates are annoying. Why can't they just leave the stuff unpatched for a couple of years or so like Microsoft does. Stupid Ubuntu developers when will they learn?

Actually I've stayed with Windows 2000 all these years, and am in fact using it right this minute because since SP3 its been rock solid and does everything I require.  I got off the MS bus with the product activation introduced in XP.

Some features or "improvements" are clearly negative!

--wally.

---

### Post by Bungo Pony on 2008-05-29
> And why would leaving Pulse Audio out make any difference?

Pulse Audio has been a bit of a pain for me since audio is crucial to me. The problems of software not being compatible with it go away when I fire up Jack Audio Control.

Speaking of audio, it still sounds like crap in Linux. It's a tad on the distorted side, and it bothers me. Windows may suck, but the audio is crystal clear. It's also not the fault of the sound card: I have two in my PC and they both sound like hell.

But I appreciate the constant updates. They give me hope that bugs get fixed. Maybe someday, my sound will be clear.

---

### Post by isaacj87 on 2008-05-29
I think it's funny how initially, people were complaining about the lack of updates. Now, there are too many? :lolflag:

I like seeing the update notification. Nothing wrong with some updates.

---

### Post by FuturePilot on 2008-05-29
> **isaacj87 said:**
> I think it's funny how initially, people were complaining about the lack of updates. Now, there are too many? :lolflag:

I like seeing the update notification. Nothing wrong with some updates.

Agreed. If there were few updates people would be complaining that we have a buggy release and nobody is release updates for it.:roll:

You can't win. :mad:

I see updates as a good thing. They usually fix security holes and provide more stability which is a good thing.

---

### Post by swoll1980 on 2008-05-29
> **wkulecz said:**
> Actually I've stayed with Windows 2000 all these years, and am in fact using it right this minute because since SP3 its been rock solid and does everything I require.  I got off the MS bus with the product activation introduced in XP.

Some features or "improvements" are clearly negative!

--wally.

What's that have to do with unfixed bugs. [This article]("www.fiercecio.com/techwatch/story/microsoft-reveals-14-bugs-win2k-most-risky/2005-10-12") describes 14 unpatched Win2k bugs that are classified as severe 6 years after it's release

---

### Post by Joeb454 on 2008-05-29
If the OP has hardy-backports or hardy-proposed enabled that would count for a fair amount of these updates :)

---

### Post by NJC on 2008-05-29
> **vav said:**
> I mean it's great to have a fully patched system....
Yes.

---

### Post by gameryoshi600 on 2008-05-29
> **swoll1980 said:**
> Yeah your probably right. Those updates are annoying. Why can't they just leave the stuff unpatched for a couple of years or so like Microsoft does. Stupid Ubuntu developers when will they learn?

/sarcasm?
i agree with what you said

---

### Post by Polygon on 2008-05-30
what the heck? 

I can understand if you have a internet cap and you cant physically download all of those updates, but if you can, why does it matter? Every update fixes at least one thing, so might as well just download them all. No piece of software is perfect, even if its a 'lts' release or not.

---

