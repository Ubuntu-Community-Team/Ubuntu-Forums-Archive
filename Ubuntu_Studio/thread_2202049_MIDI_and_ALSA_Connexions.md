---
title: "MIDI and ALSA Connexions"
date: 2014-01-27
forum: Ubuntu Studio
---

### Post by royleith on 2014-01-27
I have managed to skirt around this issue, but it is getting in the way of midi testing.

Most MIDI devices and MIDI program interfaces (such as Rosegarden and Timidity) appear under the ALSA connections in jack. However, the default MIDI utilities appear under MIDI and not ALSA and are not available to patch to the ALSA midi ports. 

Gmidimonitor with jack support should be an ideal way of testing the output of pad and keyboard devices, but it appears under MIDI connexions and cannot be connected to the ALSA connexions midi ports. With the 'Gmidimonitor with ALSA support' version, it does not appear under any of the jack connexions headings.

Do the programs have to be rewritten to use ALSA MIDI ports? I know they are open-source, but that would be a bit beyond me!

I am hoping there are config files available to change the ports over.

---

### Post by CrocoDuck on 2014-01-27
My dear, the solution to your problem: [http://home.gna.org/a2jmidid/](http://home.gna.org/a2jmidid/) . I don't remember if it is installed on UStudio by default... if not, install it through software center.

---

### Post by cub on 2014-01-27
> **CrocoDuck said:**
> My dear, the solution to your problem: [http://home.gna.org/a2jmidid/](http://home.gna.org/a2jmidid/) . I don't remember if it is installed on UStudio by default... if not, install it through software center.
On my Ubuntu Studio 13.10 it was installed by default.

---

### Post by jejeman on 2014-01-27
Even better. If you are using ALSA backend (driver) with JACK you can enable MIDI driver (seq). That will automatically duplicate ALSA MIDI ports into JACK MIDI realm. (Same thing that a2jmidid does.)

---

### Post by royleith on 2014-01-28
All,

Ha, you have been no help at all! I still cannot use the jack keyboard with any software except Gmidimonitor with jack support. However, you have explained to me what is going on in qjackctl. As cub reported, a2jmidid is installed in 13.10 by default. Running it from a qjackctl script in options or from a terminal makes no difference at all. I think the reason is that US has been configured to mirror ALSA MIDI in jack ever since I started using it some years ago. For all that time, Connections has had the three tabs of Audio, Midi and Alsa and the Alsa is where all the real and virtual midi devices appear except for two; the Jack keyboard and Gmidimonitor with jack support. 

Patchage makes it all clear. I had thought that it was just an alternative to jack Connections, but it shows the ALSA ports for MIDI and Audio even when jack is not running. ALSA MIDI is in Green and Audio is in blue. If both the ALSA and jack versions of Gmidimonitor are running (and jack), there are inputs for ALSA MIDI in green and jack MIDI in red. Playing on the Jack Keyboard appears in the jack pane and on the Virtual Keyboard appears in the ALSA pane.

So far, all of my external devices such as pads, keyboards, MIDI modules, MIDI interfaces and the like only appear as ALSA MIDI devices as does all of the US software except for the Jack Keyboard and the Gmidimonitor with jack support.

The reason that I thought stuff was not working was that I relied on Connections rather than Patchage which meant that I missed some available ports. That and the fact that Timidity only seems to work outside of jack whereas it used to be fine with jack. I just tried it again and now it is not working at all, so that needs more investigation.

Thanks all for your comments which have cleared up some of the mists of what is going on in US, for me. The only thing I would like is to use the rather nice Jack Keyboard with all my usable ALSA stuff. 

After a reboot, I will try to get Virtual Keyboard to work nicely with Timidity in the same way that Audacious does. I suspect that prior use of Audacious to play back MIDI files before launching jack may be at the root of the jack/Timidity issue.

---

