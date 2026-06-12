---
title: "OpenCV Stuck at 80% to 90%"
date: 2018-09-16
forum: Ubuntu/Debian BASED
---

### Post by itechstr on 2018-09-16
I am kinda new to both Raspberry Pi and OpenCV and I am trying to install OpenCV for a project. I did all of the steps I found on "[https://www.pyimagesearch.com/2015/07/27/installing-opencv-3-0-for-both-python-2-7-and-python-3-on-your-raspberry-pi-2/](https://www.pyimagesearch.com/2015/07/27/installing-opencv-3-0-for-both-python-2-7-and-python-3-on-your-raspberry-pi-2/)". Finally I started compiling OpenCV and after 3 hours of waiting the build stopped at %86 and Raspberry was completely frozen. I had to reboot to get it back to work and luckily I didn't lose any files. So I went over all the steps again, the build reached back to %86 without waiting and continued until %89. It is still frozen and I don't want to risk losing any files, please find a safe way to complete the installation.
[Second time frozen screenshot]("https://i.stack.imgur.com/V7gb1.png")
Thanks in advance.
Edit 1: I don't know if it helps but it seems like the CPU use might be affecting the installation process because the screen froze right after the CPU counter went up to 100%. Also I have a case, a heatsink and I am using a huge room fan to cool my Pi so I don't think the temperature is the problem.

---

### Post by wildmanne39 on 2018-09-16
Hello and welcome to the forum!

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

How long did you wait when it got stuck? maybe it is just taking a long time at that percentage to move forward.

---

### Post by itechstr on 2018-09-16
Thank you, I waited for almost 30 minutes, tried to run backup terminal, connecting to my pc via vnc but it was completely dead.

---

### Post by Frogs Hair on 2018-09-16
The screen shot appears to be the Raspbian OS , so moved to Ubuntu Debian based .  If Using U Mate let us know.

---

### Post by itechstr on 2018-09-16
Thanks mod, I am new to this forum.

---

### Post by yetimon_64 on 2018-09-16
After doing quite a bit of building for a media player on a raspberry pi 3 recently this sounds like your processor is getting too hot.

I don't see a temperature applet in your screenshot, it would pay for you to right click on the panel > select "Add / remove panel items" and add a temperature monitor. The processor shows as being at 95% which is pretty fully loaded up and would likely be at 60 + degrees.

Once the processor hits about 60 deg C any building tends to bog right down sometimes to a complete stop seemingly. 

To build applications on a pi it most definitely pays to have heat sinks installed. I ordered a few packs online when building mpv player and ffmpeg from source on my r-pi set ups. Each board had to have 2 heat sinks installed and while building the code for mpv and ffmpeg I would point a cheap pedestal fan to blow wind across the open case and fins. This kept my temps in the low to mid 50s while building the applications avoiding such bog downs. My first attempts to build mpv bogged the process down every time the processor hit about 60 to 62 degrees centigrade; after installing heat sinks and a using a pedestal fan, no more problems occurred.

**Edit:** sorry but I missed your last line on the first reading and response, but even a room fan may not be enough air flow under such loads. My pedestal fan is about 2 to 3 feet away on medium to full speed and angled down to blow air directly into the open case and fins when building code and running the processor at full loads with the most heat output. Try adding the temperature monitoring applet to your panel as 60 deg C and higher will often cause what you describe here.

---

