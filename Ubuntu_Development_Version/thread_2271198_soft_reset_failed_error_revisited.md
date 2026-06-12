---
title: "soft reset failed error revisited"
date: 2015-03-28
forum: Ubuntu Development Version
---

### Post by zika on 2015-03-28
Once upon a time there was a thread: [http://ubuntuforums.org/showthread.php?t=2086325](http://ubuntuforums.org/showthread.php?t=2086325)
In the meantime I was using that &#8222;remedy&#8220; learned, among others, from [https://paulphilippov.com/articles/how-to-fix-slow-boot-with-ata-errors](https://paulphilippov.com/articles/how-to-fix-slow-boot-with-ata-errors)
Each and every kernel up to yesterday needed that and every udev upgrade was followed with that &#8222;remedy&#8220;.
But: [http://77.244.44.75/debian/dists/testing/main/binary-amd64/linux-headers-3.19.0-pf3_0_amd64.deb](http://77.244.44.75/debian/dists/testing/main/binary-amd64/linux-headers-3.19.0-pf3_0_amd64.deb) and [http://77.244.44.75/debian/dists/testing/main/binary-amd64/linux-image-3.19.0-pf3_0_amd64.deb](http://77.244.44.75/debian/dists/testing/main/binary-amd64/linux-image-3.19.0-pf3_0_amd64.deb) do not...
As far as I remember, 3.19.0-pf2 was not with that property... So, that could lead to resolving/dissecting that longstanding &#8222;bug&#8220;... ;)
[COLOR=#45387D][FONT=Arial]Update&#8321;: I spoke too soon, it seems: it seems that newest Liquorix also does not have that bug. I will investigate further.
Update&#8322;: It seems that this bug is also guilty for &#8222;[/FONT][/COLOR]Bootup is not yet finished. Please try again later.&#8220; as answer to systemd-analyze... ;)

---

### Post by dino99 on 2015-03-28
i suppose that devs have known about it, and then disagreed about the benefits/troubles

---

### Post by zika on 2015-03-28
> **9d9 said:**
> i suppose that devs have known about it, and then disagreed about the benefits/troublesI'm bad in making suppositions... ;)
Conclusions, sometimes...
Back to topic: I've reported this simply because I found that it works and has no side-effects obvious to me.

---

### Post by ventrical on 2015-03-28
> **zika said:**
> [COLOR=#45387D][FONT=Arial]
Update&#8322;: It seems that this bug is also guilty for „[/FONT][/COLOR]Bootup is not yet finished. Please try again later.“ as answer to systemd-analyze... ;)

I beg to differ. I cannot prove exactly why but it appears that this could be a flavour dependent and machine dependent random anomoly, basically meaning that on some machines it will come up and not on others. Also .. xubuntu seems to not produce this error on same machine as when tried with ubuntu-unity flavour. I know for sure it comes up always on Ubuntu-Mate.

Regards..

---

### Post by zika on 2015-03-28
> **ventrical said:**
> I beg to differ. I cannot prove exactly why but it appears that this could be a flavor dependent and machine dependent random anomaly, basically meaning that on some machines it will come up and not on others. Also .. xubuntu seems to not produce this error on same machine as when tried with ubuntu-unity flavor. I know for sure it comes up always on Ubuntu-Mate.
Regards..I did not write/mean that this was the one and only reason for that error message to appear. I did write/mean that this might be one of reasons why somebody could see that error message. Also, I do not consider it random since I can reproduce it in a very deterministic way.
Since I'm not multi flavor guy I can only write about Ubuntu... ;)

---

### Post by ventrical on 2015-03-28
> **zika said:**
> I did not write/mean that this was the one and only reason for that error message to appear. I did write/mean that this might be one of reasons why somebody could see that error message.

Understood. Thanks :)


> 
 Also, I do not consider it random since I can reproduce it in a very deterministic way.


Well , then all I can say is that this is becoming very interesting ;) I still do think that  some of the reported results are false positives. (I am not saying I can prove that with code.. etc..) It's just an observation in real time. It may be a bug, it may not. 

Regards..

---

### Post by Elfy on 2015-03-29
Let's keep it ontopic for a while longer, thanks.

---

