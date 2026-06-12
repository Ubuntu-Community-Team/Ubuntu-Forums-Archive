---
title: "Pangolin Performance (PANP5) sound card type?"
date: 2009-08-24
forum: System76 Support
---

### Post by Cadeyrn on 2009-08-24
Alright, long story short, I've been having an e-mail session with System76's tech support, and I have a problem with my sound card that everyone who dual-boots with Windows and uses the hda-intel driver has. It's that glitch that is fixed by adding "options snd-hda-intel model=x" to /etc/modprobe.d/alsa-base(.conf). But since I'm on the PANP5, I have many choices listed for the Realtek ALC662 sound card, and I haven't the slightest clue as to which one is correct. Unfortunately, Systemm76 Support stopped replying to my e-mails when I asked them what my sound card is. It's been days now. So, here are my choices (already tried the ones in bold to no avail):

**3stack-dig	3-stack (2-channel) with SPDIF**
3stack-6ch	 3-stack (6-channel)
3stack-6ch-dig 3-stack (6-channel) with SPDIF
6stack-dig	 6-stack with SPDIF
**lenovo-101e	 Lenovo laptop**
eeepc-p701	ASUS Eeepc P701
eeepc-ep20	ASUS Eeepc EP20
ecs		ECS/Foxconn mobo
m51va		ASUS M51VA
g71v		ASUS G71V
h13		ASUS H13
g50v		ASUS G50V
asus-mode1	ASUS
asus-mode2	ASUS
asus-mode3	ASUS
asus-mode4	ASUS
asus-mode5	ASUS
asus-mode6	ASUS
**auto		auto-config reading BIOS (default)**

I've been Googling all sorts of keywords for hours now, and I can't find which one it is.

---

### Post by thomasaaron on 2009-08-24
Sorry.

We didn't stop responding to your emails. I went on vacation, but I'm back now.

The Pangolin has Intle Hi-Def Audio integrated into the motherboard. The chipset is ALC662.

You should not have to put anything in the ALSA base file (unless you found a bug that we're not aware of). This chipset is supported out of the box by Ubuntu.

Also, I'd be very careful plugging in model designations. I've seen sound cards get blown that way. (Um... more accurately, I've blown some myself. :confused: )

I'm working my way through 450 emails, so I'll examine the issue more closely when I find the last one you sent.

---

### Post by Cadeyrn on 2009-08-24
Ah, OK. Well thanks for coming back to me. I e-mailed you what I thought was the fix for my sound problems, but now they're back. I'd like to continue these discussions in the forums instead, though, since these topics are already here. In this one, I just need to know the type of ALC662 my computer has so that I can test this fix, because according to a few Google searches, almost everyone who dual-boots with Windows and uses the hda-intel driver in Linux has had this problem. I made [another topic]("http://ubuntuforums.org/showthread.php?t=1248800") for my sound issues in general.

---

### Post by thomasaaron on 2009-08-24
Honestly, this sounds a lot like a hardware issue, particularly since you are having the same issue in Windows.

We need to take it to email. Please fill out this brief online form. It goes straight to my inbox and will provide me with the information necessary to process warranty requests and repair estimates...

[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)

---

