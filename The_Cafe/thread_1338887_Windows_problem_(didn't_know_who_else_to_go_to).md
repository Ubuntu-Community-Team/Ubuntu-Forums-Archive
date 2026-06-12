---
title: "Windows problem (didn't know who else to go to)"
date: 2009-11-26
forum: The Cafe
---

### Post by supermelon928 on 2009-11-26
So, 

My mother clicked on one of those fake virus-scan pop-ups that gives you a virus. Now McAfee won't open and Task Manager won't open, and she's being told she's low on virtual memory, and I figure it's because the virus is running processes that are causing these problems.

I'm thinking if I can get cmd.exe to bring up a list of active processes, I can google the processes and find out which ones are malignant. 

Does anyone know if I'm wrong about the processes thing, or if/how I can get cmd.exe to bring up a list, or if there's a better forum on this site for me to be asking this on?

Thanks a lot.

---

### Post by aktiwers on 2009-11-26
Is the virus called Security Tools or something like that?
Then try using Spyware doctor
[http://www.pctools.com/spyware-doctor/](http://www.pctools.com/spyware-doctor/)

It removes lots of those fake antivirus spyware apps. I just did this recently for
a teacher at my work.

---

### Post by Dark Aspect on 2009-11-26
> **supermelon928 said:**
> So, 

My mother clicked on one of those fake virus-scan pop-ups that gives you a virus. Now McAfee won't open and Task Manager won't open, and she's being told she's low on virtual memory, and I figure it's because the virus is running processes that are causing these problems.

I'm thinking if I can get cmd.exe to bring up a list of active processes, I can google the processes and find out which ones are malignant. 

Does anyone know if I'm wrong about the processes thing, or if/how I can get cmd.exe to bring up a list, or if there's a better forum on this site for me to be asking this on?

Thanks a lot.

How much data does she have? I would just do a clean install, also try to take advantage of the situation and talk her into using Linux.

---

### Post by Grifulkin on 2009-11-26
Hijack This! is a very nice tool to get rid of spyware.

---

### Post by nelfin on 2009-11-26
Also, in cmd.exe tasklist and taskkill are the two programs you're thinking of for viewing and killing processes respectively.

Try:
```
tasklist
taskkill /pid <number next to rogue process>
```

---

### Post by Tipped OuT on 2009-11-26
> **aktiwers said:**
> Is the virus called Security Tools or something like that?
Then try using Spyware doctor
[http://www.pctools.com/spyware-doctor/](http://www.pctools.com/spyware-doctor/)

It removes lots of those fake antivirus spyware apps. I just did this recently for
a teacher at my work.

Oh yes. Spyware Doctor. I one hundred percent recommend this Anti Virus program. ALWAYS works. Pretty much the best, arguably.

---

### Post by lykwydchykyn on 2009-11-26
I've had to remove about 10 varieties of these over the past year at work and for friends; most of them are pretty easy to remove once you identify the executable.  Some of them are pretty sophisticated nowadays, though, especially the "security tools" on which blocks you from running a number of different programs you might use to fix it (including cmd.exe).

If you can get more information about it, post here or google it on another machine and you can probably find removal instructions.

---

### Post by cariboo on 2009-11-27
I use [Malwarebytes]("http:///www.malwarebytes.org/"). I have it on a usb thumb drive for problems like this. Start in Safe Mode then run malwarebytes, it will remove the scareware.

---

### Post by mikewhatever on 2009-11-27
Didn't know where else to go? Really? :)
I think I can help. ;) [--->click here<---]("http://lmgtfy.com/?q=windows+security+forum")

---

### Post by guitar player on 2009-11-27
I also second malwerbytes if you can get it on the computer. Also once you remove the virus ditch McAfee and install the free avast or avira. I have never had good luck with McAfee products.

---

### Post by anishd on 2009-11-27
(1) download [spybot search]("http://www.safer-networking.org/index2.html") and destroy, run it.

(2) you can also try to install [SDfix]("http://www.myantispyware.com/2007/11/09/sdfix-free-trojan-remover-tool/") and run it in safemode.

---

### Post by SunnyRabbiera on 2009-11-27
> **Dark Aspect said:**
> How much data does she have? I would just do a clean install, also try to take advantage of the situation and talk her into using Linux.

Just do it slowly, like start off with a dual boot.

---

### Post by bcn17 on 2009-11-27
> **Dark Aspect said:**
> How much data does she have? I would just do a clean install, also try to take advantage of the situation and talk her into using Linux.

Ya, without a clean install you can't be sure it's virus free.

---

### Post by wilee-nilee on 2009-11-27
> **cariboo907 said:**
> I use [Malwarebytes]("http:///www.malwarebytes.org/"). I have it on a usb thumb drive for problems like this. Start in Safe Mode then run malwarebytes, it will remove the scareware.
 
+1 and this one both are free just update when scanning.
[http://www.superantispyware.com/download.html](http://www.superantispyware.com/download.html)

---

### Post by LookTJ on 2009-11-27
> **cariboo907 said:**
> I use [Malwarebytes]("http:///www.malwarebytes.org/"). I have it on a usb thumb drive for problems like this. Start in Safe Mode then run malwarebytes, it will remove the scareware.
+1 I use this all the time, and it rarely fails.

---

### Post by Kazade on 2009-11-27
[Nixie Pixel to the rescue]("http://www.youtube.com/watch?v=9h3q5ss40oY&feature=player_embedded")

---

