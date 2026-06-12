---
title: "Wired connection options"
date: 2012-04-08
forum: Security
---

### Post by abitare on 2012-04-08
I am currently running Ubuntu 11.10 and noticed there is an option to disconnect from a wired connection.  For security reasons I would like to perform this action automatically when my computer sleeps.  Is there any built in functionality which can achieve this task?

---

### Post by raja.genupula on 2012-04-08
```
ifconfig etho down 
sudo /etc/acpi/sleepbtn.sh
```

save that as a script and run it when you wanna put your system from terminal .
first command stands for deactivating the wired connection name :eth0

2nd command stands for put your computer in sleep .

---

### Post by abitare on 2012-04-08
> **raja.genupula said:**
> ```
ifconfig etho down 
sudo /etc/acpi/sleepbtn.sh
```save that as a script and run it when you wanna put your system from terminal .
first command stands for deactivating the wired connection name :eth0

2nd command stands for put your computer in sleep .

 Thanks Raja. This works but I would like to try and take it a step further.  With your help I was able to figure out that sleepbtn.sh is basically the equivalent to hitting a sleep button on a keyboard.  This will then call the sleep.h script which actually puts the computer in sleep mode. Is it possible to add ifconfig eth0 down to the sleep.h script so this will happen every time the computer is put to sleep? Meaning even when I do not do it from the command line.

---

### Post by roelforg on 2012-04-08
> **abitare said:**
> Thanks Raja. This works but I would like to try and take it a step further.  With your help I was able to figure out that sleepbtn.sh is basically the equivalent to hitting a sleep button on a keyboard.  This will then call the sleep.h script which actually puts the computer in sleep mode. Is it possible to add ifconfig eth0 down to the sleep.h script so this will happen every time the computer is put to sleep? Meaning even when I do not do it from the command line.

Dude, Raja's script gets called by acpid right after sleep.h
So it DOES run before your pc goes to bed.

---

### Post by raja.genupula on 2012-04-08
> **abitare said:**
> Thanks Raja. This works but I would like to try and take it a step further.  With your help I was able to figure out that sleepbtn.sh is basically the equivalent to hitting a sleep button on a keyboard.  This will then call the sleep.h script which actually puts the computer in sleep mode. Is it possible to add ifconfig eth0 down to the sleep.h script so this will happen every time the computer is put to sleep? Meaning even when I do not do it from the command line.

According to the thing i have given first your eth0 will down and then computer will sleep.

---

