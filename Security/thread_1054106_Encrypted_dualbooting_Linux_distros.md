---
title: "Encrypted dualbooting Linux distros"
date: 2009-01-29
forum: Security
---

### Post by unf4b1x on 2009-01-29
Hi. I am trying to differentiate which linux distro is best before doing a full linux installation:

1.  Has anybody have done a dualbooting of 2 or more linux distros on an encrypted hd maybe in the principles of Uwe Herman's setup: [http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system?](http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system?) Would that be possible?  If it does work, could you share your basic configuration? 

2.  Or, Has anybody have done an encrypted base installation under a grsecurity-patched kernel? An Ubuntu or other linux distro dualbooting.  Is it doable considering the bugs and security risks?

3.  If I am going to use the Desktop edition, it would be an easy task, right?  But, what if I am going to use the Server edition, do I have to think which distro that I am going to use before setting up the base installation? Does it have any compatibility issues?

---

### Post by hyper_ch on 2009-01-29
what's so special about herman's setup?

---

### Post by unf4b1x on 2009-01-29
> **hyper_ch said:**
> what's so special about herman's setup?

I don't know anything much about Uwe Herman's setup moreso than you, only that he was included as a resource on "How to perform a hardened installation:" [http://ubuntuforums.org/showthread.php?t=510812&highlight=uwe+hermann](http://ubuntuforums.org/showthread.php?t=510812&highlight=uwe+hermann) which was started by bodhi.zazen on a thread regarding Ubuntu Security. Although, I've tried his setup but I failed and I could not provide you with any screencaps regarding that failed experimentation of mine.

---

### Post by Tubes6al4v on 2009-01-30
You could dual boot encrypted OSs. There are basically two ways that popped into my head imediately:

1) Two LUKS volumes with the /boot of each unencrypted (I have not idea if they can be combined).

2) Use a hardware encrypted drive. Then everything will be encrypted and you can have all the OSs and whatnot that you want! I think that Hardware encrypted SSD has come out. But that is just expensive.

---

### Post by unf4b1x on 2009-01-31
> **Tubes6al4v said:**
> You could dual boot encrypted OSs. There are basically two ways that popped into my head imediately:

1) Two LUKS volumes with the /boot of each unencrypted (I have not idea if they can be combined).

2) Use a hardware encrypted drive. Then everything will be encrypted and you can have all the OSs and whatnot that you want! I think that Hardware encrypted SSD has come out. But that is just expensive.

...since I am still noob on Ubuntu Linux many great features, reading these forums has become a hobby of mine and I try to just ask if the problems I have encountered are different from others.  It seems that, although there are so many questions asked in the forum, some remain unanswered still. I am just thankful that people have provided suggestions/replies to threads I have posted.

Thank you for your suggestions.  I might have to need more info on those two or maybe you could provide a website for its HowToGuide.

---

