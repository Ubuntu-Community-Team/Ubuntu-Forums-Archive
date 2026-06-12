---
title: "Flac Appreciation Thread"
date: 2006-12-17
forum: The Cafe
---

### Post by 3rdalbum on 2006-12-17
I had **868** megabytes of audio that I ripped from one of my DVDs. I'd already made MP3s from them to put on my MP3 player, but I also wanted to archive the original audio without losing quality. Obviously, at over 800 megabytes it is too big for a CD.

Back on Mac OS, I would have just made a 320kbps MP3 and accepted the loss of quality and my inability to recompress the audio again later for a different target.

But here on Linux, I remembered hearing about FLAC - Free Lossless Audio Codec. So I fired up the man page and a Bash prompt. It was easier than falling off a log:

```
cd gordon-lightfoot-live
flac --best *
```

Now the audio is only **530** megabytes, fits on a CD, and still sounds great!

Anyone else out there use FLAC? And what for?

---

### Post by slimdog360 on 2006-12-17
you know Ive never used FLAC before. Im certainly going to have to give it a go though.

---

### Post by 23meg on 2006-12-17
I use it to pass around audio files that I record with audio apps, as well as making my music available online. The resulting files are much smaller than a PCM wave file, and with professional audio recording, loss of quality is unacceptable, so FLAC is an excellent choice. 

Here's one occasion where it saved me: right after handing in a complete CD to be mastered, I had to take a coach to travel to another town. Listening to the CD on the road I noticed that in the rush, I had left one of the channels muted in one track before rendering, and as a result it sounded nothing like it should. After a few minutes of self loathing and desperation I figured out that I could re-render the track on my laptop with the channel unmuted, encode it with FLAC and send it via email right from the coach (it was connected via GPRS; slow but working), or from a wifi hotspot in the break. I did the latter, and it saved the day.

---

### Post by bastiegast on 2006-12-17
I once ran into a flac file, i just did: apt-cache search flac and then apt-get install it all. Then i could play it :D its so easy, but anyway, on the topic. Can you hear the difference between compressed audio and pure? I think the difference is very small if not unnoticeable.

---

### Post by 23meg on 2006-12-17
[QUOTE=bastiegast]Can you hear the difference between compressed audio and pure? I think the difference is very small if not unnoticeable.[/QUOTE]If you mean lossy compression, it depends on the recording itself, the system you use to listen to it, and the amount and method of compression. With most music I can discern between a 192 / 224kbps MP3 and an uncompressed version of it on my pro audio monitors.

---

### Post by Christmas on 2006-12-17
I think it's a great format, however I don't use it because of its size. I have all my music in OGG format at 192 kbps. But FLAC would definitely be a future format, when probably normal hard drives that anyone would afford would have somewhere around 500 - 1000 GB.

And I forgot... the MP3/OGG size allows faster music downloads, for the moment FLAC would take too much. We'll see how it changes in time anyway.

---

### Post by MetalMusicAddict on 2006-12-17
Heres my FLAC setting for GRIP.
```
[SIZE="1"]
-V --best -T TITLE=%n -T ALBUM=%d  -T TRACKNUMBER=%t -T ARTIST=%a -T GENRE=%G -T DATE=%y -o %m %w[/SIZE]
```

---

### Post by RandomJoe on 2006-12-17
I use FLAC extensively at home.  All my CDs have been ripped to FLAC and stored on the server, from which I stream to whatever computer I'm working on at the time.  It's also a pretty easy script away to encode from them to whatever smaller / more portable format I want/need at the time, or recreate a CD for my work van.  (Has a CD player that doesn't do MP3, and I'm not putting the originals in a van that sits in the sun - I've recreated quite a few CDs over the years...)

And yes, I can tell the difference - on some music, in certain situations.  If I'm using the compressed audio for "background" music then no.  But if I'm listening specifically to hear that music, I have found there are some bands that seem to really get trashed, especially in MP3 format.  Not sure just why they do, but they do.  Others will have occasional "echo-y" spots or other sometimes-noticeable glitches.  The FLACs, of course, sound fine.  (Or, as good as it's going to get! ;) )

---

### Post by Tuna-Fish on 2006-12-17
Flac is great for archiving stuff that really has to retain their quality. Other than that, Ogg Vorbis at -q5 (160kbps) Is transparent for most people while at -q6 (192kbps) it has been proven to be transparent even to trained listeners for music and speech.

---

### Post by hda on 2006-12-26
I'm using flac to archive my CD collection to disk. Right now I've got more than 800 albums stored twice (for redundancy/safety) on external/internal hard disks on my server. That collection now uses 244 GB of disk space (twice).

I use mpd/gmpc for playing my albums from the server and rhythmbox or other suitable players to play them from nfs shares at any workstation.

I consider flac as currently the best option to preserve audio recordings. It's open, free (as in speech), well supported and compresses to about 50 to 60 %.

Would be great if it was supported on more portable players!

---

### Post by neaolin on 2006-12-26
FLAC support is coming along.  Some websites are even selling their music downloads in FLAC format.

For the past two weeks, I've been archiving my CD collection in FLAC format.  So far, so good.

---

### Post by ron999 on 2007-05-17
> **3rdalbum said:**
> I had **868** megabytes of audio that I ripped from one of my DVDs. I'd already made MP3s from them to put on my MP3 player, but I also wanted to archive the original audio without losing quality. Obviously, at over 800 megabytes it is too big for a CD.

Back on Mac OS, I would have just made a 320kbps MP3 and accepted the loss of quality and my inability to recompress the audio again later for a different target.

But here on Linux, I remembered hearing about FLAC - Free Lossless Audio Codec. So I fired up the man page and a Bash prompt. It was easier than falling off a log:

```
cd gordon-lightfoot-live
flac --best *
```

Now the audio is only **530** megabytes, fits on a CD, and still sounds great!

Anyone else out there use FLAC? And what for?


Hi
I have tried to do this, but it doesn't seem to work.
Please can somebody explain what I'm doing wrong.

I created a temporary folder and put some flac files in it.
I opened a terminal.
I changed directory to the temporary folder.
I entered the command flac --best *
I got error messages.

This is the output from the terminal:-


ron@ron-desktop:~$ cd /home/ron/tempo
ron@ron-desktop:~/tempo$ flac --best *

flac 1.1.2, Copyright (C) 2000,2001,2002,2003,2004,2005  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

options: -P 4096 -b 4608 -m -l 12 -e -q 0 -r 0,6
ERROR: for encoding a raw file you must specify a value for --endian, --sign, --channels, --bps, and --sample-rate
Type "flac" for a usage summary or "flac --help" for all options
ERROR: for encoding a raw file you must specify a value for --endian, --sign, --channels, --bps, and --sample-rate
Type "flac" for a usage summary or "flac --help" for all options
ron@ron-desktop:~/tempo$

---

### Post by 3rdalbum on 2007-05-18
The files must be .wavs, not Flac or MP3 or anything else.

---

### Post by enopepsoo on 2007-05-18
> **Tuna-Fish said:**
> Flac is great for archiving stuff that really has to retain their quality. Other than that, Ogg Vorbis at -q5 (160kbps) Is transparent for most people while at -q6 (192kbps) it has been proven to be transparent even to trained listeners for music and speech.
I'm with Tuna, I can't tell the difference, and I've read tests showing that 'audiophiles' can't really tell that much either.

---

### Post by graabein on 2007-05-18
My audiophile friend can tell the difference... I must say, his home built components are awesome. Flac takes up more space than high quality mp3/ogg but I think flac's the way to go.

---

### Post by ron999 on 2007-05-18
> **3rdalbum said:**
> The files must be .wavs, not Flac or MP3 or anything else.


Yes, that** flac --best*** command works for me now.:smile:

I already had the 40 audio tracks stored in flac format and they added up to 730MB.
But I don't think that they had been encoded at 'best' compression.

So I started again.

I ripped the files from CD as 44KHz wav format. They added up to 1.2GB.
Then I used the flac --best* command..
Now they add up to 660MB.

Thanks for your help.
:cool:

---

### Post by reacocard on 2007-05-18
I used to have my whole library in FLAC, but I switched to q8 OGG. It provides nearly the same quality at 1/4 the space. You can't hear the difference, and it's high enough quality to survive a transcoding without the difference becoming noticeable.

If i get the audio from somewhere other than a CD (eg. line-in) I usually start with FLAC, burn a couple CDs for backup (and put it on my external HD), then convert to q8 OGG. 

If I had a big HD, I'd probably have stuck with FLAC, but with only 80GB to work with, the space they take up becomes a severe issue.

---

### Post by Polygon on 2007-05-18
I use it to convert a few albums that i had bought off iTunes (and were in apples FairPlay drm format). So i burnt  the fairplay tracks to a audio cd, then reripped it as flac and as a result i have the same tracks in a free open format with no quality loss from the original file that i downloaded it from, rather then suffering twice the quality loss as the songs are 128kb, and then reripping it at like 160kb ogg would make it sound really crappy, so flac does the job nicely.

---

### Post by ron999 on 2007-05-29
-

---

### Post by tehbeermang on 2007-05-29
Are there any "install and go" car audio players that support FLAC?

I don't have the time to build a carputer right now.

---

### Post by ron999 on 2007-05-29
-

---

### Post by koshatnik on 2007-05-29
> **enopepsoo said:**
> I'm with Tuna, I can't tell the difference, and I've read tests showing that 'audiophiles' can't really tell that much either.

Depends on your hifi. Mine is transparent and any compressed media is exposed. CD audio is compressed media and badly engineered CD's are noticeable too. So it depends on your equipment.

---

### Post by insane_alien on 2007-05-29
I have FLAC backups on a nice big External HDD but i use .ogg 's for day to day use as they are ever so slightly more portable. and i make mp3s for my mp3 player from the FLAC's as needed

---

### Post by stmiller on 2007-05-29
I too use

$ flac -V --best

though some flac playback codecs cannot play this compression level (this one in particular: [http://www.xiph.org/quicktime/](http://www.xiph.org/quicktime/) ). VLC plays flac excellent on every platform.

I think the Cowan portable players support Flac. As does the Rockbox project for ipods.

It's good for archiving. You retain the original quality and can then go to any popular formats you'd like. :)

---

