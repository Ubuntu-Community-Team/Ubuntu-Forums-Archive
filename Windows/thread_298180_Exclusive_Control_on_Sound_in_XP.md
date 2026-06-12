---
title: "Exclusive Control on Sound in XP"
date: 2006-11-12
forum: Windows
---

### Post by PacShady on 2006-11-12
Hey all

Running an app on my XP boot (since I have yet to find a Linux alternative, and the program don't run well in WINE because I'm yet to find out how to make sound work on it!), which makes primary use of sound output. But I'm a little concerned with sounds from other programs running in the background that might interfere. Does anyone know of a way to give one particular program EXCLUSIVE rights to sound output, so other sounds can't interfere?

'Shady

---

### Post by ShadowVlican on 2006-11-12
you need to bypass the stupid Kmixer but using kernel streaming or ASIO instead of directsound output

this sends sound data directly to the soundcard, bypassing anything that may alter it, and also stops everything else from accessing the sound card

not sure of your goal, by i use kernel streaming for bit-perfect sound to my receiver (foobar2000)

---

### Post by PacShady on 2006-11-12
OK, I'll have to have a look in WINE settings for that I take it?

'Shady

---

### Post by ShadowVlican on 2006-11-14
i have no idea how to run WINE, so might want to ask your question in the Multimedia section where linux pros can help

i play the devil's advocate here at ubuntuforums, i strictly use windows because it has worked for me and ubuntu hasn't

---

