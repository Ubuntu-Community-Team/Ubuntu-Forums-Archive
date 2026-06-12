---
title: "cannot run software"
date: 2009-05-09
forum: Wine
---

### Post by num on 2009-05-09
hello,

i am trying to run CryptLoad on Ubuntu 9.04 and I have installed Wine and Winetricks but I cannot get it running. Can anyone please help?

Cryptload's website is:

[http://cryptload.info/](http://cryptload.info/)

---

### Post by asdfoo on 2009-05-10
> **num said:**
> hello,

i am trying to run CryptLoad on Ubuntu 9.04 and I have installed Wine and Winetricks but I cannot get it running. Can anyone please help?

Cryptload's website is:

[http://cryptload.info/](http://cryptload.info/)

what did you install with winetricks?  what happens when you run the application?

---

### Post by num on 2009-05-10
it requires .net framework 2.0 but i installed it and it gives the error stating it needs it still.

---

### Post by asdfoo on 2009-05-10
> **num said:**
> it requires .net framework 2.0 but i installed it and it gives the error stating it needs it still.

just to confirm, you installed the .net framework 2.0 with winetricks not not by hand or by the programs installer?

Because the latter two can stop .net from working, in which case you need to start from scratch by moving or removing your existing wine prefix.

---

### Post by num on 2009-05-11
> **asdfoo said:**
> just to confirm, you installed the .net framework 2.0 with winetricks not not by hand or by the programs installer?

Because the latter two can stop .net from working, in which case you need to start from scratch by moving or removing your existing wine prefix.

i installed .net framework by winetricks

---

### Post by asdfoo on 2009-05-11
can you post the output of when you run the app?

---

### Post by num on 2009-05-12
what you mean by output?

---

### Post by hikaricore on 2009-05-12
What happens when you run the program from a terminal like you're supposed to when running any new software via WINE.

---

### Post by num on 2009-05-12
it just gives me two messages:

[img]http://i41.tinypic.com/2s8oh95.png[/img]

[img]http://i44.tinypic.com/2uswqd3.png[/img]

---

### Post by num on 2009-05-13
can anyone please help me?

---

### Post by asdfoo on 2009-05-14
> **num said:**
> can anyone please help me?


If it doesn't work it doesn't work.  .NET has a lot of bugs under Wine which have not been fixed yet.

---

### Post by qwertymn on 2009-05-14
try installing in a complete new, fresh .wine:

WINEPREFIX=~/garbage winetricks dotnet20
WINEPREFIX=~/garbage wine Cryptload.exe

Does it still give the error that .net can not be found?

---

### Post by num on 2009-05-15
now i am getting the exception error. not sure what to do?

---

### Post by hikaricore on 2009-05-16
Check the appdb to see if anyone else has had luck and try out any suggestions there.

Also would it be so difficult to post some terminal output?

---

