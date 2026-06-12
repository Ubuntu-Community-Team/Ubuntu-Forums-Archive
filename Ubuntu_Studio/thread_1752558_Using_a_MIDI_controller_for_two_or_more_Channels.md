---
title: "Using a MIDI controller for two or more Channels"
date: 2011-05-07
forum: Ubuntu Studio
---

### Post by halfpower on 2011-05-07
I want to control multiple MIDI channels at the same time.  Is there some way I can make my keyboard look like two keyboards to my audio software?

---

### Post by jejeman on 2011-05-08
Not shure what you want do to, but if youre keyboard suport multichannel midi output, you can send midi data thru different midi chnnels. I think you should look in keyboard manual for that.
I dont see what you will gain if you make youre keyboard look like two. It would send same midi data on two places.

---

### Post by Pablo_F on 2011-05-08
On the software side, you can use qmidiroute. You can split a MIDI keyboard so that, for example, some keys send MIDI data to channel 1 and some others to channel 2.

A typical use is playing two different instruments at the same time, one with the left hand, the other with the right hand.

> qmidiroute permits setting up an unlimited number of MIDI maps in which incoming events are selected, modified or even changed in  type  before being directed to a dedicated ALSA output port.

It is in the software center and it is described here:

[http://manpages.ubuntu.com/manpages/natty/man1/qmidiroute.1.html](http://manpages.ubuntu.com/manpages/natty/man1/qmidiroute.1.html)

Cheers! Pablo

---

### Post by halfpower on 2011-07-10
qmidiroute will solve many problems.  I can 'auto-tune' my dynamics with it too.  Thanks.

---

