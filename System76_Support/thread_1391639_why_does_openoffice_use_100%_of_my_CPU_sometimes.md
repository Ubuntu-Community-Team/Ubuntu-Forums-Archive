---
title: "why does openoffice use 100% of my CPU sometimes?"
date: 2010-01-27
forum: System76 Support
---

### Post by izquierdista on 2010-01-27
Hello,
I have a DARU2 ultra 2.5GB RAM, Intel COre DUO 1.80GHZ processer with  Ubuntu karmic koala as my current distro. 

I have noticed an annoying thing that has been happening more frequently and that is when Im using Openoffice sometimes the program freezes and becomes unresponsive even if I wait for a couple of minutes the problem does not resolve, I went ahead and checked my system monitor and noticed that it was using 100% of the CPU for a simple word processing document!!!!

I dont think it has anything to do with my laptop but am not sure, 

has anyone experienced this problem, is it a bug in openoffice?? 

I would appreciate the help.

---

### Post by thomasaaron on 2010-01-27
There are a number of bugs out there in which Open Office causes freezes...
[http://www.google.com/#hl=en&source=hp&q=ubuntu+9.10+open+office+freezes&aq=f&aql=&aqi=&oq=&fp=64df356c6a3f8304](http://www.google.com/#hl=en&source=hp&q=ubuntu+9.10+open+office+freezes&aq=f&aql=&aqi=&oq=&fp=64df356c6a3f8304)

Exactly what are you doing when you get the freeze? Converting something to a pdf? Just merrily typing along?

Do you have desktop effects enabled? Does the freeze occur if you don't have effects enabled?

---

### Post by izquierdista on 2010-01-27
well all I was doing was just editing a word processor document and typing, nothing really fancy or image heavy. 


I hope this helps,

---

### Post by thomasaaron on 2010-01-28
Do you have desktop effects enabled? Does the freeze occur if you don't have effects enabled?

System > Prefs > Appearance > Visual Effects > None

---

### Post by Hagar Delest on 2010-01-30
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try to install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

