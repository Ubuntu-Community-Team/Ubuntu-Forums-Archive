---
title: "Allowing User to Create Real-time ALSA Thread for Specific Programs Only"
date: 2009-04-27
forum: Ubuntu Studio
---

### Post by GenuineXP on 2009-04-27
Howdy. I've been playing around with some solid audio applications that often require exclusive access to ALSA (or JACK, but for various reasons I avoid installing it). They also need permission to create real-time ALSA threads.

In the past, I've accomplished this by creating an audio-rt group, adding myself to it, and allowing that group to create high priority threads via PAM. This seems dangerous though, because being a part of the audio-rt group doesn't just mean a user can create real-time threads for use with ALSA/audio, but for anything! Isn't this a bit dangerous (for example, if a program hogs the CPU *and* has a negative nice value)?

Is there some way to restrict the creation of real-time threads, perhaps for specific programs? If not, is there at least some way I could grant real-time threads for ALSA without granting real-time thread creation for anything?

If there's a good way to accomplish this without PAM, that'd be fine too. :)

Thanks!

---

### Post by GenuineXP on 2009-10-16
Bump. Still haven't solved this (potential) problem.

Just in case it's helpful to mention, the program in question is Renoise. At least, that's the one I'd like to get to work the most.

Is there no way to grant specific application/user pairs special permissions? Just specific applications at least? This seems like something that could be very handy in general.

---

### Post by kayosiii on 2009-10-17
My understanding is that an application does not automatically take more resources because it has permission to do so It must also specifically ask for those priveleges - *most alsa apps do not do this*... 

The situation is a bit different with jack since jack applications essentially share the same low level code. In jack ecosystem jackd itself is the only thing that should need elevated privileges.

I am a bit puzzled as to why you wouldn't use jack, Linux is not much of an audio platform without jack.

---

### Post by GenuineXP on 2009-10-19
Thanks for the reply. :-)

I don't want to install JACK unless I have to because it doesn't play nice with PulseAudio. If the Renoise developers added support for Pulse, I'd be very happy. I also use this system as a general desktop platform, so it can be a pain having to track which audio server is running and constantly enable and disable them. However, I *do* have to disable PulseAudio in any case to use Renoise so that it can take exclusive control of ALSA.

I'm aware that it's actually possible to route JACK through Pulse, but I've read that it causes terrible latency.

I guess I could use setuid, but that would be essentially the same thing as just running Renoise manually as root, right?

In the end, using a supported sound server is probably the best solution. :-P

---

### Post by sgx on 2009-10-20
jackd was there first, use synaptic total removal on pulse, to experience
audio with fewer hassles. Then install jackd and qjackctl.
Cheers

---

### Post by VertexPusher on 2009-10-20
> **GenuineXP said:**
> I don't want to install JACK unless I have to because it doesn't play nice with PulseAudio.
Jack is just an application like any other. Low latency audio requires exclusive access to the sound card, so if you want an application to take advantage of that, it will conflict with PulseAudio anyway.

You can either configure PulseAudio to run as a Jack client itself, or suspend or remove it to get it out of the way. However, PulseAudio will never replace Jack.

---

### Post by kayosiii on 2009-10-20
pulse and jack are designed for two different target audiences.

Jack is designed for professional audio use, the priorities are high output quality, guaranteed low latency, ability to pipe audio between different applications. Jack especially on Ubuntu is not easy to set up properly.

Pulse-Audio is designed for standard desktop use, the priorities are overall ease of use, low power usage, low latency is not really a primary design goal - though pulse can now aquire realtime privileges on some systems (not ubuntu) which may help this last thing a bit.

The latest versions of pulse will get completely out of the way when jack tries to run. (this feature is currently not available on Ubuntu).

If latency is not that important to you - and depending on what you do it may not be and you plan to use only one audio application then pulse may do the job for you. Otherwise the benifits of jack may be difficult to ignore.

---

### Post by markbuntu on 2009-10-22
By default jack will suspend pulseaudio when it starts in all versions of Ubuntu from Hardy to Karmic if you have installed over Ubuntu via the Ubuntustudio-audio metapackage. if it does not, it is very easy to fix just add

pasuspender

to the jack launch command.

In karmic new udev rules will suspend pulse when jack starts. At least that is how it is supposed to work and what the pulse and jack devs have worked out.

---

