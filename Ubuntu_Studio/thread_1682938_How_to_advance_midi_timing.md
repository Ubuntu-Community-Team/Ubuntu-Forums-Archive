---
title: "How to advance midi timing"
date: 2011-02-06
forum: Ubuntu Studio
---

### Post by dawiba on 2011-02-06
Hopefully someone help me with this little niggle.

I want to record using Ardour. I need to use QTractor to record my midi as I can't do that yet in Ardour. Therefore I record the midi in QTractor and then send that out of my computer to trigger an external synth. The audio from this then comes in to Ardour, but of course is ever so slightly delayed and is therefore ever so slightly out of sync with audio already in Ardour (or even just the click track). It's easily fixed by manually moving the audio to line up, but this can be slightly tedious.

What I need is a way of advancing the midi timing so this happens automatically. How can I advance the midi timing so that everything is in sync?

Thanks

---

### Post by cchhrriiss121212 on 2011-02-07
There are a few possible solutions on this thread:
[http://linuxmusicians.com/viewtopic.php?f=27&t=2958&p=14753&hilit=midi+timing#p14753](http://linuxmusicians.com/viewtopic.php?f=27&t=2958&p=14753&hilit=midi+timing#p14753)

---

### Post by dawiba on 2011-02-07
Thanks for the link.

Unfortunately, the suggestions there didn't work.

Poking around in QTractor though, I found the following. If I double click on the midi clip I just recorded, then click on properties in the file menu and click on Properties, I get a new window opening up (of course, with the clip properties :)).

Now, if I click on 'Frames' and set that to 128 (the same as in Jack's 'Frames/Period' settings on my computer), it seems to record into Ardour in sync with previously recorded audio. I'll test this further, but later on.

What I'd like is a way to be able to set that value for the whole QTractor project (ideally before recording anything), rather than on a track by track basis.

Any ideas?

---

### Post by AutoStatic on 2011-02-07
> **dawiba said:**
> Now, if I click on 'Frames' and set that to 128 (the same as in Jack's 'Frames/Period' settings on my computer), it seems to record into Ardour in sync with previously recorded audio.hello dawiba, you mean set Format to Frames and then enter '128' in the Start field? Which version of Qtractor?

> **dawiba said:**
> What I'd like is a way to be able to set that value for the whole QTractor project (ideally before recording anything), rather than on a track by track basis.Qtractor can't do that, Ardour can compensate for input latency. Not sure where you can set that up, I'm not an Ardour user.

Best,

Jeremy

---

### Post by dawiba on 2011-02-07
[QUOTE=Autostatic]you mean set Format to Frames and then enter '128' in the Start field?[/QUOTE]

That's the one :). I'm on version 0.4.6, from the repositories.

From what I'd read elsewhere, others have said as well that it should be possible in Ardour. If you right click on a track, there's an 'Alignment' option in the drop down menu, but neither of the options there worked and I can't see anything else in Ardour that would do the trick.

At least I now have two methods for syncing my audio :)

I'm going to use Ardour again tonight, so I'll have another look.

---

### Post by dawiba on 2011-02-08
Well the 'Frames' method didn't work. I tried several times last night, trying a good few different values, but no luck :(

Back to dragging regions around in Ardour

---

### Post by AutoStatic on 2011-02-08
What are your current JACK settings? And it isn't possible to lower the number of frames to say 64? That will lower the incoming latency of your external keyboard to an acceptable level maybe?

Best,

Jeremy

---

### Post by dawiba on 2011-02-08
I had tried lowering the frames to 64 from the current 128, but I started getting xruns so went back to 128 where everything is stable.

Even at lower rates, there will always be some sort of delay, not because of some sort of software problem, but because of the physical fact that the midi signal in QTractor is being triggered at the same time that existing audio is being played in Ardour. Then the audio from the keyboard has to come back into the system and can't help but be slightly behind the playback. In other places, I've been able to use a midi advance function to overcome this and I was hoping it would exist in Linux. It probably does, but I just don't know about it yet :)

Not to worry. It's a nuisance, nothing more than that and I have a workaround.

Thanks again for the help.

---

### Post by Pablo_F on 2011-02-08
> Back to dragging regions around in Ardour

Hi,

Instead of dragging the region you can use the nudge clock, the little display below the secondary clock. You can set it to any number of frames (or ms, etc), then click the left arrow to nudge backwards. If the offset is always the same, you just have to click a button to workaround the issue.

Cheers, Pablo

---

### Post by dawiba on 2011-02-24
I couldn't let it lie, so I'm back again.........:)

As part of trying to find a way round this midi timing niggle, I downloaded and installed Muse from the repositories. In Jack's Connections window, it showed up under the Midi tab, which meant to me that I could connect Muse using Jack Midi. So I started A2JMidi and made the connections. However, it didn't work. For whatever reason, the midi wasn't getting through.

So I tried connecting it differently. Under the Alsa tab, I connected Muse to Midi Through in both directions, then under the Midi tab, I connected Midi Through (available in a2j) to firewire_pcm in both directions. I've attached screenshots to help explain what I mean. This time, the midi got through okay, so I did a quick midi recording, then sent this out to my keyboard and then recorded the audio from that into Ardour.

Now everything sounded in time. The waveform on the screen in Ardour still shows slightly behind the grid, but plays back in time so the delay is being compensated for. When I tried in QTractor, I got the same result - the audio coming from the keyboard now sounded in time :)

I still get a small but noticeable lag connecting straight to Jack midi, but not if I make these extra connections. I have no idea why this should work, but it does (for me anyway).

Thanks to all for trying to help and hopefully this might help someone else :)

Incidentally, I'm sticking with Muse just now because I prefer the way the midi is set up in that program (and I can see a grid :))

dawiba

(still smiling :))

---

