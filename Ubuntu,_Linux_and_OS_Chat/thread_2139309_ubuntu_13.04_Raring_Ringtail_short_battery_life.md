---
title: "ubuntu 13.04 Raring Ringtail short battery life"
date: 2013-04-26
forum: Ubuntu, Linux and OS Chat
---

### Post by alvpizz on 2013-04-26
hello!
i have just installet Ubuntu 13.04 on my Samsung RC-530 S02, and I'm liking it very much. but i have one problem I would like to solve: i m noticing that this new OS is consuming too much energy. before installing it, i used ubuntu 12.04, and my battery life coult reach 6 hours (if i kept mininum brightness). now it hardy reaches 1 hour and 45 minutes. furthermore, i can hear that the PC's fan is working much more than before. can I do someting to change this?

thanks

---

### Post by dandroid13 on 2013-04-26
Tried TLP? Here: [http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)

---

### Post by rrich1974 on 2013-04-26
wrong idea.....
if the fan is constantly working at a high speed it means that you have a big load on your processor.  open "top" and detect that process. 
this is usually happen because of video driver. 
to be honest....i would wait 3 months before will eventually install 13.04, i am sure that it will become more mature!

---

### Post by alvpizz on 2013-04-26
> **rrich1974 said:**
> wrong idea.....
if the fan is constantly working at a high speed it means that you have a big load on your processor.  open "top" and detect that process. 
this is usually happen because of video driver. 
to be honest....i would wait 3 months before will eventually install 13.04, i am sure that it will become more mature!

I've just tried to do what you have said. doing this, i have also noticed that the system monitor is not working well: it said that all processes were using 0% CPU, while using "top" from the terminal i found out that thunderbird was using 50%. but, except this, no other process is charging my CPU, ad now it is at 3% usage. ad so it was before i started thunderbird obviusly. but the fan has not really slowed down.
I also know I should have waited some more to install 13.04, but i 12.04 was overloaded with programs and was slowing down, so I 've decided to reintall now. if i can't manage to solve this, I'll try debian i think. I don't want ti have such a noisy PC

---

### Post by dandroid13 on 2013-04-26
If you wait too much, better wait more and install Saucy. Only issue here is the wireless card driver.

---

### Post by alvpizz on 2013-04-26
yeah I know.. maybe I'll learn how to do that

---

### Post by dandroid13 on 2013-04-26
But try installing TLP, it really makes a difference here.

---

### Post by monkeybrain2012 on 2013-04-26
> **rrich1974 said:**
> wrong idea.....
if the fan is constantly working at a high speed it means that you have a big load on your processor.  open "top" and detect that process. 
this is usually happen because of video driver. 
to be honest....i would wait 3 months before will eventually install 13.04, i am sure that it will become more mature!

I would normally suggest that too, but now the support cycle is 9 months instead of 18, so that has to be factored in, maybe waiting for a month or a month and a half makes more sense.

---

### Post by alvpizz on 2013-04-26
I've installed it, but i really don't have unterstood how to make it work. It is already running i think, since i have restarted my PC, but nothing has changed

---

### Post by dandroid13 on 2013-04-26
Maybe you should post your issue in the General Help section, the guys there will be able to help you more than I do.

---

### Post by rrich1974 on 2013-04-26
are you telling me that with 3% load, it is still noisy? strange....
now i see..

[TABLE="width: 100%"]
[TR]
[TD="class: valuea, width: 35%"]Chipset graphics controller[/TD]
[TD="class: value, width: 65%"]NVIDIA GeForce GT540M and Intel HD Graphics 3000
[/TD]
[/TR]
[/TABLE]

see, you have hybrid graphic....am i goddamn right? 
to be honest, you are out of luck with linux. but still, if you are telling us that using 12.04 works better, then use it! 

you need to find a way to stop the nVidia card. either in bios or maybe to try bumblebee. it seems that 12.04 uses only intel HD graphics. 

[http://notebook.b4by.net/samsung_rc530__np_rc530_s02_.html](http://notebook.b4by.net/samsung_rc530__np_rc530_s02_.html)

is this the laptop?

---

### Post by cariboo on 2013-04-26
> **dandroid13 said:**
> Maybe you should post your issue in the General Help section, the guys there will be able to help you more than I do.

+1 for starting a thread in General Help, this isn't the place to diagnose and repair problems.

---

