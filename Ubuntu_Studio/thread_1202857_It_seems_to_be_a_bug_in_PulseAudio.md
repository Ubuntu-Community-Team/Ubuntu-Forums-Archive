---
title: "It seems to be a bug in PulseAudio"
date: 2009-07-02
forum: Ubuntu Studio
---

### Post by igorzwx on 2009-07-02
Hi all!

When I changed from Ubuntu 6.10 to Ubuntu 9.04,
I noticed a very strange behaviour of Audacity. 

The playback of Audacity was essentially distorted, and the quality of recordings was dramatically reduced.
It took a lot of time to fix the problem.

The magic solution is: "sudo killall pulseaudio"

Now I can hear the true sound in Audacity and I can record without overtones of 50Hz!

The the noise in recordings is much smaller!!!
ALSA is working well now!

I do not want to remove Pulse completely for many reasons.
Without Pulse I would have a lot of other problems.

Pulse is actually a great thing, but...

Many thanks Tibasic for his "howto":
Getting Audacity to Record (when time stuck at 0):
[http://ubuntuforums.org/showthread.php?t=936448](http://ubuntuforums.org/showthread.php?t=936448)

Best,
Igor

---

### Post by ajgreeny on 2009-07-02
You could just set the sound devices in audacity preferences to use alsa, surely, as I have.  If I try and use pulse I can not record anything nor play it back,  I just get error messages, but I don't have to kill pulse system-wide for the audacity session.

---

### Post by igorzwx on 2009-07-02
Hi Ajgreeny!

many thanks for advice.

But it does not help (Ubuntu 9.04)

I should first kill pulse, then start Audacity, then select ALSA:mysoundcard

This works for the internal sound card.

But it does not work for iMic USB

If you plug in iMic USB, pulse restart.
I killed it once more.
And now I can record only with command line tools from USB.
But when I record with arecord:

arecord -D plughw:1,0 -d 10 -r 44100 -c 1 -f S16_LE -t wav alsa-exp-2.wav

or ffmpeg:

ffmpeg -f oss -ar 44100 -ac 1 -i /dev/dsp1 -acodec pcm_s16le mumuv-dsp1.wav

I get odd overtones of 50Hz as before.

You see, you cannot record from USB devices without pulse.

On another computer, I have already removed both ALSA and Pulse and installed OSS4.
OSS4 records well from the internal sound card. But you cannot use USB audio devices
at all. Ekiga does not work yet, but Skype works well.

Best,
Igor





[U]

[/U]

---

### Post by igorzwx on 2009-07-02
My experiments with test audio files and Pulse (Ubuntu 9.04, old IMB notebook)

How to create test file

1. Audacity -> Generate -> Silence (5 seconds are enough)

2. Effects -> Nyquist prompt 

3. type the command:  

(mult (sum (hzosc 10) (hzosc 19500)) 0.45)

or copy-and-paste to Nyquist prompt (paste with Ctrl+V).

This produces a simple mix of 10Hz and 19500Hz (sine waves)

Export this as wave.

EXPERIMENT:

1. Open the test file with Audacity and play it
Result: strange sound

2. Close Audacity.

3. Open Terminal and type:

$ sudo killall pulseaudio

4. Open the test file with Audacity.

5. Audacity-> Preferences -> Audio I/O and open Devices

   The pseudo-OSS devices (such as /dev/dsp) vanished from the menu

6. Select your sound card: ALSA:Intel ...

7. Play the test file. No sound now!!!

8. Change to ALSA:pulse (or ALSA:default) and you hear strange sound again

---

### Post by igorzwx on 2009-07-03
The playback of OSS4 seems to be different from that of ALSA.
One of them might be wrong.
Does ALSA contain a kind of equalizer too?

---

### Post by igorzwx on 2009-07-03
The difference between ALSA and OSS4 seems to be
in high frequencies.
ALSA may have a kind of equalizer inside.
What might be a reason for such equalizer?
If you want to suppress hiss...
This should be verified.

---

### Post by igorzwx on 2009-07-04
QUOTE:
"The ALSA's OSS API emulation, however, is often buggy."
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

What does it mean?

Let us make an experiment with OSS4
(I have it installed on an old box for experiments)

Run jackd

jackd -d oss

run Ardour

record something.

run Audacity

record something

Now listen to your recordings.
The quality is bad. Clicks, etc.

Look at the spectrogram of noise - overtones of 50Hz

Close Ardour and Audacity

killall jackd

run Audacity

record something

Listen to your recordings.
Good quality, the same as with ossrecord

Look at the spectrogram of noise - no overtones, they disappeared
together with jack.

You see, if PulseAudio is buggy, it can cause similar problems with ALSA.

---

### Post by igorzwx on 2009-07-04
A clear-cut experiment with Audacity Nyquist.

1. Run Adacity

2. Audacity -> Generate -> Silence (5 seconds are enough)

2. Effects -> Nyquist prompt 

3. type the command

(mult (hzosc 50) 0.9) 

or copy-and-paste (paste with Ctrl+V)

This produced a sine wave of 50Hz.

4. Ctrl+A (select the entire wave)

5. Effects -> Nyquist prompt 

6. type the command

(clip s 0.5)

Now the wave is clipped.

7. Mark a part of the wave.

8. Analyze -> Plot Spectrum

And you see odd overtones of 50Hz.

Listen to it! Does it sounds similar to the noise in your recordings?

What is more, a non-linear transformation of amplitude, such as tanh, for example,
can also produce overtones.

This is how PulseAudio produces overtones of 50Hz on
my notebook when I record something.

---

