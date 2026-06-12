---
title: "Java"
date: 2009-11-05
forum: Wine
---

### Post by Bliksimpie on 2009-11-05
hey. 

Ubuntu 9.10 is awesome. I like the new look, but I have a problem. I have a .exe program that is written in Java. When I run it, it gives me the following error: "Could not create the Java virtual machine." This program worked perfectly on my previous Ubuntu. Could someone please help me in solving this problem.

Thanx!

---

### Post by lykeion on 2009-11-05
> **Bliksimpie said:**
> I have a .exe program that is written in Java.

A program with .exe file extension sounds more like an Windows executable than a Java program. 
Do you use WINE when you run this file? If so maybe you need to install the windows version of java with wine.

---

### Post by doas777 on 2009-11-05
assuming you meant .jar (not .exe; java does not do binary executables) post the output of these commands:"
```
java -version
javac -version
```

also please post the exact command you are running.

---

