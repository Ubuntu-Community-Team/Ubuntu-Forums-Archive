---
title: "Cheese slow after Hardy upgrade"
date: 2008-04-26
forum: System76 Support
---

### Post by TerpInHotLanta on 2008-04-26
Has anyone noticed a huge slowdown in Cheese after upgrading to Hardy?

I have a PAN-V3 system.

Any ideas?

Thanks in advance!
Charlie

---

### Post by laserline on 2008-04-26
Hi,

The same with Darter Ultra (daru2)
Please see this other post and check if you are experiencing the same: [http://ubuntuforums.org/showthread.php?t=764970](http://ubuntuforums.org/showthread.php?t=764970)

Thanks,
Idan.

---

### Post by kevin11951 on 2008-04-26
same here, gazv5 VERY slow web cam, but it works perfectly (better actually) in skype for some reason, so its just cheese.

---

### Post by thomasaaron on 2008-04-29
I don't think this problem is hardware related. I think it is actually the cheese application. I think you will find that the webcam on skype actually runs at the correct speed.

---

### Post by kevin11951 on 2008-06-14
> **thomasaaron said:**
> I don't think this problem is hardware related. I think it is actually the cheese application. I think you will find that the webcam on skype actually runs at the correct speed.

ok, but i really want to get cheese to work, is there anything i can do (besides downgrade to gutsy) that will help?

---

### Post by thomasaaron on 2008-06-16
Your best bet would be filing a bug against Cheese here...
[https://launchpad.net/cheese](https://launchpad.net/cheese)

---

### Post by unimatrix on 2009-02-27
It's still like this under Intrepid.
I see noone bothered to submit a bug report.

---

### Post by thomasaaron on 2009-02-27
Cheese is now fixed and running fine in Intrepid.

---

### Post by unimatrix on 2009-02-27
I beg to differ.

---

### Post by thomasaaron on 2009-02-27
Make sure you're fully updated. We just finished re-testing it on all of our shop machines, and it is working fine.

Also, if you are having trouble with it, it saves everyone a lot of time and energy if you include details. What happens? What are you seeing? What is your computer model? Otherwise, it is quite difficult to efficiently help you.

---

### Post by TerpInHotLanta on 2009-03-10
I'm not sure if this is the reason why there was a seeming slowdown of Cheese, but I found that the resolution (set under preferences) was defaulted to 1600x1200 for the webcam.

After adjusting the resolution down to 800x600, the webcam worked as I remember it working when I first got my system.

Did cheese previously have the default resolution lower so that many users felt as though there was a massive slowdown?

Hope this helps!

---

### Post by unimatrix on 2009-03-10
Wow, you're right. I didn't even notice Cheese had preferences.
Obviously my shitty camera can't do high resolutions.
Reducing the resolution did the trick!

---

### Post by laserline on 2009-03-10
My laptop's camera is 1.3MegaPixels (Daru2).

Just installed Cheese on Intrepid, it recognizes the resolution correctly (1280x1024) but it's dead slow.

The only resolution one step lower then that is 640x480 - and that's faster.

It's really odd...

Any clues ??

Thanks,
Idan.

---

### Post by thomasaaron on 2009-03-10
It's *probably* a problem with the intel graphics driver (since resolution affects cheese's performance). 

But, try disabling your desktop effects just to see if cheese speeds up. At least that will rule out a problem with compiz.

System > Prefs > Appearance > Visual Effects > None.

---

### Post by laserline on 2009-03-10
Hi Tom,

Disabled Compiz, it's still slow...

Idan.

---

### Post by thomasaaron on 2009-03-10
OK. I'm pretty sure it is an issue with the intel driver. Try enabling backports in Software Sources and then fully update. Then reboot. See if that fixes it. 

I'm sure I remember hearing about a problem with the Intel driver not reporting the resolution correctly to cheese.

---

### Post by tidris on 2009-04-18
I am running ubuntu 8.10 with kernel 2.6.27-11 and I have also been experiencing a major slow down in cheese with the 1.3 megapixel internal webcam on my 2.4GHz dual core2 laptop. By major slow down I mean that that the video frame rate is several seconds between frames instead of several frames per second.

However today I discovered a way to make cheese work normally. What I do is open a terminal window and type this in it followed by Enter:

while true; do echo > /dev/null;  done

That line runs a script that keeps the CPU busy. As long as that script is running cheese video runs at a reasonable frame rate. If the script stops the video goes back to ultra slow speed. Weird, eh?

---

### Post by earlra on 2009-11-22
I am having the same problem in 9.10.  Cheese was working fine for me in 9.04.  I'm having the same problem on two systems.  I tried both recommendations above, for turning off visual effects, and enabling backports, neither of which had any effect.  Any other suggestions?

---

### Post by thomasaaron on 2009-11-23
Which System76 model do you have?

---

### Post by pelastikbintang on 2010-10-29
try changing your video output from "ximagesink" (X Window System (No Xv)) to "xvimagesink" (X Window System (X11/XShm/Xv))

Alt-F2--> type "gstreamer-properties" without the "" ..change the video preference.

---

