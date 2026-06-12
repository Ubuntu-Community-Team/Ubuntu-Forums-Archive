---
title: "Rosegarden &amp;&amp; Roland SH32 Synthesizer"
date: 2009-10-31
forum: Ubuntu Studio
---

### Post by bawig1 on 2009-10-31
Hi,

I am trying to use a Roland SH32 with Rosegarden. I have managed to get jack working and the Synth is detected by Jack (i'm using a MIDI to USB cable) But I cannot figure out how to use the synth with rosegarden. Below is a screenshot of the setup. Is this correct? 

Does anyone here use Rosegarden? 

thanks,

Brett.
[IMG]http://img413.imageshack.us/img413/2622/screenshotcj.png[/IMG]

---

### Post by bawig1 on 2009-10-31
I seem to be having some problems with MIDI in Rosegarden. When I run it I get the following;

```

System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
You may be able to solve this problem by loading the RTC timer kernel module. To do this, try running sudo modprobe snd-rtctimer in a terminal window and then restarting Rosegarden.
Alternatively, check whether your Linux distributor provides a multimedia-optimized kernel. See http://rosegarden.wiki.sourceforge.net/Low+latency+kernels for notes about this.

```I have had a look around and cannot seem to find this module.  Do I really need it? under Rosegarden preferences it has an entry 'Sequencer status' - MIDI ok, audio ok.

Brett.

---

