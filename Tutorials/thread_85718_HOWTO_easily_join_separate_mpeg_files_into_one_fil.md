---
title: "HOWTO: easily join separate mpeg files into one file."
date: 2005-11-03
forum: Tutorials
---

### Post by fleshnblood on 2005-11-03
To join separate mpeg files (for example a movie) into one smooth mpeg file:
 ```
cat file1.mpg file2.mpg file3.mpg... > filename.mpg
```
Pay attention to the order of files after the cat command, it will determine the sequence within the final file.
This will ONLY join the files! It has NO EFFECT on the quality.
It DOES NOT work with AVI files!

---

### Post by poptones on 2005-11-03
Actually, it does work with avi files or ANY files split with something like hjsplit.

It will also work on ANY AVI files so long as you have mplayer installed. After joining some arbritrary group of AVI files via "cat," tell mplayer to rebuild the index

mencoder -forceidx -oac copy -ovc copy **infile.avi** -o **outfile.avi**

---

### Post by fleshnblood on 2005-11-03
[QUOTE=poptones]Actually, it does work with avi files or ANY files split with something like hjsplit.

It will also work on ANY AVI files so long as you have mplayer installed. After joining some arbritrary group of AVI files via "cat," tell mplayer to rebuild the index

mencoder -forceidx -oac copy -ovc copy **infile.avi** -o **outfile.avi**[/QUOTE]

Thanks for the tip, I haven't tried it through mplayer. When I joined AVI files with cat, the final file was OK in terms of picture but the audio was shifted. So I guess mplayer fine-tunes it, right?

---

### Post by poptones on 2005-11-03
I will try. If a file is made with MP3 (especially vbr mp3) it may not be able to do so. MP3 doesn't have a fixed frame size and so is ill suited to video soundtracks, but that doesn't stop people from (mis)using it.

If you cannot get audio and video to synch (because someone made the audio mp3) an easy way to correct this is to save the audio to a file as pcm, then use mplayer to add it back (you can specify separate audio and video files). I use 4 bit ADPCM for audio - it's larger than MP3 but it is fixed size, synchs perfectly, and the distortion it adds is much more tolerable than the darth vader whooshing added by mpeg codecs.

---

### Post by bluebyt on 2005-11-03
Thank you very much! I was looking for that since I installed Ubuntu 1 month ago.

cat Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.001 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.002 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.003 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.004 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.005 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.006 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.007 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.008 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.009 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.010 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.011 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.012 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.013 > Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg
bash: syntax error near unexpected token `('

Where is the syntax error, please?

---

### Post by fleshnblood on 2005-11-05
[QUOTE=poptones]I will try. If a file is made with MP3 (especially vbr mp3) it may not be able to do so. MP3 doesn't have a fixed frame size and so is ill suited to video soundtracks, but that doesn't stop people from (mis)using it.

If you cannot get audio and video to synch (because someone made the audio mp3) an easy way to correct this is to save the audio to a file as pcm, then use mplayer to add it back (you can specify separate audio and video files). I use 4 bit ADPCM for audio - it's larger than MP3 but it is fixed size, synchs perfectly, and the distortion it adds is much more tolerable than the darth vader whooshing added by mpeg codecs.[/QUOTE]

Can you please write a "step by step" for the above to get it work.
I'm still very new to these things :) 

Thanks.

---

### Post by dude2425 on 2005-11-05
[quote=bluebyt]Thank you very much! I was looking for that since I installed Ubuntu 1 month ago.

cat Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.001 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.002 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.003 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.004 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.005 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.006 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.007 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.008 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.009 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.010 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.011 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.012 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.013 > Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg
bash: syntax error near unexpected token `('

Where is the syntax error, please?[/quote]

Try \'ing before all the ('s and )'s.

Can this method be applied to mp3's like audiobooks?

---

### Post by poptones on 2005-11-05
Ah, you need to read the friendly manual on "cat" :)

Put the sections in one directory, go to your terminal and type "cat Madonna" and press tab. When it autocompletes to "Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.0"
press the splat key *, space, "> Madonna" and press tab again. This time when it autocompletes press backspace so the filename ends with "mpg"  Now press enter.

cat Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.* >> Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg

You can wildcard cats and it will automatically group the parts by sequence.

Linux roolz. :)

---

### Post by bluebyt on 2005-11-08
[QUOTE=poptones]Ah, you need to read the friendly manual on "cat" :)

Put the sections in one directory, go to your terminal and type "cat Madonna" and press tab. When it autocompletes to "Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.0"
press the splat key *, space, "> Madonna" and press tab again. This time when it autocompletes press backspace so the filename ends with "mpg"  Now press enter.

cat Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.* >> Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg

You can wildcard cats and it will automatically group the parts by sequence.

Linux roolz. :)[/QUOTE]

Thank you!!!!

---

### Post by cvmostert on 2005-12-25
Hi,

Thank you for the "cat" help... did not know it would be so easy to combine mpg files... 

I have another question... i once burned a vcd file but the .bin file was bigger than 700MB and it all fit on the cd? now... i made an image and it was also little big, but did not want to write on one cd... 

i used ffmpeg to change a AVI to MPG (vcd) and then made an image with vcdimager... the mpg file grew bigger? ok different compression...

what would be the easiest way to convert AVI to VCD?

thanx... command prompt pleas... :-)

born to suffer!

---

### Post by timczer on 2005-12-25
If you have transcode installed you can use avimerge to merge multiple avi files together: avimerge -o big.avi -i file1.avi file2.avi file3.avi

As for converting the avi to vcd, avidemux is a good program for this.  It will allow you to convert the file, and choose the bit rate in order to ensure that the outputed file will fit on a cd or dvd (whichever you choose).  I used this tutorial: [http://forum.videohelp.com/viewtopic.php?t=242455]("http://forum.videohelp.com/viewtopic.php?t=242455") to convert some avi movies into dvd format.  There is an option in the conversion dialog to convert to vcd.

---

### Post by cvmostert on 2005-12-25
thank you! i will try it out... and.. merry christmas!

---

### Post by raggamuffin on 2005-12-25
you can also use mpgtx (install it via APT)...

then just " mpgtx -j file01.mpg file02.mpg -o output_name.mpg " ...

---

### Post by Pete051 on 2006-07-03
I've just tried this on realmedia files on dapper, it doubles the file size but dosen't join the files simply over writes one why the file size increase I don't know. anybody any ideas on how to handles realmedia files?
Thanks

---

### Post by DirtDart on 2006-07-03
[QUOTE=poptones]It will also work on ANY AVI files so long as you have mplayer installed. After joining some arbritrary group of AVI files via "cat," tell mplayer to rebuild the index

mencoder -forceidx -oac copy -ovc copy **infile.avi** -o **outfile.avi**[/QUOTE]

Sweet...this will come in handy; thanks for the info.

---

### Post by DonVla on 2006-10-11
or easier:

```
mencoder -oav copy -ovc copy -o output.avi 1.avi 2.avi
```

---

### Post by nmyrick on 2012-12-24
> **bluebyt said:**
> Thank you very much! I was looking for that since I installed Ubuntu 1 month ago.

cat Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.001 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.002 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.003 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.004 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.005 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.006 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.007 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.008 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.009 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.010 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.011 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.012 Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg.013 > Madonna\ -\ Hung\ up\ (live\ at\ EMA).mpg
bash: syntax error near unexpected token `('

Where is the syntax error, please?

You need to change directory into the \Madonna file by entering 'cd Madonna' in the terminal.  Then you don't have to put the directory in for every file.  That's probably your syntax error.

---

### Post by GrouchyGaijin on 2012-12-30
I am trying to join multiple mpg files using
```
cat MpegA.MPG MpegB.MPG > MpegAB.MPG
```
but the resulting file only shows the data from MpegA, and nothing from MpegB.

Any ideas?

Thank you, this would be cool if I could get it to work.

---

### Post by nmyrick on 2013-01-01
I have the same issue. It only shows the data from the first mpeg file.  Haven't found a way to fix that issue yet without considerably degrading the audio quality.

---

### Post by Portaro on 2013-01-01
IM not sure but maybe with lxsplit you can do this joining try-

lxsplit -j /path to first file 

(atention all files parts of this mpeg files needs are in same directory.)

---

### Post by patronanejo on 2013-03-09
> **GrouchyGaijin said:**
> I am trying to join multiple mpg files using
```
cat MpegA.MPG MpegB.MPG > MpegAB.MPG
```
but the resulting file only shows the data from MpegA, and nothing from MpegB.

Any ideas?

Thank you, this would be cool if I could get it to work.

**If you have tried all of these options...**

> **andrew.46 said:**
> [COLOR=#000000]...mkvtoolnix only allows the addition of 'Supported Media Files'...[/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono]mkvmerge -o newfile.mkv part1.mkv +part2.mkv[/FONT][/COLOR]
```

> **Armitage1337 said:**
> [COLOR=#000000]You don't need mkvtoolnix or anything....just change the name as needed...[/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono]cat pl.mkv.* > pl.mkv[/FONT][/COLOR]
```

> **DonVla said:**
> or easier:
```
mencoder -oav copy -ovc copy -o output.avi 1.avi 2.avi
```

**...then your problem might be** that the files you are trying to join *don't share the same attributes*--e.g., audio- and video bitrates, codecs, video size, etc.

When I ran into this problem, I was able to resolve it by re-encoding each of my fragments to the same CBR.

Compare the metadata for each of your pieces, then create an FFmpeg batch file--making sure to specify a value for every attribute that is not identical across each of your fragments. If you run each of your pieces through the same batch file--applying the same attributes across the board--you should be able to join the resulting files.

---

### Post by andrew.46 on 2013-03-09
I see that this thread has been *necroposted* several times :). Much of the information here has been at least partially rendered redundant with the newer FFmpeg video filters that allow a huge range of options in merging video files together. But this would definitely be information for a new thread :).

---

### Post by QIII on 2013-03-09
> **andrew.46 said:**
>  But this would definitely be information for a new thread :).

I agree.  Several of the posts are new, but since the thread starts out so long ago, I think the two "phases" might be more confusing than helpful.

From the Forum CoC, folks:

&#65279;If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

[I]Thread **closed.**
[/I]

---

