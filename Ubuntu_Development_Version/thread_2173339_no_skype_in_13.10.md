---
title: "no skype in 13.10"
date: 2013-09-09
forum: Ubuntu Development Version
---

### Post by miobrad on 2013-09-09
dear forum,
i can not find skype in the software center.. (also sudo apt-get install skype shows nothing)
thanks for any hints/comments and all the hard work!

---

### Post by howefield on 2013-09-09
You probably need to enable the Partner repository.

Search the dash for Software & Updates, then in the "Other Software" tab check the box beside Canonical Partners, refresh your package lists and it should be there.

---

### Post by miobrad on 2013-09-09
thank you, that was it. now, the skype icon does not show up in the systray/top panel, would you know how to get it there?
many thanks!!!

---

### Post by howefield on 2013-09-09
Hmm, have just installed to check it out, and have the ugliest icon in history on my panel now :P

Do the options show in the messaging menu ? 

You could try installing the pacakge sni-qt

---

### Post by miobrad on 2013-09-09
sni-qt was installed by default when i installed skype through the package manager. hmm.. did you have to restart? (i'm currently downloading something, will try restarting later..) thanks again! 
btw, maybe this is related to the other question i asked in the forum. i installed the cpu/load indicator-multiload, and that to does not show up in the systray - hmmm???

---

### Post by howefield on 2013-09-09
> **miobrad said:**
> sni-qt was installed by default when i installed skype through the package manager. hmm.. did you have to restart? (i'm currently downloading something, will try restarting later..) thanks again! 

No restart nor logout/login required for me.

Are you running 64 bit ? If so, see if there is an sni-qt:i386 package available.

I'm temporarily using 32bit due to an unrelated issue with Crossover Office.

---

### Post by miobrad on 2013-09-09
i'm running 32 bit.. - it was a fresh/clean install (wiping out all the previous data on the disc).
 i used the beta on a usb drive and uploaded to the latest packages during and after the installation.

---

### Post by grahammechanical on 2013-09-09
As regards system load indicator, I have had it showing up in the top panel. I have noticed that things like email clients and IRC clients do not show up in the messaging indicator (envelope icon) until after they are first loaded from the Dash or Launcher. It might take a first loading from the Dash to put System Load Indicator in the top panel. From then on it will be a Startup Application. It is a few months since I installed it on Saucy. So, my memory of the event is dim.

Regards.

---

### Post by miobrad on 2013-09-09
i did start it from the dash and if i can see that it is running:
ps ax  | grep indicator
1622 ?        Sl     0:05 indicator-multiload
it just does not show up,, just as skype does not show up..

---

### Post by howefield on 2013-09-09
Not sure if it is related to this...

[https://bugs.launchpad.net/unity/+bug/974480](https://bugs.launchpad.net/unity/+bug/974480)

but that wouldn't explain why I get an icon and you don't.

---

### Post by cariboo on 2013-10-17
Have you solved the problem, and if so how? Or did you just accidentally mark this thread solved?

---

### Post by vodokotlic666 on 2013-10-17
Who, me? i don't know, maybe accidentally, i didn't pay attention, sorry.. I tried 64bit version and there was no tray icon, now i'm using 32bit version and i have problem with sound..

---

### Post by ventrical on 2013-10-18
Don't forget . MicroSoft owns Skype and most likely if you have Skype on your PC  , they own your PC too and you know how they feel about open source.

---

### Post by cariboo on 2013-10-18
Seeing as this thread has been marked as solved, I'm closing it.

---

