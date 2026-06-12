---
title: "pipe organ help"
date: 2009-08-09
forum: Ubuntu Studio
---

### Post by houshp on 2009-08-09
hello,  total newb here.  I am really getting into this and enjoying all the great information that I have found in these forums.  But, I have not found any information on driving a real pipe organ with Ubuntu.  Has anyone ever accomplished this?  Or am I "breaking" new ground?  Please, any information would help.  This would include what software I should use.  Thanks for the help in advance.

---

### Post by Stochastic on 2009-08-11
What type of hardware capabilities does this pipe organ have?  Are you able to drive it with a MIDI input or will you need to be building and programming some robotics?

---

### Post by houshp on 2009-08-13
This is a brand new project.  I have been planning on using midi software and hardware, but don't quite know where to start.  Any ideas would be much appreciated.:)

---

### Post by markbuntu on 2009-08-14
How are you planning to control the pipes or is there some automated system already in place?

---

### Post by Stochastic on 2009-08-15
I've never heard of a MIDI driven pipe organ - I'll leave that hardware puzzle up to you to work out - but if it accepts MIDI, then the following chain should do you just fine:

Your favorite sequencer/midi player/tracker/programming language/etc..  ->  Either Jack MIDI or ALSA MIDI -> MIDI soundcard -> MIDI organ

As for deciding which MIDI application you should use to drive the organ, here's a list of some apps available for Linux: [http://wiki.linuxaudio.org/apps/categories/midi_software](http://wiki.linuxaudio.org/apps/categories/midi_software)

---

### Post by houshp on 2009-08-15
there are several midi electronics that can drive pipe organs, but I am not sure which is best.  Also, I am looking at this project with a very tight budget.  I was hoping that someone else has broken ground on this subject.  Most of the information I have found is Windows based.  For obvious reasons, I would very much like to run this in a linux format.  Thanks again for your time,

---

### Post by FakeOutdoorsman on 2009-08-17
You may be interested in [Aeolus](http://users.skynet.be/solaris/linuxaudio/aeolus.html).  It's in the Ubuntu repository.  It's a pipe organ emulator, and although not a solution to what you're trying it could be worth trying out.  Some audio examples are at [How to install Aeolus, pipeorgan emulator for Linux](http://www.geocities.jp/midi_organ_net/aeolus/).

---

### Post by houshp on 2009-08-19
Thanks for the information!  I guess I am breaking some new ground as I do not see anyone else trying to drive a pipe organ with Ubuntu here.

---

### Post by InMySocks on 2009-08-24
You need a relay to process stop and key information to the pipe organ.  Inputs are keys and stops.  Outputs are usually 12 volts to the pipe magnets which is supplied by driver boards.  jOrgan is the relay which is written in Java and will work in Win or Ubuntu.  There is plenty of information about people doing this in the jOrgan forums.  Just Google it.
Kindest Regards

---

### Post by houshp on 2009-09-06
Again, thanks for the information.  I have looked at jOrgan and it looks like this a good lead to try.

---

