---
title: "Mackie Control Universal (MIDI)"
date: 2011-02-15
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2011-02-15
Hey guys, I'm trying to get a MCU Midi version to control Ardour.  I went by the instruction that I can't seem to find right now, but I don't get anything from the Controller or Ardour. The Mackie is on Logic control mode.

My setup is this:

Mackie(Midi) -> MIDIMAN Midisport 8x8 -> Computer

Is this setup possible or is Mackie support only for the USB version?  Seriously, I only need the transport buttons to work and possibly the track record and solo buttons.  That's all I need.  Jog wheel would be nice though.  Also, is there a way to use it to control the Jack transport?  That would be even better.

I've tried turning on OSC, checking Mackie, but that doesn't seem to do it.  I tried playing around with patchage and hooking the input of the midi to the Control, MCU, and SEQ input of Ardour, still nothing.  Keyboards work with this interface just fine.  In fact, I can play notes using the buttons on the Mackie.

Ubuntu Version 10.04

Ardour 2.8.11

Thanks

---

### Post by Pablo_F on 2011-02-16
Hi, 

Do you mean this?

[http://www.ardour.org/files/manual/sn-mackie.html](http://www.ardour.org/files/manual/sn-mackie.html)

What are the terminal outputs of:

cat /proc/asound/cards

ls /dev/snd

cat ~/.ardour2/ardour.rc

Cheers, Pablo

---

### Post by pepsifx357 on 2011-02-16
> **Pablo_F said:**
> Hi, 

Do you mean this?

[http://www.ardour.org/files/manual/sn-mackie.html](http://www.ardour.org/files/manual/sn-mackie.html)

What are the terminal outputs of:

cat /proc/asound/cards

ls /dev/snd

cat ~/.ardour2/ardour.rc

Cheers, Pablo

That's the one I was looking for.  I'll get back to you asap with those outputs.

Thanks

---

### Post by pepsifx357 on 2011-02-19
Sorry it took me so long...

First one:

```
ben@ben-desktop:~$ cat /proc/asound/cards
 0 [default        ]: HDSPM - HDSPM MADI
                      RME HDSPM MADI at 0xdfff0000, irq 18
 1 [M8x8           ]: USB-Audio - MidiSport 8x8
                      M-Audio MidiSport 8x8 at usb-0000:00:0b.1-2.2.2, full speed

```

Second one:

```
ben@ben-desktop:~$ ls /dev/snd
by-id    controlC0  hwC0D0    midiC0D1  pcmC0D0c  seq
by-path  controlC1  midiC0D0  midiC1D0  pcmC0D0p  timer

```

Third:

```
ben@ben-desktop:~$ cat /home/ben/.ardour2/ardour.rc
<?xml version="1.0" encoding="UTF-8"?>
<Ardour>
  <MIDI-port tag="control" device="ardour" mode="duplex" type="alsa/sequencer">
    <connections>
      <write dest="130:0"/>
    </connections>
  </MIDI-port>
  <MIDI-port tag="mcu" device="ardour" mode="duplex" type="alsa/sequencer">
    <connections>
      <write dest="130:0"/>
    </connections>
  </MIDI-port>
  <MIDI-port tag="seq" device="ardour" mode="duplex" type="alsa/sequencer">
    <connections>
      <write dest="130:0"/>
    </connections>
  </MIDI-port>
  <Config>
    <Option name="trace-midi-input" value="no"/>
    <Option name="trace-midi-output" value="no"/>
    <Option name="use-tranzport" value="no"/>
    <Option name="minimum-disk-io-bytes" value="262144"/>
    <Option name="track-buffer-seconds" value="5"/>
    <Option name="disk-choice-space-threshold" value="57600000"/>
    <Option name="xfade-model" value="0"/>
    <Option name="auto-xfade" value="no"/>
    <Option name="destructive-xfade-msecs" value="20"/>
    <Option name="mute-affects-pre-fader" value="yes"/>
    <Option name="mute-affects-post-fader" value="yes"/>
    <Option name="mute-affects-control-outs" value="yes"/>
    <Option name="mute-affects-main-outs" value="yes"/>
    <Option name="plugins-stop-with-transport" value="no"/>
    <Option name="stop-recording-on-xrun" value="no"/>
    <Option name="create-xrun-marker" value="yes"/>
    <Option name="stop-at-session-end" value="no"/>
    <Option name="seamless-loop" value="no"/>
    <Option name="quieten-at-speed" value="yes"/>
    <Option name="show-track-meters" value="yes"/>
    <Option name="jack-time-master" value="yes"/>
    <Option name="smpte-format" value="6"/>
    <Option name="timecode-source-is-synced" value="no"/>
    <Option name="no-new-session-dialog" value="no"/>
    <Option name="use-vst" value="yes"/>
    <Option name="periodic-safety-backups" value="yes"/>
    <Option name="periodic-safety-backup-interval" value="120"/>
    <Option name="default-narrow_ms" value="no"/>
    <Option name="font-scale" value="102400"/>
  </Config>
  <extra>
    <RulerVisibility smpte="yes" bbt="yes" frames="no" minsec="no" tempo="yes" meter="yes" marker="yes" rangemarker="no" transportmarker="yes" cdmarker="no"/>
    <Keyboard edit-button="3" edit-modifier="4" delete-button="3" delete-modifier="1" snap-modifier="32"/>
    <TransportControllables roll="0" stop="1" goto_start="2" goto_end="3" auto_loop="4" play_selection="5" rec="6" shuttle="7"/>
  </extra>
  <ControlProtocols>
    <Protocol name="Mackie" active="no"/>
    <Protocol name="Generic MIDI" active="no"/>
  </ControlProtocols>
</Ardour>

```

---

### Post by Pablo_F on 2011-02-19
Hi, 


My experience is with a Behringer BFC2000 in Mackie mode. It is plugged by means of a USB cable. However, I think yours will work through the midiman, at least you can try. 

First of all, set MIDI driver to "none" in qjackctl's setup. This refers to jack midi driver, you have alsa midi ports anyway. Also, don't use a2jmidid at qjackctl's poststart script (if you don't know what I am talking about you are not using it, so far so good).

Start jack, start ardour, close ardour, close jack. Edit the file ~/.ardour2/ardour.rc

(.ardour2 is a hidden directory in your home directory)

You will probably see a line under the <Ardour> tag, like this one:

  <MIDI-port tag="mcu" device="ardour" mode="duplex" type="alsa/sequencer"/>

Change it to:

  <MIDI-port tag="mcu" device="**/dev/snd/midiC1D0**" mode="duplex" type="alsa/**raw**"/>

Then, under the <Config> tab, add this line (in the first place or at any position, it does not matter):

  <Config>
    .......
    **<Option name="mackie-emulation" value="mcu"/>**
    .....



In ardour, tick Mackie option, under Options -> Control surfaces.

I think this is all. 

Cheers, Pablo

---

### Post by pepsifx357 on 2011-02-20
Pablo, your are AWESOME!!!!  Thanks!  The Mackie lit right up!  One more question...Where is the file that I can edit in order to edit the Mackie's function buttons?

---

### Post by dawiba on 2011-02-20
I don't know about any file, but I set my Nanokontrol to control Ardour this way:

Press and hold Ctrl and then click the middle mouse button over the control in Ardour you're interested in. You should get a little popup telling you to operate the control on your controller that you want to use for that function. Ardour's Midi Learn function should remember this and it should be assigned to that controller now.

However, I may be wrong, but I think this is only Session specific, so you need to go through this with every new Ardour Session. Unless of course, you create a Session with everything you need and save this as a template.

I don't know, but hopefully this will work the same for the Mackie

---

### Post by Pablo_F on 2011-02-20
I might be wrong but if you use the "Mackie mode" with the instructions above, there is not a file that you can edit. The mapping is done in the ardour sources and you can't easily change that. Well, I like the mapping in the BCF2000 as is, so I never tried to change it, that is why I am not 100% sure of this, but I think so.

What dawiba comments is a different option.

In this case, you use the "generic MIDI", not "Mackie", in Options -> Control Surfaces and you have to connect the Mackie to the ardour control input, via qjackctl's connection button, alsa tab. Then you make the assignments as explained and save a template.

If you use this method, I think that you have to revert previously the changes in ~/.ardour2/ardour.rc (at least the line under the ardour tag).

See here: [http://ardour.org/files/reference/dsy21-ARDOUR.html#dsy21-ARDOUR](http://ardour.org/files/reference/dsy21-ARDOUR.html#dsy21-ARDOUR)

I am glad I helped :) For further questions, you can ask in the ardour forum or mailing list, where several advanced users and developers give very good help. 

Cheers! Pablo

---

