---
title: "Witch gain to use with easymp3gain"
date: 2016-05-26
forum: Ubuntu Studio
---

### Post by alex9050 on 2016-05-26
I'm using ubuntustudio 16.04.
Due to a bug in Internet DJ Console every mp3 to play has to be re-gained.

Easymp3gain seems to be only a GUI for a command-line-gain but there is no mp3gain in the repository, even though it seems aacgain has been removed from repository, so witch command-line-gain is to be used?
I searched for gain-programms via  synaptic, but didn't find any (perhaps i'm to silly to find? :D )

At the end I did it like this:

got aacgain.deb from the inet, installed it via gdebi and did a symlink like ln -s /usr/bin/share/aacgain /usr/bin/share/mp3gain
easymp3gain is working now, but i wonder how it is meant in den regular way?

---

### Post by kazakore on 2016-05-29
I also use mp3gain but from the commandline so am missing this! I've installed some other missing bits from Trusty via similar methods and guess I will have to do the same with this if it isn'y added to the repo as it's very strange to have got rid of it!

Of the three gainer packages easymp3gain works with only vorbisgain is still in the repo so is it maybe a MPEG family licensing issue? Isn't that why we have Multiverse though? If it is licensing any PPA that would be recommended for this and similar packages?

---

### Post by kazakore on 2016-05-29
Actually it seems I might be able to solve my issue by using LAME.

> 
**--replaygain-fast** Compute ReplayGain fast but slightly inaccurately. This computes "Radio" ReplayGain on the input data stream after user-specified volume-scaling and/or resampling. 
The ReplayGain analysis does *not* affect the content of a compressed data stream itself, it is a value stored in the header of a sound file. Information on the purpose of ReplayGain and the algorithms used is available from **[http://www.replaygain.org/](http://www.replaygain.org/).** 
Only the "RadioGain" Replaygain value is computed, it is stored  in the LAME tag. The analysis is performed with the reference volume  equal to 89dB. Note: the reference volume has been changed from 83dB on transition from  version 3.95 to 3.95.1. 
This switch is enabled by default. 
See also: **--replaygain-accurate, --noreplaygain** 
**--replaygain-accurate** Compute ReplayGain more accurately and find the peak sample. This enables decoding on the fly, computes "Radio" ReplayGain on the  decoded data stream, finds the peak sample of the decoded data stream  and stores it in the file. 
The ReplayGain analysis does *not* affect the content of a compressed data stream itself, it is a value stored in the header of a sound file. Information on the purpose of ReplayGain and the algorithms used is available from **[http://www.replaygain.org/](http://www.replaygain.org/).** 
By default, LAME performs ReplayGain analysis on the input data  (after the user-specified volume scaling). This behavior might give  slightly inaccurate results because the data on the output of a lossy  compression/decompression sequence differs from the initial input data.  When **--replaygain-accurate** is specified the mp3 stream gets decoded on the fly and the analysis is  performed on the decoded data stream. Although theoretically this method  gives more accurate results, it has several disadvantages: 



Anybody used this? I assume it can be performed on existing mp3 files from the wording, without changing the audio data in any way. Will have to be done through a script to work on entire folders at once and no Album mode etc so still definitely not as useful as mp3gain was!


EDIT: Or maybe not. According to Hydrogen Audio the method used by LAME is different to that used by mp3gain and other ReplayGain software and is not supported by any (or at least the vast majority) of players!
[http://wiki.hydrogenaud.io/index.php?title=ReplayGain#LAME](http://wiki.hydrogenaud.io/index.php?title=ReplayGain#LAME)

---

