---
title: "Microphone - Camera Program Access control?"
date: 2009-11-19
forum: Security
---

### Post by ==Troy== on 2009-11-19
I have noticed that sometimes when I see a flash advert the CAMERA LED blinks for a moment, and it is quite concerning for me, since I have the CAMERA & Microphone DISABLED in the Adobe Flash plugin. (using the proprietary flash for the browser)


This has raised a concern for me since after a long time searching google I could not find a way to specify explicitly which programs can use the CAMERA or MICROPHONE on my system. As well as I cannot simply disable the Camera, or bind it to a switch on the panel.

Its easy for desktops where you could just unplug microphone or webcam, but you cannot do so on the desktop, and BIOS  solution is not an option in this case, since I rarely reboot the machine...


Thank you kindly for any help :)

---

### Post by Lars Noodén on 2009-11-20
Flash can access the microphone and the camera.  That's part of the deal if you choose to use flash.  

If you are watching video or listening to audio, then you may wish to patronize sites and services that support more reasonable, open formats instead:  

MPEG, Quicktime, Theora

MP3, AAC, FLAC, Vorbis


The MPEG/MP3 formats aren't quite fully open but a mile better than flash.  

If you're trying to make dancing badgers so that a manager or venture capitalist can boast about an 'interactive' web site, then consider doing the same badgers in SVG with Javascript.

---

### Post by ==Troy== on 2009-11-20
Thank you for your response, but sadly it does not answer even a slightest part of my question.


Yes flash has access to microphone and camera, I am very well aware of that. the question is :

1) How can I forbid the access to camera/mic for flash
2) If 1) fails, how do I make a software button to easily disable camera (I have it for the mic)

(plus the #1 post)

---

### Post by cdenley on 2009-11-20
1. Have you tried changing the permissions on the cameras device? (/dev/video0 ?)

2. I think you would be able to disable the kernel module used by the camera to prevent it from functioning.
```

sudo modprobe -l|grep v4l
sudo lsmod|grep v4l

```

I can't really give you specifics because I don't have a camera to test my ideas.

---

### Post by Lars Noodén on 2009-11-21
> **==Troy== said:**
> Thank you for your response, but sadly it does not answer even a slightest part of my question.


Yes flash has access to microphone and camera, I am very well aware of that. the question is :

1) How can I forbid the access to camera/mic for flash
2) If 1) fails, how do I make a software button to easily disable camera (I have it for the mic)

(plus the #1 post)


One way would be to take out flash.  Another would be to steer to sites that support open formats.  Going down the road of closed formats means you will have more problems like this regardless of application or OS.  That answers your original question in full and provides not just a short term solution but a long term one.  

However, if you have flash on linux, then probably the way to prevent flash and just flash from accessing the camera would be to use SELinux.  systrace would work, too, but is not part of ubuntu yet.

---

### Post by ==Troy== on 2009-11-21
> **Lars Noodén said:**
> One way would be to take out flash.  Another would be to steer to sites that support open formats.  Going down the road of closed formats means you will have more problems like this regardless of application or OS.  That answers your original question in full and provides not just a short term solution but a long term one.  

However, if you have flash on linux, then probably the way to prevent flash and just flash from accessing the camera would be to use SELinux.  systrace would work, too, but is not part of ubuntu yet.


You still seem to be able to give an answer which has 0 relevance to the question.

I did not ask how to avoid the issue. Neither did I ask how to remove the software.

My question was clearly stated : How do I disable access to the camera for a piece of software running under linux.

Not how to not need to disable  it. Or how to remove that piece of software.

Disabling the access by removing the software is also a nonsensical  answer.


Ubuntu uses SELinux, but you gave no indication on how to do it in SELinux.




@cdenley Thank you for your suggestions! I will give it a try and post the results!.

---

### Post by Arup on 2009-11-21
You can right click on the flash image to see flash properties and set it not to access mic and cam.

---

### Post by Lars Noodén on 2009-11-22
Removing the software solves the problem of flash accessing the microphone and camera.   The question, in the context of flash, is akin to asking how to prevent Skype from accessing the camera and microphone.   You may wish to read up on [Flash](http://www.google.com/search?q=adobe+flash+exploit).  If its intended use is for 'movies' there are safer, open formats.  

[indent]"[i]
This has raised a concern for me since after a long time searching google I could not find a way to specify explicitly which programs can use the CAMERA or MICROPHONE on my system. As well as I cannot simply disable the Camera, or bind it to a switch on the panel.[/i]"[/ident]

Again the above does that. 

A work-around is SE Linux which is designed to constrain exactly that kind of access.  Hoever, only you or your support department can configure your computer for you.  If you need pointers to [SE Linux on Ubuntu](http://www.google.com/search?q=ubuntu+selinux), then here are three:

[list]
[*] [https://wiki.ubuntu.com/SELinux](https://wiki.ubuntu.com/SELinux)
[*] [https://help.ubuntu.com/community/SELinux](https://help.ubuntu.com/community/SELinux)
[*] [http://packages.ubuntu.com/en/karmic/selinux-policy-ubuntu](http://packages.ubuntu.com/en/karmic/selinux-policy-ubuntu)
[/list]

One [policy](http://www.lurking-grue.org/writingselinuxpolicyHOWTO.html) for all applications and devices.  SELinux policies are not exactly a 5-minute, no-brainer task.  

I find making systrace policies easier than a SELinux policy.  

Seedit might be of use, but I haven't tried it myself:
[http://seedit.sourceforge.net/](http://seedit.sourceforge.net/)

---

