---
title: "New Intel N6235 wifi bluetooth adapter has poor sensitivity"
date: 2013-11-06
forum: System76 Support
---

### Post by apdobaj on 2013-11-06
I recently replaced my wifi adapter card (Intel 512AN MMW) with an Intel N6235 in a Darter Ultra because I wanted to add bluetooth functionality. It worked like a champ from the getgo, with one issue. The wifi sensitivity (ie, range) is terrible, much worse than with the original adapter. It's fine when you're right next to the router. The new card is about half as long as the old, and so one plated through-hole that was connected to the motherboard in the old card is floating in the new card. Anybody have any experience with this, or knows of any alternatives (alternative wifi adapters with BT but the same form factor as the original, for example)?

---

### Post by isantop on 2013-11-07
Are you using the card out of a Darter in a different system? I'm guessing it's something funky with the way the antennas are routed. You can try different antennas, but other than that I'm thinking it's something goofy with your specific computer.

---

### Post by apdobaj on 2013-11-07
No, I'm not using the card that came out of the DU. I thought about the antenna cable routing, but since that is hard to control and the existing cables reached the new connectors, I suspect it's more likely due to the antenna or balun specs. The old card conforms to the draft 802.11 n1 standard, not the official n standard, so there may be a difference. I'm not an RF guy and don't really want to put a lot of time into this laptop (although it's been a real workhorse for me, even after dropping it once or twice), so I'll give re-attaching that plated through hole a try. I could put the old card back in and use a USB BT dongle (not ideal because it ties up another USB port). I have an old Belkin F8T003 that doesn't appear to have Linux support (is not detected and can't find a driver), can you recommend one that for sure works?

---

### Post by isantop on 2013-11-07
If the system doesn't have BIOS support for WiFi-Bluetooth Combo cards, that might also cause problems.

---

### Post by apdobaj on 2013-11-12
Can you recommend a USB Bluetooth dongle that is supported by Ubuntu?

---

### Post by isantop on 2013-11-13
I haven't tested with any personally.

---

