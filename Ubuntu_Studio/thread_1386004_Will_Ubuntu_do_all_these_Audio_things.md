---
title: "Will Ubuntu do all these Audio things?"
date: 2010-01-20
forum: Ubuntu Studio
---

### Post by Edoardo_P on 2010-01-20
Hello everybody,

I've had Ubuntu on my laptop since more than one year, but never used it for anything special.

Now I have got a "special" need: **I want to use my laptop as an high-quality stereo audio source **(think about it as a Super-iPod), keeping the audio files on an external HDD, and connected via FireWire to and external audio board that will convert the digital signal and send the analog signal to a Hi-Fi amplifier.

Now I've just changed my laptop's internal HDD and before installing Ubuntu again I would like to know if it will be able to do *that*.

I'd like to know if it has got some problems with the things I want to do, If it has the apps I need, if it can support the drivers I will use and so on.

For this "special" task, I've used only Windows XP up to now. Ubuntu only for "the rest".

---------

I'll try to be as clear as possible.** I need:** 

**1)**  Some program/application that will copy my CDs just as they are (_without compressing them_), copying and saving the audio tracks _bit-by-bit_. 
Just like Windows does with WAV files and Mac does with AIFF files. 

Not FLAC, but just a perfect copy of what's written in the CD. 
Is it possible? Has Linux got such a kind of format?

I'm talking about 16bit/44.1KHz tracks.

(In Windows I've used EAC to do this)


**2) **Some program/application that will extract the stereo audio tracks from my DVDs, always bit-by-bit without compression.

We're going from 16bit/48KHz to 24bit/96KHz tracks.


**3) **Some program/application that will extract the whole DVD (always without compression)
(In fact the _best_ would be extracting only the movie with the stereo track.)

[B]
4)[/B]Some media player with a kind of library (like iTunes) that will classify and show me all these files by author, composer, track title, album title etc and play all these files saved on the ext HDD 

**5) **Last but (absolutely!) not least, I'd like to know if the following package will work on Ubuntu:
[http://www.ffado.org/?q=release/2.0.0#attachments](http://www.ffado.org/?q=release/2.0.0#attachments)

It's a ***.gz** package, it contains the drivers of my external FireWire Audio Board. Do you think this kind of package will give me problems with any of the distributions?


---------


Thank you very much for your attention!


Edoardo

---

### Post by AutoStatic on 2010-01-20
Hello Edoardo, everything you ask can be done with Ubuntu. I don't know exactly which programs you need, I don't rip CD's or DVD's. When it comes to mediaplayers, I think Songbird may come close, but I'm not an expert on that either.
I do know something about Firewire audio devices and Ubuntu. So, what kind of device do you have? Maybe it's already supported because Ubuntu 9.10 comes with quite a recent version of libffado. If the device is not supported yet then there's probably a PPA (Personal Package Archive) that has a more recent version.

---

### Post by Edoardo_P on 2010-01-20
> **AutoStatic said:**
> Hello Edoardo, everything you ask can be done with Ubuntu. I don't know exactly which programs you need, I don't rip CD's or DVD's. When it comes to mediaplayers, I think Songbird may come close, but I'm not an expert on that either.
I do know something about Firewire audio devices and Ubuntu. So, what kind of device do you have? Maybe it's already supported because Ubuntu 9.10 comes with quite a recent version of libffado. If the device is not supported yet then there's probably a PPA (Personal Package Archive) that has a more recent version.


Hello, it's an Echo AudioFire4 that FFADO.org says to be "fully supported".

Just... Do *.gz packages work with Ubuntu?

Thanks

---

### Post by AutoStatic on 2010-01-20
Yes *.gz packages work with Ubuntu.
But you don't need it. The libffado1 package that you can install with Synaptic supports your device. Did you already check this page: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) ?

---

### Post by Edoardo_P on 2010-01-20
No, I must admit I didn't.

I just looked for my device's drivers by Google and that site was the first useful thing I found, so I thought it was the latest!

Thank you very much! :)

So... Question 6... Solved!


Looking for the other answers, especially **2** and** 3** that seem a little harder :o

---

### Post by AutoStatic on 2010-01-20
You're welcome. Can't help you with questions 2 and 3, maybe other forumites have an idea.

---

### Post by cchhrriiss121212 on 2010-01-20
Might I ask why you do not want to use FLAC? It is the best you will get in terms of "**high-quality stereo audio**". Ogg vorbis is the open source equivalent to WAV in terms of quality and file size, though I'm uncertain on the technical differences.
 
I've used Brasero to extract DVDs to .iso images, it works fine for me.

There are plenty of alternatives to iTunes, Rythmbox is installed with the OS but there are others like Banshee as well. Not sure about the DVD audio ripping, do you want the whole DVD in audio form or just selected parts?

---

### Post by Edoardo_P on 2010-01-20
> **cchhrriiss121212 said:**
> Might I ask why you do not want to use FLAC? It is the best you will get in terms of "**high-quality stereo audio**". Ogg vorbis is the open source equivalent to WAV in terms of quality and file size, though I'm uncertain on the technical differences.

A friend of mine made some double convertions (WAV to FLAC to WAV, that's what te computer does when has to do with a "lossless" codec, and the double-converted files result different from the original :( (now I'm looking for the results to post).

I don't know if these differences are audible (in fact that's unlikely), but since there are differences, and I do not want just to store, but also to back-up my CDs, and since HDD are cheap enough, I prefer the "bit-by-bit" option.


> **cchhrriiss121212 said:**
> I've used Brasero to extract DVDs to .iso images, it works fine for me.

There are plenty of alternatives to iTunes, Rythmbox is installed with the OS but there are others like Banshee as well. Not sure about the DVD audio ripping, do you want the whole DVD in audio form or just selected parts?

Well I'd like to be able to rip just the stereo tracks in WAV and put them in the library! 

...and also to "save" the whole DVD somewhere! can I just save the .ISO file? and play it with what? VLC?


P. S. I must correct you: OGG Vorbis is a **lossy** codec!

---

### Post by Edoardo_P on 2010-01-20
That's why I don't want FLACs

[b]20642273 / 20646325 different bytes 

527659 corrispondent bytes

21169932 total bytes[/b]

[IMG]http://i45.tinypic.com/2dttxr8.jpg[/IMG]

---

### Post by cchhrriiss121212 on 2010-01-20
Sorry about the OGG mixup there, I confused vorbis with OggPCM. In any case I haven't used it myself.
Once you rip a DVD, it is saved to your hard drive as an .iso image. To watch it you can use VLC or whichever media player you prefer.
I found this [http://ubuntuforums.org/archive/index.php/t-117901.html](http://ubuntuforums.org/archive/index.php/t-117901.html) as well. It seems fairly straight forward.
Thats odd about the FLAC conversion there. Could you explain what you mean when the computer needs to do that conversion?

---

### Post by trulan on 2010-01-20
All you need to rip CD's in Ubuntu is Nautilus file manager (the default).  Simply drag and drop the files from your CD to your desired location.  In Windows this would just make a shortcut link, but in Ubuntu it will copy the raw audio file (which is a .wav of course).

With DVD's it is a bit harder, at least with encrypted DVD's.  You'll need to use a ripper program (such as Handbrake) and you'll need to get the libdvdcss library (can be gotten from Medibuntu).  This will yield one or more .vob files (mpeg2 format IIRC)

Then, to convert the DVD to audio you'll want a program like WinFF (in the repository), and convert the .vob files to audio.  You'll probably want to create your own preset in WinFF to get the the audio formatted the way you want it.

To play back your audio over a firewire device, you'll need a media player that supports Jack.  This can be a bit tricky.  I use VLC personally (you have to install the Jack module separately) but I don't use the library features so I can't say if they are any good or not.    It is however very stable when playing back through Jack, unlike some other programs I have tried.  (You need Jack as it is the only sound server that the ffado firewire drivers will connect to.)

---

### Post by AutoStatic on 2010-01-21
Maybe Aqualung could be an option too as a mediaplayer.

---

### Post by kayosiii on 2010-01-21
> **Edoardo_P said:**
> Hello everybody,

I've had Ubuntu on my laptop since more than one year, but never used it for anything special.

Now I have got a "special" need: **I want to use my laptop as an high-quality stereo audio source **(think about it as a Super-iPod), keeping the audio files on an external HDD, and connected via FireWire to and external audio board that will convert the digital signal and send the analog signal to a Hi-Fi amplifier.

Now I've just changed my laptop's internal HDD and before installing Ubuntu again I would like to know if it will be able to do *that*.

I'd like to know if it has got some problems with the things I want to do, If it has the apps I need, if it can support the drivers I will use and so on.

For this "special" task, I've used only Windows XP up to now. Ubuntu only for "the rest".

---------

I'll try to be as clear as possible.** I need:** 

**1)**  Some program/application that will copy my CDs just as they are (_without compressing them_), copying and saving the audio tracks _bit-by-bit_. 
Just like Windows does with WAV files and Mac does with AIFF files. 

Not FLAC, but just a perfect copy of what's written in the CD. 
Is it possible? Has Linux got such a kind of format?


Sure you can. AIFF, AU and WAV all come to mind and are all available. I use K3B for this. However FLAC is a more popular for this purpose as it provides quality 100% equal to that of a WAV file at a smaller file size (+ a provision for meta data).

> I'm talking about 16bit/44.1KHz tracks.

(In Windows I've used EAC to do this)


**2) **Some program/application that will extract the stereo audio tracks from my DVDs, always bit-by-bit without compression.

We're going from 16bit/48KHz to 24bit/96KHz tracks.

Also quite possible - I use vobcopy to decrypt the disk. Then I use cinelera to extract the Audio tracks. Again Wav is definatley available.

> **3) **Some program/application that will extract the whole DVD (always without compression)
(In fact the _best_ would be extracting only the movie with the stereo track.)

This is possible but if you do that for a full movie you are INSANE. Without compression 2GB of disk space buys you 2 minutes and 18 seconds of diskspace and you don't gain any quality for this. I do this when I am doing visuals where I remix the same video source into the product several times - removing the compression helps with generational loss but for playback it is pointless. 

Anyways if you want to know how mplayer can generate a YUV4Linux stream which is essentially uncompressed DVD format.

> [B]
4)[/B]Some media player with a kind of library (like iTunes) that will classify and show me all these files by author, composer, track title, album title etc and play all these files saved on the ext HDD 
I like Amarok for this purpose but there are other choices.

> **5) **Last but (absolutely!) not least, I'd like to know if the following package will work on Ubuntu:
[http://www.ffado.org/?q=release/2.0.0#attachments](http://www.ffado.org/?q=release/2.0.0#attachments)

It's a ***.gz** package, it contains the drivers of my external FireWire Audio Board. Do you think this kind of package will give me problems with any of the distributions?

There are a few things you have to go through to get firewire based cards on Ubuntu Studio. You won't need the package from ffado.org as it is already included within the ubuntu package system. There is a ppa that will help you (look in this forum for a ppa for musicians) and there are good things coming for Lucid Lynx (I am led to believe).

---

### Post by Edoardo_P on 2010-01-21
> **cchhrriiss121212 said:**
> Sorry about the OGG mixup there, I confused vorbis with OggPCM. In any case I haven't used it myself.
Once you rip a DVD, it is saved to your hard drive as an .iso image. To watch it you can use VLC or whichever media player you prefer.
I found this [http://ubuntuforums.org/archive/index.php/t-117901.html](http://ubuntuforums.org/archive/index.php/t-117901.html) as well. It seems fairly straight forward.
Thats odd about the FLAC conversion there. Could you explain what you mean when the computer needs to do that conversion?


Well CDs have stereo PCM 16bit/44.1KHz tracks

DVDs have stereo PCM from 16bit/48KHz (onwards) tracks. ( may be 24bit/48Khz, 24bit/96Khz, etc.)

WAV, AIFF and also OggPCM (thank you, :) I didn't know this format) are just a copy-and-paste of these bytes.

For what I read and understood (and I may be wrong), FLAC-ing a file means to compress the PCM file's bytes through an algorhythm, to reduce the file's size. 
Anytime you play a FLAC, the computer passes the FLAC file's bytes through an anti-algorhythm so that it's just like playing a WAV, *without any loss* of information.

So this friend of mine has tried to get a WAV back from a FLAC and those were the results! :( The bytes are not the same, even with the smallest compression.

---

### Post by Edoardo_P on 2010-01-21
> **kayosiii said:**
> 
This is possible but if you do that for a full movie you are INSANE. Without compression 2GB of disk space buys you 2 minutes and 18 seconds of diskspace and you don't gain any quality for this. I do this when I am doing visuals where I remix the same video source into the product several times - removing the compression helps with generational loss but for playback it is pointless. 

Anyways if you want to know how mplayer can generate a YUV4Linux stream which is essentially uncompressed DVD format.



I don't understand, is it possible to extract just the "movie + 2.0 track" as a file or not? I know it will take a lot of space but I wish to keep just *everything* there. 

If it'll possible to do that without copying the whole of the DVD then I will be happier!


P.S.: Thank you everybody, so helpful!!!

---

### Post by StephenF on 2010-01-21
> **Edoardo_P said:**
> The bytes are not the same, even with the smallest compression.
FLAC doesn't guarantee a digitally identical WAV file. What it does guarantee is digitally identical audio data when decoded.

WAV files can be encoded in a number of different ways with respect to endianness and alignment which can make the data look completely different but when the WAV files are decoded to PCM actually turns out the same.

Try taking the WAV file that the FLAC decoder produced and take it through an encode/decode cycle. Chances are it should look the same afterwards. That's because FLAC always uses the most standard way of assembling WAV files.

---

### Post by cascade9 on 2010-01-21
> **Edoardo_P said:**
> For what I read and understood (and I may be wrong), FLAC-ing a file means to compress the PCM file's bytes through an algorhythm, to reduce the file's size. 
Anytime you play a FLAC, the computer passes the FLAC file's bytes through an anti-algorhythm so that it's just like playing a WAV, *without any loss* of information.

So this friend of mine has tried to get a WAV back from a FLAC and those were the results! :( The bytes are not the same, even with the smallest compression.

Yes, thats 100% correct. Well, that is the way that flac is meant to work, but obviously, not always.....

I've seen similar results from comparing .wav files ripped from 2 different rippers. I've heard that its possible to get the same result from flac->wav->flac, but as far as I know there are only 2 reasons why you could get this is- 

1- user error. 
2- bad decoder/encoder. 

If you did that test with EAC (setup right, using test and copy ripping, etc) and then converted them back to .wav with EAC (or foobar) I doubt you'll have the same issue. 

I've done quite a few flac tests and I'm yet to see a bit-difference.

I would always prefer a (done right) .flac over .wav. Wav works, for sure, but apart from the size difference (wav is normally about x1.5 to x2 bigger) and wav not getting metadata, the internal checksum with .flac is a brilliant idea. 

BTW, the best ripper I've found for linux is rubyripper. It will do EAC style 2-pass rips (to make sure you havent ripped bad data).

---

### Post by kayosiii on 2010-01-21
> **Edoardo_P said:**
> I don't understand, is it possible to extract just the "movie + 2.0 track" as a file or not? I know it will take a lot of space but I wish to keep just *everything* there. 

If it'll possible to do that without copying the whole of the DVD then I will be happier!


P.S.: Thank you everybody, so helpful!!!

I think that should be possible - I would probably use mplayer for that but I am pretty sure there are dedicated programs to do that (acid rip?).

As to the rest of it you asked for uncompressed which can be done but be careful about what you wish for.

---

### Post by VertexPusher on 2010-01-21
> **Edoardo_P said:**
> **1)**  Some program/application that will copy my CDs just as they are (_without compressing them_), copying and saving the audio tracks _bit-by-bit_.
cdparanoia: [http://packages.ubuntu.com/karmic/cdparanoia](http://packages.ubuntu.com/karmic/cdparanoia)

> Not FLAC, but just a perfect copy of what's written in the CD.
cdparanoia can write WAV, AIFF or raw 16bit PCM.

However, there seems to be a misconception on your part. FLAC is lossless. It reduces the size of an audio stream, but decompression will reproduce the original bitstream. It's like .zip or .gz, optimized for audio.

> **2) **Some program/application that will extract the stereo audio tracks from my DVDs, always bit-by-bit without compression.

We're going from 16bit/48KHz to 24bit/96KHz tracks.
If you are talking about audio DVDs: There is a library (libdvdcpxm) to decrypt DVD-Audio media, but I don't know any Linux tools using it because I don't own any DVD-A media.

If you are talking about video DVDs: Most of these have compressed audio, either AC-3 or MPEG-1 Layer 2. Video DVDs with uncompressed PCM are rare.

However, vobcopy ([http://packages.ubuntu.com/karmic/vobcopy](http://packages.ubuntu.com/karmic/vobcopy)) will decrypt and extract content from video DVDs, and MPlayer ([http://packages.ubuntu.com/karmic/mplayer](http://packages.ubuntu.com/karmic/mplayer)) can extract audio streams from any video file and save them as WAV files. It can also dump a raw AC-3 stream if you prefer that.

> **3) **Some program/application that will extract the whole DVD (always without compression)
(In fact the _best_ would be extracting only the movie with the stereo track.)
vobcopy can do both. By default it will only copy the main movie. Use the --mirror option if you want to copy the entire DVD, including menus and extras.

---

### Post by VertexPusher on 2010-01-21
> **Edoardo_P said:**
> That's why I don't want FLACs

[B]20642273 / 20646325 different bytes 

527659 corrispondent bytes

21169932 total bytes[/B]

[IMG]http://i45.tinypic.com/2dttxr8.jpg[/IMG]
This is not a valid way to compare PCM bitstreams. WAV files have headers that can differ in size. The bitstreams can be stored with the least or most significant byte first, they can be arranged in chunks of arbitrary length, interleaved with metadata etc.

If you want to know whether two PCM bitstreams are identical or not, you need to do a cancellation test: Load the two WAVs as separate tracks into an audio editor, then invert one of them and mix down both tracks into one. If the bitstreams are identical, they will completely cancel each other out, and the result will be digital silence, i.e. a signal of -oo dBFS.

Artifacts of lossy compression survive cancellation. However, you won't see any of these with FLAC files because FLAC is 100% lossless.

---

### Post by Edoardo_P on 2010-01-21
> **VertexPusher said:**
> cdparanoia: [http://packages.ubuntu.com/karmic/cdparanoia](http://packages.ubuntu.com/karmic/cdparanoia)


cdparanoia can write WAV, AIFF or raw 16bit PCM.

However, there seems to be a misconception on your part. FLAC is lossless. It reduces the size of an audio stream, but decompression will reproduce the original bitstream. It's like .zip or .gz, optimized for audio.


If you are talking about audio DVDs: There is a library (libdvdcpxm) to decrypt DVD-Audio media, but I don't know any Linux tools using it because I don't own any DVD-A media.

If you are talking about video DVDs: Most of these have compressed audio, either AC-3 or MPEG-1 Layer 2. Video DVDs with uncompressed PCM are rare.

However, vobcopy ([http://packages.ubuntu.com/karmic/vobcopy](http://packages.ubuntu.com/karmic/vobcopy)) will decrypt and extract content from video DVDs, and MPlayer ([http://packages.ubuntu.com/karmic/mplayer](http://packages.ubuntu.com/karmic/mplayer)) can extract audio streams from any video file and save them as WAV files. It can also dump a raw AC-3 stream if you prefer that.


vobcopy can do both. By default it will only copy the main movie. Use the --mirror option if you want to copy the entire DVD, including menus and extras.

Up to now only videoDVDs!

Thank you very much I'll try as soon as possible

---

### Post by Edoardo_P on 2010-01-21
> **VertexPusher said:**
> This is not a valid way to compare PCM bitstreams. WAV files have headers that can differ in size. The bitstreams can be stored with the least or most significant byte first, they can be arranged in chunks of arbitrary length, interleaved with metadata etc.

If you want to know whether two PCM bitstreams are identical or not, you need to do a cancellation test: Load the two WAVs as separate tracks into an audio editor, then invert one of them and mix down both tracks into one. If the bitstreams are identical, they will completely cancel each other out, and the result will be digital silence, i.e. a signal of -oo dBFS.

Artifacts of lossy compression survive cancellation. However, you won't see any of these with FLAC files because FLAC is 100% lossless.


OK now things are going too technical for me... But I'll tell the guy... :o

---

