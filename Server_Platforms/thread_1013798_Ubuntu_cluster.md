---
title: "Ubuntu cluster"
date: 2008-12-17
forum: Server Platforms
---

### Post by mydesires100 on 2008-12-17
I am new to linux and want to create clusters to make my own application to perform better.
I have one program written in java using sockets.I want that program to run on cluster so that it can server many requests at a time.
Anyone please guide me through.:confused:

Thanks,
Pramod

---

### Post by keithclark on 2008-12-17
Here is a good place to start learning:

[http://www.clustermonkey.net/](http://www.clustermonkey.net/)

Keith

---

### Post by mydesires100 on 2008-12-18
Thanks for the reply,
It is a good one but i wanted something whare we can write codes in java
It is C based.
Thanks,
Pramod

---

### Post by Ferret-Simpson on 2008-12-20
C and Java are reasonably closely related languages, so you shouldn't have too much difficulty porting your code. The big problem is that Java is an INTERPRETED language - making it run a massive factor slower than native C, CPP, Obj-C, ASM, and other compiled languages.

---

