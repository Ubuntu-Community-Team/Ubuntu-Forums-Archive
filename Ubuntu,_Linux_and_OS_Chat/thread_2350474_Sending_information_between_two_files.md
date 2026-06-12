---
title: "Sending information between two files"
date: 2017-01-24
forum: Ubuntu, Linux and OS Chat
---

### Post by superspy1615 on 2017-01-24
Is there any simple way to send any type of information between two files? Nothing specific, but what I want to be able to do is if i know the location of file one and run some command against it, this command will show me what other file this file is in communication with. I am still looking into a program that does that but i need to be able to do this with two files to test it first.
If at all possible, the information being sent would be constant but use minimal ram on the computer

---

### Post by Geoffrey_Arndt on 2017-01-24
Please clarify . . . .

---

### Post by ian-weisser on 2017-01-24
There are many ways to send data between two running processes, threads, or applications.
Some of the ways include pipes, named pipes, temp files, Unix sockets, TCP sockets, and dBus.

Some of those methods can be eavesdropped. Some cannot.
For example, it takes less than 0.05 seconds for an application to open a tempfile, write, and close...on a slow HDD. That's much faster than a blink, easy for a human to miss. The system does not keep a lengthy record of every file touched by each application.

---

