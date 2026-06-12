---
title: "Audacity - playing and exporting MIDI files (to MP3 files)"
date: 2010-11-26
forum: Ubuntu Studio
---

### Post by shayli147 on 2010-11-26
hello:)
i use ubuntu 10.04 and Audacity 1.3.12-beta. i got a MIDI file from friends and wanted to record a demo for our song using it, but it didn't seem to work for me. i pressed Play but it stopped the moment i pressed it. i thought i could export the file to mp3 and then work but in the end i couldn't export it to mp3...

i saw [Periswell]("http://ubuntuforums.org/member.php?u=510980")'s thread with [FuturePilot]("http://ubuntuforums.org/member.php?u=178962")'s comment, the "how to" he suggested there cannot help me since i don't have any "Plugins tab" in my Preferences or anywhere else.

what can it be? how can i fix it?:)

thanks for helpers!:)
Shay-li

---

### Post by prokoudine on 2010-11-26
There is a galaxy-large difference between Audacity which is sound editor and Audacious which is a music player. You want the second, not the first.

Nevertheless Audacity (the sound editor) is going to feature experimental support for MIDI output soon.

---

### Post by shayli147 on 2010-11-26
oh i see... so what could be the reason for the midi not to played or exported? how can i fix it? :)

---

### Post by prokoudine on 2010-11-26
[http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/](http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/)

---

### Post by shayli147 on 2010-11-27
yea i saw this one, i have Audacity so it wouldn't help... do you know something else?:)

---

### Post by Pablo_F on 2010-11-27
Afaik and by the time being Audacity does not play midi files:

[http://wiki.audacityteam.org/wiki/Midi](http://wiki.audacityteam.org/wiki/Midi)

As already mentioned, you can use audacious. It is in the software center.

Cheers! Pablo

---

### Post by sgx on 2010-11-28
> **shayli147 said:**
> hello:)
i use ubuntu 10.04 and Audacity 1.3.12-beta. i got a MIDI file from friends and wanted to record a demo for our song using it, but it didn't seem to work for me. i pressed Play but it stopped the moment i pressed it. i thought i could export the file to mp3 and then work but in the end i couldn't export it to mp3...

i saw [Periswell]("http://ubuntuforums.org/member.php?u=510980")'s thread with [FuturePilot]("http://ubuntuforums.org/member.php?u=178962")'s comment, the "how to" he suggested there cannot help me since i don't have any "Plugins tab" in my Preferences or anywhere else.

what can it be? how can i fix it?:)

thanks for helpers!:)
Shay-li

If it stops, you may need to install lame, or it can mean the audacity sound preferences are not set to your sound card. Or another app is already using the sound. Or rarely, you are using apps that got all the memory.

Install lame and change the preferences, there are just a couple possibilities, oss, alsa, portaudio, reboot, and try again.

also,
sudo alsaconf

will usually start a short utility to configure the soundcard.

(mp3 works fine in audacity to load, edit, and plavback, once the bits are in a row)

Cheers

---

