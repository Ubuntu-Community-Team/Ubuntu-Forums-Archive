---
title: "Midi recording using external keyboard"
date: 2010-02-07
forum: Ubuntu Studio
---

### Post by eagle136 on 2010-02-07
Several hours of tweaking and searching and still no midi events being accepted by Rosegarden.  I have a Soundblaster Live!  I can play back MIDI files fine (through QSynth) but any attempt to record MIDI files - i.e. NO EVENTs being registered.

I'm v happy doing this in Windows (which has just become unusable - good excuse to force the family into Linux!) but I need an idiot's guide to getting this to work in Linux (I have Ubuntu Studio) and have a deadline approaching .... aaargh!

Is there such a thing - I'm getting v confused with stuff I'm reading.

---

### Post by trulan on 2010-02-08
I've had much better success recording midi in Qtractor than in Rosegarden.  If Qsynth is working for you, I'd recommend adding QTractor to the mix.

Wait - are you getting sound out if you hook your midi keyboard directly to Qsynth, or aren't you getting any midi from your keyboard into the computer at all?

---

### Post by eagle136 on 2010-02-08
Hi,
Thanks - I'll take a look QTractor as well.  Is it stable?  I see it's in alpha release at the moment.

I can get MIDI files to play using sounds on QSynth (not trying to output to external sound sources) but am unable to get any events from the MIDI keyboard to the S/W.  

The correct MIDI modules are loaded.  

I'm prob. just getting confused with the names of the MIDI devices ......

---

### Post by trulan on 2010-02-08
I don't know if QTractor is more or less stable than something like Rosegarden or Muse, it's just that I was able to make some sense of QTractor in a matter of minutes, and success in Rosegarden and Muse is still eluding me.

But about your midi issues:  How are you connecting your keyboard to your computer?  With a USB-midi cable?

Have you tried a virtual midi keyboard?  They can be very helpful for testing things, and for figuring out the connection scheme.

Lastly, how are you making Jack connections?  Jack Control's 'connect' tab?  Patchage?  Maybe a screenshot or two would be helpful.  Thanks!

---

### Post by raboofje on 2010-02-08
> **eagle136 said:**
> no midi events being accepted by Rosegarden.

I'd start by firing up kmidimon and connecting your keyboard to that. Do the events get trough there?

Then connect your keyboard to rosegarden in the same way in record there I guess...

---

### Post by eagle136 on 2010-02-08
Hi, thanks for the reply.  MIDI keyboard is connected to a breakout box connected to a Soundblaster Live! card.  Rosegarden can see the kybd, it is listed as an input device but no data is being received ..... why is this so difficult ...?  I'd almost prefer to get my Windows box up and running .... :-(

---

### Post by eagle136 on 2010-02-08
Using kmidimon - no events - kybd is listed. but no event received when I play on the kybd.  Perhaps teh breakout box is not getting the messages thru ... somewhere I had  MIDI cable to plug into the joystickport of the soundcard ....

---

### Post by trulan on 2010-02-08
This is more of a question than a suggestion, but does a joystick port midi connection need a special module loaded?  I know I had a bit of work to get a joystick port joystick working.  Everything is so geared toward USB hookups these days.

I do remember years ago when I was using a joystick port midi hookup, I did have to have the correct switch settings on my keyboard ,to select whichi midi interface to use.  (My keyboard has an internal 'breakout box').

Another option might be getting a USB-midi cable.  There are a number of inexpensive cables available.

---

### Post by eagle136 on 2010-02-09
I don't know.  I can't find the cable but the ports were working with Windows.  I have tried another MIDI keyboard via USB - same result i.e. nothing.  I know I'm prob.  approaching this from A Windows perspective:  I open the sequencer, the keyboard is picked up, I play, it records.  Not with Ubuntu Studio.  I really need an idiot's guide, cos that's how I'm feeling right now.  How do I set up the system to receive input from an external MIDI keyboard.  It can't be that tricky ... can it?

---

### Post by AutoStatic on 2010-02-09
Hello eagle136, maybe this post could be helpful: [http://ubuntuforums.org/showpost.php?p=8540958&postcount=18](http://ubuntuforums.org/showpost.php?p=8540958&postcount=18)

---

### Post by mango42 on 2010-02-09
Hi **eagle136**

I've never used the items you're trying to connect, but I would endorse **trulan**'s suggestion of trying Qtractor, as it does have an immediacy to it.

First off though, if you're running UbuntuStudio, there will be a program on your Apps menu for **JACK Control**. Start that up first, start a virtual synth, then click the **Connect** button; go to the MIDI & ALSA tabs and note whether your MIDI interface is recognised. If it is then connect your interface output (left pane) to the virtual synth's input. Then go to the Audio tab and connect VS to audio out. Et voila?

Hmm, maybe ;-)

My only other comment would be to respectfully suggest that learning any new environment is going to be a serious impediment if you are under project time constraints! I am amazed daily at what I am learning about Linux Audio, but it has taken me 5 months so far to realise that it is a truly professional and very flexible system - and I doubt I will ever stop learning new facets.

One of the steepest slopes on the learning curve can be circumvented if one takes the time to study the philosophy and development cycle of all the fundamental software underlying the use of DAWs etc (ALSA, JACK, PulseAudio and their sub-systems) - I still can't decide which is uppermost, anarchy or co-operation ;-)

It all works wonderfully once set up - getting there is a kind of test; no bad thing, IMO ;-)

---

### Post by eagle136 on 2010-02-09
Thanks - that's v useful.  USB MIDI is working having connected with aconnectgui ... so much easier to understand than Jack etc..

Now to sort out going via the MIDI port direct ... ummmmm

---

