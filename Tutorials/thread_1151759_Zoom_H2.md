---
title: "Zoom H2"
date: 2009-05-07
forum: Tutorials
---

### Post by jwkungfu on 2009-05-07
Hi folks!

Time for me to repay Ubuntu!

I have just purchased a Zoom H2 Handy (Audio) Recorder.
Just plug it in and set it to USB and you will be able to access the files that are saved onto it's SD card.

Now here's the good bit...
The manual says that for the unit it to work as a USB microphone you need the 'obvious' operating systems <yawn>....
I found this command on another Ubuntu forum thread...

```
sound-recorder -A /dev/dsp2 -c 2 -s 44100 -b 16 -f wav -S 00:10 foo.wav
```

Copy and paste that into a terminal (make sure the H2 is set to USB microphone)

Voila!!

***Note*** for subsequent recordings you will have to change the 00:10 to the desired about of time you wish to record for (00:10 is 10 seconds) and also change foo.wav to something else eg. fo1.wav

ENJOY!!! :)  :guitar:

---

### Post by jpeddicord on 2009-05-11
Approved; thank you for your tip contribution. :)

---

### Post by SteveNorman on 2009-06-22
In audigy under edit>preferences>recording devices it showed up in my drop down menu just fine.

---

### Post by jwkungfu on 2009-06-23
Excellent!
By Audigy do you mean "Audacity"...?
I went to Applications > Add/Remove.... typed in Audigy... nothing?
So I'm guessing Audacity & Audigy are the same?

What do you think of the Zoom H2?
I have only played around with my H2 a little so far... but so far, so good!
A great little unit!!

Cheers!
jw.

---

### Post by treesurf on 2009-06-23
I recently purchased a Zoom H4n, and was also pleased to find that Audacity recognized it with no problems.

---

### Post by prince.buster on 2010-01-26
confirmed with the H4n in Karmic.

appears as a device in audio settings and in audacity.

but how do we get it to appear in JACK (with all 4 channels)?

EDIT: 2 channels is simple, just select it as the interface in the qjackctl setup dialog

is it possible to expose the built in microphone plus external imputs simultaneously in JACK (4 channels)?

also, exposing the H4n _and_ your internal soundcard simultaneously in JACK is another thing altogether... but it can be done.

---

### Post by gunterkoenigsmann on 2013-03-14
Did write a small command line tool that converts the two stereo files the Zoom H2N generates in the surround recording mode into one 4-channel flac file that can lateron be edited by standard tools like audacity or can be imported into kdenlive: [https://launchpad.net/h2n2flac/](https://launchpad.net/h2n2flac/)
ppa:[https://launchpad.net/~peterpall/+archive/h2n2flac](https://launchpad.net/~peterpall/+archive/h2n2flac)

---

