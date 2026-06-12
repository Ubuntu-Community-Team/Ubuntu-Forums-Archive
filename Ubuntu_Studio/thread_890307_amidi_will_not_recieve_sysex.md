---
title: "amidi will not recieve sysex?"
date: 2008-08-14
forum: Ubuntu Studio
---

### Post by dbsoundman on 2008-08-14
I've been trying to find a program I can use to do sysex dumps from my midi devices. I tried sysexxer, and it wouldn't install, and simple sysexxer freezes up when I try to load a file I have saved. So, I tried amidi, but for some reason, it doesn't seem to be "finding" the sysex dump. Here's what I've been doing:

```
amidi -p hw:1,0,0 -r srv330.syx
```

However, I get nothing but an empty text file named "srv330.syx". I know that the device is transmitting because I was able to get simple sysexxer to receive and save a dump from it, I just can't load it with that program now. What might be the problem? I only have one midi device, and it was listed as hw:1,0,0 when I did amidi -l.

Any ideas?

-Dan

---

### Post by leighgable on 2009-12-09
Hello Dan,

I don't have an answer to this, but I am interested if anyone does, as I am having the exact same problem trying to get an old synth to dump sysex through amidi with a UA-25 sound card's midi ports. Like Dan, they show up as hw:1,0,0

and in aconnect -i and -o show:

host@tiny:/$ aconnect -o
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'UA-25' [type=kernel]
    0 'UA-25 MIDI 1    '
host@tiny:/$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'UA-25' [type=kernel]
    0 'UA-25 MIDI 1    '

Do we actually need to connect anything manually with aconnect? I can see the synth is recieving midi, but the sysex dump is an empty file.

---

