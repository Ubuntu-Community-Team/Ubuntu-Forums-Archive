---
title: "Rosegarden ignores dynamic/volume changes"
date: 2012-09-22
forum: Ubuntu Studio
---

### Post by catquarks on 2012-09-22
Hi everyone! I don't really post -- I'm usually able to solve all issues by reading old posts, but this has me really stumped: In Rosegarden I've tried using the notation editor to make dynamic changes, tried using the volume controller within the notation editor, tried selecting everything and doing Adjust --> Interpret (which seems to only work through the volume controller anyway), and there are no dynamic changes whatsoever on playback. I have also tried simply using the MIDI mixer to see if that would do anything, and there are no changes at all in the levels. I'm using ZynAddSubFX for the instruments.

Any idea of what's wrong or what I should do? I appreciate any help!

---

### Post by catquarks on 2012-09-22
Woops, figured out the answer this morning! All I had to do was check the box, under Zyn's "controller" options, that says volume is controlled by something else... So Rosegarden was totally innocent.

Issue solved.

---

