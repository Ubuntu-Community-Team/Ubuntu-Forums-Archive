---
title: "Converting Wav Sample rate to 96k"
date: 2010-08-30
forum: Ubuntu Studio
---

### Post by Sylos on 2010-08-30
Hello and thanks for looking.
I have a nice little Maudio delta card that is capable of running at 96k sample rate so, in the interests of getting the best quality I have switched it to this mode.

As a result all my hydrogen drum samples and samples for soundfonts need resampling to 96k so they dont sound all high pitched and weird.

Can anyone give me a way of doing all WAV files in a directory to 96k as I am currently going doing them 1 by 1 in Audacity and I fear for my sanity if I have to continue this way. 

Im using the Hardy version of Ubuntu Studio and I have Sox installed but I cant figure out how to use it (Im a simpleton I know).

Many Thanks

---

### Post by Jormeliini on 2010-08-30
Here's a short script for you.

```

#!/bin/bash
# list all files ending with text "wav" to FILES variable
FILES=`ls *wav`
# loop through FILES
for f in $FILES
do
	# converts a file. new file is named as resample_<original filename>
	sox $f -r 96000 resample_${f}
	# renames resampled file as original file
	# original file is overwritten
	mv resample_${f} $f
done

```

Save it to a file, for example resample.sh, in the folder you have your wavs. Make sure you have back-ups of the wav files in some other folder. Open terminal and go to the directory where your wavs and the script are.

Add execute permission by following command.

```
chmod +x resample.sh
```

Then run the script.

```
./resample.sh
```

Now your wavs should be 96 kHz wavs.

---

### Post by tgalati4 on 2010-08-30
If sox is not installed then:

sudo apt-get install sox

---

### Post by RaumTrug on 2010-08-30
"offtopic": wtf...!!!11!1elev'n??? those programs play back samples in different speeds depending on the master sample rate they're (the sound card is) running at? sorry...but I can't believe any serious sampler-like software has a serious limitation like that!!! please clarify for me what program does mad things like that, and under which circumstances.

sounds to me like a bug that needs urgent fixing, really. resampling source-samples should not be the way to adjust for proper playback speed, the prog. should resample either when loading, or on the fly while playback!

---

### Post by Jormeliini on 2010-08-31
> **RaumTrug said:**
> sounds to me like a bug that needs urgent fixing, really. resampling source-samples should not be the way to adjust for proper playback speed, the prog. should resample either when loading, or on the fly while playback!

At least on my system resampling on the fly works just fine with ALSA (using pulseaudio) and JACK. Can't remember if there was something wrong in Hardy.

---

### Post by Sylos on 2010-08-31
Hi guys and thanks for the input.

Jormelini: Thanks for the script. I havent tested that one out to see if it works as I found another one on the Hydrogen Drum Machine forums that worked for me (hadnt returned to the forum to update until now). I'll try your script too as I dont think the other one I have uses Sox.

RaumTrug: for info: The particular prog I have had trouble with is Hydrogen Drum Machine. Once I had switched to 96k all the drums were all high pitched and comedy style. I assumed the problem would be the same with using samples to make sf2 soundfonts but as I have only recently started doing that (since changing to 96k)Im not sure if they are playing too quick. Now that I have some at 96k I will try them in a soundfont and see if they sound different. To be honest I didnt think they were supposed to resmaple automatically. I wouldnt fancy it being done on the fly as I have a pretty old and haggard PC (hence sticking with Hardy as I have it working and fear the breakage and slowing down - my main Ubuntu system got considerably slower when I upgraded to 9.10 Karmic).

Im marking this as solved but if anyone wants any further investigation to see if its a bug (not a lot of point I suppose given the support for hardy runs out in April but it could be interesting) then give me a shout.

Many Thanks you all.

---

