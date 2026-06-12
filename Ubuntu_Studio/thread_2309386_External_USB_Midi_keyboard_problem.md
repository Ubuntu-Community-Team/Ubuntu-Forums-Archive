---
title: "External USB Midi keyboard problem"
date: 2016-01-10
forum: Ubuntu Studio
---

### Post by Keith_Beef on 2016-01-10
After a great deal of time, I've got Jack working, playing sound through Alsa and my computer's internal sound hardware.
I can connect the Jack virtual keyboard to QSynth or to ZynAddSubFX and get sound.

But when I connect my Alessis Q49 external keyboard, this shows up in the Connections panel of QJackControl in the ALSA tab, not in the MIDI tab.

I've also tried Patchage and Aconnectgui, but I cannot make a connection from the Q49 MIDI1 output to any midi input…

Modules are loaded:

```
$ lsmod | grep usb | grep snd
snd_usb_audio         155013  0 
snd_usbmidi_lib        29215  1 snd_usb_audio
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102099  6 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_rawmidi            30144  2 snd_usbmidi_lib,snd_seq_midi
snd                    69322  25 snd_hda_codec_realtek,snd_hrtimer,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_dummy,snd_seq_midi
```

The device is visible to the system:
```
$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 24: 'Q49' [type=kernel]
    0 'Q49 MIDI 1
```

MIDI events are being sent from the keyboard:
```
$ aseqdump -p 24
Waiting for data. Press Ctrl+C to end.
Source  Event                  Ch  Data
 24:0   Note on                 0, note 71, velocity 83
 24:0   Note off                0, note 71, velocity 64
 24:0   Pitch bend              0, value 128
 24:0   Pitch bend              0, value 0
 24:0   Control change          0, controller 1, value 65
 24:0   Control change          0, controller 1, value 66
 24:0   Control change          0, controller 7, value 1
 24:0   Control change          0, controller 7, value 2
 24:0   Control change          0, controller 7, value 3
 24:0   Control change          0, controller 7, value 4
 24:0   Control change          0, controller 7, value 5
 24:0   Control change          0, controller 7, value 6
 24:0   Note on                 0, note 70, velocity 99
 24:0   Note off                0, note 70, velocity 64
 24:0   Note on                 0, note 70, velocity 106
 24:0   Note off                0, note 70, velocity 64
```

And for the time while aseqdump is running, patchage shows me a connection between  Q49 MIDI1 and aseqdump.

I tried using a few other options to aconnect, but I am confused by the terms use.
```
$ aconnect -h
aconnect: invalid option -- 'h'
aconnect - ALSA sequencer connection manager
Copyright (C) 1999-2000 Takashi Iwai
Usage:
 * Connection/disconnection between two ports
   aconnect [-options] sender receiver
     sender, receiver = client:port pair
     -d,--disconnect disconnect
     -e,--exclusive exclusive connection
     -r,--real # convert real-time-stamp on queue
     -t,--tick # convert tick-time-stamp on queue
 * List connected ports (no subscription action)
   aconnect -i|-o [-options]
     -i,--input list input (readable) ports
     -o,--output list output (writable) ports
     -l,--list list current connections of each port
 * Remove all exported connections
     -x, --removeall
```

It says that -i lists all "input (readable) ports" and that -o lists all "output (writable) ports". I would have expected an input port to a device to be writable, and an output port to be readable (i.e., I can read data from the output port of a device, and I can write data to the input port of a device).

Anyway, ```

$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 24: 'Q49' [type=kernel]
    0 'Q49 MIDI 1    

$ aconnect -o
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 24: 'Q49' [type=kernel]
    0 'Q49 MIDI 1      '
client 128: 'TiMidity' [type=user]
    0 'TiMidity port 0 '
    1 'TiMidity port 1 '
    2 'TiMidity port 2 '
    3 'TiMidity port 3 '
```

Now if I start aseqdump and look at the list of active connections, I can see that the output from device 24, the Q49 keyboard, is connected to the input of device 132, aseqdump.
```
$ aconnect -o -l
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 24: 'Q49' [type=kernel]
    0 'Q49 MIDI 1      '
	Connecting To: 132:0
client 128: 'TiMidity' [type=user]
    0 'TiMidity port 0 '
    1 'TiMidity port 1 '
    2 'TiMidity port 2 '
    3 'TiMidity port 3 '
client 132: 'aseqdump' [type=user]
    0 'aseqdump        '
	Connected From: 24:0
```

So it looks very clear that packets of MIDI data are being sent over the USB cable, are being caught by ALSA, but I cannot find a way to route those packets to the input of any synthesizer.

Can anybody help me out?

---

### Post by jejeman on 2016-01-10
It is simple - there are two realms of MIDI in Linux: ALSA MIDI and JACK MIDI.
Both are independent and don't see each other without additional software. You need to bridge them in order to work together.
There is two ways for this:
1. a2jmidid
2. MIDI driver in JACK settings. I choose seq driver. (-Xseq)

---

### Post by marseille2 on 2016-01-11
I use a2jmidid (for Jackd2), and in my qjackctl '**Setup** > Settings' tab ... I have the "MIDI driver" set to none.

If I must start a2jmidid manually (usually not), jackd must be on before I can fire it up at the command line:

```
$ a2jmidid -e
```

Once it's activated... you should see your MIDI in qjackctl's MIDI tab in connections.

Read more about the a2jmidid at [Ardour]("http://manual.ardour.org/setting-up-your-system/setting-up-midi/midi-on-linux/")...

---

### Post by Keith_Beef on 2016-01-16
> **jejeman said:**
> It is simple - there are two realms of MIDI in Linux: ALSA MIDI and JACK MIDI.
Both are independent and don't see each other without additional software. You need to bridge them in order to work together.
There is two ways for this:
1. a2jmidid
2. MIDI driver in JACK settings. I choose seq driver. (-Xseq)

> **marseille2 said:**
> I use a2jmidid (for Jackd2), and in my qjackctl '**Setup** > Settings' tab ... I have the "MIDI driver" set to none.

If I must start a2jmidid manually (usually not), jackd must be on before I can fire it up at the command line:

```
$ a2jmidid -e
```

Once it's activated... you should see your MIDI in qjackctl's MIDI tab in connections.

Read more about the a2jmidid at [Ardour]("http://manual.ardour.org/setting-up-your-system/setting-up-midi/midi-on-linux/")...

Thanks, both of you. Using a2jmidid worked.

It had crossed my mind that a daemon could listen for ALSA MIDI signals and duplicate them into Jack, so that a single keyboard could control, for example an ALSA-only application with the left-hand half  of the keyboard and a Jack-only application with the right-hand half  of the keyboard.

---

