---
title: "very weird, but sometimes happens"
date: 2008-11-02
forum: The Cafe
---

### Post by jordilin on 2008-11-02
It's second day since I made a clean install of Intrepid Ibex 64bit. While doing some coding and listening to music with Rhythmbox, everything freezed, keyboard and mouse unresponsive, so I could not jump into virtual console to try to kill any process or manually shutdown. I had to just press the restart button and shutdown abruptly. I've been using Ubuntu since nearly day 0, and I've had if I seem to remember only a couple of freezes. It's really annoying and I lost about 10 lines of my coding that were not saved. 

After booting, I went straightaway to check system logs /var/log/messages, but no trace of what the hell could have caused the problem. Although we don't have those blue screens of death, sometimes these freezes are memorable to say the least. I have a couple of proprietary drivers enabled for broadcom and nvidia graphics, all both working like a charm for first time without having to use ndiswrapper or anything, just System->Administration->Hardware drivers. Maybe having these binary blobs installed caused some kind of problem. I don't know, but I will always be a happy Ubuntu user :guitar:

Just wanted to share this experience and know if anyone of you have ever had any complete "freeze".

---

### Post by garwaymatt on 2008-11-02
It could be a hardware issue, overheating due to build up of dust?

---

### Post by Saint Angeles on 2008-11-02
> **garwaymatt said:**
> It could be a hardware issue, overheating due to build up of dust?
this is what happened to me. i was doing an upgrade to intrepid and everything froze. when i went to boot up, nothing worked...

i opened up my case and saw what looked like black mold between the CPU fan and the heat sink. i was like "what the ****!"

i started digging at it and sure enough, it was a super-dense layer of dust... about 1cm thick and compacted like crazy. i couldn't even believe my computer was still working!.

i got as much as i could removed but i'm gonna have to get some of that computer cleaner and blow it all away.

---

### Post by Mr. Picklesworth on 2008-11-02
There is one active bug report on Launchpad for a kernel panic which has recently developed in Intrepid, where (unusually!) most people there seem to be suffering the same problem instead of just the same symptoms.

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/286285)

Do you, by chance, have a newer Intel wireless card with the iwlagn driver? (To find out, right click on Network Manager and go to Connection Information).

---

