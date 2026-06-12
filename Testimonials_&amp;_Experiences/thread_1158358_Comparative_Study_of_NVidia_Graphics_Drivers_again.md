---
title: "Comparative Study of NVidia Graphics Drivers against Flash Player"
date: 2009-05-13
forum: Testimonials &amp; Experiences
---

### Post by LesterPalooza on 2009-05-13
Hello everyone!

I was bored this afternoon so I made a series of tests comparing **NVidia graphics drivers and their effects on Flash Player**. The test was conducted using **PowerBench** found on the Internet on this website: [http://www.powerflasher.de/bench/powerbench.html](http://www.powerflasher.de/bench/powerbench.html)

A series of _16 tests_ were conducted between 3 NVidia graphics drivers and results were taken from Total Score from PowerBench tests. The Total Score directly reflects the FPS(Frames Per Second) of the flash player I was using. The Total Score is based from 10 tests concerning 7 different processes in flash:
[LIST]math
controlling structures
bitmap graphics
drawing
masking
video embedding
transparency[/LIST]
*Therefore, the higher the Total Score, the better Flash experience. (More score means more FPS)*

**Here's the System Setup:**
HP Compaq Presario CQ50
AMD64 Athlon Dual Core QL-50
NVidia Graphics Card 8200M G (running on 65 to 87 degrees Centrigrade)
(about : plugins from Firefox)
File name: npwrapper.libflashplayer.so
Shockwave Flash 10.0 r22
1.9Ghz
250Gb RAM
60 Gb Allocated for Ubuntu
Ubuntu 9.04 Jaunty Jackalope x86_64
Kernel Version: 2.6.28-11
Browser: Mozilla Firefox 3.0.10
Compiz Disabled (Effects set to None)

**Graphics Drivers Used in this test:**
*everything indicated are all NVidia graphics driver versions
[LIST]
173.14
180.44
185.19Beta (installed using this guide: [http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185"))[/LIST]
**None indicates the test was conducted without any NVidia graphics drivers installed on the system and using VESA*

[CENTER][IMG]http://i97.photobucket.com/albums/l238/lhester_12/1-1.jpg[/IMG]
[IMG]http://i97.photobucket.com/albums/l238/lhester_12/2-1.jpg[/IMG]
[IMG]http://i97.photobucket.com/albums/l238/lhester_12/3-1.jpg[/IMG]
[IMG]http://i97.photobucket.com/albums/l238/lhester_12/4-1.jpg[/IMG][/CENTER]

[SIZE="2"]**For my system, I believe 173.14 is the fastest among the three. Although 185.19 is still in BETA. I personally do not know the reason why I find 173 faster than 180 and 185 but I'm gonna use 173 now! :D**[/SIZE]

Attached is a copy of my OpenOffice spreadsheet. Just in case you wanna see my data table!

_**Disclaimer**_
*I am not advertising PowerBench or any other products. This test was just for fun and I was interested in optimizing and finding the best possible Flash experience! (for my system at least)*

Credits:
Thanks to [tinivole]("http://ubuntuforums.org/member.php?u=490875") of Ubuntu forums for his awesome guide to installing 185.19 and to PowerBench for the great Flash tests.

---

### Post by LesterPalooza on 2009-05-13
What do you guys think of this?

[http://ubuntuforums.org/showthread.php?t=1158358]("http://ubuntuforums.org/showthread.php?t=1158358")

I was definitely bored :D

---

### Post by BuffaloX on 2009-05-13
I don't get it.
16 tests divided into 10 concerning 7.
4 results posted?

Otherwise it's cool with the graphics and all.
Seems like none would be the best choice of driver.
Is it vesa nv or nouveau.

---

### Post by LesterPalooza on 2009-05-13
> **BuffaloX said:**
> I don't get it.
16 tests divided into 10 concerning 7.
4 results posted?

Otherwise it's cool with the graphics and all.
Seems like none would be the best choice of driver.
Is it vesa nv or nouveau.

is it clearer now? sorry for that :D

---

### Post by Skripka on 2009-05-13
> **LesterPalooza said:**
> is it clearer now? sorry for that :D

A little...there are 4 graphs, do they each represent a different run?  different tests?  

I ran that same Benchmark site on my machine, I get 3102 for Opera and 3320 for Arora.  Nvidia 180.51 and GTX260.

---

### Post by BuffaloX on 2009-05-13
Wow I got 1811 with my Gforce 7950-X2.
My system definately isn't high-end anymore.

---

### Post by Skripka on 2009-05-13
> **BuffaloX said:**
> Wow I got 1811 with my Gforce 7950-X2.
My system definately isn't high-end anymore.

I could probably get it to go a bit quicker, if I turned off all the bling I have in KWin ):P

---

### Post by LesterPalooza on 2009-05-13
What does one do if he/she wants to optimize performance on flash and their video card?

---

