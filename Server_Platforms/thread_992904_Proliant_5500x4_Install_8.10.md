---
title: "Proliant 5500x4 Install 8.10"
date: 2008-11-25
forum: Server Platforms
---

### Post by StumpyXL on 2008-11-25
Well I knew this was going to be a pain since I read up on all of the other threads about how much of a pain in the butt the Smart Controller was.
Here is whats going on...

Used SmartStart 5.50 on the machine, ran diagnostics and the configuration tool to ensure it was setup correctly.  I created a RAID 0 array using the "Guided Full Disk" option.
Worked nicely, installed but then dropped straight to a blue screen with a white area for terminal input on boot.  Stuck there, so I rebooted.  Then it booted correctly but to a black terminal looking screen with no prompt.
I researched more about Intrepid Ibex and found out that someone had created the correct compilied kernel (something to do with the ISA and PCI requesting or something) with the Feisty Fawn OS all on one .iso.  The only thing I don't like it that it is Feisty Fawn. I would like to be current.

I downloaded this last night and will retry today.

If anyone is getting the same issue please feel free to lend a hand of insight.  This is the first time ever installing Linux and the first time ever messing with RAID or controllers.  I am a linux newbie, but an intelligent person so I think it will be a fun learning experience.

---

