---
title: "pymidi - any familiarity?"
date: 2012-02-13
forum: Ubuntu Studio
---

### Post by Noobuntu79 on 2012-02-13
Okay so this isn't exactly Ubuntu related but I figure there must be some Python gurus who trawl these pages and hopefully I might be so lucky as to grab their attention.........

So I'm learning myself a bit of Python with a mind to code myself a simple synthesiser and my first goalpost is to get Python talking to my USB MIDI controller and start printing simple real-time note-on, velocity, and note-off events on the screen.  I have the pyMIDI module and I've been trying to digest it's code with limited success and I can't even be certain whether it will talk to a USB controller instead of a traditional MIDI one.  

The trouble is that it comes with no documentation on use and after stabbing combinations of keywords at Google it seems that everyone who does know how to use it is keeping damn quiet about it.

So my first question is
a) Is pymidi the tool I'm looking for?  Does it talk to USB controllers too?  And can it deliver me realtime MIDI data?

and finally...
b) if (a = yes), please tell me how...?

Thanks,

Steve

---

### Post by CivilizationII on 2012-02-17
for the python / midi binding and programming, i am happy with python midi [http://www.mxm.dk/products/public/pythonmidi/](http://www.mxm.dk/products/public/pythonmidi/)

and for midi documentation, maybe this will do the trick [http://www.sonicspot.com/guide/midifiles.html](http://www.sonicspot.com/guide/midifiles.html)

---

### Post by Noobuntu79 on 2012-02-18
Hi, thanks for the reply and of course the links...  The MIDI format page is quite nice and in depth - more so than the notes I've grabbed elsewhere though at this time I'm not looking much beyond simple note-on/off velocity aftertouch and CC data...  The python MIDI module looks pretty good though it states it doesn't handle real-time data, just data from MIDI files?  Has this since changed?  Real-time data is of course what I'll be using.....file handling will happen once I get a sequencer built as well lol.

Thanks again :)

---

### Post by CivilizationII on 2012-02-20
Hello,

trying to answering your various questions:

1/ sure, python midi _only_ handle midi data, to convert them into sound you need to send them to other softwares which then will translate them into sound. For sample you can send your midi data to Rosegarden, or a simple keyboard player linked to a synthesizer, or directly to a synthesizer, Fluidsynth for sample.

2/ you must first realize that realtime is only promising you to _interrupt_ a task if this taks was not ended before some amount of times. Translated into the sound department this means that realtime system will produced _more_ click and sound drop-out than a standard system (what you want in fact is higher priorities for sound programs, which have nothing to do with realtime). And now answering the question, python midi is obviously running under some python interpreter (whatever from cpython to ironpython) and have nothing to do with realtime. I don't know if realtime libraries exist for python, but if you really want to program realtime stuff around midi (i have of lot of doubts about this, really), you will have to find Python/realtime libs and then encapsulate your python/midi under them, _if_ feasible regarding system constraints.

---

### Post by Noobuntu79 on 2012-02-22
Thanks again for the reply...
 
I think I may have mis-used the term 'real-time' in this case, as of course I appreciate that nothing in this department has true real-time priority - what I meant was just simply using this Python module to respond to a live stream from the keyboard where as much of the examples shown handle MIDI files as their input.
 
I've experimented with the example code given and substituting in various MIDI files, and sure enough I'm returned a printed list of
 
    channel    note    velocity    time
 
for an entire track, which is a good starting point in knowing if it works and for what and where I'm looking when disecting the module code.  My next step is to establish a list similar in format to that above that will update when keys are pressed on my controller...
 
I can see that I can potentially do this through the classes MidiInStream and MidiOutStream, but my stumbling block is in the line:
 
    __init__(self, midiOutStream=None, device)
 
The keyword here is 'device'.  This appears to be where I declare where the live stream is coming from yet I am unsure of what I am to declare (device ID?) especially when you consider my keyboard is USB rather than MIDI.  
 
As for the sound processing part of the operation, this is something that will come in a later project when I start programming oscillators and other various sound modules.  Until then, I need to get my live data input right and that needs to start with just some printed numbers on the screen :)
 
Steve

---

