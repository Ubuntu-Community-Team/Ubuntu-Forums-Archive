---
title: "how to get stepmania rc3 work in hoary?"
date: 2005-08-12
forum: Requests
---

### Post by anacron on 2005-08-12
Hi guys, im requesting that someone would make a good tutorial how to get latest stepmania work with ubuntu hoary, (with dancemat/pad too!). I have tryed that now with source and binary and i can't get it work. For an example, it complains about lib files, and I have managed to get those at some point, but I can't get all of those files? ffmpeg is one of those evil packages. 

So please, could someone make a good(specific) tutorial or perhaps an .deb file from stepmania rc3?, and one more thing, can I download rc2 from somewhere easily?, I couldn't download it from sourceforge and there isn't link in stepmanias page. I don't really like to use p2p softwares for that kind of files. 

I'll hope someone will help us stepmania freaks. Thanks.

---

### Post by gerbman on 2005-08-28
[QUOTE=anacron]it complains about lib files, and I have managed to get those at some point, but I can't get all of those files? ffmpeg is one of those evil packages[/QUOTE]

This was my main problem, and was solved by symlinking to the files Stepmania said it couldn't find.  They were all there in /usr/lib, but not under the names Stepmania was looking for.  So try that for the lib files.  libavformat.so was kinda troubling as it was not present even though I had installed the ffmpeg package.  See my post [here](http://www.ubuntuforums.org/showthread.php?t=60435) for my workaround.  For the sound problems on startup, try disabling the Ubuntu's sound server by going to "System", "Preferences", "Sound", and unchecking "Enable sound server startup". 

As for the gamepads, try poofyhairguy's [tutorial](http://www.ubuntuforums.org/showthread.php?t=28538&highlight=stepmania) 

Hope it helps.

---

### Post by anacron on 2005-09-03
Ah, finally playing with stepmania cvs 3.9!  \\:D/  that rpm package you gave did the trick. Joystick tutorial worked just like that with my psx to usb adapter (smartjoy) except I can't configure analog buttons in zsnes, or other programs, but that's a way off the topic, since stepmania works just great.

anyway, im still requesting someone to make tutorial of this, since linking those lib-files might be too much for total newbies with linux. Also it would be good that there would be a list of all files I have to change and download so it would be much quicker to install it to friend or reinstall it to your own machine, what ever.

---

### Post by tommy04 on 2005-09-03
What we *really* need is a .deb file :D

---

### Post by Dreezard on 2005-10-13
> What we really need is a .deb file
done.
look at [http://www.ubuntuforums.org/showthread.php?t=60435](http://www.ubuntuforums.org/showthread.php?t=60435) on the bottom. ;-)

---

