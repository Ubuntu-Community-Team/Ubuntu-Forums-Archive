---
title: "Horizontal Fiber distribution"
date: 2011-06-26
forum: The Cafe
---

### Post by iaculallad on 2011-06-26
This question is directed to members doing/had done telecom jobs:

Here are the given:

1. 24 individual villas built on the same direction and not scattered
2. The last villa is 500 meters away from the MDF room
3. 1 data line and 1 extension line (which will later be paralleled to 4 IP phones using the same extension number inside the villa)

I decided to do fiber cabling (multi-mode) on all villas from MDF to villa telephone room because of copper distance limitation. Is it recommended to purchase a fiber optic switch that support multi-mode fiber for the MDF room and a single-mode-fiber to ethernet converter on all villas? I'm looking for a cost effective solution which can deliver and not be limited because of distance.

ONT (MDF)<------->24 ports MMF Switch<------->MMF-To-Ethernet Adapter (Villa telephone room)

Can someone suggest a good solution for this.

---

### Post by jerrrys on 2011-06-26
i do not have the facts in front of me, but would seem copper is cheaper for such a short distance.

500 meters from the MDF would cover voice and data could be handeled with repeaters.  one repeater station is required every mile.  also giving options on voice like CM_8 or AML to further reduce wire cost.  just a thought

another thought...

if your running a DMS switching center then you have PCM capability

---

### Post by iaculallad on 2011-06-26
If it were me, I'd choose to have the design of using shielded twisted pair cable and let it run on conduits down the manholes and have it repeated at a distance of 80m till I reach the last villa.

Unluckily, it was their choice. They do have copper connection as of the moment (w/c they didn't like) and wanted to upgrade it to fiber solution. All terminations from the MDF room to villa telephone room would be fiber.

Connecting all fiber cables to a central FO switch and terminating it with MMF-to-Ethernet converter would be my solution. Any other suggestions?

Forget copper for now.


ONT<----->Router/Modem<--UTP patch cord--->FO switch<----->MMF-to-Ethernet
 |                                           
 |<--Cat 3 cable--->IP-PABX<--Connected to FO switch->


'One drawback on using repeaters is connection consistency. If one outer switch got busted, then every cable plugged to it would get disconnected'

---

### Post by jerrrys on 2011-06-26
I retired in the 80's.  when fiber was very young.  so not any help here.  goodluck

---

### Post by mips on 2011-06-26
So have you run individual fiber pairs to each villa for a total of 24 pairs terminating in the MDF? Is this work complete? What speed do you need for each villa, 10Mbs, 100Mbs, 1Gbs etc?

What are you aiming to achieve here wrt services for each villa, data, voice, video etc? Do you want to provide a full solution to each villa or just provide it with raw connectivity?

Just trying to get a understanding of your needs.

Edit: Will there be any more villas in the future?

What country are you in?

---

### Post by juancarlospaco on 2011-06-26
What service do you plan to use now and future?, VoIP ?, P2P?

I say Fiber

---

