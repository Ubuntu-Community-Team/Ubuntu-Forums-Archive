---
title: "Classic example of linux desktop fragmentation"
date: 2009-12-02
forum: The Cafe
---

### Post by Regenweald on 2009-12-02
[http://www.phoronix.com/scan.php?page=news_item&px=Nzc2NA](http://www.phoronix.com/scan.php?page=news_item&px=Nzc2NA)

For bumpy upgrades, I wonder who will get the blame ? upstream or distro ?

---

### Post by Crunchy the Headcrab on 2009-12-02
Oh joy.  :neutral:

---

### Post by Regenweald on 2009-12-02
> **Crunchy the Headcrab said:**
> Oh joy.  :neutral:

off topic: forgot to thank you for the advice on the logo, been playing with some ideas :D Also, you seem like you know what you are talking about so you should definitely check out Inkscape, may be a good tool to add to your collection.

On topic: progress is progress, but with so many individual projects  comprising the desktop, moving forward is sometimes rough....;)

---

### Post by NoaHall on 2009-12-02
Oh. I thought the switch from HAL to device-kit was obvious(I thought? Maybe not).

---

### Post by Keyper7 on 2009-12-02
What this has to do with fragmentation?

It's about replacing, not forking.

---

### Post by SunnyRabbiera on 2009-12-02
More like a re name really.

---

### Post by Regenweald on 2009-12-02
> **Keyper7 said:**
> What this has to do with fragmentation?


One project makes a decision. cascades through entire desktop environment. your software must be changed to reference correct naming structure or be faced with looking for a component that does not exist. 
These changes happen on a modular level, each does their own thing, no real 'umbrella' view exists for the desktop. It's then the distro developers who have to scramble to bring it all together.

---

### Post by SunnyRabbiera on 2009-12-02
But HAL was showing signs of falling apart anyhow, Devicekit was supposed to fill its spot
The change of name from device kit to UDisks probably refers to its merger with udev

---

### Post by Regenweald on 2009-12-02
> **SunnyRabbiera said:**
> But HAL was showing signs of falling apart anyhow, Devicekit was supposed to fill its spot
The change of name from device kit to UDisks probably refers to its merger with udev
And a bunch of programmers now have to make their software look for u-something and not device-something.

All I am saying is that with every individual project decision, comes a ripple throughout the desktop that can sometimes be problematic.

---

### Post by Hwæt on 2009-12-02
> **Regenweald said:**
> All I am saying is that with every individual project decision, comes a ripple throughout the desktop that can sometimes be problematic.

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/3/35/Kleiner_Fuchs_%28Nymphalis_urticae%29.jpg/800px-Kleiner_Fuchs_%28Nymphalis_urticae%29.jpg[/IMG]

I hope everyone knows why I posted that in relation to that quote.

---

### Post by ZankerH on 2009-12-02
Fragmentation and diversity is a good thing. Upstream shouldn't be a slave to those who use their work.

---

### Post by SunnyRabbiera on 2009-12-02
> **Regenweald said:**
> And a bunch of programmers now have to make their software look for u-something and not device-something.

All I am saying is that with every individual project decision, comes a ripple throughout the desktop that can sometimes be problematic.

Yes but by the time of the next major distro flow it would be bypassed anyhow.
Most distros are moving away from HAL anyhow, its slowly becoming phased out.
By the time HAL is completely dropped the name change wont be an issue.

---

### Post by Keyper7 on 2009-12-03
> **Regenweald said:**
> One project makes a decision. cascades through entire desktop environment. your software must be changed to reference correct naming structure or be faced with looking for a component that does not exist. 
These changes happen on a modular level, each does their own thing, no real 'umbrella' view exists for the desktop. It's then the distro developers who have to scramble to bring it all together.

I don't want to be picky, but what you describe is an example of the *consequences* of fragmentation, not an example of fragmentation itself.

Anyway, about the renaming: not breaking compatibility is good and all, but the current names do not make sense and are misleading. Legacy names kept only for compatibility purposes would eventually rot. It's better to do this now, when udev is the center of attentions due to HAL deprecation, than later.

---

### Post by Excedio on 2009-12-03
> **Hwæt said:**
> 
 
[Image moved to attachment]
 
I hope everyone knows why I posted that in relation to that quote.
 
Nice...butterfly effect.

---

### Post by 3rdalbum on 2009-12-03
It's not fragmentation. It's a transitional period for this part of the Linux system. Name changes and API changes happen in proprietary software too, of course.

The name change is a good thing, actually. It means that, until programs are updated to use the new API, they can still continue to call Devicekit and use its old API; and then when they are ready they can use udevices' new API. If the name stayed the same, they would be trying to call the old API and instead getting the new one, which would be highly confusing and would probably break things.

---

### Post by Skripka on 2009-12-03
> **SunnyRabbiera said:**
> But HAL was showing signs of falling apart anyhow, Devicekit was supposed to fill its spot


And both are gigantic pains in the but to get working right.

---

### Post by Skripka on 2009-12-03
> **Excedio said:**
> Nice...butterfly effect.

Mis-usage of the concept.  

The Butterfly Effect refers to computational chaos from seemingly minute data errors, not actual "ripples" of anything that actually change anything in the real world.

The idea being, you can have a butterfly dancing near your doppler weather radar antenna, and your forecast your computer generates will say there will be a hurricane next week in Australia....all due to a tiny butterfly mucking up your measurements.  The butterfly does NOT actually CAUSE a hurricane.  Not in this theory anyway.

---

### Post by Xbehave on 2009-12-03
> **Skripka said:**
> And both are gigantic pains in the but to get working right.
Yeah, because interacting with hardware directly was soo much nicer?
Hal is a great improvment on user programs having to deal with drivers.
Devkit was an improvement on that, by spliting it up into device specific abstractions.
This name change represents a serious redesign that is even better because it removes the need for always running daemons.

But hey if you don't like it don't use it, nobody is forcing you to use hal, but i guess you knew that it's jsut you prefer to moan on forums rather than to think.

edit: /me cries because skripa won't see the message :'(... LOL well my point still stands HAL is a damn good piece of technology, devkit is better, udisk/etc is even better.

Regarding fragmentation all this shows is that fragmentation is a good thing as it allowed fedora to be reckless and develope this tech without a need for backwards compatibility while users of more stable distros like debian/RHEL/etc will never notice the change.

---

### Post by Skripka on 2009-12-03
@XBehave:

[QUOTE=UbuntuForums]
 9 Minutes Ago 
Remove user from ignore list
Xbehave 
This message is hidden because Xbehave is on your ignore list.
[/QUOTE]

I told you a few weeks ago you were on it.  And you still are.  Have a nice day.

---

### Post by Hwæt on 2009-12-03
> **Skripka said:**
> Mis-usage of the concept.  

The Butterfly Effect refers to computational chaos from seemingly minute data errors, not actual "ripples" of anything that actually change anything in the real world.

Wait, how is it a mis-usage of the concept? The concept in popular speech refers to when one tiny change causes a bunch of others, right? I'm confused, as the OP was talking about one project changing its name, and a ton of others having to issue massive changes because of this small change, correct?

---

