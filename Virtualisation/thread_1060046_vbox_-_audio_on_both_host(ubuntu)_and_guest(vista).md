---
title: "vbox - audio on both host(ubuntu) and guest(vista)?"
date: 2009-02-04
forum: Virtualisation
---

### Post by Nareto on 2009-02-04
Hello, i'm running on Intrepid 8.10, have succesfully installed virtual box and windows vista as guest. 

Is it possible to have audio simultaneously from vista and ubuntu?

I'm having this problem: audio on ubuntu is working fine until i power on vista - from that moment on i can hear audio from the vista virtualization (from *that* moment - even the "welcome" sound) but i can't hear anymore audio from ubuntu: vlc will open audio and video files and play them with no sound, while flash player in firefox (youtube, myspace etc.) will load files but won't even play them - if i press play the cursor will just stand still.
When the vista vm is completely shut off, i can again hear sound on ubuntu.
This is happening with the ICH AC97 chosen as the emulated soundcard in the virtualbox settings for the vista vm; if i chose Soundblaster 16, audio on ubuntu will still stop working, but vista will find no sound card at all (have to say though that till now, through installation and everything, i've used ICH AC97 so it may simply be drivers missing)

I tried starting vista while a file in vlc was correctly playing, and i got the following pop-up window from vbox
```
Some audio devices (PCM_out) cold not be opened. Guest applications generating audio output or depending on audio input may hang. Make sure your host audio device is working properly. Check the logfile for error messages of the audio subsystem.

Erro ID:                HostAudioNotResponding
Severity:               Warning

```
then i closed vlc, and when vista booted up still same problem: audio ok on vista, no audio on ubuntu.

if, while vista is running, i try the audio test utility in the Sound module, under Preferences (in Ubuntu) i get the following:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.
```

It seems to me it could just be a misconfiguration of sound on ubuntu, but i have no more precise idea.

---

### Post by Nareto on 2009-02-06
up. Do you think i should post this on the virtual box forum too?

---

### Post by Nareto on 2009-02-07
Please someone tell me if it's happening only to me or if it's normal that audio is exclusive between host and guest

---

### Post by Ng Oon-Ee on 2009-02-08
Are you using the default soundserver on Intrepid (I presume you are)?

If so, just set your sound output in VBox to Pulseaudio instead of Alsa or OSS (which is probably what you're using now.

PulseAudio is a sound server, its MEANT to play sounds from various apps simultaneously. ALSA and OSS don't, though ALSA has a dmix plugin which does if you enable it (not sure if its enabled by default).

But ya, try that out and then post back here if it works. I'll check back when I can.

---

### Post by Nareto on 2009-02-08
Thank you very much, that did it ;)

---

### Post by Ng Oon-Ee on 2009-02-08
You're welcome, I'm glad you didn't experience any OTHER audio problems. Intrepid's Pulseaudio implementation must be pretty good out of the box :)

---

### Post by BryanFRitt on 2010-05-23
[FONT="Courier New"]sudo apt-get install pulseaudio[/FONT]
and setting the VM to PulseAudio got it working for me.
Thanks Ng Oon-Ee!

---

