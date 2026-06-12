---
title: "Audio call hangs the MS office communicator with win xp as guest in virtualbox"
date: 2012-07-01
forum: Virtualisation
---

### Post by jittopjose on 2012-07-01
Hi,
I am currrently using Ubuntu 12.04. It works fine in my asus netbook. But to connect to my office system I need windows since we have frequently use ms office connunicator. Moreover our vpn will not work with newer version of ubuntu. I duel boot the pc to with windows 7. and everything was working fine in it. Now I installed virtualbox in ubuntu and installed windows xp sp3 as guest os in it so that i can manage both personal and work things in a single boot. Now the prolem is , when I tried to make audio call from office connuicator in gest os, it hangs. I checked playing mp3 files in guest os (win xp). Its working fine. I tried skype call also.. but not luck. That also end in hanging the application.  Anybody has any idea about this kind of problem? Do i need to change any settings in virtualbox?. I am using the latest version of virtualbox.
Thanks,
Jitto P.Jose

---

### Post by Zookey500 on 2012-07-01
Hi,
There are just a couple of things that I would try......It should work as it basically a PC on a PC. 

1. Make sure that both OS's have enough CPU and RAM to function correctly. ( I had a big problem with that, because it ended up meaning that my ubuntu PC needed more to CPU to run the virtual PC, due to the virtual PC running more CPU intensive programs.)

2. Try uninstalling the program. Then reinstalling.

3. Also, you should check to make sure the Internet settings of both PC's do not conflict. (Sorry, I wouldn't know exactly what to do.)

Hope I could be of assistance :)

Best regards,
Mat

---

### Post by jittopjose on 2012-07-01
Thank you for your reply...I actually installed win xp sp3. I gave 256 mb ram for guest os. I think that is enough for win xp to run properly if no big programs are installed. My net book is run on atom 1.6 GHz processor. I dont know whether that cpu is enough for running a guest os. But everything except this audio call works properly.. I can use text chat and remoting to other computer. no issues in that. but when it comes to audio call, then it hangs.

---

### Post by jittopjose on 2012-07-01
And one more thing... Just now i noticed that, there is a hight cpu usage, nearly 100% when trying to use mic in skype (when i tried to test microphone). I think my atom processor don't have enough power to handle audio call in skype and office communicator..  :(

---

### Post by Cheesemill on 2012-07-03
Minimum system requirements for Office communicator are 512MB of RAM.
This is on top of what you need to run XP.

---

### Post by Zookey500 on 2012-07-04
Yeah, it seems that you may not have the system requirements for this. Sorry.

---

### Post by jittopjose on 2012-07-09
Yes .. I got the point.. I am using a netbook with atom processor.. moreover total ram for the machine is 1gb. :(

---

