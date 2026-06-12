---
title: "Configure Realtek ALC888 with alsa for frequencies &gt; 20 kHz"
date: 2014-03-11
forum: Ubuntu, Linux and OS Chat
---

### Post by katutxakurra on 2014-03-11
Hi,

I'm using an atom-pc with Ubuntu 12.04 and alsa to control an audio card Realtek ALC888.
I need to send and receive frequencies in the range 0 - 40 kHz.
So far I cannot see anything above 20 kHz.
Could anyone please help me to find out if this is possible and how to do it?

Thank you

---

### Post by lykwydchykyn on 2014-03-11
The Nyquist theorem tells us that the maximum frequency you can represent in digital audio form is 1/2 the sampling rate.  
Most consumer-level audio samples at 44.1kHz by default, so 22050 Hz is the maximum frequency you can record.

You need to set your sampling rate to something like 96kHz to get up to 40 kHz audio frequencies.  Looks like the hardware is capable of doing this, are you having issue setting your software to record at that rate?

---

### Post by katutxakurra on 2014-03-11
Hi and thanks for your answer.
Yes, I've tried setting the sample frequency to 96kHz. 
I then tried to send a sine signal to the audio card and measure it with an oscilloscope.
Anything above 20kHz gets converted to 20kHz. It looks like the alsa driver is setting that cut off frequency for the Realtek ALC888.
Sorry if I didn't explain my question correctly in the first place.

---

### Post by lykwydchykyn on 2014-03-12
What are you recording into?  Audacity?  Is it posssible playback is being filtered or resampled?

---

### Post by katutxakurra on 2014-03-13
I'm not recording it. I have an oscilloscope in the jack connector that outputs the sine signal.

---

### Post by lykwydchykyn on 2014-03-13
Ok, I was confused I thought you were recording.  How did you go about setting the sampling frequency to 96kHz for playback?

---

### Post by katutxakurra on 2014-03-21
Thanks for your help.
I managed to solve it editing the /usr/share/alsa/alsa.conf and setting the 
defaults.pcm.dmix.rate 96000

---

