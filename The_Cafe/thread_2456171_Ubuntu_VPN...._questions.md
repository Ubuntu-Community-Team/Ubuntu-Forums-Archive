---
title: "Ubuntu VPN.... questions"
date: 2021-01-05
forum: The Cafe
---

### Post by Old Jimma on 2021-01-05
Hello Ubuntu Community:

I've been using a commercial VPN service with my ubutu machines. It seems to work well. But, I'm well aware of all the back doors commercial vendors have written into communication code for meet-up video softwre.... just as 1 example. And, of course, there is the telecommunications act and treaties that "share data" between countries.

Within the context of all of this, I must wonder whether my commercial VPN service is really bullet proof.

I've known for a long time that I could configure VPN for my ubuntu machines. I'd be very grateful for comment from the community on its true ability to provide secure communication. Comparisons are welcome, but  encouraged not to name commercial VPN servides by name. Let's keep this clean.

Thank you,

Old Jimma from the Old Country
Since 6.04

---

### Post by crip720 on 2021-01-06
Think the only bullet proof system is not being on the internet.  Best you can hope for from any VPN is bullet resistance, hopefully better than cardboard.  Quite a few VPN lists that will give some points to consider when choosing a VPN for your requirements.

---

### Post by ActionParsnip on 2021-01-06
All I can suggest is read reviews and critiques. See how they operate and any breaches and so forth.

---

### Post by slickymaster on 2021-01-06
Not a support request.

Thread moved to **The Cafe**.

---

### Post by TheFu on 2021-01-06
A security is about risk management appropriate for the information and data involved.
If you don't have state secrets to protect, it doesn't make sense to setup state-level security either.
If you only worry about a 12 yr old hacking you, then there are some common steps for security, but mostly it includes "don't do stupid things."

Different VPN providers are located in different jurisdictions, so how they must behave will determine on where they are and where you are, not just how trustworthy the provider claims to be.  For example, we know that all VPN providers located in China and Russia must pre-provide their keys to the state.  If you live in Uruguay and work in a liquor store, does that matter to you at all?

In Squidbilly-land where I live, my private details have already been leaked/stolen by the Chinese govt when they hacked in the OPM in 2013.  For multiple other reasons, the Russians had a file on my family, so regardless of my current job, I'm always concerned about them AND my own country having too free access to what I consider personal data.  In my country, the govt has been refused access to a few VPN provider's data in court multiple times, because they were able to claim they didn't have any.  That's a pretty big thing for my confidence in that VPN provider even though they are located in my country.  They fought the govt AND WON!  Govt denied.  Would that work in your country?  It won't in many countries, since the govt runs the telecom.

But none of this is helpful if your ISP and VPN setup are leaking data. Again, the actual data to be protected matters.  If you are looking at porn (pick any sort you like) and that is legal in your country, does it really matter if the state knows this?  Does your position there mean that someone could blackmail you because you like animal porn or would that be normal enough that it didn't matter? What do you have to lose personally?  If you are 20 yrs old and not living at home, probably not too much to lose. If you are at the height of a career, peek earning time, with lots and lots of family ties, each with important contacts, then what you have to lose is much greater.  Teens don't usually understand that their actions greatly impact their parent's careers. I didn't.

Someone will certainly suggest using TOR at some point.  TOR is fine, slow, and the tracing of TOR users generally comes back to getting those users to install some self-reporting software OR using account profiling to link TOR uses to non-TOR uses.  Something around 30% of all TOR nodes are run by different govt security departments - US, Russian, China, Israeli, and a bunch more. That means they either see the last or first data in and out of the TOR network.

<tinfoil hat>
Being aware of these things is something everyone striving to have privacy online need to learn.
In general, it comes down to lots of tiny SecOPS things that are needed.  There are a number of stories on the internet about SecOPS failures. These are interesting reads for people like me.  CIA teams kidnapping people in Italy who were caught because one of the CIA guys wanted hotel reward points and used his own cell phone on the OP. Italian police traced that cell phone.  Similar, simple, things like that are going to break computer network security too.

**If you want bullet proof**, build a bunker, no networking, not wifi, no Bluetooth, in a shielded Faraday box, put your computer in there and only visit it after you've verified nobody is watching using every available means - IR, RF, telescopes, and huge IR/RF-defeating tarps protecting the entryway and access to the tarp area so satellites don't see it.  Don't bring any electronic device into the bunker. No digital watch, no music player, no cell phone of any sort.  Perhaps should ride a bicycle there, certainly don't bring a car or truck or motorcycle. Really, you should have left your cell phone 20 miles away from the bunker, powered on, with an external answer-auto-responder. Use only LUKS encryption for any flash storage taken in and out of the bunker with well-controlled, long, random, unlock codes that use 2FA.  Not exactly realistic, but a smartphone sitting within 1m of a wired keyboard can determine what you are typing.  Wireless keyboard? Just hand over the transcript. If you care about security, don't use wireless anything (I can't say why, sorry).  Vans with special equipment sitting within a 100m of a room can listen in to both sound and RF happening inside that room if there isn't any shielding.  Fax machines, copiers and some printers can be listening devices with a modified firmware. I've seen a demo of this from an IT security "Red Team".

What are you trying to protect and from whom are you trying to protect it?  What sort of a target are you?  How crazy do you want to be for bulletproof security?

Sometimes it is just better to do a little more than everyone else + not be stupid. That is often sufficient to handle security against non-state actors.

</tinfoil hat>

---

