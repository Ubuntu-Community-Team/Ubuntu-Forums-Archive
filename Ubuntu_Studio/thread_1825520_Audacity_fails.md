---
title: "Audacity fails"
date: 2011-08-15
forum: Ubuntu Studio
---

### Post by astuc on 2011-08-15
When I try to open a file the program locks up until I reboot. It reminds me that my favorite FTP app FileZilla would not work at all. I just want to cut and paste sound files but don't know much about it. How can I make Audacity work?

---

### Post by jejeman on 2011-08-15
Run it from terminal, maybe it show something.

---

### Post by astuc on 2011-08-15
wilf@asavetheuniverseclub:~$ audacity&
[1] 2352
wilf@asavetheuniverseclub:~$ ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1666
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1826
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2088
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2760
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4537
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4537
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4537
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4537

---

### Post by sgx on 2011-08-16
Hi, what soundcard/chip are you using? It sounds like
too many audio options are trying to access the card.
In audacity menu   Edit --> Preferences -->Devices

choose alsa

For editing, you don't need jackd/qjackctl, or pulseaudio.

Run the command

ps ux

look in the output for those types of names, and quit the program
using them, or use the command

killall name-of-pulse    killall jackd

Then start audacity, and use the import audio option to load a file
for editing, and the export audio option to convert formats, and export the results. Saving will save a project of audacity files, for later use. These van be loaded, instead of imported.

There is an option to use a copy of a file, instead of working on the original, very good to use this option.

Cheers

---

### Post by astuc on 2011-08-17
Intel Corporation 82801H HD Audio Controller is the sound card. Thanks a lot for you concise instructions! On the ps ux it did not show any of those names. On killall name-of-pulse    killall jackd it said there were no processes running. Alsa is selected. I attempted to inport a .wav file that I made with Sound Recorder. As soon as I selected the file Audacity became unresponsive and had to reboot just to get it out of the way.

Later in the day I re installed Audacity and now it works! Thanks!

---

