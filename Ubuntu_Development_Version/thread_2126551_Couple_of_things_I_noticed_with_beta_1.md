---
title: "Couple of things I noticed with beta 1"
date: 2013-03-17
forum: Ubuntu Development Version
---

### Post by carl4926 on 2013-03-17
wifi seems slower to load at boot and after suspend (just compared to 12.10) - it works fine, just takes it's merry time.

On 2 machines I have had trouble installing at the wifi section - it wont go past it
Had to add boot options acpi=off noapic, then it worked

Once installed it's fine, smooth and sweet

---

### Post by deri on 2013-03-17
I haven't noticed anything...better to make the developers aware of those issues you said.

---

### Post by carl4926 on 2013-03-17
> **deri said:**
> I haven't noticed anything...better to make the developers aware of those issues you said.

Some more testing needed first.
Did a couple of installs tonight, but without the power connected and it went ok. I'll check in the AM with the power connected and see if it's related.

The wireless does take longer to connect though..

---

### Post by carl4926 on 2013-03-18
So I was able to test this again and had positive results, with it booting OK this time.

The wireless is still slow making the connection though.

---

### Post by ft_ on 2013-03-18
You could maybe post the model of your wifi card...

---

### Post by carl4926 on 2013-03-18
```
[COLOR=#333333]Broadcom BCM4312 802.11b/g LP-PHY driver: b43-pci-bridge[/COLOR]
```

Tried both b43 and wl
Makes no difference
Works flawless in 12.10 and other distros

---

### Post by dino99 on 2013-03-18
have you tried wicd ?

---

### Post by carl4926 on 2013-03-18
> **dino99 said:**
> have you tried wicd ?

No
Never had the need before

I can live with it, rather than go off at a tangent from the Unity defaults.
It was just an observation and was wondering if it was isolated to me?

---

### Post by zika on 2013-03-18
> **carl4926 said:**
> No
Never had the need before

I can live with it, **rather than go off at a tangent from the Unity defaults.**
It was just an observation and was wondering if it was isolated to me?
That's a spirit... I wish I had that attitude... Life would be much easier... ;)
I was like that in my first Win-days...
Seriously, there should be stronger restrictions (at least) for us in U+1 on how much are we allowed to stray from the stuff we are &#8222;testing&#8220;...

---

### Post by carl4926 on 2013-03-18
> **zika said:**
> That's a spirit... I wish I had that attitude... Life would be much easier... ;)
I was like that in my first Win-days...
Seriously, there should be stronger restrictions (at least) for us in U+1 on how much are we allowed to stray from the stuff we are „testing“...

I'm not intelligent enough to understand this comment.

But when testing a release it's generally better to work with the OS as it is.

I do though appreciate the suggestion to try something else.

My attitude is a willing one, whatever @zika was suggesting

---

### Post by zika on 2013-03-18
> **carl4926 said:**
> I'm not intelligent enough to understand this comment.

But when testing a release it's generally better to work with the OS as it is.

I do though appreciate the suggestion to try something else.

My attitude is a willing one, whatever @zika was suggesting
I was "suggesting" just that. Even though I do not do that and I do regret that, we all should test OS "as it is"... So, I do appreciate that You're doing it just the way it should be done... Nothing less and nothing more than that... Sorry if I was (and if I am) ambiguous, that was not my intention at all... I certainly did not even thought of trying to cause Your sarcasm...

---

### Post by carl4926 on 2013-03-18
> **zika said:**
> I was "suggesting" just that. Even though I do not do that and I do regret that, we all should test OS "as it is"... So, I do appreciate that You're doing it just the way it should be done... Nothing less and nothing more than that... Sorry if I was (and if I am) ambiguous, that was not my intention at all... I certainly did not even thought of trying to cause Your sarcasm...

No worries
I'm thick skinned anyway.  :D

So far though 13.04 is really nice.
I'm trying to crash it, but it ain't going down.

---

### Post by Seb71 on 2013-03-18
> **carl4926 said:**
> So far though 13.04 is really nice.
I'm trying to crash it, but it ain't going down.

Try to copy a few GB over LAN and report back.

---

### Post by carl4926 on 2013-03-18
> **Seb71 said:**
> Try to copy a few GB over LAN and report back.

It's running now
Seems fine

Report back soon

---

### Post by carl4926 on 2013-03-18
> **Seb71 said:**
> Try to copy a few GB over LAN and report back.

Success :D

To be clear 3GB folder containing files and folders of images .png/.jpg

From Laptop running (wireless) 13.04 beta 1 > Nautilus SSH > Box running openSUSE

---

### Post by Seb71 on 2013-03-18
In mine case, the transfer freezes after a few hundred MB at most (the data was copied from another PC to 13.04 PC in my case - maybe that maters). And [I am not the only one with this problem]("http://ubuntuforums.org/showthread.php?t=2120952").

---

