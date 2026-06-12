---
title: "could a router be deliberatly configured to blow a fuse?"
date: 2010-10-08
forum: The Cafe
---

### Post by fantastic on 2010-10-08
I tried some googling but was unable to find anything on it, so I consult the Community:

> Could/Can a network router be modified, either through software, hardware or "hack", to draw too much power resulting in blowing a fuse to the external power source's fuse? (like trip a breaker in a house)

(*It's for my class... just something that popped in my head and no one could provide a "reasonable" answer*).

---

### Post by CharlesA on 2010-10-08
No.

If you use the wrong power pack, you can fry the router, but that wouldn't cause it to blow a fuse. Normally that would happen if there is too much current being pulled at a specific area.

Also note: I'm leaving this open for the moment, but we don't normally allow schoolwork/homework questions.

---

### Post by lisati on 2010-10-08
Through software? Unlikely...

I'd advise against the exercise: even if it's recognized as a practical joke, is the risk of straining your relationship with the router's owner worth it?

---

### Post by SlugSlug on 2010-10-08
could be shorted out via a 'hack'

---

### Post by zer010 on 2010-10-08
Maybe not blow a fuse, but:
"The [DD-WRT manual]("http://www.informatione.gmxhome.de/DDWRT/Standard/V23final/help/index.html")  suggests that a "safe increase of up to 70 would be suitable for most  users." Anything too much above that and you'd be flirting with  overheating your router and damaging the life of your router (though  I've heard that many people have pushed it up to 100 or above)."
[http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router](http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router)

---

### Post by fantastic on 2010-10-08
Thank you for the responses everyone. It still leaves me wondering though.

> **CharlesA said:**
> Also note: I'm leaving this open for the moment, but we don't normally allow schoolwork/homework questions.

I understand. We were having a discussion in our security class and it was never resolved; no assignment or work associated with it; I was merely trying to "let that go" (so to speak) in my head.

---

### Post by CharlesA on 2010-10-08
Makes sense. :)

I'm kinda curious as to how this all came up. Doing something like that would normally require physical access to the equipment.

---

### Post by zer010 on 2010-10-08
I guess if the goal is to just bring down a router, DD_WRT could be specially configured and packaged to run like a virus in the background under the cover of another app being installed. I'm not a dev or anything so I wouldn't know if this is possible. At best(worse) the router wouldn't be supported and be bricked or they would have hell of a amped router. Again, I have no idea if this would be possible.

---

### Post by juancarlospaco on 2010-10-08
Lastest versions of JunOS blow up everything...   ;)

---

### Post by psusi on 2010-10-08
The most you could do is overload the internal power supply, causing it to shut down.  You aren't going to blow a breaker unless that outlet is already on the verge of overload.

---

### Post by pwnst*r on 2010-10-08
Just set the damn house in fire.  Done.

---

### Post by pricetech on 2010-10-08
Come to think of it, I think my Netgear has a "set house on fire" option.

---

### Post by juancarlospaco on 2010-10-08
Its on the Fire*_wall* tab...
:D

---

### Post by giddyup306 on 2010-10-08
I don't know that much about routers, but I do know a bit about electricity.  

It's pretty much impossible to blow a fuse with a hack.  The number one reason for blown fuses is short to power/ground.  Can't do that with a hack.  Another way to blow the fuse is if you physically put something in the circuit that draws too many amps.  Another thing is if the input voltage is increased.  I'd assume that most routers have some sort of a voltage regulator, but lightning might blow a fuse.  Keep in mind that even if it is overloaded, the engineers designed the circuit to handle that sort of stress.  After all fuses are to prevent fires, not protect the circuit (at least in the automotive industry).

At this point I say it's all just theory...

---

### Post by fantastic on 2010-10-09
> **giddyup306 said:**
> I don't know that much about routers, but I do know a bit about electricity.  

It's pretty much impossible to blow a fuse with a hack.  The number one reason for blown fuses is short to power/ground.  Can't do that with a hack.  Another way to blow the fuse is if you physically put something in the circuit that draws too many amps.  Another thing is if the input voltage is increased.  I'd assume that most routers have some sort of a voltage regulator, but lightning might blow a fuse.  Keep in mind that even if it is overloaded, the engineers designed the circuit to handle that sort of stress.  After all fuses are to prevent fires, not protect the circuit (at least in the automotive industry).

At this point I say it's all just theory...

Ah, wonderful! This sets my mind more at ease.

It had nothing to do with a house. In thinking with security related matters, I posed whether or not a router, or networking routing device, could be "modified" in order to blow a breaker. Depending where these networking devices were physically located and what other possible critical devices (non-network routing devices) shared the same breaker, it would then take other electric "life supporting" dependent equipment down/off-line, thus possibly compromising a system. And then with my further stretching imagination...well, I think you might get the idea how I scramble things in my head.

I actually went and talked with a librarian yesterday whose subject area is electrical, [something], and [something else] engineering and computer science. My searching didn't come up with much.

And now, on this sunny Saturday morning, my mind will be at peace so I can get back to reading other "more interesting" class material, which is what I should have been doing for the last two days.

thanks all for the many responses.

---

### Post by MisterGaribaldi on 2010-10-09
Short out? No, that's an electrical issue.

Best three things you could make happen would be to deliberate screw up the flashing of the router, thereby bricking it; or, you could overclock the router sufficient to overheat it; or, you could crank up the transmitter power so that you overheat it. That's really about it.

---

