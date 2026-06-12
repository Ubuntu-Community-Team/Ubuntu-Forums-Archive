---
title: "exe virus attack wine"
date: 2011-04-29
forum: Wine
---

### Post by d15tu121314 on 2011-04-29
hy everybody, i'm still an ubuntu noob, going to install wine on maverick, but i'm still afraid of something, that would be my question, is there any posibilities that an exe virus could attack wine?would it affected maverick too?...i would appreciate so much for the reply... i'm sorry for my bad english...thanks b4...

---

### Post by Sub101 on 2011-04-29
This is quite a common question.

[http://www.linux.com/archive/feed/42031](http://www.linux.com/archive/feed/42031)

Viruses can run, and as the link shows, can affect Linux.

---

### Post by d15tu121314 on 2011-04-29
so it can affect linux too, i see, hmm, maybe i should think again about install wine on maverick..,thanks for the reply Sub101...

---

### Post by Sub101 on 2011-04-29
> **d15tu121314 said:**
> so it can affect linux too, i see, hmm, maybe i should think again about install wine on maverick..,thanks for the reply Sub101...

I wouldnt consider it a major risk really.

I think you would actively have to try and run a virus for it to be a real risk. A Windows virus would need to be started in Wine to do anything.

---

### Post by d15tu121314 on 2011-04-29
mmm, sub101.. do u mean if i have a w32 virus on my wine that affected my linux so bad, then i should just remove the wine,and linux will be back fine, right?.....

---

### Post by Sub101 on 2011-04-29
> **d15tu121314 said:**
> mmm, sub101.. do u mean if i have a w32 virus on my wine that affected my linux so bad, then i should just remove the wine,and linux will be back fine, right?.....

No if you got a virus in Wine that also affected the Linux stuff then the Linux stuff would still be changed regardless of uninstalling Wine.

What I am saying is that in order to run a virus in Wine you would probably have to start the Virus yourself. 

Lets say you receive an attachment from someone via email which claims to be a picture, but is in fact a virus. Opening said picture in Linux would probably do nothing at all. Yet if you opened the picture using Wine it may be able to run. But chances are you would not open it in Wine.

Essentially what I am saying is if you are running something in Wine you would normally know what it is, as you would be running it expressly for that purpose. Therefore it would be difficult for a Virus to start.

---

### Post by cogadh on 2011-04-29
However, it should be noted that if you have Wine configured correctly and securely, the only thing a Windows virus could damage would be Wine's own "fake Windows" directory. In a worst case scenario, that is easily fixed by simply deleting and re-creating the .wine directory. The simplest thing to do is don't run any executables in Wine that are from untrustworthy sources and you should be fine, even if you don't configure Wine securely.

---

### Post by d15tu121314 on 2011-05-01
okay..thanks a lot guys,... sub101 and cogadh, that the most  important thing to do in using wine is to beware of running an  executable files from untrustworthy sources ...like we always did in  wind*ws, :-p ....,i'll try wine..., there is something i wanna try with  it.....

---

