---
title: "choral music software"
date: 2009-09-22
forum: Ubuntu Studio
---

### Post by elliotn on 2009-09-22
i use to sing choral music at school, i still have the notes stored in my file. now i am wondering if there is a software that i could use to type those notes, and play em digitaly. I mean make what was suppose to be vocally sanged into digital instrumental music

---

### Post by kayosiii on 2009-09-22
It depends on what type of file you have things recorded to...

---

### Post by elliotn on 2009-09-22
i need something that i could use to play the notes with ease

---

### Post by raboofje on 2009-09-23
Generally, you'll use 2 components: 1 application providing a MIDI stream of notes to be played, and 1 application to turn those MIDI notes into sounds.

For the latter, zynaddsubfx is a simple option.

For the former, there are several options: if you want to play the notes 'live', you might try vkeybd.

If you prefer to enter music notation notes, I think most music notation applications prefer a 'play though midi' (rosegarden, noteedit, musescore come to mind).

If you prefer a 'piano roll' representation, you might try a sequencer (rosegarden comes to mind again)

To connect the applications, you might use 'aconnectgui' or the 'ALSA' tab of the 'Connections' window of qjackctl.

---

### Post by Stochastic on 2009-09-23
Try Denemo

---

