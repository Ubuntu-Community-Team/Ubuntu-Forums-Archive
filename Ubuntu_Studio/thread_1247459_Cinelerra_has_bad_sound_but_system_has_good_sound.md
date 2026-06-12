---
title: "Cinelerra has bad sound but system has good sound"
date: 2009-08-23
forum: Ubuntu Studio
---

### Post by rapattack1 on 2009-08-23
Hi I have read a few older posts that partially cover this problem but they are not the same. I installed Ubuntu about a month ago and everything is going well. Sound is great. Installed Cinelerra and works ok except when I am importing, playbacking video/sound. The latest video was from my Canon Powershot A460 ( [http://www.cnet.com.au/canon-powershot-a460_specs-339281129.htm](http://www.cnet.com.au/canon-powershot-a460_specs-339281129.htm) ) which is really just a still camera with video as an extra thing. The videos once imported into ubunut and played with any media player play well so there is no problem there but Cinelerra does not play it well(sound wise) or export is well(as in sound is bad). I looked up the file formats on this page [http://cinelerra.org/docs/wiki/doku.php?id=supported_file_formats](http://cinelerra.org/docs/wiki/doku.php?id=supported_file_formats) and I found that my camera is in 'motion jpegs' even though the file extension is .avi. I looked at the properties of the video file and it said it was the 'motion jpeg' type. I am still understanding all this stuff so be patient with me. I just did a two part Final Cut Pro (mac) course and it was pretty intensive. I can see FCP is very similar to Cinelerra so I am able to do a lot in there with no trouble at all so I hope this is not an issue that Cinelerra will not work with my hardware. I have forgotten how to find out through Ubuntu how to report what hardware i have so please let me know how so that info might help in getting this sound issue solved.
Would appreciate any help as I am dying to get this done even though the information on that page about the formats seems to be discouraging.

---

### Post by wildhostile on 2009-08-23
Hi rapattack1,

First, the informations on this page are just some tests. They are not official as the author didn't say how he got these results.
Second, if cinelerra doesn't play sound well it may be due to either a codec problem or a device problem.
For the codec thing you can always convert your media into a format(videocodec,audiocodec) that is readable by cinelerra. You can use converter like: tabencode, handbrake, winff, and others.
For the device thing, go to Settings --> Preferences --> Playback and try to change the audio device to see.

Have fun.

Roland.

---

### Post by rapattack1 on 2009-08-24
Oh ok I seached so much I was not reading everything on the page. Thanks!
Yes i was thinking about converting but i seem to be having trouble getting winff. I have ffmpeg. I am trying the medibuntu way but somewhere things go wrong. I have intrepid Ubuntu btw. I am not sure how far I got because i did it late last night and my brain dropped out on me so I shut the computer down and went to bed but attached is a pic of the repositories. That might tell something as I am lost not. 
I also downloaded and installed Handbrake. I converted the .avi i have to .mpg4 but the sound seems to be even worse. i did that last night too and that is the most i can remember.

As to the part about the preferences there seemed to be no change doesn't matter what i chose. One thing though on my system I do not see an ok or apply button as the window with the preferences is too long for my desktop. Is that an issue? I can't seem to change that window to make it shorter so i can see the bottom of it.

---

### Post by wildhostile on 2009-08-24
Hi rapattack1,

I really advice you tabencode first ==> [http://devel.zs4.net/tabencode.html](http://devel.zs4.net/tabencode.html). You will need some dependancies and that's it. When done, choose the "avi for ZS4 compositing option". It's an avi(mjpeg,pcm) combination.
To see the bottom of the Preferences window you can Alt Click to move it. I have this problem here too. You can also just hit the enter key to accept the modifications you did.

Roland.

---

### Post by rapattack1 on 2009-08-24
Hi yes i did look at tabencode first but i keep forgetting how to install things from a tar . Anyway it is downloaded now and i have it open with is it Gdeb? I got the name of the thing. I don't remember what to do from there. 
Ah that next bit seem clear on how to deal with it once i have tabencode open and happening thanks.

I will try those other things if I need....thanks for that.:)

---

### Post by paul.gevers on 2009-08-25
> **rapattack1 said:**
> Oh ok I seached so much I was not reading everything on the page. Thanks!
Yes i was thinking about converting but i seem to be having trouble getting winff. I have ffmpeg. I am trying the medibuntu way but somewhere things go wrong. I have intrepid Ubuntu btw. I am not sure how far I got because i did it late last night and my brain dropped out on me so I shut the computer down and went to bed but attached is a pic of the repositories. That might tell something as I am lost not.

With respect to winff: ffmpeg is not in medibuntu, so that should be no problem. Did you add the winff repository [1]? Maybe it also helps to remove the presets.xml file in ~/.winff/ (that might be from a previous version), see [2] or your /usr/share/doc/winff/README.Debian file.

[1] [http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)
[2] [http://code.google.com/p/winff/wiki/InstallPresetsxml](http://code.google.com/p/winff/wiki/InstallPresetsxml)

---

### Post by rapattack1 on 2009-08-25
Here is the reference to Medibuntu [http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)
I did what was on this page [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) under Intrepid. Not sure about the bit to be removed. I didn't see anything about that. Could be on that page but there is so much info it is too much!

---

### Post by rapattack1 on 2009-08-31
I found an easy solution thanks to my friend Kris who just came back from overseas. He used Cinelerra all the time!

OK so first transfer the *.avi file to your hard drive then use Kino to export as a raw *.dv file then load into Cinelerra and the sound is great!!!!

Happy Happy Happy!!!!\\:D/:lolflag:

---

