---
title: "How to run an application in the background"
date: 2005-11-12
forum: Server Platforms
---

### Post by vinjvinj on 2005-11-12
I work on my ubuntu server nfs through  a ssh shell on my laptop. Sometimes I have long running cp commands that I would like to run when I go to work. How can I run the commands and keep the shell active so that when I logon again I'll come back to the same process

---

### Post by adwait on 2005-11-13
Adding an ampersand at the end of a command makes it run in the background. 
eg:
```
cp *.mp3 /mnt/c/songs&
```

---

### Post by stuporglue on 2005-11-13
Using an & will make let the process quit when you log out. You may want to look into "screen". Screen lets you login, start screen, run a process, detach screen, log out and resume what you were doing.

---

