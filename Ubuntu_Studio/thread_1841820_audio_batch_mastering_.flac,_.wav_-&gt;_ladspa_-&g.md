---
title: "audio batch mastering: *.flac, *.wav -&gt; ladspa -&gt; jamin -&gt; *.mp3, *.ogg"
date: 2011-09-10
forum: Ubuntu Studio
---

### Post by Marek Cupak on 2011-09-10
hello folks,

looking for the best way how could i process lots of FLACs, or WAV files. for each file, i need to apply some LADSPAs (for example somehow configured CALF reverb), then master it in Jamin (EQ, compressors, limiter, etc. - settings stored in JAM file) and finally convert them into MP3s and OGGs with specific bitrates and ID3 tags from source files

so, how do i script all these things together? thanks in advance for each reply

a bonus would be running it on all CPU cores simultaneously, just to have the results asap

---

### Post by sgx on 2011-09-10
Hi, put these in google, there should be many command line examples in the responses that you can modify

ffmpeg flac wav mp3 batch convert

in addition to ffmpeg, mencoder may be useful, as well as sox, for batches of ladspa processes.

easytag is a gui tool for batch editing tags by the folder or playlist

Cheers

audacity may be useful to,
 
[http://manual.audacityteam.org/man/Batch_Processing](http://manual.audacityteam.org/man/Batch_Processing)

---

### Post by Marek Cupak on 2011-09-10
audacity does really cool batches with its chains of effects applied to each selected file, and conversions too, but... only built-in effects, no ladspa processes.

lame and oggenc can do conversions into MP3 and OGG. soundconverter too, but dunno how to force bitrate when called from command line only

well, going down to "man sox" :)

---

