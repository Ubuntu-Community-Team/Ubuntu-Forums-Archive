---
title: "MIDI OUT M-Audio 2496 card"
date: 2014-08-19
forum: Ubuntu Studio
---

### Post by obx777 on 2014-08-19
Hello,

Just installed Ubuntu Studio (latest download 64 bit).  I have an M-Audio 2496 card and audio is workling fine.  I tried for some time to find an answer to this question online and am not finding a clear answer.

I want to send MIDI data out of my M-Audio 2496 card to an external MIDI device.  How do I do it?  What needs to be configured where?

The End in Mind Goal-  Run Bitwig Studio- Use their hardware instument plug-in on an instrument track and control my Alesis DM Pro Drum machine and put drum loops on the track and route the audio back into Bitwig.  Research tells me Bitwig will do this I just need to crawl before I can run and get simple MIDI out of my M-Audio 2496.  I know the DM Pro works because I can run MIDI OUT form my keybaord and play the drum sounds.

Thanks, 
Cos

---

### Post by jejeman on 2014-08-21
Give
```
amidi -l
```

---

### Post by obx777 on 2014-08-21
Hi, and thanks for helping.

This was the reply returned :

Dir Device    Name
IO  hw:0,0    M Audio Audiophile 24/96 MIDI

---

### Post by jejeman on 2014-08-22
MIDI ports form the audio card are recognized.
Just connect what you need. MIDI form software to this port.

---

### Post by obx777 on 2014-08-22
First thanks again.  

Ok, so I did a fresh install to make sure all my tinkering around has not messed up stuff.  

I went in QJackQtl and Setup and set the MIDI driver to "seq" and started Jack.  

Then I opened the jack-keyboard application and was able to have "Connect to:" option now show up.  Listed are:
system: midi_playback_1 
system: midi_playback_2

selecting system: midi_playback_2 results in the jack-keyboard playing the sounds on my connected device.

I am not sure what system: midi_playback_1 actually is ?  Possibly the default system mini thru that shows up in Jack?

I have done as much studying as possible on this since the first post.  This pages was very helpful in getting me up to speed:
[http://tedfelix.com/linux/linux-midi.html](http://tedfelix.com/linux/linux-midi.html)

Next is getting Bitwig to drive it.  Thanks again!

---

### Post by jejeman on 2014-08-24
Just remember there is ALSA MIDI and JACK MIDI. Hardware ports for ALSA devices are always ALSA MIDI. These two are different realms, and you need a bridge between them in order to see each other. There are, at least, two bridges. First is by utilizing seq driver in JACK (witch you did), this is only for ALSA devices. Second one is with a2jmidid.

---

### Post by obx777 on 2014-08-26
I found this page because I did not know what a2midiid was:
[http://manual.ardour.org/setting-up-your-system/setting-up-midi/midi-on-linux/](http://manual.ardour.org/setting-up-your-system/setting-up-midi/midi-on-linux/)

I tried this and got the  bridge to load up in terminal box and kept opening Bitwig and trying various combos.  Still no luck yet.  I will continue to try.

---

### Post by jejeman on 2014-08-27
Start up everything.
JACK, BItwig...
Then give mi outputs from these commands
```
aconnect -o
jack_lsp
```

---

### Post by obx777 on 2014-09-02
Hi Again,

Thanks for all your help.  I am learning from this.  That was still a no go.  I have been in touch with the Bitwig "Linux guy" at Bitwig.  I think they realize there is a small issue.  He said that they were going to focus on getting MIDI via Jack straight as I understood.  That may or may not make a legacy card like the M-Audio Delta work.  My guess is it will as the Jack Keyboard works fine with the card.

Also,  I have a M-Audio UNO MIDIsport USB midi adapter.  That works fine!  Plugged it in Ubuntu auto-detacted, Bitwig sees it and it works fine.  I'm good to go for now and I think the Bitwig folks will iron out the rest.  Take care and thanks again.

---

### Post by CraigPid on 2014-10-01
Maybe I'm stating the obvious but did you try making the connections in Qjackctl connections window or a patchbay app? I don't know what your routing would be but if you connect midi cables from the card to the drum machine and from the drum machine into midi in on the card, the drum machine will not show up in the patchbay. You'll still just have midi out and in. I think you're saying that you want to send midi from a plugin in Bitwig out to the drum machine and then send it from the drum machine back into another midi app and record that onto a track in Bitwig. So make the connections in a patchbay. Connect the Bitwig midi track to midi out and connect midi in to the track that you want to record in. Sounds simple to me unless I'm missing something. I'm guessing that you're trying to patch it within Bitwig and something is amiss in Bitwig so you should just open the connections window in Qjackctl and patch it there.

---

