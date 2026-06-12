---
title: "Mixed Midi Messages (Hydrogen)"
date: 2011-04-07
forum: Ubuntu Studio
---

### Post by swedstal on 2011-04-07
I am trying to use a midi controller (Yamaha DD-55) to trigger drum sounds in Hydrogen. Perhaps I am mistaken, but it does not appear that Hydrogen is capable of assigning different pads (or keys of a keyboard) to sounds. "No worries" I thought, "I'll just figure out what notes the controller is sending to Hydrogen and move the desired sound to that spot."

Unfortunately, I ran into a bit of a glitch. I get the same note (the first 'C' generally a bass drum sound) whether I am playing the bass drum (pedal 1) or the snare (lower left pad). 

I do not believe Yamaha would have designed two different pads to send the same signal and am really baffled by this. Does anyone have any bright ideas?

Note: Using ALSA for the MIDI driver. I do not have an option in the drop-down box to use JACK.

---

### Post by AutoStatic on 2011-04-08
> **swedstal said:**
> I am trying to use a midi controller (Yamaha DD-55) to trigger drum sounds in Hydrogen. Perhaps I am mistaken, but it does not appear that Hydrogen is capable of assigning different pads (or keys of a keyboard) to sounds.That's right, the instruments only listen to fixed MIDI notes starting at 35 and onwards. It tries to follow the General MIDI specs: [http://en.wikipedia.org/wiki/General_MIDI#Percussion](http://en.wikipedia.org/wiki/General_MIDI#Percussion)

> **swedstal said:**
> I do not believe Yamaha would have designed two different pads to send the same signal and am really baffled by this. Does anyone have any bright ideas?Start **aseqdump** from a terminal, connect your DD-55 to aseqdump in the ALSA tab of the QjackCtl Connections window and start hitting some pads. aseqdump should then output what MIDI messages the DD-55 is sending. Could be possible you'll need to reprogram your DD-55. Not sure if that's possible. If not then it's a bit silly this MIDI drumpad doesn't follow the GM specs. 

> **swedstal said:**
> Note: Using ALSA for the MIDI driver. I do not have an option in the drop-down box to use JACK.That's right, Hydrogen doesn't have JACK MIDI support yet.

Best,

Jeremy

---

### Post by swedstal on 2011-04-08
Thank you for your response, Jeremy. I have been helped dozens of times by your posts on these forums. I hope you realize that your expertise is helping many more than just the original poster.

That **aseqdump** was exactly what I was looking for. It turns out that the snare pad is actually sending in 34! In my experience with using a keyboard, anything below 35 triggers a 35, thus the seeming duplication.

I don't have the option of reprogramming the DD-55 so I am wondering if there may be another work-around.

If Hydrogen only plays nicely with Channel 10, I think I am out of luck with that program.

Could Rosegarden help? I should be able to assign sounds from the Hydrogen kits anywhere on the keyboard (or drum in this case), right?

I'll try that.

---

### Post by AutoStatic on 2011-04-09
Hello swedstal, there are solutions to this, one of them is to use the qmidiroute application to reroute incoming MIDI signals. qmidiroute will allow you to raise the number of the incoming notes by one for example and it will allow you to output everything on a specific MIDI channel. And afaik Hydrogen listen on all MIDI channels, not specifically channel 10. And even it would only listen on channel 10 qmidiroute would allow you to output everything on channel 10. I'm not a qmidiroute expert but if you have any questions about it just shoot, I did play around with it a couple of times.

Edit: and yes, anything below 35 and above another number is interpreted as 35 by Hydrogen.

Best,

Jeremy

---

### Post by swedstal on 2011-04-10
Ah...very cool. I would not even have known that anything like this existed. I will see if it works once I get my internet to connect (Here: [http://ubuntuforums.org/showthread.php?t=1714572](http://ubuntuforums.org/showthread.php?t=1714572)
in case anyone has a bright idea) but for now I will mark this as solved!

Thanks again, Jeremy!

---

### Post by AutoStatic on 2011-04-11
You're welcome. Can't help you on the Wireless thing though unless you'd like to do it the way I prefer too, and that's with plain wpa_supplicant. NetworkManager has no business on my music installations, it's prone to cause xruns so I always uninstall it right away.

Best,

Jeremy

---

