---
title: "Wine won't run"
date: 2009-01-15
forum: Wine
---

### Post by ubudog on 2009-01-15
I have wine and for some reason it won't run any windows program.  If anyone knows whats wrong then please tell me.






Thanks

---

### Post by stefangr1 on 2009-01-15
It is really difficult to help you with this little information. Can you maybe try to start a windows program from the command line, and then post the error messages you get?

---

### Post by ubudog on 2009-01-15
Yeah sure hang on ......

---

### Post by ubudog on 2009-01-15
Here is the error message:wine: Unhandled page fault on write access to 0x00459000 at address 0x7bc45faf (thread 001b), starting debugger...
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart.

---

### Post by hikaricore on 2009-01-16
Output of the following please:

```
wine --version
```

---

### Post by ubudog on 2009-01-16
Here it is:wine-1.1.12

---

### Post by hikaricore on 2009-01-16
And what version of ubuntu are you using?

Have you read my thread that is **STICKIED** at the top of this very forum?
[**>>>> Wine 1.1.12 Crash - Read Me! <<<<<**]("http://ubuntuforums.org/showthread.php?t=1032317")

I'm guessing that you are running 1.1.12 on Intrepid as I've warned people against.

---

### Post by ubudog on 2009-01-16
I am using hardy heron (8.04)

---

### Post by hikaricore on 2009-01-16
Try version 1.1.10 and tell me if this fixes it:

[http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.10~winehq0~ubuntu~8.04-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.10~winehq0~ubuntu~8.04-0ubuntu1_i386.deb)

I think something is really really wrong with all 1.1.12 packages.

---

### Post by ubudog on 2009-01-16
OK hang on .......

---

### Post by hikaricore on 2009-01-16
If you're unsure which programs will actually run under WINE btw please search here:

[http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by ubudog on 2009-01-16
Yessssss!!!  Thanks soooo much!!!!!!!!  It works!

---

### Post by hikaricore on 2009-01-16
Now don't upgrade WINE until 1.1.13 comes out!

^_^

Best of luck.

---

### Post by ubudog on 2009-01-16
OK Thanks sooo much!!

---

### Post by ubudog on 2009-01-16
All right.  I have the older version of wine installed now and I can run basic programs but I can't run programs with 3D graphics.  If anyone can help please help me.







Thanks

---

