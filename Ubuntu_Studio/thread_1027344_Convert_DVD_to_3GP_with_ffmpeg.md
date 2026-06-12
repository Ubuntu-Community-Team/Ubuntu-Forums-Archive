---
title: "Convert DVD to 3GP with ffmpeg?"
date: 2009-01-01
forum: Ubuntu Studio
---

### Post by letmein on 2009-01-01
As the title suggests, i would like to convert a DVD to a 3GP file using ffmpeg, what is the syntax - i've been searching online for days and find nothing :-(

If you could help itd be much appreciated

---

### Post by FakeOutdoorsman on 2009-01-01
If you are using Ubuntu Hardy (8.04) get ffmpeg from the [Medibuntu](https://help.ubuntu.com/community/Medibuntu) repository.  It has an amr enabled ffmpeg package.

If you're using Ubuntu Intrepid (8.10) you will have to compile ffmpeg yourself.  First add the Medibuntu repository and then install the AMR development files:
```
sudo apt-get install libamrnb-dev libamrwb-dev
```
Then follow this guide to install ffmpeg:

[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

On step 5 "Install ffmpeg", you will need to add the following to the ffmpeg configure line:
```
--enable-nonfree --enable-libamr-nb --enable-libamr-wb
```
Once you install ffmpeg you can try this command:
```
ffmpeg -i input.vob -s 352x288 -ar 8000 -ac 1 -ab 12.2k output.3gp
```
Other valid video sizes are 128x96, 176x144, 704x576, and 1408x1152.

---

### Post by letmein on 2009-01-02
Thanks, i've actually already got ffmpeg installed, all im seeking is the syntax to convert a dvd to 3gp usines ffmpeg,

Many thanks

---

### Post by timcredible on 2009-01-02
the poster gave you the command.  also, if you would prefer a gui, try using winff, it's a front end for ffmpeg.

---

### Post by timcredible on 2009-01-02
> **FakeOutdoorsman said:**
> 
If you're using Ubuntu Intrepid (8.10) you will have to compile ffmpeg yourself. 

?  - ffmpeg is in the ubuntu repos for 8.10, installs fine.

---

### Post by FakeOutdoorsman on 2009-01-02
> **timcredible said:**
> ?  - ffmpeg is in the ubuntu repos for 8.10, installs fine.
The repository ffmpeg in 8.10 does not support AMR audio.  The 3GP container format often uses AMR for the audio stream.  I was assuming the original poster wanted AMR.  I believe 3GP can also use AAC audio, but I am not totally sure.  The repository ffmpeg can handle AAC, but the unstripped ffmpeg libraries are required:
```
sudo apt-get install libavcodec-unstripped-51
```

---

### Post by RomanIvanov on 2009-08-02
I use WinFF from Ubuntu repository.

```
sudo apt-get install winff
```

Run winff, select file to convert and select:
Convert to = Mobile Phones
Device Preset = 3g2

works like a charm :) for my SE k810i, just before coping to mobile need rename file extension to 3gp.

---

