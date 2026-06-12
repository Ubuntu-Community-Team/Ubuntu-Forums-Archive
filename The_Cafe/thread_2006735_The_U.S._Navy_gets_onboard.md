---
title: "The U.S. Navy gets onboard"
date: 2012-06-19
forum: The Cafe
---

### Post by fballem on 2012-06-19
If this article is accurate, then this is very good news for Linux: [http://www.techrepublic.com/blog/opensource/linux-grabs-its-single-biggest-win/3690?tag=nl.e011](http://www.techrepublic.com/blog/opensource/linux-grabs-its-single-biggest-win/3690?tag=nl.e011)

---

### Post by jockyburns on 2012-06-19
I hope they pick 12.04LTS, and sincerely hope they don't decide to dual boot. :lolflag::lolflag::lolflag:

---

### Post by wilee-nilee on 2012-06-19
Not new for the US.
[http://www.focus.com/fyi/50-places-linux-running-you-might-not-expect/](http://www.focus.com/fyi/50-places-linux-running-you-might-not-expect/)

---

### Post by |{urse on 2012-06-19
They've been using Solaris and Linux up until now, not news but surely noteworthy. ^^

---

### Post by drawkcab on 2012-06-19
You would hope that, in the wake of Stuxnet and Flame, the gov't would get with the program.  Better late than never.

---

### Post by Bandit on 2012-06-19
> **|{urse said:**
> They've been using Solaris and Linux up until now, not news but surely noteworthy. ^^

Correct. SUDAPS-RT and R-Supply on the server side has been for years, they just use Windows Apt to access it. IIRC all critical systems have been Unix or Linux for years, just none critical like desktop work wasnt.

---

### Post by Dr. C on 2012-06-19
This is to prevent, for example, a Windows virus from causing a US drone patrolling the US Canada border from going of course and crashing into the Microsoft Campus in Redmond WA.

---

### Post by alexfish on 2012-06-19
> **Dr. C said:**
> This is to prevent, for example, a Windows virus from causing a US drone patrolling the US Canada border from going of course and crashing into the Microsoft Campus in Redmond WA.

No

Here

48.8742° N, 2.3470° E

---

### Post by fballem on 2012-06-19
> **Dr. C said:**
> This is to prevent, for example, a Windows virus from causing a US drone patrolling the US Canada border from going of course and crashing into the Microsoft Campus in Redmond WA.

More likely to cross the border and cause a war - similar to the war of 1812, which, depending on what side of the border you are on, was won by the British (Canada wasn't an independent country then) or by the Americans. We did burn the White House.

---

### Post by alexfish on 2012-06-19
Nice , Ubuntu it[IMG]http://www.journeyetc.com/wp-content/uploads/2012/05/Toronto.jpg[/IMG]

---

### Post by Artemis3 on 2012-06-19
Curious, one would think they used something real time such as QNX, well now we know how Iran got one ;)

---

### Post by alexfish on 2012-06-19
> **Artemis3 said:**
> Curious, one would think they used something real time such as QNX, well now we know how Iran got one ;)

It was easy , some one sent this drawing

[IMG]http://diychamber.com/wp-content/uploads/2010/01/DIY-Construct-an-Indoor-Model-Plane-for-Aeromodellers.png[/IMG]

and it was guided by this

[I have my  gyro mounted onto a graphite plate in my chopper and am seeing some  slight drifting. Is there anything I can do about this?]("http://www.futaba-rc.com/faq/faq-gyros.html#q313")

---

### Post by mips on 2012-06-20
I wonder if their ships still run windows. Recall the one incident where a ship was dead in the water due to a WinNT (or system running on it) no longer performed as it should have.

For more DoD stuff scroll down to the bottom of the page [http://www.terrybollinger.com/index.html#dodfoss](http://www.terrybollinger.com/index.html#dodfoss)

---

### Post by Paqman on 2012-06-20
> **mips said:**
> I wonder if their ships still run windows. Recall the one incident where a ship was dead in the water due to a WinNT (or system running on it) no longer performed as it should have.

For more DoD stuff scroll down to the bottom of the page [http://www.terrybollinger.com/index.html#dodfoss](http://www.terrybollinger.com/index.html#dodfoss)

A warship is going to have a lot of different systems on board. Much of it is going to be proprietary SCADA, but some of that (terminals, interfaces, etc) could be running embedded versions of OSes like Windows or Linux.

I would be surprised to find a ship that didn't have a mishmash of several different OSes on board, including some Windows. That's just the way industrial SCADA systems roll.

---

### Post by mips on 2012-06-20
> **Paqman said:**
> A warship is going to have a lot of different systems on board. Much of it is going to be proprietary SCADA, but some of that (terminals, interfaces, etc) could be running embedded versions of OSes like Windows or Linux.

I would be surprised to find a ship that didn't have a mishmash of several different OSes on board, including some Windows. That's just the way industrial SCADA systems roll.

[http://en.wikipedia.org/wiki/USS_Yorktown_(CG-48)#Smart_ship_testbed](http://en.wikipedia.org/wiki/USS_Yorktown_(CG-48)#Smart_ship_testbed)

> From 1996 Yorktown was used as the testbed for the Navy's Smart Ship program. The ship was equipped with a network of 27 dual 200 MHz Pentium Pro-based machines running Windows NT 4.0 communicating over fiber-optic cable with a Pentium Pro-based server. **This network was responsible for running the integrated control center on the bridge, monitoring condition assessment, damage control, machinery control and fuel control, monitoring the engines and navigating the ship.** This system was predicted to save $2.8 million per year by reducing the ship's complement by 10%.

On 21 September 1997, while on maneuvers off the coast of Cape Charles, Virginia, a crew member entered a zero into a database field causing a divide by zero error in the ship's Remote Data Base Manager which brought down all the machines on the network, causing the ship's propulsion system to fail.

Looks like it controlled pretty much the entire ship.

---

### Post by Paqman on 2012-06-20
> **mips said:**
> 
Looks like it controlled pretty much the entire ship.

Well, it looks like a high-level system designed to integrate information from all the other systems. How much of an impediment it was when it went down depends on how much local control was capable with those other systems. When they say "caused the ship's propulsion system to fail" I'd be *very* surprised if the stokers down in the engine room didn't remain in full control, even if it was no longer possible to do so from the bridge.

A warship, like any large system, integrates subsystems from a variety of manufacturers. The system that runs the navigation radar won't be the same as the one controlling a generator or making fresh water. They'll have a protocol they have to speak to communicate to the control systems above them, but the individual systems would be running whatever that manufacturer used (which may or may not be what you'd call an OS).

I would be amazed if full local control wasn't in the spec for a system designed to be damage-tolerant. Warships are designed to keep battling even after having big bites taken out of them. Lots of redundancy in systems, procedures and manning levels. In fact the amount of bodies you have crewing a warship is largely decided not by how many people it actually takes to run it, but by how many it takes to do damage control.

---

### Post by mips on 2012-06-20
> **Paqman said:**
> Well, it looks like a high-level system designed to integrate information from all the other systems. How much of an impediment it was when it went down depends on how much local control was capable with those other systems. When they say "caused the ship's propulsion system to fail" I'd be *very* surprised if the stokers down in the engine room didn't remain in full control, even if it was no longer possible to do so from the bridge.

It was dead in the water for several hours from what I recall. No override from the engine room.

---

### Post by Paqman on 2012-06-20
> **mips said:**
> It was dead in the water for several hours from what I recall. No override from the engine room.

Doesn't mean they didn't stop the ship deliberately while trying to get a handle on the problem.

Seriously, would you design a system for damage-tolerance and not put in any redundancy? Even in non-military systems you design them so that parts can fail and you can just isolate them and still recover your plant/train/ship/whatever back to base.

---

### Post by mips on 2012-06-20
> **Paqman said:**
> Doesn't mean they didn't stop the ship deliberately while trying to get a handle on the problem.

Seriously, would you design a system for damage-tolerance and not put in any redundancy? Even in non-military systems you design them so that parts can fail and you can just isolate them and still recover your plant/train/ship/whatever back to base.

I'm not speculation, merely relaying the facts of the case. I have no vested interest in whether the ship was completely crippled or limping.
[http://gcn.com/Articles/1998/07/13/Software-glitches-leave-Navy-Smart-Ship-dead-in-the-water.aspx](http://gcn.com/Articles/1998/07/13/Software-glitches-leave-Navy-Smart-Ship-dead-in-the-water.aspx)
[http://gcn.com/articles/1998/08/31/smart-ship-inquiry-a-go.aspx](http://gcn.com/articles/1998/08/31/smart-ship-inquiry-a-go.aspx)

---

### Post by Paqman on 2012-06-20
> **mips said:**
> I'm not speculation, merely relaying the facts of the case. I have no vested interest in whether the ship was completely crippled or limping.
[http://gcn.com/Articles/1998/07/13/Software-glitches-leave-Navy-Smart-Ship-dead-in-the-water.aspx](http://gcn.com/Articles/1998/07/13/Software-glitches-leave-Navy-Smart-Ship-dead-in-the-water.aspx)
[http://gcn.com/articles/1998/08/31/smart-ship-inquiry-a-go.aspx](http://gcn.com/articles/1998/08/31/smart-ship-inquiry-a-go.aspx)

Tbh, I'm not completely clear what your point is. It didn't fail because it ran Windows, it failed because of operator error. The whole thing seems largely the opinion of one source ("a self-described whistle-blower"), and what he's saying is at odds with what the Navy said.

Also, from your link:
> Although the Yorktown did not have backup systems, Redman said that future Smart Ships
will have systems redundancy to ensure that ships can continue to operate.


As you would expect. So it seems to have been an isolated case, limited only to their testbed, and caused by something that would affect any OS if the application layer wasn't able to handle the error:

> “So far, it doesn’t seem like it’s an NT issue but a basic programming problem,” said deputy CIO Ron Turner, who is in charge of the inquiry.


I don't really see how it's relevant to anything much.

---

### Post by Willynux on 2012-06-20
French national police also use Ubuntu and saves 2 million €/year.
[http://www.ubuntu.com/products/casestudies/french-national-police-force-saves-2-million-year-ubuntu](http://www.ubuntu.com/products/casestudies/french-national-police-force-saves-2-million-year-ubuntu).

But apparently the Matrix runs on Windows XP :o
[ http://www.collegehumor.com/video/3722767/the-matrix-runs-on-windows]("http://www.collegehumor.com/video/3722767/the-matrix-runs-on-windows")

---

### Post by MoebusNet on 2012-06-24
> **Willynux said:**
> But apparently the Matrix runs on Windows XP :o
[ http://www.collegehumor.com/video/3722767/the-matrix-runs-on-windows]("http://www.collegehumor.com/video/3722767/the-matrix-runs-on-windows")

Neo: "Ubuntu...I'm going to learn Ubuntu?"

That's just too good! :lolflag:

---

