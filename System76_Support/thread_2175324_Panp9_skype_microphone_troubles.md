---
title: "Panp9 skype microphone troubles"
date: 2013-09-18
forum: System76 Support
---

### Post by forbajato on 2013-09-18
Does the Panp9 have a built in microphone?  I can get Skype to recognize my webcam and produce sound out but not record any sound, got to thinking maybe the laptop doesn't even have a microphone on it.  There is a small hole right next to the mouse pad which looks like a microphone - could it be something else?

thomas

---

### Post by isantop on 2013-09-19
That's definitely a mic. First, check that the volume is turned up in sound settings (on the input tab) and that it isn't muted. If it's all good there, then check in Skype settings to ensure that it's using the system default audio devices.

---

### Post by forbajato on 2013-09-19
> **isantop said:**
> First, check that the volume is turned up in sound settings (on the input tab) and that it isn't muted.

Done.
>  If it's all good there, then check in Skype settings to ensure that it's using the system default audio devices.

Done.

Results - no sound in Skype (via system speakers or headphones), hard to test the microphone function without being able to do a test call due to the total lack of sound.  Should I be using a different (i.e. non-default) setting for microphone, speakers and ringing in the Skype sound devices settings?

---

### Post by forbajato on 2013-09-22
Interesting - I seem to have found a work around.  Turns out Skype works fine under the Unity interface.  I found that if I will boot into Unity, use Skype, run a test call, etc. then boot back into XFCE everything is great.  Odd but that seems to be the way to solve a problem with the function keys as well.

thomas

---

### Post by Sarai the Geek on 2013-09-23
I have a gazelle professional that the built-in microphone wasn't working on- this sounds bizarre but plugging my headphones into the microphone jack and then unplugging them actually made it work. Apparently this is a known bug with the gazp9- might be worth a try on a panp9.

---

### Post by forbajato on 2013-09-23
I saw that solution in some other threads and tried it but it didn't work for me.  It is odd that running the package in Unity seems to set it up to work in other DTEs but I can do that if it means a functional machine.

---

### Post by raphael-estrada on 2013-09-25
I'm no expert on the subject but could it be that launching Unity causes some startup commands to execute which are missing in your XFCE? Compare their autostart configurations and see if there's anything audio related?

---

### Post by forbajato on 2013-09-25
Interesting thought - where are the startup scripts for unity?  What are they called?

---

### Post by raphael-estrada on 2013-09-25
I'd have to google that - I just remember having similar issues with multiple window managers before (was on Crunchbang with OpenBox and Ratpoison, they had separate startup scripts)

---

