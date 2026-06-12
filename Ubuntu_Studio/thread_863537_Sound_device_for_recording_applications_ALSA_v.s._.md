---
title: "Sound device for recording applications ALSA v.s. Firewire"
date: 2008-07-18
forum: Ubuntu Studio
---

### Post by jukingeo on 2008-07-18
Hello All,

I am considering a new audio interface for my computer that would work in both Windows and Ubuntu Studo.

In this distribution of Linux I would like to know what anyone's opinions are in regards to these devices.  I do have firewire capability on my machine.

My price range is around $300 and I narrowed it down to these devices.

These are my picks.

PCI--ALSA:

Echo Gina 3G

[http://www.echoaudio.com/Products/PCI/Gina3G/index.php](http://www.echoaudio.com/Products/PCI/Gina3G/index.php)

Terratec DMX 6fire (I think this may be discontinued)

[http://alag3.mfa.kfki.hu/dcsabas/hardware/images/Terratec_DMX_6fire_3.jpeg](http://alag3.mfa.kfki.hu/dcsabas/hardware/images/Terratec_DMX_6fire_3.jpeg)


Firewire--Freebob/FFADO

Focusrite Saffire / Saffire LE

[http://www.focusrite.com/products/saffire/saffire/](http://www.focusrite.com/products/saffire/saffire/)
[http://www.focusrite.com/products/saffire/saffire_le/](http://www.focusrite.com/products/saffire/saffire_le/)


A quick overall background is that I was looking for something that had at least 4 inputs and 6 outputs within that price category of $300.

The PCI choices would obviously have the advantage that the sound device can work with the internal sounds and streaming audio without the need for Jack, whereas the firewire devices DO need jack and cannot play system sounds unless some other means of patching the audio into Jack could be attained.  So that is a disadvantage to the firewire devices. The advantage is obvious because the devices are portable and can be moved to another machine.

The Terratec 6Fire is the odd ball of the bunch because it really doesn't quite fit my criteria, yet this box offers a phono pre-amp as well as just about every other type of level imaginable. What more is that it can be installed in the bay of a computer and (almost) everything is accessable from the front.  The huge disadvantage of this device is that everything is unbalanced.  It does have more outputs accessable on the rear of the card though (I believe it is 6 channels total).


The Echo Gina has the least functionality of all the items as it only has 2 inputs and 6 outputs.  But it does have full digital (optical and SPDIF)


In the firewire corner we pretty much have two similar devices, both are in the same series; the Focusrite Saffire and Saffire LE.

The original Saffire has 2 inputs and 8 outputs and while that would not make it too much better than the Echo Gina, what it does have over every other interface here is that it has 192khz capability.

The slightly cheaper Saffire LE, replaces two of the outputs with another set of inputs, making this a 4 in, 6 out box.  The LE part comes into play that this is box can only go to 96khz.


So my questions are as follow and are aimed at those who have set up Linux recording studios of thier own.

1) Do you notice a tremendous difference in capturing the warmth and quality of a recording when using 192khz or 96khz?
2) How easy was it to set up any of the above described units?
3) If you chosen a Firewire/Freebob unit (generally, not fixed to those selected above), how did you managed to get the system sounds and streaming internet sounds to go through Jack?

Thank you for your opinions and advice.

Geo

---

### Post by russo.mic on 2008-07-26
Well, to offer my thoughts, 

The Presonus Firepod should be considered by you.  You can daisy chain up to 3 of them in tandem, allowing for 24 tracks of input.  Don't know you you'll need that, but it's certainly nice to know that you'll have some place to go.  And they run great under Freebob, and offer spdif input and output.


As far as your sampling rate question goes, There really is no need to record at 192 khz.  Your Disc space needs will skyrocket!  and latency will be an issue as well.  Unless your thinking of getting an HD system with a dedicated controller card such as the MOTU HD line, or Protools HD, your bound for trouble. 

Honestly, my career has left me with the good fortune to assistant engineer some known and well respected engineers and most of them are quite happy at 48 khz, 24 bit.  but if you do want to go high rez, consider 88.2 instead of 96 khz.  that way, when you downsample to 44.1 theres less rounding involved (as 88.2 is exactly x2 44.1).  Alot of guys doing DVD sessions and such swear that it comes out better that way. 

Just things I've picked up and opinions i've formed.  If you want to hear some recordings done natively at 48 khz, 24 bit, your welcome to hear a record I just finished up.  

[http://www.myspace.com/baakgwai](http://www.myspace.com/baakgwai)

I did the 1st 3 tracks on there playlist, alabamsterdam, falcor, and dandruff.  Now, it is myspace compression, but see if you can get a sense of it.

Russo

---

### Post by jukingeo on 2008-07-27
> **russo.mic said:**
> Well, to offer my thoughts, 

The Presonus Firepod should be considered by you.  You can daisy chain up to 3 of them in tandem, allowing for 24 tracks of input.  Don't know you you'll need that, but it's certainly nice to know that you'll have some place to go.  And they run great under Freebob, and offer spdif input and output.

I have heard of Presonus before and I would accept that as along the same lines as Focusrite.  However I been on the fence about the whole firewire thing right now because of the recent changeover from Freebob to ffado.  At any rate much has changed and I recently made a huge score on Ebay.  I won an Echo Mona, which is a 4in/6out device.  Its' 4 inputs are all preamped and accept either 1/4" or XLR.  The outputs accept XLR or RCA.  It has both optical and SPDIF digital in/outs too.  There are even front panel meters.  The only problem is that it doesn't have MIDI, but that can be easily handled by an M-Audio Midisport box.  The good thing is that it is a Linux compliant device and it is PCI...so I don't have to deal with the freebob thing or worry about how to get my system sounds to play through Jack.  It is a 24bit/96k unit.

> As far as your sampling rate question goes, There really is no need to record at 192 khz.  Your Disc space needs will skyrocket!  and latency will be an issue as well.  Unless your thinking of getting an HD system with a dedicated controller card such as the MOTU HD line, or Protools HD, your bound for trouble.

I would say that for the most part I would only look to 192khz for mastering very important projects and NOT for regular recording.  I also thought of using it for very rare records that I know are not available on CD.  Again for mastering.  I would say that most of my work I would do in 96k anyway. 

> Honestly, my career has left me with the good fortune to assistant engineer some known and well respected engineers and most of them are quite happy at 48 khz, 24 bit.  but if you do want to go high rez, consider 88.2 instead of 96 khz.  that way, when you downsample to 44.1 theres less rounding involved (as 88.2 is exactly x2 44.1).  Alot of guys doing DVD sessions and such swear that it comes out better that way. 

I have not heard how 88.2 khz sounds, and given your advice, I think I will give it a shot with a few test recordings.  I know for a fact though that 48k isn't enough for me.  A while back I had a 48k studio based on hardware equipment.  I had a Tascam DA-88 and it's output was mixed via a Mackie mixer (analog) and then mixed down to a Tascam DA-30 two track digital recorder.  Anyway, I never liked the sound of this setup.  I didn't even sound as good as my four track CASSETTE unit...let alone my old 8 track reel to reel set up.  Needless to say, the digital conversion cost me a fortune and my sound really didn't improve any.  In fact it had a more sterile sound.  My old analog studio was better.  It was later I talked to a recording studio guru and he said that because of my digital-analog-digital (and in the case of a cassette deck another analog step was included), I was experiencing 'zipper distortion', and the only way to fix that would be to go with a higher sampling rate...such as 96k.  At any rate I put digital aside for a long time and then I heard an analog manipulated 192khz recording of one of my old records which was pumped through a tube pre-amp and the sound was beautiful.  I couldn't tell that it was analog and I could say the resultant mixed sound was pretty much an exact copy of my record.  I say pretty much because all the crackles and pops were digitally removed from the record.  So in that aspect...it sounded better and of course I right away fell in love with the 192khz sampling rate.

But I do know it is a hog and at that time 192khz equipment could only be had through pro-tools and I couldn't afford that.

But over the years as prices came down on equipment and techology advanced for computers, I realized that I DON'T have to have an intermediate analog stage at all.  Thus for CD, DAT recordings there would only be ONE A/D conversion and that is at the point of entry to my audio device on the computer.  All the mixing editing would be done in digital.  Furthermore the mixdown could also be handled digitally in the case of going to a CD or DAT.  So by removing all the extra analog/digital conversions.  I would think that I could possibly fair well with 96k, or as you pointed out 88.2.  I never tried that frequency before. But I do hear you out and I know exactly where you are coming from.

For example video photo editing.  I have noticed that multiples seem to produce the least image distortions.  So exactly doubling or halving the size of a photo is best.  Going for odd values seems to increase the distortion a bit more.

So if that theory applies to audio as it does video then I can see where you are coming from.  At any rate, it is worth a shot because if there is little difference between 96k and 88.2k, I sure can save some disk space.

> Just things I've picked up and opinions i've formed.  If you want to hear some recordings done natively at 48 khz, 24 bit, your welcome to hear a record I just finished up.  

[http://www.myspace.com/baakgwai](http://www.myspace.com/baakgwai)

How about a comparison. Do some recordings at 48k and then at 88.2k.  I would like to hear the difference.

Anyway, thanx for the 88.2 tip.  It was something I didn't think of before.

Geo

---

### Post by russo.mic on 2008-07-30
I'm actually doing a session today, i'll record at 88.2 for the hell of it.  after all, disk space is cheap!  Hey, if you've not given it a read, I can recommend bob catz's book on mastering.  He litterally wrote the book on it so to speak.  Possibly it can be found on a website named after some criminals of the sea.

russo

---

### Post by ussndmac on 2008-10-02
Hi,

I am considering an FP10 on a laptop running Ubuntu 804.

Do you use the rt kernel?

Have you used the FP10 on a pc platform (I see from posts you use a mac.)

Best Regards,
Mac

---

### Post by jukingeo on 2008-10-02
> **ussndmac said:**
> Hi,

I am considering an FP10 on a laptop running Ubuntu 804.

Do you use the rt kernel?

Have you used the FP10 on a pc platform (I see from posts you use a mac.)

Best Regards,
Mac

Yes, I have the RT kernel.  I made the decision to go with something that is easy on the pocketbook and settled on the M-Audio Delta 44 (A PCI based card).  I just got yesterday and installed it last night.  I have not dabbled with it too much but I do have audio in all my Linux distros, so that is a major plus from where I was.

I may eventually look down the road at the firewire devices once FFADO gets fully underway.

Geo

---

