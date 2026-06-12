---
title: "Install freezing"
date: 2006-07-10
forum: Server Platforms
---

### Post by BonBonTheJon on 2006-07-10
It freezes at Configuring apt - Scanning the mirror....

Any ideas?

---

### Post by lamego on 2006-07-10
Switch to another console usinf CTRL-ALT-F1, check for the processes with "ps". Kill the process that seems related to the apt operation.
I have used this procedure during some problems on systems without network and I was able to skip the mirrors check.

---

### Post by theachillius on 2006-07-23
> **lamego said:**
> Switch to another console usinf CTRL-ALT-F1, check for the processes with "ps". Kill the process that seems related to the apt operation.
I have used this procedure during some problems on systems without network and I was able to skip the mirrors check.

I would say, do not configure network while installing (Do offline) or you need to wait for long time. It happened to me , sometimes i waited and it went thru. worked for me, hope it works for u too

---

### Post by whiteguysamurai on 2006-07-23
Same thing happened to me, so i unplugged my wireless card.
And now it's freaking out afyter install because i added my card back.

How could someone not see this coming?

And don't they understand, no everyone connects to the internet in staditional ways?!

Stupid!

---

