---
title: "Rushing Bender error"
date: 2007-11-14
forum: Ubuntu Gamers Arena
---

### Post by nedkelly on 2007-11-14
Hi

when I try to run this game I get this error 

```
./rushing_bender: symbol lookup error: ./rushing_bender: undefined symbol: XF86VidModeQueryVersion
```

I have look at [http://www.swiix.ch/rb]("http://www.swiix.ch/rb") and [https://help.ubuntu.com/community/RushingBender]("https://help.ubuntu.com/community/RushingBender") and I have search this forum and google it, but I can not find a solution or see what is missing or what the problem is??

---

### Post by fanfantasy7 on 2008-04-15
same problem

```
bertrand@fanfantasy7:~/Desktop/RushingBender$ cat rushing_bender.sh 
#!/bin/sh

cd `dirname $0`
export LD_LIBRARY_PATH=./lib:$LD_LIBRARY_PATH
./rushing_bender

bertrand@fanfantasy7:~/Desktop/RushingBender$ ./rushing_bender.sh
./rushing_bender: symbol lookup error: ./rushing_bender: undefined symbol: XF86VidModeQueryVersion
```

---

### Post by cggaret on 2008-09-20
This game has apparently not worked in Ubuntu for quite a while, but I got it too work under Wine no problem.  Hope this helps anyone else who is curious about this game.

---

