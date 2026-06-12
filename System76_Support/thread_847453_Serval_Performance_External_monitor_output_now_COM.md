---
title: "Serval Performance: External monitor output now COMPLETELY broken"
date: 2008-07-02
forum: System76 Support
---

### Post by jan_nienaber on 2008-07-02
Good Day all

Will the external monitor switching be ever fixed for Serval Performance laptops (SERP1)? It is now completely and totally BROKEN (Since Ubuntu 8.04)... Which means that I can no longer use my laptop for presentations AT ALL, and that in turn means that it is now a boat anchor and I need a new laptop.

Previously, on 7.10 I could at least restart the X server and the display would default to an external monitor, if one was connected. This now no longer works.

Any comments? Opinions? Hope for the future? Perhaps I am just missing something?

-- Jan N., BC, Canada.

---

### Post by thomasaaron on 2008-07-02
A few things...

First, Try it from a Hardy live CD to ensure there is no hosed configuration resulting from your upgrade. If you did a fresh install, disregard this step.

Second, Plug in your monitor and start your computer. Then go to System > Preferences > Screen ReSolution. Do you see two squares? If so, one represents your LCD, and the other represents your external monitor. Select the one that represents your external monitor, select the appropriate screen resolution for it, etc... Then click Apply. Any dice?

---

### Post by jan_nienaber on 2008-07-02
> **thomasaaron said:**
> ...Do you see two squares? If so, one represents your LCD, and the other represents your external monitor. Select the one that represents your external monitor, select the appropriate screen resolution for it, etc...
Woo-hoo! I tried this earlier on, did not work - then in consideration of your advice, I realized I had to run nvidia-settings as root, and that did the trick! (For some reason, starting it from the System->Administration menu starts it as a non-sudo user)

Things are not perfect yet but I can totally use this as a workaround.

Thanks a ton, Thomas!


-- Jan (BC, Canada)

---

### Post by hkarl629 on 2008-08-04
I too want to use my Serp 2 for presentations.  Directing the output of my monitor to a projector is not easy. I have to go to terminal then type in nvidia-settings. This brings up the nvidia screen and after making serveral changes, I eventually get the output of my monitor through the projector on to the wall screen.

On an earlier laptop. the function key + F7 toggled between my monitor or the projector or BOTH (which is what I want).

Is there a more direct way to do this with my Serval (Serp 2)? I am running Hardy Heron (8.01). Love the computer otherwise.

I appreciate your input/help.  Am a novice to Ubuntu so need explanations at the most basic level.

Thank you.

hkarl629

[email]hjuelch@sc.rr.com[/email]

---

### Post by thomasaaron on 2008-08-05
No, nvidia settings is the only way.

---

### Post by hkarl629 on 2008-08-05
Thanks Tom,

Thought I would ask. Always interested in making things easier.  

Any word on when the webcam on the Serp 2's will be enabled through the system 76 drivers?  It's been a long time.

Karl Juelch
[email]hjuelch@sc.rr.com[/email]

Bluffton, SC

---

### Post by thomasaaron on 2008-08-06
Hi, Karl.

The fix for the webcam is now available...
[http://ubuntuforums.org/showthread.php?t=774863&highlight=webcam](http://ubuntuforums.org/showthread.php?t=774863&highlight=webcam)

We are striving to get it all put into the next System76 driver release. It will probably be when the new line of laptops come out around the 15th.

---

