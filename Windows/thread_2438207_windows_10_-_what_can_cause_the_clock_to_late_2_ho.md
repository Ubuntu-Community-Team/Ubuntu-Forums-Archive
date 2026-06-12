---
title: "windows 10 - what can cause the clock to late 2 hours? i've tried some many things"
date: 2020-03-07
forum: Windows
---

### Post by ronjjjg8885 on 2020-03-07
for solving it.

each time i boot into windows 10 (a fresh relaese) i get the clock late for two hours until i hit the sync time button.
**on ubutnu everything is ok with the clock.**
it is just in windows that i can't get the clock to show the right time.
i've tired changing time servers but it is the same.
:confused:

if you have a solution for that it will really be amazing

thank you

---

### Post by jeremy31 on 2020-03-07
I don' remember the exact steps to fix but this is caused by Windows wanting the BIOS clock to be local time and Ubuntu sets it to UTC

---

### Post by Frogs Hair on 2020-03-07
I use the Ubuntu method for my dual boot. When you boot Windows the time will need to be set and should be correct after that.  ```
[COLOR=#000000][FONT=&amp]timedatectl set-local-rtc 1[/FONT][/COLOR]
```
[http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html](http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html)

---

### Post by ronjjjg8885 on 2020-03-08
to just type:```
[COLOR=#000000][FONT=&amp]timedatectl set-local-rtc 1[/FONT][/COLOR]
```

?

---

### Post by CelticWarrior on 2020-03-08
Yes...
Or use an alternative method in Windows as describe here: [https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)

Either way works, we just need both OSes to be using the same "metrics".

---

### Post by ronjjjg8885 on 2020-03-11
thank you so much!
at the moment the command below has solved the problem completely.
```
[COLOR=#000000][FONT=&amp]timedatectl set-local-rtc 1[/FONT][/COLOR]
```

---

