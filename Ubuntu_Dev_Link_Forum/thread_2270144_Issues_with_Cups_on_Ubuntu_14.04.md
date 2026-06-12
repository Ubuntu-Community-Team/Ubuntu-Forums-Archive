---
title: "Issues with Cups on Ubuntu 14.04"
date: 2015-03-20
forum: Ubuntu Dev Link Forum
---

### Post by helio.cola on 2015-03-20
Afternoon folks,

I am having a few issues compiling cups library on my ubuntu.
The latest version I was able to compile and run without major problems was 1.7.5.

It does compile and run but the command lpstat -p (and also -a) is logging the following errors:
desk@desk-home:~$ lpstat -p
**lpstat: symbol lookup error: lpstat: undefined symbol: _cupsStrDate**

The command -t is interesting because it prints a few things but it fails near to the end:
desk@desk-home:~$ lpstat -t
scheduler is running
system default destination: Canon_MG3100_series
device for Canon_MG3100_series: usb://Canon/MG3100%20series
**lpstat: symbol lookup error: lpstat: undefined symbol: _cupsStrDate**


I've trying to find out what is wrong for a few days already without any progress.

Does anybody seen something similar before?

Follow a few more configs:
desk@desk-home:~$ cups-config --version
1.7.5
desk@desk-home:~$ cups-config --libs
-lcups -lssl -lcrypto -lz -lpthread -lm -lcrypt -lz
desk@desk-home:~$ cups-config --serverbin
/usr/lib/cups
desk@desk-home:~$ cups-config --serverroot
/etc/cups
desk@desk-home:~$ cups-config --build
cups-1.7.5
desk@desk-home:~$ cups-config --api-version
1.6

**UPDATE:** *make test* on my installation folder indicates that *lpstat -t* pass the test successfully and print the date at the end correctly.
I am starting to suspect that I may have more than one cups library installed on my system and they might be fighting each other.


Thanks,
Helio

---

### Post by SeijiSensei on 2015-03-20
Is there some reason why the version of CUPS in the repositories doesn't work for you?  Compiling your own software is usually unnecessary unless there is some new feature of a program that you need.  You'll get much better support here and elsewhere if you use the repository versions rather than rolling your own.

---

### Post by gordintoronto on 2015-03-21
+1!

---

### Post by rmisk on 2015-06-02
I am using  cups-config version 2.0.2 from the repository and I am having the exactly the same problem.  Of course I have absolutely no idea about what is the problem.  Printers with Ubuntu have always been  an enigma with me it always takes hours to get something printed.  Then a few days later I do exactly the same process but then Ubuntu wants something else!!!  Thank goodness I have access to a windows OS from which I can always print reliably!  What's up with that??

---

