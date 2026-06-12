---
title: "digital voice recorders"
date: 2009-06-04
forum: Ubuntu Studio
---

### Post by jodianne on 2009-06-04
Hi! I am looking for a simple (and cheap) digital voice recorder that is compatible with Ubuntu. Any information would be helpful!

Thank you!

---

### Post by igorzwx on 2009-06-04
I tried iRiver E100

It is not very cheap.
No AGC
very sensitive mic

But it might be an interesting option.
It depends on what you are going to record... :)

---

### Post by jodianne on 2009-06-04
Thank you! I was hoping to find something cheaper, but this should work. My only thought is that it has more features than I need (e.g., screen).

Thanks again!

---

### Post by igorzwx on 2009-06-04
Some sociologists said, as I remember, that mic is really very sensitive...
If you turn paper of your script with questions, it can record a loud noise.
2 meters from a speaking person might be optimal.

The absence of AGC is not a big problem.

Apply a Chebyshev filter

Install SoX 

sudo apt-get install sox  

Install Steve Harris's LADSPA plugins (swh-plugins) 

sudo apt-get install swh-plugins 

Filter:

     sox in.wav out.wav ladspa highpass_iir_1890 65 10 ladspa 
lowpass_iir_1891 12000 10 norm

Then my "non-linear compressor" with Audacity

[http://n2.nabble.com/Nonlinear-Compressor-Expander-Classic---Nyquist-plugin-for-Audacity-td1692523.html#a1692523](http://n2.nabble.com/Nonlinear-Compressor-Expander-Classic---Nyquist-plugin-for-Audacity-td1692523.html#a1692523)

 Then filter once more:

     sox in.wav out.wav ladspa highpass_iir_1890 65 10 ladspa 
lowpass_iir_1891 12000 10 norm

see also:
[http://n2.nabble.com/user/UserNodes.jtp?user=126956](http://n2.nabble.com/user/UserNodes.jtp?user=126956)

---

### Post by cpetercarter on 2009-06-04
I use an Edirol R-09 with an external condenser mike. It is slightly bigger than a pack of cigarettes, uses either mains power or batteries and records either as WAV or MP3. Simply plug it into a USB port to download recordings to Audacity for editing.

---

### Post by igorzwx on 2009-06-04
Great podcast!
Many thanks for the link!
Could you please enlighten me about "external condenser mikes"?
I am going to buy one for similar purposes.
Could you please give an advice?

---

### Post by cpetercarter on 2009-06-05
The Edirol R-09 has a built-in microphone, and many people find that it works well for the sorts of recordings that they want to make. But you can also plug in an external microphone if you want.I use an Audio-Technica PRO 24 microphone, but there are many others which are equally suitable. If you decide to go with an Edirol recorder, try using it with the built-in microphone first, and buy an external mike later if you need one.

I am glad you like the podcasts! They run on an Ubuntu server, naturally!

---

### Post by igorzwx on 2009-06-05
Many thanks for the hint!
I will certainly try Audio-Technica PRO 24 mic with iMic, and a notebook running on accu.
Can you name other suitable mikes? 

Your podcast is really very nice!
I have already subscribed to it with Rhythmbox and grabbed
everything what is available for download.
And I sent the link to all my friends who might be interested in.
And to the faithful, as a good example :)

I really love your podcast!
And, therefore, I believe I can permit myself to say something about
the quality of recordings.

(You are allowed to say something about the quality of my English :) ).

The technical performance is not very impressive...

I downloaded your mp3:
ListEngPodcast-2009-06-01-53348.mp3

and studied the spec of the noise.

Subsonic noise: 8Hz -22dB 

Quasi-hum:
42Hz - 31.4dB
65Hz - 33.3dB

Hum 50Hz with odd overtones:
50Hz -28.6dB
150Hz -32dB
250Hz -37dB
350Hz -46dB
and so on

Even overtones of 50Hz hum:
100Hz -38.4dB
200Hz -40dB
300Hz -43dB
400Hz -42dB
and so on

If it was really Edirol with a condenser mic, 
I would not buy such things for 10 Euro.
Was that an ALSA recording with Audacity on PC?

To summarize:

1. Edirol R-09HR MP3/WAV Recorder 339 Euro amazon.de

2. Audio-Technica PRO 24 microphone 99 Euro [www.thomann.de](www.thomann.de)


An alternative solution:

1. a new notebook for 340 Euro
2. iMic for 30 Euro
3. a cheap headset for 20 Euro

And the result will be excellent recordings without noise.

see also: 
[http://n2.nabble.com/New-experiments-with-recording-audio-on-Ubuntu-9.04-%28ALSA-vs.-OSS%29-td3026230.html](http://n2.nabble.com/New-experiments-with-recording-audio-on-Ubuntu-9.04-%28ALSA-vs.-OSS%29-td3026230.html)

---

### Post by igorzwx on 2009-06-07
A friend sent me his recordings made on Olympus LS-10

I would buy Olympus LS-10, or nothing at all.

All the kids who record sound on computer should try this thing first.

Uncompressed 24 bit/96kHz Linear PCM recording capability, to capture the rich sound quality of music performances.
Can record 14 hours on two AA batteries.
The LS-10 can play back the high-quality audio it records and play it back on its built-in stereo speakers with vibrancy and clarity.
The LS-10 has two gigabytes of internal flash memory to capture lengthy recordings. It also features an SD/SDHC removable media card slot to further expand its capacity
WAV, MP3 and WMA recording and playback

---

