---
title: "What kind of RAM should I use for a home fileserver?"
date: 2009-06-17
forum: Server Platforms
---

### Post by learningcurb on 2009-06-17
Hi, I'm thinking about building a home fileserver that will be on 24/7, or maybe 12-18 hours a day if I set up automatic startup and shutdown. 

Anyway, after reading some horrible stories about mysterious bitrot and data corruption, I think ECC RAM is a good idea. I'm thinking about installing about 4GB of memory, but I'm a bit confused about the whole issue of buffered versus fully buffered versus unbuffered RAM as it relates to running a fileserver.  I'm shopping around for an inexpensive Dell or HP tower server that will support ECC RAM, but I'm unclear whether I should be looking for systems that support buffered or fully buffered RAM. FMDIMMs and buffered memory purportedly increase reliability, but is having ECC enough?  Or is buffered memory only really for people are running really big servers that require way more than 4-8GB of RAM?

---

### Post by evermooingcow on 2009-06-17
Not all ECC RAM is FB but I believe all FB RAM naturally support EC.

FB RAM is only designed to go into (as far as I know) Intel 5000 series and 5400 series chipset dual LGA771 boards. FB allows such platforms to support (address) more RAM than they are normally capable of supporting from a parallel bus by providing a parallel to serial translation of the memory bus. You only need FB if you need lots of RAM. They run hot too because of the overhead.

FYI..

I have been running 24/7 home servers/download boxes for a while now (~8years?) and I have never had a problem with data corruption using normal RAM.

---

### Post by binary10 on 2009-06-17
I have a NSLU2 Linksys with 32MB running ubuntu acting as a dhcpd,dns,mediatomb (streaming to the PS3) server.
No memory corruption on them..

Sure it's not fast but it does what I want and it's low powered.

No matter how much memory you in your system.. just make sure you have a decent backup strategy.

---

### Post by windependence on 2009-06-17
Use what you have laying around. I have been in this business since before PCs, and I have machines running for YEARS on the same non-ECC RAM without incident. All that may be true in theory, but IMHO it's bull$hit in practice.

Also, I see so many people going nuts trying to turn off their servers, put them to sleep, etc. My advice? Leave them on, 24/7. The components expand and contract as they heat up and cool down. If you constantly shut down, boards will crack, components soldered to the board will break loose, etc. I have worked in many many large corporate environments, and have tried it both ways. ON is better. Worrying about power is gonna drive you nuts. If you have a "green" problem, then I can't help you, but if you want to save power in a practical way, virtualization is a much better choice than power management on the box.

-Tim

---

### Post by TwiceOver on 2009-06-17
For a home server, leave it on 24/7.  Use whatever memory is compatible with the board and is cheap.  You don't need to waste the money on super duper over clocking ram or ECC dimms.

Trust me, you could go overkill all day long but will you really get a return on that investment?  At home, probably not.

---

### Post by ghen on 2009-06-17
Just to add my 2c. ECC memory really only starts to be useful when you're servicing 100+ clients. In a home environment you won't come anywhere near taxing the system to the point where you need error correcting memory. 

There's no such thing as data loss due to memory, its just if there's errors it has to be run through memory again. You won't notice this speed difference as running everything through ECC takes just as long as re-running the errors as they happen.

---

### Post by grantemsley on 2009-06-17
I agree with the majority here.  ECC RAM isn't worth it unless you are doing super high end stuff.  Sure it's *possible* that some cosmic rays might rain down and corrupt a bit.  Or maybe you live near a nuclear plant and want the system to perform well during a meltdown.  But otherwise, invest the money you save by getting normal RAM into a solid power supply.

---

