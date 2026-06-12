---
title: "ffmpeg/libx264 no longer working in karmic?"
date: 2009-11-02
forum: Ubuntu Studio
---

### Post by Jumbs on 2009-11-02
I wrote myself a little script that converted vids to ipod using ffmpeg, and it worked great in Jaunty.

I install karmic and ffmpeg and now it fails. 
Give me a "Unknown encoder 'libx264'"

The only one available is libx264-67, and it doesnt do anything.

I don't recall doing anything special to get this to work in jaunty, did something change?

---

### Post by alphacrucis2 on 2009-11-02
> **Jumbs said:**
> I wrote myself a little script that converted vids to ipod using ffmpeg, and it worked great in Jaunty.

I install karmic and ffmpeg and now it fails. 
Give me a "Unknown encoder 'libx264'"

The only one available is libx264-67, and it doesnt do anything.

I don't recall doing anything special to get this to work in jaunty, did something change?

I had a problem related to this where mplayer wouldn't start because it couldn't find libx264-67 after upgrade to karmic even though it was there. Seems to be a problem with a version of this lib installed from a PPA when I was running Jaunty. To fix it I had to remove libx264-67 which forces removal of ffmpeg, mencoder and all the apps that depend on these. Disabled medibuntu and any PPA's related to any of the above and reinstalled all the removed packages. This fixed the problem for me but rather messy.

---

### Post by andrew.46 on 2009-11-03
Hi Jumbs,

> **Jumbs said:**
> I install karmic and ffmpeg and now it fails. Give me a "Unknown encoder 'libx264'"

I believe you will find the answer in the Karmic section of Fakeoutdoorsman's guide:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

All the best,

Andrew

---

### Post by Jumbs on 2009-11-03
Hmm, tried the suggestions i got, and nothing worked.

Compiling from source ends in working programs, but now i get that stupid itunes "public atom" error. 

Thanks for the help anyway! I have to go figure out some new options!

---

### Post by chconnor on 2009-12-02
Had the exact same issue...

I fixed it through the package uninstall/reinstall method as well.

I didn't need to remove any software sources, but i don't think i had those turned on anyway.

I removed libx264, mencoder, ffmpeg, and x264, but note that i also had to remove libavcodec... when i reinstalled it i reinstalled all the -unstripped versions (e.g. libavcodec-unstripped)... not sure if that mattered. Also installed libavcodec-extra-... but that probably wasn't needed? It was "messy" for me too, in that i had to go step at a time with stuff as there seemed to be package problems... things not installing with a vague error, and then I'd removing the related package reported in the error and reinstalling, etc. I think libavutil49 was one of the weird ones. Sorry, that's vague. I should have taken notes. :-)

Anyway, after reinstalling everything that had to be uninstalled, it seems to be working fine again. :-)

-c

---

### Post by VertexPusher on 2009-12-03
I'd recommend using x264 (the command line encoder) for encoding video, faac (the command line encoder) for encoding audio, and MP4Box (from gpac) or mkvmerge for muxing both into one. This is way better than ffmpeg which always happens to be crippled in one way or another.

Or use Avidemux if you prefer a GUI.

---

### Post by aliencam on 2010-01-09
Just another alternative to removing everything one by one and dealing with all the unresolved dependencies, I went into synaptic and did the following: 

install: mencoder, x264, libavcodec-unstripped-52 (this last one automatically removes libavcodec52, and something else related, and also installs libacvodec-extra-52) 

reinstall: ffmpeg, libx264

applied the changes within synaptic in only one pass, and everything was go in about 2 minutes.  ffmpeg works now! thanks.

---

### Post by *syst3m on 2010-01-30
I had the same issue after a clean install of 9.10 but after installing DeVeDe the issue was resolved and I am now able to use WinFF without errors.

---

### Post by markitoxs on 2010-02-11
> ***syst3m said:**
> I had the same issue after a clean install of 9.10 but after installing DeVeDe the issue was resolved and I am now able to use WinFF without errors.


This works for me as well.

---

### Post by louvann on 2010-03-21
I had the same issue. My install was fresh Mythbuntu 9.10.
I used aliencam's method with good success.

install: mencoder, x264, libavcodec-unstripped-52 (this last one automatically removes libavcodec52, and something else related, and also installs libacvodec-extra-52)

---

### Post by Jumbs on 2010-05-09
The libavcodec unstripped replacing seems to work in Lucid as well, will confirm

---

### Post by Jumbs on 2010-05-23
> **Jumbs said:**
> The libavcodec unstripped replacing seems to work in Lucid as well, will confirm

It seems the working way for me is to install the mediabuntu repos

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then do the earlier method of installing libavcode-unstripped and then ffmpeg

---

### Post by bcg30506 on 2010-08-10
> **Jumbs said:**
> It seems the working way for me is to install the mediabuntu repos

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then do the earlier method of installing libavcode-unstripped and then ffmpeg

This worked for me as well to get both libx264 and libfaac in 10.04.

---

### Post by Jumbs on 2010-10-13
Just installed 10.10 and i am getting the missing libaac issue again... has anyone got this to work?

---

### Post by Jumbs on 2010-10-13
Ok, it seems you need to install ffmpeg THEN libavcodec-extra forcing it to use the mediabuntu one. If you do it in the other order, ffmpeg changes the other to the base one.

---

