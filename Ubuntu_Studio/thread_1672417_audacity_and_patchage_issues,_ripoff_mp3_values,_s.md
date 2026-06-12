---
title: "audacity and patchage issues, ripoff mp3 values, sound converter not able to convert"
date: 2011-01-20
forum: Ubuntu Studio
---

### Post by sevenenemy on 2011-01-20
two things. im sort of a noob-untu, and i messed with **** in patchage that removed my specific playback device from the preferences>devices>playback device drop down menu in audacity. i still get output if i set the menu to default. what i did was connect the blue inputs to the blue outputs in patchage thinking this would give me a direct link from my mic to the speakers so i could hear myself while i was recording. it wound up breaking some stuff in audacity which i fixed after changing some settings and now i can at least get it to record, but i cannot get sound converter to convert any audio files. i get the following error when trying to convert to mp3 ... GSTreamer error when creating pipeline could not link audioconvert1 to lame0, i assume those are what i connected and they cannot be linked. problem is i saved the layout in patchage and now when i open patchage, the blue boxes are gone, only the green midi boxes are there, that were present when i first started the program up lastnite. so my first question is how do i set patchage back to default, i can do this easily in terminal with some direction (like i can cut and paste code lol) and also, i have the lame mp3 plugin for ripoff and would like to know the track output values for mp3 format please.

---

### Post by sgx on 2011-01-21
[http://www.liberiangeek.net/2010/07/quickly-convert-audio-cd-mp3-wav-ogg-flac-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/quickly-convert-audio-cd-mp3-wav-ogg-flac-ubuntu-10-04-lucid-lynx/)

This has screenshots of its gui, for ripping and converting.

Also, install ffmpeg if its not installed, and type

man ffmpeg, it will display lots of options, and examples. 

Install transcode and win32codecsall, to work with ffmpeg.
It will serve you well for years to come, and is worth thorough study.
Lots of google hits for specific combos to convert.

Cheers

---

### Post by sevenenemy on 2011-01-21
i love the new ripper i was looking fast for one the other day and just grabbed the first one i saw, thanks a million! got all the other stuff to work, im more geared towards the musician end of ubuntu studio so most of the video stuff i dont need, but i will use it for helping my friend make his video games i am sure, so thanks again for that, and unfortunately i couldnt locate win32codecsall's package info ... i might need a PPA for that, if you know what it is i would be much obliged.

---

### Post by sgx on 2011-01-21
[http://packages.medibuntu.org/lucid/index.html](http://packages.medibuntu.org/lucid/index.html)

This page should have the goods. w32codecs is the main one.
Click the little blue i386 link
Or the 64 version if thats your system spec

This page has some good info to bookmark

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Cheers

---

### Post by sevenenemy on 2011-01-22
i use some (Multimedia)(Entertainment)(Distractions)ibuntu for those who dont already know cuz i thought it was for hospitals at first lol what i need are the repositories for the win32codecsall package and i have the packages dependency libc6 already so its not that ...

anyone?

Regards,
hunter 8)

---

### Post by sgx on 2011-01-22
In ubuntu-speak, win32codecsall is w32codecs, same codecs, just a different title than the distros I use most often.
 
Download the file from the link at medibuntu in my previous post, and install it manually:

sudo dpkg -i insert-actual-filename.deb  You will be asked for your password, then the codecs will be installed.

Cheers

---

### Post by sevenenemy on 2011-01-29
turns out its fixed after a wipe and fresh install of ultimate edition  thrillseekers unite. i linked the jack system captures to the system  playbacks and i suggest people refrain from doing this. 8) solved

---

