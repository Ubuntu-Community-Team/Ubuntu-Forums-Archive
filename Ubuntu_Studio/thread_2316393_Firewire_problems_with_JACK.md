---
title: "Firewire problems with JACK"
date: 2016-03-07
forum: Ubuntu Studio
---

### Post by LuckyAstronaut on 2016-03-07
Hi all, 
Is anyone else having problems with JACK and the ffado driver? I set up a dual boot system with Ubuntu studio 14.04lts to see if it would work for me for music production. It all worked great for a month or two. All of a sudden (around end of Feb), I think after updating software, I can't get jack to read the audio inputs - only midi. This is what I can figure out:
1. The box (edirol  fa-66) and cable work fine
2. Jack still works but only for internal connections - like, I can connect hydrogen to record right into ardour.

I've searched for solutions and tried some suggested fixes for similar issues but nothing seems to get things running again.  I'd appreciate any suggestions to help. Am I stuck going back to my old windows set up until another update fixes the problem? I'm pretty new to Linux so if you need some more info, please be specific on how to get it for you. 

(sorry for the second post. I tried posting on the beginners forum but haven't had any responses in about a week. Thought I'd try the distribution specific forum to see if I'm the only person with the issue)

---

### Post by jejeman on 2016-03-08
What is the chip on the firewire controler?
As you may have already read, I had problems with NEC & MSI chip since kernel 3.5+. Only VIA worked for me (didn't tried TI).
I didn't had time to troubleshoot, I changed the audio interface.

---

