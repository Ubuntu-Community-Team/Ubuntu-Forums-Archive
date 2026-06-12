---
title: "Lograthmic (dB) volume scale"
date: 2008-05-23
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2008-05-23
Problem:
1. My computer sound won't go loud enough at a party
2. My computer sound won't go quiet enough for night time use.

Problem 1 can only be solved by getting bigger/better speakers and amplifiers, but that makes problem 2 even worse.

Problem 2 should be fixable.  In essence, when at 1% the volume is too loud to not wake someone sleeping nearby, but muted is silent (obviously).  In cases where 1% is slightly too quiet, the next step up, (2%) is too loud.

Effectively, we need more control near the bottom of the scale, therefore a log scale should be used.  The question is what base log?  Base 1.5 seems a good starting point.

Any comments?

PS. no this isn't because I've got my audio hardware set up wrong - this problem happens with Ubuntu on all PC's - I guess many people work around it by adjusting the volume control on the physical speaker amplifier as well, but it isn't really an ideal situation having to adjust the volume in two places to get the right volume.

---

### Post by qamelian on 2008-05-24
> **CrazyGuy123 said:**
> PS. no this isn't because I've got my audio hardware set up wrong - this problem happens with Ubuntu on all PC's - I guess many people work around it by adjusting the volume control on the physical speaker amplifier as well, but it isn't really an ideal situation having to adjust the volume in two places to get the right volume.
Well, you're wrong about it happening on all PCs. I don't experience this issue on any of four computers that I current have Ubuntu installed on.

---

### Post by CrazyGuy123 on 2008-05-24
how loud is the sound at 1%?

I don't have any sound measuring equipment, but the volume I want is so that voice sound is audible and understandable in a totally silent room (ie. not in a city) at 2 feet from the speaker, but entirely inaudible at 10 feet from the speaker in the same room.  

My problem is this volume is very hard to achieve by adjusting just the onscreen volume with most reasonable PC sound systems (ie. like the bog standard surround sound system that comes with dell PC's).

---

### Post by diafanos on 2008-05-25
You can try this:

1. Open gnome configuration editor (gconf-editor)
2. Navigate to /apps/gnome_settings_daemon
3. Change volume_step 

I set it to 2 (means 2%) and I think it's quite good now

---

### Post by mister_pink on 2008-05-27
What I think you really want is dynamic range reduction. My sound card software had this in XP (it called it night mode). Would be a neat addition to pulseaudio by default - and I'd be surprised if the code doesn't already exist somewhere.

---

### Post by CrazyGuy123 on 2008-05-27
> **mister_pink said:**
> What I think you really want is dynamic range reduction.

Yep that would do as well, although I think that might be something a bit more complex (ie. it does some pretty complex transforms on the audio to make the loud bits quieter and the quiet bits louder).

If dynamic range reduction can be implemented in Ubuntu then great, otherwise a log volume scale would probably do, and I reckon a log scale could be implemented with a patch to just 1 line of code - if only I could find it!

PS. I've already been into audio step size and set it to 1%.

---

### Post by Gina on 2008-05-27
No need for any complicated maths - a simple look up table would suffice.  I've put virtually logarithmic gain controls in signal processing software in the past in that way.

---

### Post by BlueSkyNIS on 2008-05-27
I am also interested in this. This is the proper way of controlling the volume. So, is there a solution for this?

---

