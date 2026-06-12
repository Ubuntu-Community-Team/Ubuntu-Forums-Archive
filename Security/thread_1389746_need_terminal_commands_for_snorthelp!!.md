---
title: "need terminal commands for snort:help!!"
date: 2010-01-24
forum: Security
---

### Post by archer67 on 2010-01-24
I am running karmic koala with a recent install of snort 2.4.8.1(build 38) and i am at a loss for useful commands in solving an internal problem(within the network).All i have  is `"sudo snort -v -i wlan0" on my very short list of useful commands regarding ids.
It is doing little to no good in resolving my problem with a network snoop besides showing that it is running;i need some more weight (knowledge) in order to rectify the problem;can anyone help?

---

### Post by Sarmacid on 2010-01-25
Usually the flags -h or --help will provide more help. If not, you can always read the man pages```
man snort
```

---

### Post by archer67 on 2010-01-25
I need something more in depth;I am not getting the sequence correct and it's very frustrating.As i indicated in my initial post the only command i know is `"sudo snort -v -i wlan0" i try other commands with similar sequences such as `"sudo snort -v -i -a wlan0" and im getting errors w/ a big fat quit. In short:i really don't know what i'm doing.
   
Anything a little more definitive?

---

### Post by bodhi.zazen on 2010-01-25
I do not think snort works with wireless interfaces, so that could be a big part of the problem.

There is also a stick at the top of these forums :

[Intrusion Detection]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by Saghaulor on 2010-01-25
[http://linux.die.net/man/8/snort](http://linux.die.net/man/8/snort)

---

