---
title: "Dead Space 2"
date: 2011-02-20
forum: Wine
---

### Post by KingLex on 2011-02-20
hey i installed Dead Space 2 - thing is when i click on the game icon on my desktop - it dont start - anyone have this game and having trouble playing it ? or i cant play it in Linux

---

### Post by howefield on 2011-02-20
Moved to the *"Wine"* forum.

You are more likely to get appropriate help here.

---

### Post by KingLex on 2011-02-20
> **howefield said:**
> Moved to the *"Wine"* forum.

You are more likely to get appropriate help here.

Thnx i was kind of puzzled where the this thread would go ;)

---

### Post by J697 on 2011-02-20
Try running it through the terminal instead. In terminal navigate to the folder something like this:
```

example@ubuntu:~$ cd .wine
example@ubuntu:~/.wine$ cd dosdevices
example@ubuntu:~/.wine/dosdevices$ cd c:
example@ubuntu:~/.wine/dosdevices/c:$ cd ElectronicArts
example@ubuntu:~/.wine/dosdevices/c:/ElectronicArts$ wine deadspace2.exe

```

Or something like that, mind you the terminal can't cd into directories with a space so you might have to delete the space and then cd into it.

---

### Post by KingLex on 2011-02-21
> **J697 said:**
> Try running it through the terminal instead. In terminal navigate to the folder something like this:
```

example@ubuntu:~$ cd .wine
example@ubuntu:~/.wine$ cd dosdevices
example@ubuntu:~/.wine/dosdevices$ cd c:
example@ubuntu:~/.wine/dosdevices/c:$ cd ElectronicArts
example@ubuntu:~/.wine/dosdevices/c:/ElectronicArts$ wine deadspace2.exe

```

Or something like that, mind you the terminal can't cd into directories with a space so you might have to delete the space and then cd into it.

thnx man ill let u know what i get if i dont work from the looks of what u talkin bout i were thinkin i had to do it thru terminal i just wont for sure how to go about it

---

