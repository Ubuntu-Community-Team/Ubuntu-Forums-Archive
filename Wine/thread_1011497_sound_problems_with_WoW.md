---
title: "sound problems with WoW"
date: 2008-12-14
forum: Wine
---

### Post by themusicalduck on 2008-12-14
I have a weird problem with my sound while playing WoW. The sound will work fine for about 15 minutes or longer, but eventually it'll cut out. Although this sometimes happens much sooner. It also seems to happen sooner if I use other sound programs, like amarok, or if I use another sound using program in wine at the same time it'll often cut out very quick or straight away. The only way to fix it is to restart the game.

I am using alsa, and would rather not use oss if I can avoid it so that I can use multiple sound programs at once. Otherwise the sound is setup as ubuntu default.

I use an m-audio audiophile 192 sound card.

Ubuntu version 1.10, wine version 1.1.5

---

### Post by themusicalduck on 2008-12-15
bump

---

### Post by kochecc2 on 2009-05-04
I too am having this issue. It appears to happen more in instances and reloading the UI doesn't fix it. I need to actually exit WoW and relaunch it.

---

### Post by BigGuyWhoKills on 2011-01-28
This just started for me about 2 weeks ago, about a year and a half after the last post.  I figured that my onboard sound was going out.

I am using Wine 1.3.12 and WoW version 4.0.3a.  I can temporarily fix this by enabling or disabling "Use Hardware" in the WoW "Sound & Voice" options.  No other audio in Linux has problems.

---

### Post by cwwilson721 on 2011-01-29
That's because Ubuntu uses Pulse, and wine does not, therefore, on occasion, wine will "fall off the map". Ubuntu packages wine without Pulseaudio support. However, wine CAN use pulse.

There are a few remedies:
[LIST]
[*]Make sure wine is running as an XP session
[*]the sound driver for wine is ONLY alsa, NOT oss
[*]Do a Google search for "wine ppa pulse", and install that version. If you go this route, only have Pulseaudio as your sound driver in wine.
[/LIST]Either way, do the first 2. The last is optional, but useful

---

### Post by gufide on 2011-01-30
check the option window and the option optimized and choose your fine resolution. this simple this worked with me

---

### Post by biotob on 2011-06-08
Can't wait to try this when i get home! It's been bugging me ever since I got my Tascam to work...I need my music while playing lol.

---

### Post by biotob on 2011-06-09
> **cwwilson721 said:**
> That's because Ubuntu uses Pulse, and wine does not, therefore, on occasion, wine will "fall off the map". Ubuntu packages wine without Pulseaudio support. However, wine CAN use pulse.

There are a few remedies:
[LIST]
[*]Make sure wine is running as an XP session
[*]the sound driver for wine is ONLY alsa, NOT oss
[*]Do a Google search for "wine ppa pulse", and install that version. If you go this route, only have Pulseaudio as your sound driver in wine.
[/LIST]
Either way, do the first 2. The last is optional, but useful

Well I tried this yesterday with no luck. I searched and searched for a rep with Wine+Pulse and found one. When  installed it I ran winecfg and made sure that i had pulse selected as my audio drivers. it seemed to have worked for the first 30 min, then i just crapped out again. 

Anyone else have this issue?

---

### Post by Dragonkin on 2011-09-18
Had the same problem now with 11.04, what seems to fix it was that in winecfg under sound settings i chose OSS instead of Alsa (only OSS, nothing more).
Before that i tried to add

options snd-hda-intel model=hp-dv5 enable_msi=1

Didnt help though, but then i removed the enable_msi part, dunno if that fixed it or the OSS setting

---

