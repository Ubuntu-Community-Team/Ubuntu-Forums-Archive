---
title: "Wine application won't run with ntdll error RtlpWaitForCriticalSection"
date: 2010-12-13
forum: Wine
---

### Post by jwaclawsky on 2010-12-13
I am trying to run a airplane GPS/navigation trainer under Wine. It is called Diamond DA40 G1000 Trainer v8.01. I tried running the program in a terminal and got the following error messages. The first message I got about 5 seconds after typing in the wine command. "wine CDUSINv2" which is a ".exe" file in the current directory

err:ntdll:RtlpWaitForCriticalSection section 0x7bca78e4 "loader.c: loader_section" wait timed out in thread 001b, blocked by 0009, retrying (60 sec)

...then a 1 minute wait and the following message...

err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc34a53

[ATTACH]178345[/ATTACH]

I couldn't find anything about the windows program I am trying to run or from searching at WineHQ:  [http://www.winehq.org](http://www.winehq.org)
I did notice a similar problems doing some Google searching but no resolutions and this one here is a very old example:
[http://www.winehq.org/pipermail/wine...ry/006628.html](http://www.winehq.org/pipermail/wine...ry/006628.html)
since this example is so old and there a a lot of this type of error, I have to think it is a common easily fixed error or some kind of generic message because of a configuration issue. 

Does anyone know what the error messages mean or, better yet, how to correct the problem? Thanks!

---

### Post by dino99 on 2010-12-14
into a terminal:

wine --debug yourapp > log.txt

then watch this log to find errors

---

### Post by jwaclawsky on 2010-12-14
I tried the debug command "wine --debug yourapp > log.txt" and I get an error that "debug.exe" is missing from C:\\windows... (see screen shot). I reproduced the original error and then tried the debug command suggested. I can't find anything labeled "debug" in the "winetricks" packages. Do I have to be in a certain directory to enter the command? ...or am I missing one or more packages that I should install from winetricks? BTW, where will the log file be located once I get this working?  ...any suggestions are appreciated. 
[ATTACH]178433[/ATTACH]

---

### Post by jwaclawsky on 2010-12-20
bump ..any further advice before I remove my wine 1.3.9 and install a prior "stable" version. Thanks

---

