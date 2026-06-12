---
title: "Can't get audio recording working..."
date: 2011-06-24
forum: Ubuntu Studio
---

### Post by wrybread on 2011-06-24
I installed Ubuntu Studio with hopes of recording with Python using Pyaudio, but its turning out to be much more complicated than I expected. At this point I can't even get Sound Recorder (gnome-sound-recorder 2.32.0) to record any audio. 

What I've done:

- gone to AlsaMixer, hit tab to go to "capture" devices, and set the Mic as the capture device

- plugged an audio source into the mic jack of my soundcard

Nothing.

- went to File --> Open Volume Control from Sound Recorder, to open Sound Preferences. Tried a few different inputs, nothing.

- tried Audacity, couldn't get anything using Alsa. Started Jack and could record sound! But then when I restarted I couldn't record sound any longer. Also, I'd rather not use Jack, since I'm trying to build an automatic continuous sound recorder, that records 24/7, so the simpler the better.

I don't imagine anyone has any tips?

---

### Post by sgx on 2011-06-24
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

This should help. Install the recording app
timemachine using synaptic, or get it here:

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

and install with this command:

sudo dpkg -i timemachinexxx.deb  

(copy/paste the title of the timemachine version you download)

Its default file format is .w64, but you can also choose .wav

audacity can import, edit, convert, and export them.

More links are here:  [http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

and youtube videos of ardour, hydrogen, and zynaddsubfx often
detail the jackd connections, and recording options.

Cheers

---

### Post by wrybread on 2011-06-24
Do I *need* to use Jack if I'm simply recording the input from a soundcard? In other words, I don't need to share audio between applications, and I don't care about latency, I only want to record an audio file... 

I'm surprised that's so complicated, especially in a Linux distro built for multimedia?

I'm setting up an archiver for a radio station, that records everything that comes from the mixing board, and splitting the files into hour chunks for podcasting. Ideally it'll be recording for months or years without a reboot. I'm worried that introducing complexities like Jack is asking for trouble somewhere down the line.

---

### Post by cchhrriiss121212 on 2011-06-24
No you don't need jack at all. If you had jack working, then ALSA should work fine, as jack uses ALSA as it's backend, this should just be a matter of selecting the right input channel and checking it is not muted. 
Type arecord -l into a terminal to see what your channels are. Type alsamixer into a terminal to set volume levels. 

For what you are doing I think arecord + cron would work just fine (assuming you are cool with using CLI?). Here is a thread where I helped another user set up something similar (2nd page):
[http://ubuntuforums.org/showthread.php?t=1659529](http://ubuntuforums.org/showthread.php?t=1659529)

> I'm surprised that's so complicated, especially in a Linux distro built for multimedia?
This is linux, everything is more complicated than it should be. :)

---

