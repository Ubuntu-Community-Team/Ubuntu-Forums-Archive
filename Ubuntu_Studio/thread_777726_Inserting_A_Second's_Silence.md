---
title: "Inserting A Second's Silence"
date: 2008-05-01
forum: Ubuntu Studio
---

### Post by sharpycore on 2008-05-01
Hello there,
I just got a phone (Sony Ericsson w810i) that acts as an audio player but does the incredibly irritating thing of fading in and out of every song I play. This makes me spit with rage and it can't be turned off. Can anyone think of an audio app that would let me go through a copy of my MP3 collection and insert a second of silence at the start and end of every track to work around this, probably by recording a macro and then applying to every file in a directory. Even if there isn't one in Ubuntu, any apps for windows would be welcome recommendations.
Thanks
Tom

---

### Post by itix on 2008-05-01
That's called crossfading, you know.
Check the settings for crossfading. Good audio editing devices are Audacity, but I don't know if it does what you're looking for.

---

### Post by olejorgen on 2008-05-01
Two pacakges should help you do this without re-encoding:
- quelcom
- mpgtx

Make a 1 second silence mp3 file with audacity and do this per file: (mpgjoin for mpttx)
```

qmp3join -f -o mysilenced.mp3 silence.mp3 myfile.mp3 silence.mp3

```

A problem is that lots of mp3 files have invalid / no headers and these tools don't like that.

Yeah, and it's only for mp3.

You can achieve the same with re-encoding using a combination of a decoder, qwavjoin (from quelcom) and a encoder (eg. lame). This will take a long time though

---

### Post by sharpycore on 2008-05-02
> **itix said:**
> That's called crossfading, you know.
Check the settings for crossfading. Good audio editing devices are Audacity, but I don't know if it does what you're looking for.

The phone interface is very simple, there's no option to turn it off. But thanks for the tip on naming.


> **olejorgen said:**
> Two pacakges should help you do this without re-encoding:
- quelcom
- mpgtx

Make a 1 second silence mp3 file with audacity and do this per file: (mpgjoin for mpttx)
```

qmp3join -f -o mysilenced.mp3 silence.mp3 myfile.mp3 silence.mp3

```

A problem is that lots of mp3 files have invalid / no headers and these tools don't like that.

Yeah, and it's only for mp3.

You can achieve the same with re-encoding using a combination of a decoder, qwavjoin (from quelcom) and a encoder (eg. lame). This will take a long time though

Brilliant, that helps a lot. In theory I could write a script to do that recursively to every directory in my music folder right? And when you say invalid headers, do you mean tags? All my music is tagged properly so this should be OK. Or does headers mean something else.
And just so I know what I'm doing a little better (say if I wanted to add 1/2 second silence), could you explain what the command actually does, like what the parameters are?
Thanks so much
Tom

---

### Post by olejorgen on 2008-05-02
No, not the tags. Install both the packages, and try to run 
```

qmp3info MP3FILE
mpginfo MP3FILE

```
If the output says anything about invalid / missing header, the join command might not work. I'm not sure, but I think this is because the mp3 was constructed incorrectly.

Anyway, if you have good mp3 files, the join command simply joins, or concatenate FILE1 FILE2 etc. and writes the result to OUT. -f means to do the joining even if the bitrates are different. This works pretty good in my experience, but if the result comes out bad, you should create a silence file with matching bitrate.
```

qmp3join -f -o OUT FILE1 FILE2 FILE3 ...

```
The length of the silence is controlled through the length of the silence.mp3 file. I know this is quite "hackish" :P

To generate silence use audacity and insert -> silence. then export to mp3 (iirc)

Yes it should be quite easy to make a script that does it on all files. Easiest is probably to make one that does it to all files in a single directory first.

EDIT: This should do the trick for one directory:
```

#!/bin/bash

for file in *.mp3; do
	base="$(echo $file | sed -e 's/.mp3$//')"
	qmp3join -f -o "${base}.silenced.mp3" /path/to/silence.mp3 "$file" /path/to/silence.mp3
done

```

I should also make it clear that joning raw mp3 files is not a perfect process. It might be some glitches. eg. Small deviations from the 1. sec

---

### Post by sharpycore on 2008-05-08
That's incredible. Thanks so much. Solved!

---

### Post by olejorgen on 2008-05-08
All your mp3 files worked? Not bad, I have dozens which makes qmp3 puke

---

