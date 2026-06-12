---
title: "Converting Audio Files to different formats"
date: 2006-01-19
forum: The Cafe
---

### Post by DigitalDuality on 2006-01-19
I normally download a good deal of music..normally in pretty high quality formats, but I'd love to aid in making ogg and flac popular as well and contribute to that.

So how do i go about converting an audio file to a FLAC or OGG?  What software should i use? What software is the best if i have a list to chose from?  

Didn't know if this really belonged in "Desktop support" so i just dropped this here.

---

### Post by xequence on 2006-01-19
You shouldent convert ANYTHING to flac unless it is already lossless. And the only time you convert something to a lossy format is from a lossless one. (WAV, FLAC, APE).

Now that thats over, I have no idea how to convert to Ogg or Flac in linux :P

(Oh, and FLAC is basically the standard for lossless compression on the internet :))

---

### Post by DigitalDuality on 2006-01-19
Oh i'm quite aware of that, the ones that are lossless would go to FLAC, the ones that are lossy would go to OGG

---

### Post by Lovechild on 2006-01-19
This would do wma to ogg reencoding:

gst-launch-0.8 filesrc location=path-to-file/name-of-file.wma ! spider ! vorbisenc ! filesink location=path-to-file/name-of-destination-file.ogg

If you want another type just replace vorbisenc with the encoder element of choice, the spider will ensure that gstreamer figured out what type the input is.

---

### Post by xequence on 2006-01-19
[QUOTE=DigitalDuality]Oh i'm quite aware of that, the ones that are lossless would go to FLAC, the ones that are lossy would go to OGG[/QUOTE]


No, you dont encode a lossy format to another lossy format :P Its called transcoding and gives you bad quality.

Heh, its your files, do whatever you feel

---

### Post by Lovechild on 2006-01-19
[QUOTE=xequence]No, you dont encode a lossy format to another lossy format :P Its called transcoding and gives you bad quality.

Heh, its your files, do whatever you feel[/QUOTE]

In many cases your average person can't tell the difference unless the quality for transcoding is set way low. At least that's my impression - I regularly transcode files to use on my mp3 player.

---

### Post by DoeRayMe on 2006-01-19
mp3 to ogg

install mp32ogg

and then do this

sudo mp32ogg /DIRECTORY OF MP3S/

---

### Post by kaamos on 2006-01-19
why does mp32ogg need sudo?

---

### Post by Lovechild on 2006-01-19
I completely forgot to add, the only reason I can see for doing what you want is that you downloaded in violation of copyright mind you music files and you want to spread them in a different format in an effort to help open standards - however in doing so you are putting the movement in bad light and put yourself at legal risk.

I urge you to not do this, there are far better ways to promote such formats - say your local TV station offers a download of a media file but only in e.g. .wmv format, politely inform them that you are unable to view it and request that they put an Ogg Theora versions up. If enough people do this we can get the right people to listen to us.

The same thing goes for things like the .odt standard, I regularly request with information on how to perform this conversion a document I can read.

---

### Post by DoeRayMe on 2006-01-19
[QUOTE=kaamos]why does mp32ogg need sudo?[/QUOTE]

i just added that jus in case

---

### Post by DigitalDuality on 2006-01-19
Actually no.  I downloaded about 15 albums today from:

[http://www.legaltorrents.com/](http://www.legaltorrents.com/)

and

[http://www.jamendo.com/en/](http://www.jamendo.com/en/)

All legally distributable.

---

### Post by wmcbrine on 2006-01-20
Don't reencode. Seriously.

If you have lossless originals (e.g., from CD, or FLAC), *those* you could consider encoding to Ogg Vorbis. Not anything else. Otherwise, you're just taking already-degraded audio and degrading it further.

mp32ogg is a really really bad idea.

---

### Post by xequence on 2006-01-20
> In many cases your average person can't tell the difference unless the quality for transcoding is set way low. At least that's my impression - I regularly transcode files to use on my mp3 player.

Heh. I guess I am sort of a semi-audiophile or something.

> Don't reencode. Seriously.

If you have lossless originals (e.g., from CD, or FLAC), those you could consider encoding to Ogg Vorbis. Not anything else. Otherwise, you're just taking already-degraded audio and degrading it further.

mp32ogg is a really really bad idea.

Amen to that.

---

### Post by UbuWu on 2006-01-20
[QUOTE=DigitalDuality]
So how do i go about converting an audio file to a FLAC or OGG?  What software should i use? What software is the best if i have a list to chose from?  
[/QUOTE]

SoundConverter is the only thing you will need. It is in the repositories and it is very easy to use.

[http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

---

### Post by matthew on 2006-01-20
[quote=UbuWu]SoundConverter is the only thing you will need. It is in the repositories and it is very easy to use.

[http://soundconverter.berlios.de/]("http://soundconverter.berlios.de/")[/quote]I second that. Use Synaptic to install or ```
sudo apt-get install soundconverter
```

---

### Post by DigitalAxis on 2006-02-12
There are actually a lot of music sites out there that will let you download .mp3 files (magnatune.com; some artists' sites; music from some demos on Pouet.net)

And I personally ripped a couple of my CDs with MusicMatch Jukebox a long time ago back before I knew what MP3 or Ogg Vorbis really was, and converted them to Ogg later... Since then I've been replacing those with Oggs ripped from the original CDs (they sound much better).

The question can be legitimate.

---

