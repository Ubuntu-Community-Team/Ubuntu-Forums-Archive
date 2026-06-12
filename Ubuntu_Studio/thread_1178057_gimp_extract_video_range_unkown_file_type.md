---
title: "gimp extract video range unkown file type"
date: 2009-06-04
forum: Ubuntu Studio
---

### Post by kolibri on 2009-06-04
I'm trying to use GAP in GIMP to "extract video range" but i keep getting the message 'unknown file type"

I've got all the necessary codecs installed, I'm editing the videos with Blender, and it isn't having a problem writing the videos, Ubuntu players can read the files, but GIMP says unknown file type.

I've tried AVI, FLV, quicktime and numerous codecs.

Any suggestions?  Is there a particular wrapper/codec that Gimp/Gamp is known to like?

Do i need to save the video with just the video track and not the audio track or something like that?

TIA

(Gimp 2.6.1)

---

### Post by Pqqu on 2009-06-12
I'm having the same problem. I tried to compile gap, got frustrated, realized it was in the repositories and picked it up. There was a significant bit in the readme, I remember, about making sure the video decoders were properly installed, and my only guess would be that the repository install didn't include that bit. Either way, when trying to open a .avi file in Extract Videorange, I'm met with:

```
Execution error for procedure 'gimp-file-load':
Unknown file type
```

---

### Post by dopple on 2009-08-14
I'm also having this issue. A reinstall of gimp and gap didn't work.

---

### Post by dopple on 2009-08-15
An alternative that I have found is PyTube and this also does media conversion.
[http://marcosrodriguez.me/pytube/index.php?option=com_remository&Itemid=2](http://marcosrodriguez.me/pytube/index.php?option=com_remository&Itemid=2)

---

### Post by cotcot on 2009-08-15
I remember that I read somewhere that you need gap 2.6 for gimp 2.6 but I could not find where. I see gimp 2.6 and gap 2.4 in the repos. This might be the reason for your problem. 
For this reason I compiled it myself. This went without problems and GAP is working fine. I googled and found that there is package available now : [[COLOR="Red"]see here[/COLOR]]("http://webupd8.blogspot.com/2009/07/download-gimp-animation-package-260-gap.html") .

---

### Post by dopple on 2009-08-15
Looks like it's only for Jaunty. Is it out for intrepid?

---

### Post by dopple on 2009-08-15
Never mind. I took this as an opportunity to upgrade. :)

UPDATE: After installing 2.6 GAP it still doesn't work.

---

### Post by eival on 2010-11-27
im having this same exact issue in 10.4

i checked the repos an it says GAP is for 2.6+ which would make me think its compatible with the current 2.6.8-2 GIMP in the repos

has anyone figured out what the issue is?

is there a specific codex or file container we have to use?

---

### Post by jasondean on 2011-02-05
> **eival said:**
> im having this same exact issue in 10.4

i checked the repos an it says GAP is for 2.6+ which would make me think its compatible with the current 2.6.8-2 GIMP in the repos

has anyone figured out what the issue is?

is there a specific codex or file container we have to use?

I had the same issue in 10.10, I ended up downloading from source and compiling it. I followed the ./configure instructions that told me what development  packages where needed and installed them.

---

### Post by perro68 on 2011-09-13
I am having the same problem ....I wish there was a solution for a novice on this thhing

---

### Post by Chiapo on 2011-11-19
Same issue here... :confused:

---

### Post by Pednick on 2012-04-03
Hello? Has anyone firgured this out?

---

### Post by SeijiSensei on 2012-04-03
Are you trying to convert a video into a collection of still frames and edit them in GIMP?

I use this method:

1)  Play the file with mplayer and use "-vo png" to create individual PNG files for each frame:

```
mplayer -vo png -ao null file.mkv
```

You'll get a sequence of PNG images numbered 00000001.png and so forth.

If you only want to extract a portion of the video use the "-ss hh:mm:ss" and "-endpos NN" directives to start at hh:mm:ss and extract NN seconds of video.

2) Open the first frame of the sequence (00000001.png) with GIMP.  Now use File > Open as Layers and select all the remaining images.  You'll end up with an image containing all the frames as layers.

I've used this method frequently to create animated GIFs from movie sequences.

---

### Post by Pednick on 2012-04-03
Nope not looking for alternate methods, already know them just want a solution for gap cause I actually would like to try it through that.

> **SeijiSensei said:**
> Are you trying to convert a video into a collection of still frames and edit them in GIMP?

I use this method:

1)  Play the file with mplayer and use "-vo png" to create individual PNG files for each frame:

```
mplayer -vo png -ao null file.mkv
```You'll get a sequence of PNG images numbered 00000001.png and so forth.

If you only want to extract a portion of the video use the "-ss hh:mm:ss" and "-endpos NN" directives to start at hh:mm:ss and extract NN seconds of video.

2) Open the first frame of the sequence (00000001.png) with GIMP.  Now use File > Open as Layers and select all the remaining images.  You'll end up with an image containing all the frames as layers.

I've used this method frequently to create animated GIFs from movie sequences.

---

