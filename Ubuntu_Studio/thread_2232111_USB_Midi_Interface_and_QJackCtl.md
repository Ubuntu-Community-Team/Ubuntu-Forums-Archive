---
title: "USB Midi Interface and QJackCtl"
date: 2014-06-29
forum: Ubuntu Studio
---

### Post by bjgowers on 2014-06-29
Hello,
  I have a generic MIDI to USB (1x1) cable.  I would like to connect it to Ardour through QJackCtl.  At first, my device appeared in the ALSA tab of the connect menu in QJackCtl, but in order to patch it in to Ardour, it needed to appear in the MIDI tab.  I followed the instructions here: [http://manual.ardour.org/setting-up-your-system/setting-up-midi/midi-on-linux/](http://manual.ardour.org/setting-up-your-system/setting-up-midi/midi-on-linux/) to enable a2jmidid to bridge the ALSA and Jack Midi controls.  This included disabling ALSA sequencer support in QJackCtrl, which promptly deleted the ALSA tab in the connections window.  According to the instructions, my device should now show up in the midi tab instead, but it doesn't.  Any suggestions on how to troubleshoot this problem?  Thanks for your help!

---

### Post by CrocoDuck on 2014-06-30
Hi! I don't think you need to disable ALSA sequencer. I am used to do this:


[LIST=1]
[*]Start jack with Qjackctl 
[*]Start a2jmidid from a terminal
```
a2jmidid
``` 
[*]In the ALSA tab:
Connect you controller to Midi Through 
[*]In the MIDI tab:
Connect a2j to what you need 
[/LIST]

Hope it helps.

---

### Post by brianmc on 2014-07-11
> **CrocoDuck said:**
> Hi! I don't think you need to disable ALSA sequencer. I am used to do this:


[LIST=1]
[*]Start jack with Qjackctl 
[*]Start a2jmidid from a terminal
```
a2jmidid
``` 
[*]In the ALSA tab:
Connect you controller to Midi Through 
[*]In the MIDI tab:
Connect a2j to what you need 
[/LIST]

Hope it helps.

Easier still: In the Options tab on QJackCTL, tick the box next to "Execute script after Startup" and put 'a2jmidid &' (without quotes) into the box. That'll roll steps 1 and 2 into a single operation and always start the ALSA to JACK MIDI bridge. Without putting together a cleanup script, it'll probably spit a few errors onto the end of your JACK log when you stop the daemon.

---

### Post by gboer01 on 2014-07-15
You are on the right track with a2jmidid, please read my post (bottom half) how to integrate it into QJackCtl :
[http://ubuntuforums.org/showthread.php?t=2227547](http://ubuntuforums.org/showthread.php?t=2227547)

Cheers and good luck,
Bert.

---

