---
title: "bundled 64-bit OS's on the horizon?"
date: 2008-08-01
forum: The Cafe
---

### Post by insane_alien on 2008-08-01
i was helping a friend shop for a new PC(she won't let me build her one for some reason) and i noticed that a lot of the prebuilts were being sold with 4GB of RAM(though strangely only a 32-bit OS).

now, they can't reasonably expect to push out PC's with more than that and still have a 32-bit OS. even the more technically inept users would notice the mismatch and if not then PC magazines would be up in arms about it, i hope.

so, does that mean we will finally see commercial and non-free applications like skype and flash ported to native 64-bit?

---

### Post by Canis familiaris on 2008-08-01
It is possible to utilize upto 64GB RAM in a 32bit OS using PAE.
Not that they will use it. :)
I am just making clear 32-bit OS *can* access over 3.5GB RAM.

> **insane_alien said:**
> 
so, does that mean we will finally see commercial and non-free applications like skype and flash ported to native 64-bit?
Flash does run in 64bit Ubuntu. And 64bit Vista has also 32bit IE7. So it'll probably run FLash too.

---

### Post by insane_alien on 2008-08-01
i know it can, but the way they are implemented just now they can't.

there are also inefficiencies of doing that as well as the memory must be dealt with in multibyte chunks.

i guess i'm just a bit frustrated that we could be there now. all hardware sold is 64-bit and your going to have to maintain legacy 32-bit for a while anyway. might as well get the users of it early.

---

### Post by forger on 2008-08-01
> **insane_alien said:**
> so, does that mean we will finally see commercial and non-free applications like skype and flash ported to native 64-bit?

Who knows, but I'd love to have a native 3.x skype in linux and to be built for 64-bit :)
You could ask for people to sign up petitions at [www.petitiononline.com](www.petitiononline.com) and forward the results to the administration of the programs such as skype.com

---

### Post by Paqman on 2008-08-01
Is Vista still limited by the 4GB barrier though?

---

### Post by insane_alien on 2008-08-01
the 32-bit one is. i have 32-bit vista on a 4GB laptop and it only recognises 3.2GB (although thats only if you do a bit of digging to find the real value. the value it presents to the average user says 4GB.

more lies.

---

### Post by forger on 2008-08-01
[http://msdn.microsoft.com/en-us/library/aa366778.aspx](http://msdn.microsoft.com/en-us/library/aa366778.aspx)

> Physical Memory Limits: Windows Vista

The following table specifies the limits on physical memory for Windows Vista.
Version - Limit in 32-bit Windows - Limit in 64-bit Windows
Windows Vista Ultimate - 4 GB - 128 GB
Windows Vista Enterprise - 4 GB - 128 GB
Windows Vista Business - 4 GB - 128 GB
Windows Vista Home Premium - 4 GB - 16 GB
Windows Vista Home Basic - 4 GB - 8 GB
Windows Vista Starter - 4 GB - Not applicable

---

### Post by Superkoop on 2008-08-01
> **forger said:**
> [http://msdn.microsoft.com/en-us/library/aa366778.aspx](http://msdn.microsoft.com/en-us/library/aa366778.aspx)
> 
Physical Memory Limits: Windows Vista

The following table specifies the limits on physical memory for Windows Vista.
Version - Limit in 32-bit Windows - Limit in 64-bit Windows
Windows Vista Ultimate - 4 GB - 128 GB
Windows Vista Enterprise - 4 GB - 128 GB
Windows Vista Business - 4 GB - 128 GB
Windows Vista Home Premium - 4 GB - 16 GB
Windows Vista Home Basic - 4 GB - 8 GB
Windows Vista Starter - 4 GB - Not applicable 

What the heck? They are limiting the amount of usable memory? 64bit can use up to 16 exabytes (although I believe that most of todays consumer processors place a limit on the bit width which doesn't allow as much memory anyhow)...but still, placing that low of a limit is just wrong.

---

### Post by insane_alien on 2008-08-01
hmm, the artificial limits on 64-bit vista (home basic and premium) could possibly be surpassed within their lifetimes. that could cause issues. then again i suppose its only an update away from being raised i think. infact, my numbercruncher has 8GB so its already at home basics limit. and that was months ago i built that. 16GB is probably feasible now. 128GB is still high end server range though.

> What the heck? They are limiting the amount of usable memory? 64bit can use up to 16 exabytes (although I believe that most of todays consumer processors place a limit on the bit width which doesn't allow as much memory anyhow)...but still, placing that low of a limit is just wrong.

yes they are. linux limits it as well IIRC although this limit is more than your box could possibly hold. this can be fixed by recompiling the kernel. but as not even servers come close to this limit (and if they follow moores law they won't even get close for another couple of decades.)
i think linux limits it the same as the processors.

---

### Post by FuturePilot on 2008-08-01
Well I would think so.

We recently bought a computer form HP and if you opted for 4 GB of RAM they would only let you have a 64bit OS. So I think 64bit as standard is not too far off which would hopefully push Adobe and others to produce 64bit versions.

---

### Post by insane_alien on 2008-08-01
i have never seen a 64-bit OS offered with 4GB of RAM here (scotland) only macs are sold like that, but unfortunately they are not a majority.

---

### Post by Daveski on 2008-08-01
> **insane_alien said:**
> ...
so, does that mean we will finally see commercial and non-free applications like skype and flash ported to native 64-bit?

Well, ESR thinks that the end of 2008 is the deadline:

[http://ubuntuforums.org/showthread.php?t=380534](http://ubuntuforums.org/showthread.php?t=380534)

---

### Post by insane_alien on 2008-08-02
its a soft deadline but i would say that the end of the year could roughly be the time of the transition although its likely to be blurry.

the most common RAM configuration just now seems to be 2GB but 3GB is coming up in a lot of the midranges. 4GB as standard should be cropping up at the end of the year and then they're going to have to switch soon after that. i'd say its more likely to be spring 2009. perhaps summer.

but then, the software companies will have to port everything and that might slow it down somewhat, maybe even to the end of 2009.

---

### Post by SunnyRabbiera on 2008-08-02
I doubt 32 bit as a standard is going anywhere, even with all these super core processors and junk the 32 bit era will go on for a long time sorry to say.
Until Microsoft takes full interest in 64 only no one will go to it as they own so much of the market.
Just because the technology is there it doesnt mean they will use it wisely.

---

### Post by insane_alien on 2008-08-02
oh i don't expect it do die off anytime soon. i just expect there to be a surge in the commercial 64-bit software along with more computers being sold with a 64-bit OS. 

i expect that low power computers like the eeepc and their successors will remain 32-bit until even those have more than 4GB of RAM.

---

