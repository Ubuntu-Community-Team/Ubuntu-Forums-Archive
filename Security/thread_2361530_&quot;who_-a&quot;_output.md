---
title: "&quot;who -a&quot; output"
date: 2017-05-17
forum: Security
---

### Post by juan53 on 2017-05-17
Hi ladies and gentlement

I write this post because I've got a tille paranoic after installing "dash to panel" a gnome extention. I've been checking ports and so forth. I have also cheched open sessions and bash sessions. In one of the checks I have found this:

user@device:~$ who -a
          system start 2017-05-17  20:50
          'run-level' 5 2017-05-17 20:50
LOGIN  tty1   2017-05-17 20:50   1463 id=tty1
user   +tty2   2017-05-17 20:50   1581 (:1)

So, I understand that there are two connectons directly made to the computer. At levels 1 and 2. I am not sure of the meaning fo the levels. I don't know the "+" character there, and I don't know "(:1)" as well.
Could you please tell me what are the meanings of such things?

Thanks a lot.

---

### Post by Xian on 2017-05-17
The "(:1)" tells which display you are using.

The "+" means the user is accepting messages. 
Could also appear as a "-" (no) or "?" (can't be stated)

Edit: Sorry .... forgot you mentioned runlevels.

Good explanation: [https://www.liquidweb.com/kb/linux-runlevels-explained/](https://www.liquidweb.com/kb/linux-runlevels-explained/)

---

### Post by juan53 on 2017-05-17
What does accepting messages means? Thanks for your answer Xian.
I've checked the display number by issuing in the terminal: w.
My display is :1, but in many distributions and flavours, the default number is :0. Why does it changes?

---

### Post by Xian on 2017-05-17
The mesg command provides control over whether/not other users have write access to your terminal. 

$ mesg y  [allows write access]
$ mesg n  [disallows access]

$ mesg     [displays current write status]


For an basic explanation of write command access: [https://www.computerhope.com/unix/write.htm](https://www.computerhope.com/unix/write.htm)

---

### Post by juan53 on 2017-05-17
This is a good advise. Thanks a lot, but i fear that it can't give me clue about if my computer was compromised. Anyway, I have reached the author of Dash to panel" so I guess the code is clean.

---

