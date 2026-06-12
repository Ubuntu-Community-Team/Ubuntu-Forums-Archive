---
title: "ClamAV avoiding false positives?"
date: 2013-02-15
forum: Security
---

### Post by Nebelhom on 2013-02-15
Hi folks,

I ran ClamAV/Tk recently to make sure that I don't accidentally have a windows virus or some such somewhere (I am dual booting) and ClamAV found some 35(!) Threats.

Afterwards, it turned out they are all files that I know to be no threat at all... Although I must say, I was sweating bullets during the scan and trying to retrace my steps ;) Iknew they were a non-issue mostly, because I created them myself (~23 CV or diploma pdfs and the rest is a bunch of crashtests for the webbrowser)

Is there a way to show them as "safe" for the next run? I wouldn't want to sieve through all these files again, in case there is a real threat next time.

Thanks guys,

Johannes

---

### Post by kc1di on 2013-02-15
Hello Nebelhom,
I haven't used Clamav much lately but will give it a try.
first if you haven't already install clamtk which is a gui front end for clamav

once you have that installed bring it up (should be in the menu under accesories heading.) and and under Preferences you find a tab that call whitelist simply add the files there you want clamav to ignore. that's all. 
Good luck ;)

---

### Post by Nebelhom on 2013-02-15
@kc1di: Ah, awesome! Thanks! I was looking in the entirely wrong places. Sorry for that. I got it now.

---

### Post by kc1di on 2013-02-15
Glad it's working for you :) 
Enjoy.

---

