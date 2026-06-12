---
title: "Is Intel Melting Down?"
date: 2018-01-08
forum: The Cafe
---

### Post by DuckHook on 2018-01-08
In hindsight, what is becoming clearer and clearer is that some of the biggest security flaws going forward will be HW holes and not OS bugs. They are *much* harder to fix, and I'm no longer confident that CPU companies (particularly Intel) give a rat's keester about security. In Intel's case, it either doesn't care, is incompetent, is grossly negligent or all of the above.

The recent Spectre/Meltdown debacle is not the first time that Intel (at least) has been caught with their pants down. The MINIX OS that is baked into many modern Intel CPUs in the form of Intel's Management Engine (ME) has already demonstrated how utterly idiotic Intel has been on security: [http://www.zdnet.com/article/minix-intels-hidden-in-chip-operating-system/](http://www.zdnet.com/article/minix-intels-hidden-in-chip-operating-system/) The shame is that this prior debacle is much more blameworthy, but did not receive anywhere near the press mania that Spectre/Meltdown is getting.

At a minimum, this baked-in secret OS is vulnerable to the AMT bug: [http://www.zdnet.com/article/intel-amt-vulnerability-hits-business-chips-from-2008-onwards/](http://www.zdnet.com/article/intel-amt-vulnerability-hits-business-chips-from-2008-onwards/) Who knows what else it is vulnerable to? It's *baked in* for goodness sake! *It cannot be patched.*

One can almost forgive the Spectre and Meltdown vulnerabilities: they are the result of purely technical flaws arising from the desire to make CPUs faster. However, the ME debacle is driven by a far more pernicious motivation: the attempt to control, modify and restrict CPU functions remotely. Good god. What was Intel thinking? Who in their right mind would be comfortable with the idea that their OS of choice can be bypassed remotely and superseded by an even more primary but secretive OS? If that's possible, what's the point in even booting into an OS of choice in the first place?

This is not even Security 101—it's Security Kindergarten—yet, Intel went ahead and did it anyway. And now, hard in its heels, we have Meltdown, which is almost entirely an Intel problem (Spectre is admittedly almost universal).

I used to be very big on Intel. In the time of Noyce and Moore and Grove, it was an amazing, innovative, technologically awesome company. But no more. They've somehow morphed into one that has less technical security savvy than even some WIFI home automation startups. I'm not that much more confident about AMD either.

As Linus says, maybe it's time to consider ARM?

---

### Post by mastablasta on 2018-01-08
> **DuckHook said:**
> 
I used to be very big on Intel. In the time of Noyce and Moore and Grove, it was an amazing, innovative, technologically awesome company. But no more. They've somehow morphed into one that has less technical security savvy than even some WIFI home automation startups. I'm not that much more confident about AMD either.

As Linus says, maybe it's time to consider ARM?

AMD can't afford such bad press Intel can. their shares simply bounced up...

looks like meltdown is worse. the other one is just a bug.

---

### Post by MoebusNet on 2018-01-08
What I find ironic is that the antique hardware that I use (Dell D800 w/ Pentium-D CPU, Tyan K8E S2865-based server w/ Athlon 64 Dual-Core CPU) is the least likely to be affected by these vulnerabilities but most at risk to lose hardware support in Linux. My 32-bit Pentium-D notebook is in apparently the most imminent peril to the of hardware support. My shiny new 64-bit notebook (2011) is the most likely to be affected by all this.

[Update] After reading some more, it appears that all my CPU's are vulnerable. I'll be glad when we get some patches!

---

### Post by DuckHook on 2018-01-08
> **mastablasta said:**
> …looks like meltdown is worse. the other one is just a bug.

I think the biggest issue is actually ME. But sometimes, I feel like mine is a lone voice in the wilderness. :(

---

### Post by pqwoerituytrueiwoq on 2018-01-08
> **DuckHook said:**
> I think the biggest issue is actually ME. But sometimes, I feel like mine is a lone voice in the wilderness. :(
You are not alone, unless that was your post i saw on phoronix
I do not know enough about the microcode to have a right to say anything about it...

---

### Post by grahammechanical on 2018-01-13
And to think that all these years I have been worried about machines developing Artificial Intelligence when I should have been worried about existing biological machines with limited intelligence of a completely artificial type. :)

Regards

---

### Post by galacticstone on 2018-01-13
> **DuckHook said:**
> In hindsight, what is becoming clearer and clearer is that some of the biggest security flaws going forward will be HW holes and not OS bugs. They are *much* harder to fix, and I'm no longer confident that CPU companies (particularly Intel) give a rat's keester about security. In Intel's case, it either doesn't care, is incompetent, is grossly negligent or all of the above.

The recent Spectre/Meltdown debacle is not the first time that Intel (at least) has been caught with their pants down. The MINIX OS that is baked into many modern Intel CPUs in the form of Intel's Management Engine (ME) has already demonstrated how utterly idiotic Intel has been on security: [http://www.zdnet.com/article/minix-intels-hidden-in-chip-operating-system/](http://www.zdnet.com/article/minix-intels-hidden-in-chip-operating-system/) The shame is that this prior debacle is much more blameworthy, but did not receive anywhere near the press mania that Spectre/Meltdown is getting.

At a minimum, this baked-in secret OS is vulnerable to the AMT bug: [http://www.zdnet.com/article/intel-amt-vulnerability-hits-business-chips-from-2008-onwards/](http://www.zdnet.com/article/intel-amt-vulnerability-hits-business-chips-from-2008-onwards/) Who knows what else it is vulnerable to? It's *baked in* for goodness sake! *It cannot be patched.*

One can almost forgive the Spectre and Meltdown vulnerabilities: they are the result of purely technical flaws arising from the desire to make CPUs faster. However, the ME debacle is driven by a far more pernicious motivation: the attempt to control, modify and restrict CPU functions remotely. Good god. What was Intel thinking? **Who in their right mind would be comfortable with the idea that their OS of choice can be bypassed remotely and superseded by an even more primary but secretive OS?** If that's possible, what's the point in even booting into an OS of choice in the first place?

This is not even Security 101—it's Security Kindergarten—yet, Intel went ahead and did it anyway. And now, hard in its heels, we have Meltdown, which is almost entirely an Intel problem (Spectre is admittedly almost universal).

I used to be very big on Intel. In the time of Noyce and Moore and Grove, it was an amazing, innovative, technologically awesome company. But no more. They've somehow morphed into one that has less technical security savvy than even some WIFI home automation startups. I'm not that much more confident about AMD either.

As Linus says, maybe it's time to consider ARM?

Agree on all points.

Call me conspiratorial, but maybe it was intentional - to provide a backdoor for intelligence agencies. It would have been great for them if these were never discovered and published, but now the cat is out the bag. 

Probably not, but it wouldn't shock me.

---

### Post by DuckHook on 2018-01-14
> **galacticstone said:**
> …Call me conspiratorial, but maybe it was intentional - to provide a backdoor for intelligence agencies. It would have been great for them if these were never discovered and published, but now the cat is out the bag. 

Probably not, but it wouldn't shock me.
I'm sure it wasn't intentional. At least, not intentionally malicious, which is what most mean by "intentional". The ME implementation was so obviously awful that I doubt a three-lettered agency would be so incompetent. They operate under the radar. In fact, some of the biggest concerns have been expressed by three-letter agencies who think this is such a gaping security hole that it disqualifies such chips from government use.

I think it was more a case of some dim bulb at Intel saying: "…hey, wouldn't *this* functionality be cool!" without even pausing to think what security holes such a "functionality" would open up. A lot of Intel's bad decisions are being driven by an attempt to differentiate themselves from their competitors. But unfortunately for them, the days of easy victories are over. The low-hanging performance fruit have all been plucked. I mean, for Pete's sake, I've got a 6-core hyperthreaded CPU in my main box. Total overkill, but I picked it up cheaply enough that I went ahead and bought it. So, where do they go next? Make it 16 cores? How many people could effectively use that? And what cost/benefit advantage would it yield?

So, instead, they chose to add some "newer", "better", "improved formula" marketing-driven shtick to their CPUs that no one really needs or wants. They can then claim that they've got "features" that no one else has. The fact that these "features" come at the cost of an entire stealth operating system hiding underneath the one you choose to install didn't appear to concern anyone at Intel. It's *that* attitude, that lack of even the most basic security competence, that has me worried.

---

### Post by DuckHook on 2018-01-14
> **grahammechanical said:**
> And to think that all these years I have been worried about machines developing Artificial Intelligence when I should have been worried about existing biological machines with limited intelligence of a completely artificial type. :)

Regards
:lolflag:

---

