---
title: "Serval Microphone does not appear to work"
date: 2008-02-25
forum: System76 Support
---

### Post by Bromo on 2008-02-25
I have a Serval Performance, running 7.10 (bought in December of 2007)

I have recently installed Skype and while the webcam appears to work OK, I cannot get the microphone to work at all.  I attempted to use another program (name escapes me, as I left the computer at home)

I reinstalled system 76 drivers and have also "reverted to factory settings" to no avail.

I am sure it is something really simple that I am missing, but I haven't had the time to dive into it.  Can you help me? :)

---

### Post by thomasaaron on 2008-02-25
It is just a configuration issue.

I don't have a Serval to work on today, but if memory serves, you have to use "Front Mic" and fiddle with the "Digital" slider.

Also, with Skype, you have to configure the mic from WITHIN skype. Attached are some photos of how you would do that using USB headphones/mic (which will give you a lot better sound quality, by the way).

---

### Post by Bromo on 2008-02-25
I was unable to get good results.

I did Preferences -> SOund

And Selected "Front Mic Boost" from the drop down menu.

(SOund playback for Sound Events, Music and Movies, Audio conferencing all set to "autodetect")

(Sound capture under conferecing set to ALSA
Default MIxer Tracks:
Device set to HDA Audio (ALSA mixer) -> "Front Mic Boost" selected

I then hit "Close"

DOuble clicked on "Volume Control" and SLid up "Front Mic Boost" to max

I ran "Sound Recorder" from the Applications->Sound&Video menu
and was unable to playback any sound. (I selected "Front Mic Boost" from menu and then "record" and shouted a few words, stop then play)

Tried Skype as well amking "test calls" in all configurations - I heard a hiss but no sound.  

:confused: This is a curious problem...

(Serval Performance, serp3 model)

---

### Post by thomasaaron on 2008-02-26
OK. I just put on my whiteboard to test this on our shop serval. I'll try to get it done and post the necessary configurations by the end of today.

---

### Post by Bromo on 2008-02-28
Any news?

---

### Post by deeGraYve on 2008-03-02
have exactly the same issue, have been fighting with this for a long time already
any news?

---

### Post by hkarl629 on 2008-03-02
Hi,  deeGraYve

I also have a Serval Performance, serial Serp2, What model is yours?  I would like to get my webcam to work but as yet System 76 doesn't seem to have the right driver.

---

### Post by deeGraYve on 2008-03-02
serp3
and I have webcam working with new version of skype
i'm also working on face recognition project using openCV library and it does acquire the webcam input and works wonderfully, so some standard methods should work. But I couldn't make any of the standard ubuntu programs to work with it...

---

### Post by thomasaaron on 2008-03-03
Sorry, guys. I got really slammed at the end of last week and didn't have a chance to run the check. I'll try to get it done today.

Best,
Tom

---

### Post by thomasaaron on 2008-03-06
Building a Serval right now for testing...

---

### Post by thomasaaron on 2008-03-06
OK, here are screenshots of my SerP3 settings for using the internal mic to record with Applications > Sound & Video > Sound Recorder.

---

### Post by blackbeastofaarrgh on 2008-03-07
Awesome, was having this same problem. Works nicely, thanks!

---

### Post by Bromo on 2008-03-09
I tried it and - works great!

Only note for people who are adjusting volumes -- 

DOuble click on volume control to get individual sliders, then do this:

Edit -> Preferences and then click on all the availabel volume controls to get the graphical representations.

Thanks, man!  I was able to use Skype AND voice in Second life, recording and so on!!

I am going to gear up to get the Wild Dog next! :D

---

