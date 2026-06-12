---
title: "M-Audio Key Rig 49 doesnt seem to work"
date: 2008-05-07
forum: Ubuntu Studio
---

### Post by sakuramboo on 2008-05-07
This is a rather weird problem that i am having. im using Ubuntu Studio, for starters. when i plug in the keyboard, it gets detected, but dmesg only reports that a new usb device using uhci_hcd has been configured. lsusb lists it as midiman (which was the old name for m-audio). Patchage displays the patch for Key Rig 49, however, it doesnt matter how i connect everything up, i dont get any output from it. i tried patching Key Rig through Timidity and Midi Through and even directly to ZynAddSub or Hydrogen, still a no go.

any thoughts on how to get this keyboard working?

also, an interesting piece of information is, from the searching i did, i found people just saying that everything worked out of the box. yet, it does not for me.

---

### Post by warbread on 2008-05-08
So, when you hook it up to zynadsub, it doesn't respond to key presses at all?  Check to make sure that your keyboard is sending on channel 0.

---

### Post by sakuramboo on 2008-05-08
correct. there is no response to any keys pressed on the keyboard, but the virtual keyboard and even the computer keyboard works fine.

and what do you mean, make sure its going through channel 0? that zynaddsub is set to channel 0? if so, there is no channel 0. if you mean the device, its listed as 0:Key Rig 49 Midi 1 which is going to 0:ZynAddSubFX. and in ZynAddSub's settings, under Midi in Dev, that is set to 0.

EDIT: an update, the volume and pitch wheel both work, just the keys dont. now im starting to think that the keyboard is just broken.

EDIT 2: OMG. i figured it out. i took the keyboard apart and the ribbon that connected the keys to the board was unplugged. i plugged it back up and now everything works.

---

### Post by warbread on 2008-05-08
All standard MIDI controllers send on one of 16 channels and synth devices receive on any one of those same 16. [According to M-Audio's manual]("http://www.m-audio.com/index.php?do=support&tab=manuals&serie_ID=3&PID=7a710eb826376fb2c7d4efa36feb1df3&language=en"), you can set the channel by pressing the "Edit Mode" button and then select channel 0 by hitting key D1 (second white key from the left).  

BUT that doesn't seem to be the problem, as you've connected yer darn ribbon.  Crazy, that.

---

