---
title: "Spyware/Virus in Ubuntu"
date: 2008-04-14
forum: The Cafe
---

### Post by kenweill on 2008-04-14
I thought viruses/spywares dont infect Linux or Ubuntu in particular...

Read here:
[http://www.download.com/8301-2007_4-9916375-12.html?tag=dlblog-security](http://www.download.com/8301-2007_4-9916375-12.html?tag=dlblog-security)

---

### Post by jmore9 on 2008-04-14
Remomber wine is an interface to run windows / apps.  Therfor it has to appear to be somekind of windows which means it would use some of the software that windows uses and there is the virus attack area.  It did not attack linux it attacked the windows area that was runnig on linux , if i am not mistaken in that.

---

### Post by kenweill on 2008-04-14
> **jmore9 said:**
> Remomber wine is an interface to run windows / apps.  Therfor it has to appear to be somekind of windows which means it would use some of the software that windows uses and there is the virus attack area.  It did not attack linux it attacked the windows area that was runnig on linux , if i am not mistaken in that.

> 
I used Ubuntu's virus scanner and it found one virus in the Wine folder, one virus in the Apt folder, and one in the Root folder.


Its outside wine folder. Worst, its in Root folder.

---

### Post by SunnyRabbiera on 2008-04-14
well its why they say dont run as root.
as long as you dont run root you should be fine a good percent of the time.

---

### Post by swoll1980 on 2008-04-14
this is fud from what this guy is saying his friend was opening an email and the virus opened its self under wine not possible and even if it was wine would have to be ran as root for a program to be placed in the root folder but since wine wasn't ran at all again not possible unless his friend was running the email program under root. Why would he do that? but even if he did that virus couldn't have opened wine on its own. now we are back to the beginning again. if that was a windows virus it wouldn't know anything about a linux file structure so were would it put the file /root/.wine would be the only possibility and thats if he intentionally opened a virus  with his root account sudo wine virus.exe then password, but the virus would still be stuck in that one folder /root/.wine

---

### Post by Eclipse. on 2008-04-14
Running wine as root is the worse thing a user could ever do.

Its the users own fault imo, sudo is there for modifying files outside the home folder, virtual c: in wine is in the home folder which means theres total no need to do it.

---

### Post by original_jamingrit on 2008-04-14
It's always been to the credit of the Wine devs, that even the crappy parts of windows can be ported.

---

### Post by mikewhatever on 2008-04-14
> **kenweill said:**
> I thought viruses/spywares dont infect Linux or Ubuntu in particular...

No operating system is bullet proof and Ubuntu is no exception. We don't know how what Chris describes happened, one possible explanation is that wine was run as root, but anyway, there seems to be no damage done to Ubuntu and its files. I think it's obvious that with growing user base and an influx of Windows users with perverted practices, we'll see more incidents like that.

---

### Post by swoll1980 on 2008-04-14
It never happend.

---

### Post by handy on 2008-04-15
The guy that posted that in the cnet blog fabricated the story for what ever reason.

It is a fairy tale, probably to get attention.

---

### Post by p_quarles on 2008-04-15
I agree: this is fabricated, and meant only to spread FUD. Thread closed. 

Should someone be able to provide concrete evidence (which this article does not do, by a long stretch), this decision could be appealed.

---

