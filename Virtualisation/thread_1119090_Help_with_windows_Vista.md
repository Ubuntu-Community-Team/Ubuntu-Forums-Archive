---
title: "Help with windows Vista"
date: 2009-04-07
forum: Virtualisation
---

### Post by famous3warriors on 2009-04-07
I am using Ubuntu 9.04 beta version and I would like to know how to setup virtual box and windows vista to get the Internet going. Thanks for your help in this matter.:guitar:

---

### Post by famous3warriors on 2009-04-07
OOps really vague sorry about that.  I downloaded the binary virsion of the latest virtual box witch i believe it is 2.1.  I tried to use the internet and it did not work at all.  I have sound and usb working just not the internet.

---

### Post by bobmatino17 on 2009-04-07
Is the Internet Wireless, Dial-Up, DSL, Cable... what type is it?

---

### Post by famous3warriors on 2009-04-07
Internet is DSL

---

### Post by Perryg on 2009-04-07
Should not matter whether it is DSL or Cable.  What does matter is what interface you told VBox to use.  To start with I suggest the host interface because you do not need to do port forwarding or anything fancy.
Then you need to make sure that you are in the same subnet with the host.
Send the ifconfig from ubuntu and the ipconfig /all from windows and lets take a look.

---

### Post by famous3warriors on 2009-04-07
hey guys thanks for you help I really do appreciate everything.  I installed the virtual box guest additions and it worked.  The Internet is working and when all the downloads are done I hope everything else works just as well.:popcorn:

---

