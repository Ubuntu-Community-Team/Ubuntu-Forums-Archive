---
title: "My first Raspberry Pi project - success!"
date: 2015-05-28
forum: Ubuntu/Debian BASED
---

### Post by coldraven on 2015-05-28
I set up a kiosk mode browser for a small local charity. It shows an offline version of their web-site, there is no internet access on site. I simplified it so that it's only HTML and Javascript.
Their museum is an all wood structure so at the end of the day they switch off the power at the main breaker. This means that the Pi is having a hard shutdown each day. A month has passed and the Pi is still working perfectly.

Parts:
AOC I2369VM 23 inch IPS LED Monitor (Nice screen, the speakers are not very powerful)
Raspberry Pi 2
USB mouse

Software:
Raspbian
Kweb3 (Using the HTML5 Video tag makes life easy!)

Problems:
After getting it all working as user pi I created a user called guest to stop anybody messing with the system. When logged in as guest the videos would not play.
The solution was to add user guest to the video group as shown here: [http://omxplayer.sconde.net/](http://omxplayer.sconde.net/)
Then add user guest to the group "audio".

At boot-up the Pi logs in as "guest" and auto-runs Kweb3. Sweet :)

I'm so impressed with the Pi 2 that I just bought two more! One I gave to a friend with Kodi installed and the other is for me to play with.
Mods, I maybe should have posted this in the Cafe, feel free to move it.

---

