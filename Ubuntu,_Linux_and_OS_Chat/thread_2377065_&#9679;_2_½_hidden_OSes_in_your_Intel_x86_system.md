---
title: "&#9679; 2 ½ hidden OSes in your Intel x86 system"
date: 2017-11-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Geoffrey_Arndt on 2017-11-08
Decided to post this as an entre to full write-ups & links here at UbuForums:  (see post #5)

[https://ubuntuforums.org/showthread.php?t=2376957](https://ubuntuforums.org/showthread.php?t=2376957)
..........................................................................................

Summary

&#9679; [U][B]2 ½ hidden OSes in your Intel x86 system
[/B][/U]
&#9679; They have many capabilities

&#9679; They have network stacks and web servers

&#9679; They implement self-modifying code that can persist across power cycles and re-installs

&#9679; They hide, have bugs, and control Linux

&#9679; Exploits have happened

&#9679; Scared yet? We sure are!

---

### Post by TheFu on 2017-11-09
Seems we can disable that other OS, but it hasn't been well tested.

Intel's Secret CPU-On-Chip Management Engine (ME) Runs on MINIX OS
[https://www.bleepingcomputer.com/news/hardware/intels-secret-cpu-on-chip-management-engine-me-runs-on-minix-os/](https://www.bleepingcomputer.com/news/hardware/intels-secret-cpu-on-chip-management-engine-me-runs-on-minix-os/)

---

### Post by ulysses77 on 2017-11-16
Now, is it actually a security threat? If so do tell. 
Or is it just a micro-management system for smaller parts within the computers hardware configuration?

---

### Post by TheFu on 2017-11-16
To begin: [https://securitytracker.com/id/1038385](https://securitytracker.com/id/1038385)
> Impact:   A local user can obtain elevated privileges on the target system.
A remote user can gain elevated privileges on the target system
Severity rating:  	Critical


It runs Minix - which is a full OS. Every full OS has bugs.  That makes the added complexity of this OS a concern.  When was the last time you patched this OS?  I've never patched it or even heard of patches for it. THAT is very concerning, especially since it has a full network stack, runs a webserver and can completely alter the network traffic.

[https://itsfoss.com/fact-intel-minix-case/](https://itsfoss.com/fact-intel-minix-case/)  "direct access to out-of-band network" and "no one outside Intel knows exactly what it CAN do."

Is that a concern? I'd say yes.  I'm not worried about the Intel corporation. They don't care about me or you.  What I am worried about is nation-state actors cracking into these subsystems, since there is no way to know what can be done, across international lines, without a legal warrant or for corporate espionage.

Eventually, these hacks will become public to criminals and they will be used for their purposes. Seems to work on Linux:
[http://manpages.ubuntu.com/manpages/xenial/man1/amttool.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/amttool.1.html)

---

### Post by greyfaux01 on 2017-11-25
> **TheFu said:**
> To begin: [https://securitytracker.com/id/1038385](https://securitytracker.com/id/1038385)


It runs Minix - which is a full OS. Every full OS has bugs.  That makes the added complexity of this OS a concern.  When was the last time you patched this OS?  I've never patched it or even heard of patches for it. THAT is very concerning, especially since it has a full network stack, runs a webserver and can completely alter the network traffic.

[https://itsfoss.com/fact-intel-minix-case/](https://itsfoss.com/fact-intel-minix-case/)  "direct access to out-of-band network" and "no one outside Intel knows exactly what it CAN do."

Is that a concern? I'd say yes.  I'm not worried about the Intel corporation. They don't care about me or you.  What I am worried about is nation-state actors cracking into these subsystems, since there is no way to know what can be done, across international lines, without a legal warrant or for corporate espionage.

Eventually, these hacks will become public to criminals and they will be used for their purposes. Seems to work on Linux:
[http://manpages.ubuntu.com/manpages/xenial/man1/amttool.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/amttool.1.html)


Yea i got a little app called 'thehackernews' for android only, i been reading about this recently, and a few months ago when some other stuff about the intel ME came out.. The news first broke as a security vulnerability, then people started questioning what all it can do... i do find it either ironic, or maybe obvious, that their name is 'intel', because with all the unknowns, we sure know they can gather intel, at the very least for the nationstate that lets them be part of the bi-opoly with amd, who works so closely with microsoft and drm providers, etc etc.. Now i know a lot of people will be all like 'stop being conceded, whats so special that the govt will waste resources to track you, your just being self centered, delusional, paranoid, etc'... but thanks to snowden, we now know that all the stuff people have been saying relating to all this sort of govt hacking its own citizens, mass surveillance w/out warrants, etc, is all 100%, beyond our wildest imagination..

I mean hell, wannacry is our fault, and its kind of like the chickens coming home to roost. we create these exploits, hell sometimes we help create the vulnerabilities themselves with the vendors, were the ones that unleashed stuxnet on the world, its no surprise that real criminals are watching US, and learning how to 'do it right'.. lead by example, and thats exactly what we've done.. all i can hope is more and more people become knowledgable about technology and realize that it can always be a double edged sword, and whatever 'they' can do with tech to take our rights, we can use the same tech to defend them..

Heres an example of the 'secure enclave' thats used to verify DRM on our devices, used in an opposite manner, to verify who we are speaking with (beta testing by signal, the creators of this method)
[https://nakedsecurity.sophos.com/2017/09/29/signal-apps-address-book-security-could-upset-governments/](https://nakedsecurity.sophos.com/2017/09/29/signal-apps-address-book-security-could-upset-governments/)

Bonus link, threatpost is great
[https://threatpost.com/signal-testing-new-private-contact-discovery-service/128167/](https://threatpost.com/signal-testing-new-private-contact-discovery-service/128167/)

Granted, that does imply that we trust the vendors (intel/arm/amd) cant see inside the enclave either, which of course is debatable, but of course signal is trying their best to account for this as well..

Also, great avatar FU, im pretty much a linux noob even though i been using it exclusively  since 8.10, but i never knew i could get the man pages like that.. i just tried that, and it worked..

---

### Post by DuckHook on 2017-11-25
A highly useful and informative discussion.

Just a friendly reminder that security is a welcome topic; "company/country/three-letter-agency is bad/evil/spying-on-us" bashing is not, so please don't let the thread drift there. It would be a shame to close such a useful thread, so such posts will be promptly jailed.

---

### Post by greyfaux01 on 2017-11-25
Sorry. Thank you. But yea re-reading my post, i can see where i was on the verge of drifting to an entirely different topic, so thanks. Still trying to learn the ways of the force here.

---

### Post by mastablasta on 2017-11-27
from all articles i read i am still not sure - is this something found on all intel system or only latest ones? also, what about AMD? Do they have something similar?

if i understood correctly this kind of thing became possible with UEFI, which can do a lot more than BIOS. on the other hand i am not sure why normal users would need to tinker around in BIOS or touch it anyway. to me it was always a part of system i would nearly never touch. and the only reason i did touch it was when i installed new hardware. most people do not even know it exists.

---

### Post by DuckHook on 2017-11-27
> **mastablasta said:**
> …most people do not even know it exists.
True enough. I think the main concern is not people inadvertently messing with it, or accidentally misconfiguring things, but bad actors exploiting it. Like most general users, I'm not really that familiar with UEFI. I just understand that it is much more complex and versatile than the old PC BIOS. Like you, I rarely enter the UEFI setup screen once the computer has been initially set up.

The issue that TheFu links to is also a bit different than UEFI. If I read things correctly, Intel is adding chips to their MOBOs that encapsulate within them whole OSes. These may not even address UEFI and could possibly be used to bypass UEFI-level controls altogether. I have to agree with him that it has dangerous potential.

I'm intrigued by the open firmware projects, [libreboot.org]("https://libreboot.org") and [www.coreboot.org](www.coreboot.org), but they don't seem to have gained much traction. I'm only aware of very preliminary development of actual usable computers based on such firmware. And besides, if my reading of those links is accurate, a MOBO chip with a built-in OS might be able to bypass any open firmware anyways, thus rendering their open status moot. Intel's decision to add these chips seems almost like having a parasite living within our hardware. Even if the intentions are harmless, the unintended consequences may not be.

---

### Post by mastablasta on 2017-11-27
but does the intel add it on their own motherboard or other manufacturers as well?

For example as i understand on my old motherboard all the chips are actually from nvidia, then it's just a plug/socket for the intel CPU. motherboard is then made by AsRock who added the nvidia chips, which run the motherboard and connect to Intel. 

i would have to check but i think that maybe even on the other AMD CPU board the board chips might be from nvidia.

as i understand BIOS ran completely separate from network, while UEFI could be connected to network. this is where the actual danger could come from. previously a rootkit was "needed" to do something like that, but now an unpatched OS already has the capability to connect to network and give full access to machine.

another thing that is not clear is if this was done on purpose (to gain user access) or if this was just a bad design (for example - that firmware should only be accessible via keyboard or on-site and should have the encrypted option).

---

### Post by DuckHook on 2017-11-28
I'm so far behind on modern HW, it's embarrassing.

My understanding of MOBO design is based on the old 8086/286/386 days when all sorts of critical functions were offloaded onto separate chips and good MOBO design was hyper-critical to computing efficiency. So Intel looked after the CPU, but someone else's separate controller looked after the BIOS, RAM bus, I/O bus, etc. These days, so many things are integrated into the CPU itself, including entire audio and video subsystems, that I have no idea what's left outside anymore. So what are these MOBO chips that are problematic? What is it that they actually do?

**EDIT**

I should learn to read more carefully. The functionality in question is Intel's ME (Management Engine) and *it's already embedded in Intel's CPU.* :!: In other words, it's not those further external MOBO chips from Intel or nVidia that expose us; we've already been exposed for the last ten years in every Intel CPU that's been sold during that time. That includes almost every box I own. And if it's integrated into the CPU itself, then it has nothing to do with UEFI either—it will be active no matter what we do—so long as we're powered on. And, according to the article, it is so interwoven into the bootup process that it cannot be extricated from the CPU.

One commentator mentions that, yes, AMD do this too—though it's important to note that this is a post from a commentator and not part of the original article.

Apparently, there is a firmware bit that can be flipped to disable ME as soon as the bootup process has completed. The article describing the preceding dangers and linking to how to disable ME is [here]("https://www.bleepingcomputer.com/news/hardware/researchers-find-a-way-to-disable-much-hated-intel-me-component-courtesy-of-the-nsa/"). The article warns that attempts to invoke the disablement bit can brick your computer. Oh joy.

That article also links to episodes in which Intel ME has already been exploited for nefarious purposes.

You asked if:> **mastablasta said:**
> this was done on purpose (to gain user access) or if this was just a bad design (for example - that firmware should only be accessible via keyboard or on-site and should have the encrypted option).
I think the answer is "both". It *was* done on purpose—to offer additional functionality. It seemed like a good idea to some Intel dim bulb to allow sysadmins to remotely manage systems at the CPU level. However, the law of unintended consequences inevitably reared its ugly head, and whatever powerful tool that can be used to manage can also be exploited by villains to prosecute their bad intent.

How can an organization as large as Intel make such an elementary security blunder?

---

### Post by mastablasta on 2017-11-29
> **DuckHook said:**
> 
How can an organisation as large as Intel make such an elementary security blunder?

well there was a video on i think BBC of a thief waving a box in front of house window, then using its collected date to unlock the car and start it. all in a couple of seconds. the car was Mercedes. at least with the key they need to put in a but of effort... also how and why they would design the key to emit the unlock frequency, without any button on it being pressed is beyond my understanding.

IoT is all the rage in my company as well.  connected appliances. never mind they don't really know why they would need to have the devices (in their current state of development) connected (a solution in search of a problem) i can't help but wonder how they handled security. i would bet that despite assurances it is not that good. also it was made utilising various Microsoft solutions.

---

### Post by DuckHook on 2017-11-29
I am by no means making excuses for them, but Mercedes specializes in cars. I sort of expect them to be awful at IT. Intel on the other hand&#8230;

As for IoT, I approach these new gadgets with high trepidation. The latest WPA2 exploit (Krack) does nothing to lessen my worries.

---

### Post by greyfaux01 on 2017-11-29
> **DuckHook said:**
>  [here]("https://www.bleepingcomputer.com/news/hardware/researchers-find-a-way-to-disable-much-hated-intel-me-component-courtesy-of-the-nsa/").

Wow. just wow.

amazing that ME is there, active, yet so undocumented, and allows one to gain full access even on a computer thats powered off, as long as theres an ethernet cord and power cord plugged in. Even more amazing that theres a convenient, yet completely hidden and undocumented disabling switch.

---

