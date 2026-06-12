---
title: "Controlling Filter Q and Cutoff using Rosegarden's Matrix Editor"
date: 2011-01-04
forum: Ubuntu Studio
---

### Post by GraysonPeddie on 2011-01-04
Hi. I am working in my music in Rosegarden. I have a ensemble instrument that I have just made and I want to control the instrument with filter cutoff and filter resonance (Q).

I've looked in Views -> Rulers -> Add Control Rulers and there does not seem to have a selection to specify controller numbers. This is in the Matrix Editor.

Are there any workarounds for adding a controller ruler for both filter cutoff and filter Q?

I have compiled Rosegarden from the SVN trunk, if that helps.

---

### Post by GraysonPeddie on 2011-01-05
Because there are about 90+ views for my thread, I thought I'd make a new post with my resolution.

In Rosegarden, you'll need to go to Studio -> Manage MIDI Devices, and click in Controllers for your MIDI device ([ZynAddSubFX](http://zynaddsubfx.sourceforge.net/doc_3.html) in my case). There, you will see something like this:

[[IMG]http://img823.imageshack.us/img823/1672/rgcontrollerlist.png[/IMG]](http://img823.imageshack.us/i/rgcontrollerlist.png/)

I hope I can be of assistance for those who are searching for information.

---

### Post by Pablo_F on 2011-01-05
> I hope I can be of assistance for those who are searching for information.

Yes! Thank you!

---

### Post by GraysonPeddie on 2011-01-06
No problem.

Now, if only I could draw a line in the controller ruler to make it transition from one value to another very smoothly; without it, it'll take me about 3 minutes to construct something that does not look like a straight line like in:

[[IMG]http://img337.imageshack.us/img337/4570/rgcontrollerruler.th.png[/IMG]](http://img337.imageshack.us/i/rgcontrollerruler.png/)

I checked the [OpenOctave Project](http://www.openoctave.org/), but there does not seem to be any development in this project (I tried it a couple of months ago, but the cursor tools (Select, Insert, Move, Erase, etc.) have all been assigned to a shortcut of F2. I do like the pure MIDI sequencer, as it all does away with audio and notation editing, which I rarely use, but I like Rosegarden's workflow. I'm thinking of waiting for [Ardour 3](http://www.ardour.org/a3_features) (with MIDI editing and [exporting to surround sound format](http://www.ardour.org/a3_features_export), which would be nice to have) to come out, but it's a long wait.

---

