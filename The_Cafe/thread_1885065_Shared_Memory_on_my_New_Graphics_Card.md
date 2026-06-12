---
title: "Shared Memory on my New Graphics Card"
date: 2011-11-22
forum: The Cafe
---

### Post by thig1002 on 2011-11-22
So, I ran into something interesting yesterday when installing my new graphics card. A strange anomaly, I guess you could say:
 
I recently installed an ATI Radeon 4350 (Overclocked, but I haven't really noticed a difference. Nor is this important). The card has a 512mb of dedicated memory, and as much as I understand shouldn't use any more than that. I have have 4gb of ram installed, and Yes all 4gb are being used by the system.

Now here's where things get interesting. I checked the properties of my new hardware and it states that it has 512mb of dedicated memory, **BUT **also another 1gb of shared memory. Like I stated before, I have 4gb of ram installed and all reserved for the system. It is not sharing that memory.

Now here's what I think: The motherboard has NVidia integrated graphics with 1gb of dedicated memory (See where I'm going with this?). My hypothesis is somehow the new graphics card is accessing the unused memory of the old integrated graphics.

Honestly, I have no clue what's going on, but I found it an interesting thing to discuss. Any feedback would be nice, even if only to say, "You're an idiot."

---

### Post by 3Miro on 2011-11-22
I don't thin the ATI can touch the RAM from the Nvidia. Assuming the information from that the tool for reading memory is accurate, what is probably happening is that the 1GB of shared memory is not reserved, but allocated dynamically. That is, the card is using its own 512MB and it will use more only if it is needed (i.e. if you are doing something intensive like gaming). In the mean time, the system can take all of the 4GB if it needs, hence you get the 4GB reading.

---

### Post by BrokenKingpin on 2011-11-22
> **3Miro said:**
> I don't thin the ATI can touch the RAM from the Nvidia. Assuming the information from that the tool for reading memory is accurate, what is probably happening is that the 1GB of shared memory is not reserved, but allocated dynamically. That is, the card is using its own 512MB and it will use more only if it is needed (i.e. if you are doing something intensive like gaming). In the mean time, the system can take all of the 4GB if it needs, hence you get the 4GB reading.
I would also guess that this is the case.

The system is probably smart enough to know when it should or shouldn't be dipping into the system RAM, so I wouldn't worry about it too much.

---

### Post by mips on 2011-11-23
> **thig1002 said:**
> 
Now here's what I think: The motherboard has NVidia integrated graphics with 1gb of dedicated memory (See where I'm going with this?). **My hypothesis is somehow the new graphics card is accessing the unused memory of the old integrated graphics.**

No, that won't happen.

What could be happening is that both GPUs are active in which case the nVidia one would continue to use it's shared gfx. On my MB I have the options to 1) Turn off the onboard gpu, 2) enable it when no other gpu is present or 3) enable it regardless.

---

### Post by thig1002 on 2011-11-24
After further evaluation, it is only sharing from the Ram when needed (Like when playing Team Fortress, or what ev's). Which obviously makes more sense, I just didn't check the Ram during a game before.

Thanks all for the feed back.

---

