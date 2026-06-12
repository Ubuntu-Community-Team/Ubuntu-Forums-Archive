---
title: "can i put ubuntu_studio as a seshon ples help"
date: 2010-09-04
forum: Ubuntu Studio
---

### Post by thebrainard on 2010-09-04
i have ubuntu as my os on my decktop and i wunt to put ubuntu_studios as a seshon but i don't know how

---

### Post by sgx on 2010-09-04
> **thebrainard said:**
> i have ubuntu as my os on my decktop and i wunt to put ubuntu_studios as a seshon but i don't know how
Hi, look in the Synaptic package manager for meta packages, these
will install groups of software in one go, so the audio and video
parts of ubuntu studio can be separate from other categories.

In a terminal, type

sudo synaptic

and give your password

Make sure you are online, and press the 'Reload'  button on the top
row of the synaptic gui. This downloads lists of the newest updates.

In the lower left of synaptic gui, click top bar labeled 'Sections'
In the new list above the bars, Scroll down to 

Meta Packages (universe)

Click that, and the list of choices to the right includes

ubuntustudio-audio

ubuntustudio-audio-plugins

right click on the ones you want, choose 'Mark for Installation' from the popups,
then click the 'Apply' button on top row of the synaptic gui once all your choices are made.

Cheers :)

---

