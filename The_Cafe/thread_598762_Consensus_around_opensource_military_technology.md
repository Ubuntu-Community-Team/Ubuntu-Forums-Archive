---
title: "Consensus around opensource military technology"
date: 2007-10-31
forum: The Cafe
---

### Post by r0b0h0b0 on 2007-10-31
It sounds as if it may qualify as an oxymoron on a number of levels, but the concept intrigues me. What's your feeling about OS military software? Would it make sense, if not also lots of money? Would Linux the People be ok with such stuff?

---

### Post by magordoom on 2007-10-31
ok im sorry this is really pointless.
and why did you put it in the help area?

---

### Post by tubasoldier on 2007-10-31
Yeah, wrong category first off.

The United States military already uses it for many applications. Although not openly, and not on desktops.

---

### Post by hikaricore on 2007-10-31
Moved..

---

### Post by r0b0h0b0 on 2007-10-31
> **tubasoldier said:**
> Yeah, wrong category first off.

The United States military already uses it for many applications. Although not openly, and not on desktops.

OK, yeah, wrong category. Sorry about that. This one is evidently quite more suitable.

I know many military forces world wide use OS graphics api's for training and simulation stuff, or freeware GIS, routing and management stuff for planning and forecasting, but I'm talking about weapons systems/targeting/AI level. It's different from the other stuff because those are libraries and api's integrated into military systems. What I'm referring to is the actual front line packages...where the bullets fly and the soldiers die.

---

### Post by Frak on 2007-10-31
When it comes to military technology, I see the value in keeping it closed to everybody.

---

### Post by Nano Geek on 2007-10-31
> **Frak said:**
> When it comes to military technology, I see the value in keeping it closed to everybody.Same here. It wouldn't be good if average joe could download the software used for guided missiles.

---

### Post by r0b0h0b0 on 2007-10-31
> **asjdfwejqrfjcvm msz34rq33 said:**
> Same here. It wouldn't be good if average joe could download the software used for guided missiles.

But what I am saying is that average joe **uploads** the software used for guided missiles. If such things are provided, surely there'll be enormous competition for this resource?

---

### Post by Frak on 2007-10-31
In economy, closed source software is unethical, OSS is the way to go.

But in military situations, I'd be P***ed if the US just started sharing its source codes with other nations.

---

### Post by sr20ve on 2007-10-31
offensive material

---

### Post by bruce89 on 2007-10-31
A Free Software project added a non-military clause to their licence, but I can't remember which one.

---

### Post by Frak on 2007-10-31
> **bruce89 said:**
> A Free Software project added a non-military clause to their licence, but I can't remember which one.
Well, the Apple license doesn't allow you to use iTunes to create Weapons of Mass Destruction. ;)

---

### Post by davahmet on 2007-11-01
Several years ago in my own military service (USAF), I worked on an advanced radar and signals analysis system.  The central computer for this equipment was an i386-based system running Red Hat Linux and variety of specialized, open-source applications.  I was part of the design team that made this decision based on the need for high reliability, low-cost (primarily maintenance cost) and the flexibility necessary to future-proof potential mission changes.

Yes, a concern was raised about adversarial access to the source code.  Based on the consensus across all branches of the US military service, the greater danger was adversarial access to data.  I remember specifically addressing this issue in conference approximately 10 years ago.  In this conference I made the assertion, "With open source, your source code is open and your data remains relatively closed.  With a proprietary solution, your source code is closed but your data is subject to compromise."

I have since retired from service, but I believe these OSS-systems are still very much in use, not only in the US military but in other nations as well.

---

### Post by popch on 2007-11-01
> **asjdfwejqrfjcvm msz34rq33 said:**
> It wouldn't be good if average joe could download the software used for guided missiles.

I would find it much worse if average joe (or, indeed,  *anyone*) would have guided missiles to use the software with.

As far as I can see, there are two problems with open source weapon systems:

[LIST]
[*]'competitors' would be able to produce systems which are 'just as good' or better. Depending on the license applied, they could not even be forced to disclose the source of their enhancements. (This is meant ironically).

[*]'Customers' (people or organisations being shot at with those weapons) could - by inspecting the source code - find means of outfoxing or otherwise reducing the effect of weapon systems controlled by that software.
[/LIST]

---

### Post by FG123 on 2007-11-01
So long as the missles are running virus/spyware checkers, I'm cool.

---

### Post by 23meg on 2007-11-01
Many countries who are buying advanced weapons, especially aircraft with sophisticated avionics, have started insisting on getting the source code of the software that runs on the avionics. Simple reason: just like you can't be sure that a proprietary OS vendor isn't doing something nasty with their code you're running on your home computer, there's no guarantee that the country selling you the weapon can't put a trojan horse in its software that they may use against you if you ever turn hostile.

As an example, I don't know if this is an urban myth or has some truth in it (and it's hard to know), but F-35s are said to have software that allow them to be completely disabled by other F-35s, pretty much in the same fashion as a computer shutting down another one via SSH. And whether it's urban myth or not is irrelevant; theoretically, it's entirely possible. 

Imagine paying millions of dollars for a fighter plane, and when time comes to utilize it, being shut down remotely and unable to even take off, or unable to strike targets that the manufacturer doesn't want you to. Nobody wants that, hence the insistence on access to source code.

---

### Post by az on 2007-11-01
The first freedom defined by "Software Freedom' is the right to use the software for any purpose.  A non-military clause makes the software non-free.

As for revealing the source code, we all know that "security by obscurity" doesn't work.  On the other hand, the only time that revealing the source will compromise security is when keeping the code a secret the only way you have of securing your program - which is pretty weak.

It's okay to let others know how the lock is made if you simply cannot pick it.

---

### Post by kragen on 2007-11-01
Surely if open source software is meant to be more secure than closed source software on the desktop, it should also be more secure in other applications too?

The only danger I can think of would be someone looking at the source code and reverse engineering the capabilities of the machine.

Besides, I wasnt aware they they had to release the source code to anyone and everyone? And I also wasnt aware they had to release the source code at all - if I create a script in python, I dont *have* to publish the source code if I'm going to use it privately do I?

---

### Post by davahmet on 2007-11-01
> **kragen said:**
> Surely if open source software is meant to be more secure than closed source software on the desktop, it should also be more secure in other applications too?

Absolutely.  Most security problems in software come from flaws in the code which leave vulnerabilities for exploit.  Open source makes vulnerability detection and patching much easier.  Closed code is designed by intent to hinder user maintenance, creating a dependency on the vendor to supply patches.  This would fine if you could trust the vendor to put your best interests over their own.

> The only danger I can think of would be someone looking at the source code and reverse engineering the capabilities of the machine.

Possible, but they would also have to replicate the hardware and the data.  Even with a closed system, this happens.

> Besides, I wasnt aware they they had to release the source code to anyone and everyone? And I also wasnt aware they had to release the source code at all - if I create a script in python, I dont *have* to publish the source code if I'm going to use it privately do I?

Again, you are correct.  The concept behind code sharing in open source is that you must make the code available to the user base.  That is, if you intend to distribute the application worldwide, you must also make available the source code worldwide.  If your distribution is strictly in-house, you may also limit source-code access to in-house.

---

### Post by Frak on 2007-11-01
> **kragen said:**
> Surely if open source software is meant to be more secure than closed source software on the desktop, it should also be more secure in other applications too?

The only danger I can think of would be someone looking at the source code and reverse engineering the capabilities of the machine.

Besides, I wasnt aware they they had to release the source code to anyone and everyone? And I also wasnt aware they had to release the source code at all - if I create a script in python, I dont *have* to publish the source code if I'm going to use it privately do I?
There is really no reason to license software for private use. You are not going to break your own restrictions, since you are the holder.

---

