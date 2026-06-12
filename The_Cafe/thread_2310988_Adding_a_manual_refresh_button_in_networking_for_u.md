---
title: "Adding a manual refresh button in networking for unity"
date: 2016-01-23
forum: The Cafe
---

### Post by michael337 on 2016-01-23
hello, in this topic, I wanted to say this suggestion because sometimes the list doesn't refresh, so yes, I do know the command:
sudo iw dev wlan0 scan ap-force so, if someone was a bit too lazy to search it up, how about we add the function to unity. great?
Thanks.

---

### Post by cariboo on 2016-01-23
This isn't the place to make suggestions for enhancements to Unity, as developers rarely check out what is going on here. Your best bet would be to make a suggestion on the [ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss") mailing list.

---

### Post by michael337 on 2016-01-23
thx, because I didn't see that section in the first place :D

---

### Post by grahammechanical on 2016-01-23
Surely we can do this by simply un-ticking and then ticking again either Enable Networking or Enable WiFi. Surely, that switches off the WiFi adapter and then switches it back on and in this way forcing a fresh scan for available WiFi networks.

You may also find that the wireless adapter is receptive to wireless access points that are transmitting within range. If I load Ubuntu with my wireless router switched off then Network manager will not be able to automatically connect to that router but it will advise that there are wireless access points available. That proves that a scan has been done.

Then if I switch on the router Network manager will immediately start handshaking with the router to automatically make the connection. That proves that the wireless adapter is receiving a transmission from the router as the router broadcasts its existence.

Regards.

---

### Post by michael337 on 2016-02-03
ok, but that's not the same with my laptop, which I have to completely restart the card, maybe it's because it's an odd card, or because it's named wlp3s0
instead of wlan0 oh, and the network card model is an intel 6200

---

