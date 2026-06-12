---
title: "Jack was working with Ardour..."
date: 2010-10-27
forum: Ubuntu Studio
---

### Post by ansionnachcliste on 2010-10-27
Hey guys,

I had Jack working with Ardour earlier but I disconnected every by an accident in the "Connect" area of Jack.
 
When I click "Connect", there are no inputs or outputs in the Audio tab and I could have sworn there was earlier. There are only input and output selections in the ALSA tab but that doesn't seem to have much effect.

I do have ardour running too to see if it can pick it up but can only do it in the ALSA tab.

Also when I run jack it says:

p, li { white-space: pre-wrap; } [COLOR=#999999]16:18:36.745 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]16:18:36.950 Statistics reset.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66CC99]16:18:36.999 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]16:18:37.299 ALSA connection change.[/COLOR]

I might have disabled something but I'm not sure.

Cheers.

---

### Post by ansionnachcliste on 2010-10-27
I got it working but not sure how. I connected the Ardour inputs to its ouputs like I did before in Jack but just seemed to work now.

I think it tries to annoy me sometimes.

A good old restart probably sorted it too.

;)

---

### Post by ThaKidChillz on 2010-10-29
hey, i was having the same problem but i somehow got it to work. now my usb mic works in ardour but it only shows movement on the left bar in the mixer. the right one wont do anything...i have the track set to stereo and everything...any suggestions??

---

### Post by Pablo_F on 2010-10-29
Hi, 

In Jack Control's connection window, audio tab, make sure that the capture source (system:capture_1 probably) is connected to both track inputs.

You can check/do these connections in ardour too, in the Mixer window or through the track/bus inspector.

Anyway, if the source is mono (I suppose this is the case with your mic) you don't need a stereo track to get sound from both speakers. I suggest you use a mono track.

Cheers! Pablo

---

