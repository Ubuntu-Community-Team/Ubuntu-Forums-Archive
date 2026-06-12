---
title: "Yoshimi Crashing frequently when changing instruments"
date: 2012-04-28
forum: Ubuntu Studio
---

### Post by Sylos on 2012-04-28
Hello all!

So as the title suggests, Yoshimi is giving me all kinds of grief. I cant seem to get anything done on account of frequent crashes when Im trying out different instruments.

I started using Yoshimi as Zynn gives a lot of dirty scratchy noises (and crashes - although less frequently). I installed it from Autostatics ppa (looked in FalkTX ppa but it seems the Lucid repos arent being maintained these days).

Tried starting Yoshimi with "yoshimi --show-console" and get the following showing when the crash occurs:

```
Yoshimi 0.058.1
Clientname: yoshimi
Audio: jack -> 'default'
Midi: jack -> 'default'
Oscilsize: 1024
Samplerate: 96000
Buffersize: 256
Alleged latency: 256 frames, 2.67 ms
Gross latency: 512 frames, 5.33 ms
Jack error report:jack_client_thread zombified - exiting from JACK

```

On some (but not all) occasions when I try to exit Yoshimi it hangs really badly. I try using System Monitor to kill the process but only after "sudo killall yoshimi" does it disappear. Before issuing that it just sits there and then retains the graphics of any window that overlays it at any point.

Despite my recent issues getting my sound card up and running my other normal apps (ardour, hydrogen, rackarak, phasex etc) all seem to be as stable as normal.

Any help appreciated.


Cheers

EDIT: Also got this in the terminal I used to open it:

```
X_ChangeProperty: BadValue (integer parameter out of range for operation) 0x40
X_ChangeProperty: BadValue (integer parameter out of range for operation) 0x40
X_ChangeProperty: BadValue (integer parameter out of range for operation) 0x40
X_ChangeProperty: BadValue (integer parameter out of range for operation) 0x40
X_ChangeProperty: BadValue (integer parameter out of range for operation) 0x40
X_ChangeProperty: BadValue (integer parameter out of range for operation) 0x40

```

---

### Post by sgx on 2012-04-28
If the 96000 samplerate setting is done in qjackctl, I would bump that down to 44100 or 48000

 There is a -Z option for jackd, 'no zombies', so it allows for
some performance issues, without killing yoshimi. You may have to
edit .jackdrc, as I don't think qjackctl implements that.

And then start jackd using the .jackdrc text file itself as the command,
and start qjackctl second.

[http://linux.die.net/man/1/jackd](http://linux.die.net/man/1/jackd)  for jackd options

a newer yoshimi:

[http://packages.debian.org/unstable/sound/yoshimi](http://packages.debian.org/unstable/sound/yoshimi)

sudo dpkg -i nameof.deb

You may need to update libfftw3-3 or others
from the dependencies collection the same page.
Look in termianal output for errors.

But I don't manually update any system libraries, just
the ones specific to an app, or range of installed apps,
especially no c libs, hal, X11, or dbus things

Cheers

---

### Post by Sylos on 2012-05-01
Thanks for the suggestions sgx. 

Tried the -z option but it didnt seem to help - when the crash came it still complained of a jack zombie. Im going to give the newer build of Yoshimi a chance and see waht gives.

Dont really want to switch down from 96k - the rig should handle it without issues so I want to keep to the best I can quality wise.

More worryingly Im now starting to notice a variety of instabilities. It seems that phasex is also being flakey. Everytime I try to go into the preferences it exits immediately leaving the following in a terminal

```
SSE2 detected
Unhandled ALSA MIDI error.
Please make sure that the 'snd_seq_midi' and 'snd_seq_midi_event'
kernel modules are loaded and functioning properly.
PHASEX Exiting...

```

I did a modinfo on the modules mentioned and they seem to be there (not really sure what the output tells me).

Also had a few hickups with rackarak - not too many though and I havent caught one in a terminal yet.

Any ideas if these could be linked?

Cheers

---

### Post by sgx on 2012-05-01
Pretty strange happenings. You can try in qjackctl a higher midi 'Timeout (msec)' 
Mine is at 1000, 5000 is too high. Trying a lower sample rate is temporary, worth trying to find issues. The -Z
is case sensitive. -X is another option to block xruns from
shutting things down.

Check synaptic for a newer libfltk, libmxml, zlib libfftw3
supporting yoshimi and rakarrack, press reload first to update files.

/usr/share/alsa/pulse-alsa.conf

if you have this, rename it temporarily and try phasex again.

You can try various linux live CDs/dvds, dynebolic, avlinux have
things preinstalled, you can install apps in a live session for
testing, so Mint or Bodhi (400 meg iso) based on ubuntu can be
used, different kernels/alsa details can be important.

I have an maudio pci soundcard and nvidia graphics card, maybe
the most compatible way to use linux audio. If you can buy or trade
in that direction, it will help in the longrun. I have many years of
hassle free recording.
Cheers

---

