---
title: "Some Render options are not available in kdenlive such as Flash, MP4, XVid4 &amp; H.264!"
date: 2009-11-11
forum: Ubuntu Studio
---

### Post by Rytron on 2009-11-11
Hi.
Some Render options are not available in kdenlive such as Flash, MP4, XVid4 & H.264!
Below are screenshots of them.

---

### Post by kayosiii on 2009-11-12
do you have ffmpeg installed?

---

### Post by Rytron on 2009-11-12
> **kayosiii said:**
> do you have ffmpeg installed?

Yes. I installed Medibuntu before but have since uninstalled it. I reckon Medibuntu may have a part to play.

---

### Post by FakeOutdoorsman on 2009-11-12
> **Rytron said:**
> Yes. I installed Medibuntu before but have since uninstalled it. I reckon Medibuntu may have a part to play.

Unless you are using Ubuntu Hardy, I doubt Medibuntu can offer you anything that will enable your render options in Kdenlive.  I haven't tested this, but it is likely you need to enable the restricted FFmpeg encoders:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Rytron on 2009-11-13
I can render files to .mpg format. I will settle with that for the interim. Thanks for the link FakeOutdoorsman. ;)

---

### Post by r_mano on 2010-02-06
Hi,

I had the same problem. I followed the instructions to install Medibuntu [here]("https://help.ubuntu.com/community/Medibuntu") and  [here]("http://ubuntuforums.org/showthread.php?t=1117283"), rerun kdenlive wizard, closed and opened again kdenlive, and now I have all the rendering option enabled. 

HTH,
       [Romano]("http://rlog.rgtti.com")

---

### Post by Mustache Villain on 2010-02-06
> **Rytron said:**
> Hi.
Some Render options are not available in kdenlive such as Flash, MP4, XVid4 & H.264!
Below are screenshots of them.

It's probably due to the licensing changes in [FAAC]("http://www.audiocoding.com/faac.html"), I would try installing a newer version of Kdenlive. Preferably from either PPAs:


[LIST]
[*][https://launchpad.net/~sunab/+archive/ppa ]("ttps://launchpad.net/%7Esunab/+archive/ppa")(stable)
[/LIST]
 
[LIST]
[*][https://launchpad.net/~sunab/+archive/sunab2]("https://launchpad.net/%7Esunab/+archive/sunab2") (unstable)
[/LIST]

---

### Post by Rytron on 2010-02-06
> **r_mano said:**
> Hi,

I had the same problem. I followed the instructions to install Medibuntu [here]("https://help.ubuntu.com/community/Medibuntu") and  [here]("http://ubuntuforums.org/showthread.php?t=1117283"), rerun kdenlive wizard, closed and opened again kdenlive, and now I have all the rendering option enabled. 

HTH,
       [Romano]("http://rlog.rgtti.com")

Thank you r_mano. ;)

---

