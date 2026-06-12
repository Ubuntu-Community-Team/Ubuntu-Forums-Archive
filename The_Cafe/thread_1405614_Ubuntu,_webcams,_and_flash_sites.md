---
title: "Ubuntu, webcams, and flash sites"
date: 2010-02-12
forum: The Cafe
---

### Post by jamesey on 2010-02-12
anyone with a webcam get chat roulette to work? I'm having issues. I know my webcam and mic work, but I cant get [www.chatroulette.com](www.chatroulette.com) to work in firefox or chrome.

---

### Post by Kdar on 2010-02-12
I am not sure about that site. But I know my cam doesn't work online in flash.

---

### Post by samantha_ on 2010-02-12
use [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

to set your webcam permissions

---

### Post by Ric_NYC on 2010-02-12
[B]Webcam/Flash
[/B]

You can test it here:

[http://www.testwebcam.com/](http://www.testwebcam.com/)

After clicking on "Allow".

---

### Post by Kdar on 2010-02-12
> **Ric_NYC said:**
> [B]Webcam/Flash
[/B]

You can test it here:

[http://www.testwebcam.com/](http://www.testwebcam.com/)

After clicking on "Allow".

weird. There it works. But on another web-site it never did.

---

### Post by danootz on 2010-02-13
I'd like to second the request of any info to get a webcam to work in chatroulette.

The test site above does work for me as well and I've found another site suggesting to configure adobe flash settings to auto allow rather than question for permission. It didn't help.

---

### Post by witeshark17 on 2010-02-14
What a game! You *may* get results with your web cam by clearing your browser history etc.

---

### Post by Kdar on 2010-02-14
My camera just blinks and thats all.

---

### Post by sledge73 on 2010-02-14
both sites work fine for me. I wouldn't recommend setting adobe flash to auto for any reason!!

---

### Post by loell on 2010-02-14
chatroulete seems to work in chrome, although my webcam requires **v4l1compat.so** to work.

ie ** LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so google-chrome**

---

### Post by user1397 on 2010-02-14
chatroulette is the wave of the future! :popcorn:

---

### Post by malegria on 2010-02-15
[FONT=Arial][SIZE=3]I have successfully gotten Chatroulette.com to work with my machine. Firstly, I am using Ubuntu 9.10 Karmic and a **[Creative Live! Video IM Ultra Webcam]("http://www.amazon.com/Creative-Labs-Video-Ultra-Webcam/dp/B001NEK0PC")**. 
1. Install WebcamStudio. The instructions for that are simple, and are** [here]("http://www.ws4gl.org/download/installing-on-ubuntu")**.
2. Use this **[webpage ]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html")**to set your Global Flash Settings to always allow access by Chatroulette.com
3. Bring WebcamStudio up before going to Chatroulette.com
4. First Click on "Sources" scroll down to "Webcams" and select your webcam (it should be detected).
5. Next a small window will appear. Click on "Source" and select "Start." At this point your webcam should turn on and show you an image of yourself!
6. Next open up a browser and go to chatroulette.com . It should be working now just fine!

If you want sound you'll have to configure that in your Sound Preferences as "Input." Also, I find Firefox really slows down with this flash website so I prefer using the *newest* Opera which works better for me.

Good luck![/SIZE][/FONT]

---

### Post by user1397 on 2010-02-17
i don't know if anyone cares, but chatroulette isntantly worked without ANY configuration when I got my dell mini 10v ubuntu netbook, just thought it was kindof neat.

---

### Post by gspawn69 on 2010-05-29
I also need to use the LD_PRELOAD command for my webcam to work. Is there some way I can get my system to just use that by default so I don't have to type it in every time? I tried adding the command to the launcher but it doesn't work.

---

### Post by Script Warlock on 2010-06-08
i remember using in the launcher....    bash -c LD_PRELOAD

---

### Post by samalex on 2010-06-08
For UStream specifically I had to modify the Flash Settings Manager to always allow some sites to work, so I bet this'll need to be done for other Flash sites to use the webcam.

[Here's a post]("http://ubuntuforums.org/showpost.php?p=8669775&postcount=30") I made in January 2010 when we were talking about this on the System76 forum.  And [here's a link]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html") on the Macromedia site that'll give you access to the settings manager.

HTH,

Sam

---

