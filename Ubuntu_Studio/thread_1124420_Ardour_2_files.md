---
title: "Ardour 2 files"
date: 2009-04-13
forum: Ubuntu Studio
---

### Post by Icebear on 2009-04-13
Hi

 I am trying to record some audio books. I am using ubuntustudio 8.10 with a saffire LE audio interface with Ardour. I am using different readers. So if I save each reader as a different file. How can I then later import the different Ardour files together. I have upgraded to Ardour 2.8 so not to have the bug of importing files. But that option means I have to export the different readers to wave (or something) then Adour then convert it when importing it.

---

### Post by kayosiii on 2009-04-14
I think you ran foul of this bug

[https://bugs.launchpad.net/ubuntu/+source/ardour/+bug/279723](https://bugs.launchpad.net/ubuntu/+source/ardour/+bug/279723)

---

### Post by bolex100 on 2009-04-14
Sorry to sound stupid but I don't see the problem. 

1/ You are recording some readers ( i assume you mean "people reading" ).  What are you using to record them?  Does it not output a wav file?  Even if it doesn't, I always used to convert everything to wav before use.

2/ You are using the version of Ardour that isn't broken so you just import the files.

3/ You put your project together.

4/ You output a wav file.

What am i missing?

---

### Post by Icebear on 2009-04-15
SO in Ardour if I export a file to a wav. Then later I import the wav file to another session with Ardour I loose no quality.

---

### Post by thorgal on 2009-04-15
wav is an uncompressed lossless format, so what would you lose any quality ?

What matters is that you record all your material at the same sample rate and bit depth. Ardour will anyway convert all these files to 32bit floating point internally, in order to respect the original quality of the wav files, so do not worry my friend ;)

---

### Post by Stochastic on 2009-04-15
If you want you can save yourself the export step by simply importing from the other Ardour session internal file.

If your ardour folder is /home/you/recSession/ then all the internal audio files can be found at /home/you/recSession/interchange/recSession/audiofiles/
These are mono 32bit float wav files that most other programs can't use but can be imported into your new ardour session just fine - although all stereo tracks are split into two files.

The conversion from 32bit to 16bit on export does actually loose a bit (read *miniscule ammount*) of quality. This is assuming that Ardour uses dithering in the bit conversion process (what they should be doing). But you'll only notice this difference if you're playing around with the noise floor a lot or if you're going through this export/import an extraordinary ammount (like thousands of times). It could also loose some miniscule (read inaudible) quality for files that have been time stretched. It also doesn't have to happen - the settings allow you to export to whatever bitrate you desire.

Essentially unless you're mastering an album you really don't need to worry about quality loss as you move between Ardour projects - just hard drive space.

---

### Post by Icebear on 2009-04-16
Thank you Stochastic for your input. I really appreciate it.

---

