---
title: "timidity question"
date: 2011-02-19
forum: Ubuntu Studio
---

### Post by il lupo on 2011-02-19
Hello, All--

The ultimate problem is that i get no sound when i direct Hydrogen's midi output to timidity.  i tried plugging Hydrogen into Qsynth, too, with the same result.  i would like to convert midi to sound so i can eventually run the midi output of Hydrogen into Ardour and record drum tracks.  It is certainly less trouble to plug Hydrogen's audio output straight into Ardour, but the sound of the midi file is far preferable--and we musicians will go to absurd lengths for a good sound.

My working solution is to export my song or pattern to a midi file, use timidity to convert that to an audio file, and then import it into Ardour.  By the way, timidity does play the midi file.

Those aren't absurd lengths, but for time's sake, i wouldn't mind reducing the steps.  Have i missed something in any configuration files?  Is it possible to redirect timidity's output to Ardour?  That could probably be done by modifying a configuration file, but i still feel a little too green to do that without guided instruction.

i would love to hear any possible solutions, even those that go outside of what i've said.

il lupo

---

### Post by Pablo_F on 2011-02-19
> Is it possible to redirect timidity's output to Ardour?

Yes, but you need to tell timidity (or qsynth or whatever soft synth) to use jack as audio output. For example, 

timidity -Oj -ia

Cheers, Pablo

---

### Post by il lupo on 2011-02-19
Thank you, Pablo!  i'd been reading the man page and saw those switches, but just couldn't put two and two together.  Like i wrote, i'm still just a little too green.  Thanks for the patience.

In any event, with a little experimenting, i came up with this:

timidity -A[desired volume],[desired drum strength] -Oj -ia [your file].mid

which allowed me to control the initial volume of the midi file and its drum strength while calling up the file i actually wanted.  Terminals can be so much better than GUI's!

It would still be nice to go straight from Hydrogen to timidity (or Qsynth) and get sound.  i just tried it with the switches you showed me, but to no avail.  Does anyone know if Hydrogen was set to run its midi with real-time priorities?  Is it possible to change this?

Thank you, again, Pablo!

---

### Post by Pablo_F on 2011-02-19
> It would still be nice to go straight from Hydrogen to timidity (or Qsynth) and get sound

Yes, connect the hydrogen midi output to the soft synth's input.

Then, in hydrogen, look at the instrument Tab, right of the pattern editor. First select an instrument in the pattern editor, and set the midi channel and the note. By default, midi channel is off, so no midi notes to the synths. Of course, you need to do some mapping, notes to instruments. Disconnect hydrogen audio outs or set master to 0 so you only hear (or connect to ardour) the soft synth. 

You can also prepare your own hydrogen drumkits, layers and all, from your favourite audio samples. The makekit script by GarryO comes handy: 

[http://forum.linuxmusicians.com/viewtopic.php?f=24&t=1000&p=5289](http://forum.linuxmusicians.com/viewtopic.php?f=24&t=1000&p=5289)

Cheers, Pablo

---

### Post by il lupo on 2011-02-21
Thank you, again, Pablo.  i followed your instructions and got sound after plugging Hydrogen into timidity and Qsynth.  However, i only get piano notes and not any drum sounds.  Is this because the midi coming out of Hydrogen was designed strictly to control other devices and not as a second means of producing drum sounds?

After your first response, i've basically been able to get Hydrogen to do exactly what i need it to do.  That link will come in handy, later, too.  Again, many thanks, Pablo!

---

### Post by Pablo_F on 2011-02-21
> I only get piano notes and not any drum sounds. Is this because the midi coming out of Hydrogen was designed strictly to control other devices and not as a second means of producing drum sounds?

Let's see, hydrogen sends midi events, note on, note off, pitch... It normally sends the midi events to its own sampler which makes noise one way or another depending on the drumkit loaded. 

Another option, what we are discussing here:

In order to hear a drumkit through an external soundfont player, such as timidity or qsynth, you need to (1) use the H2 midi outs as explained above and (2) load a drumkit soundfont in timidity or qsynth so that they can produce drum sounds and/or (3) choose the right midi channel and pitch-to-instrument mapping. 

Cheers! Pablo

---

### Post by il lupo on 2011-02-22
i had tripped to a few of your solutions, myself, Pablo, but they added unnecessary steps.  As for now, i can get Hydrogen to do pretty much what i need, and much of what i was doing was an attempt to work around a few problems.  One of the biggest is that when Hydrogen recognizes velocity values only in midi.

Last night, i got gstreamer to run through JACK, and that solved many problems.  It allowed me to run an audio file through totem, which i could then reroute anywhere, so long as i kept the file in a playlist.

So, i'll mark this as solved.  Thank you, again, for all your help, Pablo.

Best,
il lupo (bill)

---

