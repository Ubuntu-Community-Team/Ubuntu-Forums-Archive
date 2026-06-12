---
title: "Pangolin performance random freezes in Ibex"
date: 2008-11-05
forum: System76 Support
---

### Post by marcor on 2008-11-05
I have a pamp4i with intel graphics and installed Ibex twice on it. Once it was an upgrade from 8.04 that came with the laptop and the other time was a fresh install. Both times the system became unusable because it started to freeze very often (every ten minutes or so). When it freezes the two rightmost LEDs on the front of the laptop are blinking. Please help.

Marco

---

### Post by Lee_Machine on 2008-11-05
There is a Kernel bug in Ibex. I have/had the exact same thing. 

I found it to crash when I am using a bittorrent program, Transmission and Deluge. Also when transferring files via my in home network computer to computer over wifi. 


See this thread [http://ubuntuforums.org/showthread.php?t=969887](http://ubuntuforums.org/showthread.php?t=969887)

but im sure Tom will have something to say to as this must NOT be an nVidia driver as you are using an Intel Graphics card and I have a Gforce 9300. That doesnt rule out Xorg but its pretty solid now days. Every since the overhaul done for 6.04.

Are you using wifi? and a bitorrent program when it happens? Even if the torrent program is closed if you have used it that session without rebooting I get freezes but it I dont use it at all then no freeze. 

Good luck.

---

### Post by formol on 2008-11-06
I got the exact same problem.  It freeze when I transfers with WIFI or LAN, or when I play a movie (.mkv, 1080p)

configuration :
Pangolin (black)
Ubuntu 8.10 32bit
Nvidia binary driver for the 9300
no system76 driver (.deb)

should I :
- re-install 8.04 64Bit (or 32bit as I wish?)
- post an log file here (if yes, which one?)

---

### Post by Lee_Machine on 2008-11-06
> **formol said:**
> I got the exact same problem.  It freeze when I transfers with WIFI or LAN, or when I play a movie (.mkv, 1080p)

configuration :
Pangolin (black)
Ubuntu 8.10 32bit
Nvidia binary driver for the 9300
no system76 driver (.deb)

should I :
- re-install 8.04 64Bit (or 32bit as I wish?)
- post an log file here (if yes, which one?)

Try the fix that I posted, I've yet to have a crash.

---

### Post by marcor on 2008-11-06
I am not exactly sure what it is related to because my laptop freezes when I am doing nothing. I just let the compute stand there while I am logged in with no programs running and it will freeze. And I have never used a bittorent client by the way. I really would like to hear system76 support about that.

thanks
Marco

---

### Post by thomasaaron on 2008-11-06
Lee_Machine and formol, you guys have a different machine than marcor. And since he's not using bit torrent downloading, it may not be the same issue.

But Lee_Machine's fix is probably going to be the fix. So, marcor, go to...

[http://ubuntuforums.org/showthread.php?t=969887](http://ubuntuforums.org/showthread.php?t=969887)

...and follow his directions there.

---

### Post by formol on 2008-11-06
Hi,

I tryed the Lee_machine solution, it didn't work.

note : I was not using a torrent software, I was transferring, by WIFI and LAN, between my main computer and my laptop.

I've, unfortunately, no choice for now than returning to 8.04, for school and professional purpose.  I'm sorry, I would have like to solve this problem, but I cannot allow my computer to be unstable.  I tested the Alpha version of 8.10 this summer because I could, but now, I'm sorry.

---

### Post by thomasaaron on 2008-11-07
If you still have 8.10 installed, run...
sudo apt-get install linux-backports-modules-intrepid

If you've moved to 8.04 already, and the problem occurs, try...
sudo apt-get install linux-backports-modules-hardy

That should cure it. It is a problem with Intel's wirless driver for the 4965 wireless card.

---

### Post by marcor on 2008-11-07
I tried the solution you proposed from the other thread for a couple of hours and still no freeze. for now it seems to work and if the freezes start again I will report it again on this thread. thanks. 

When do you think this will be fixed by default be it in the ubuntu repos or at least in the s76 drivers. I suggest s76 to solve it by default as fast a possible since I am sure many users are not ready to face the process of going though the forums to find the fix.

Thanks again for the fix
Marco

---

### Post by Lee_Machine on 2008-11-09
Yeah I have yet to have a freeze since installing the backports. It is nice to know that the problem lies in the Intel wireless card driver. 

Again I'm grateful for companies like S76. Freedom is what it's all about. 

Also your support is great! At least for me it is, but I've been using Linux for 8 years; but the support is nice to have. A nice change from me being peoples tech support :D

---

