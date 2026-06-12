---
title: "transcoding through a pipe ..."
date: 2008-10-21
forum: Ubuntu Studio
---

### Post by pmooney78 on 2008-10-21
I'd like to transcode .mp3 files to AAC (in the .m4b format, so I can play them as audiobooks on my iPod) with a minimum of manual intervention. I can transcode .mp3 to PCM with a command like 

mplayer -vc null -vo null -ao pcm:nowaveheader:fast:file=- \Disc-1_MP3WRAP.mp3

and then re-encode to .m4b with a command like

faac -R 44100 -B 16 -C 2 -X -w -q 60 --artist "Robert Pinsky" --album "The Inferno of Dante" --title "(Disc 1)" --track 1 --genre "Spoken Word" -o "Disc 1.m4b" Disc_1.wav


but this requires that I be at the computer after the computer finishes the first stage. Can't I transcode through a pipe, somehow? And can I do something that will run the process over multiple files in the same directory?

---

### Post by Stochastic on 2008-10-21
I think this sounds like the perfect job for a bash script.  Read further here: [http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial)

---

### Post by pmooney78 on 2008-10-30
I'll learn scripting eventually, probably soon ... but in the meantime, I've found a useful link at blog.mjava.ch/2008/08/10/convert-mp3-to-m4b-audiobooks/ that pointed the way.

Now what I'm using is a command like:

mpg321 -s "King John_MP3WRAP.mp3" | faac -q 85 -P -X -w -C 2 --artist "William Shakespeare" --title "King John" --album "King John" --genre "Drama" --track 1 -o "King John.m4b" -

Some of the audiobooks I'm transcoding are in stereo, some in mono, so it's necessary to choose -C 2 (two channel, stereo) or -C 1 (one channel, mono) as appropriate to avoid rate problems in the audiobook that's output. I can tell the difference by just running the first part of the command with the first frame of the input file, as:

mpg321 -s -n 1 "King John_MP3WRAP.mp3" >~/delete.me

and the output in the terminal tells me whether it's mono or stereo.

---

