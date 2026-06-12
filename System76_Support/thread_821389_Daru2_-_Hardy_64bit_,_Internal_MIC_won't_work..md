---
title: "Daru2 - Hardy 64bit , Internal MIC won't work."
date: 2008-06-07
forum: System76 Support
---

### Post by laserline on 2008-06-07
Hello,

I'm trying to get the internal microphone to work with Sound Recorder and Skype, but I'm unable to.

Because Skype wasn't working, I tried Sound Recorder, and when that wasn't working, I suppose making that work will also make Skype work (as it uses the default configuration).

I've tried to follow [_**this**_]("http://ubuntuforums.org/showpost.php?p=4689923&postcount=5") post (with the screenshots from Tom) but that doesn't work.

Also, I tried all possible combinations and that doesn't work. I always get this "hissss" sound from speakers when trying to play my recording.


I own a Darter Ultra (daru2).

Thanks,
Idan.

---

### Post by byebyebill1 on 2008-06-08
4 got 2 add on my post, i get the hiss 2. after the settings set as per screenshot, i could barely make out my voice.

---

### Post by thomasaaron on 2008-06-09
Those screenshots are for the Serval.

Run the system 76 driver (System > Admin > System 76 Driver). Then both your internal and external mic will work.

Double-click your speaker icon, and, in the resulting window go to edit > preferences. Make sure all boxes are checked.

Your internal mic is "Front Mic." Your mic jack is "Mic".

If that doesn't get you up and running, I'll put together some screenshots.

The good news is that the mic works great on the DarU2.

---

### Post by laserline on 2008-06-09
Hi Tom,

That doesn't work - I played with all the options before, and I think it's all screwed up... :(

Could you please post detailed screenshots of the exact state everything should be (including Sound Recorder) so I could record sound there ?
There are many devices and its confusing.. Digital, Capture, Capture1 etc...

I already have System76 driver installed and working, should I reinstall it ? anyway to check all is good ?

That would be great if I could get that mic to work.

Thanks in advance,
Idan.

---

### Post by thomasaaron on 2008-06-10
OK. Screenshots attached.

Talk to me...

---

### Post by laserline on 2008-06-10
Hi Tom,

Thanks for the effort - but that doesn't work :-(

Any other suggestions ?

Thanks,

Idan.

---

### Post by thomasaaron on 2008-06-10
I've always got suggestions!:lolflag:
But whether or not they will work is another question. ](*,)

1. You are using the *internal* mic, right? That's what the screenshots are for. If you have an external mic installed, unplug it (just for fun).

2. System > Administration > System76 Driver > Install Tab > Install Button
Then *REBOOT* your computer. Then set up your system like the screenshots above and try it.

3. Post a screenshot of System > Preferences > Sound > Devices Tab

4. Do NOT use a bigger hammer. We'll get it figured out. It's just a configuration issue.

---

### Post by byebyebill1 on 2008-06-10
still working, my controls are not quite the same as yours.

---

### Post by motimbo on 2008-09-03
Did you ever get this figured out?  I'm having a similar problem with a Daru2 using Gutsy 64bit.  Any help would be appreciated.

---

### Post by laserline on 2008-09-04
> Did you ever get this figured out? I'm having a similar problem with a Daru2 using Gutsy 64bit. Any help would be appreciated.


Nope, I didn't have the time.

If you make any progress, please let me know.

Thanks.

Idan.

PS: Intrepid Ibex is just around the corner.

---

### Post by thomasaaron on 2008-09-04
laserline,

Are you using Kubuntu or some other derivative? Are *your* controls the same as the ones in the screenshots?

What is the output of 'cat /proc/asound/version' ?

---

### Post by laserline on 2008-09-07
Hi Tom

I'm using Ubuntu Hardy 64bit.

I followed exactly the screenshots you posted but it didn't help.

I have one more exam this semester (Tuesday) and after it I'll post my screenshots of the same screens you posted.

Thanks,
Idan.

---

### Post by thomasaaron on 2008-09-08
Sounds good Idan. When you do that, please post the output of...
cat /proc/asound/version
...at the same time so that I can do a more thorough comparison.

---

### Post by motimbo on 2008-11-12
I got it to work on my Gutsy 64bit install on a Daru2, but I'm not completely sure how.  I thought I'd post this in case it helps.  I was having the same problems, and decided to try an external mic.  It worked, but the second or third time I tried recording something, there was an echo.  It was the internal mic recording at the same time!!  For some reason, I can't reproduce any of the above, but both mics now work independently of each other.  The one thing I fiddled with that wasn't in your screenshots was the "Digital" slider in the volume control.  I've included a screenshot of that.  

Also, the output of cat /asound/version/ is :  Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).

I hope this helps if anyone is still having this problem.

---

