---
title: "Can't remotely log out *tty sessions?"
date: 2011-07-10
forum: Server Platforms
---

### Post by Strid on 2011-07-10
I had to manually fix a broken disk on my 10.04.2 LTS server, and logged in via the tty, and launched several different tty sessions (Alt+F1, Alt+F2, etc). However, stupid me forgot to log out of the sessions, so although the server right now does not have a monitor or keyboard attached, anyone could in principle attach a such and use my account...

I tried to do the following, but to no avail (tried both pkill and skill):

Any other trick I could try, other than a God-awful sudo reboot now?

```
testuser@lando:~$ sudo pkill -KILL -u andersx
testuser@lando:~$ finger
Login     Name                 Tty      Idle  Login Time   Office     Office Phone
andersx   Anders Christensen  *tty2      60d  May 11 09:43
andersx   Anders Christensen  *tty3      60d  May 11 09:43
andersx   Anders Christensen  *tty1      60d  May 11 09:42
testuser  Test Testensen       pts/1          Jul 10 23:06 (soprano)
testuser@lando:~$ sudo skill -9 -u andersx
testuser@lando:~$ finger
Login     Name                 Tty      Idle  Login Time   Office     Office Phone
andersx   Anders Christensen  *tty2      60d  May 11 09:43
andersx   Anders Christensen  *tty3      60d  May 11 09:43
andersx   Anders Christensen  *tty1      60d  May 11 09:42
testuser  Test Testensen       pts/1          Jul 10 23:06 (soprano)

```

Cheers!

---

### Post by karlson on 2011-07-10
Easiest way:

```
sudo kill -9 `ps -t ttyX | awk -F {'print $1'}`
```

The getty will be restarted and all other processes running on the terminal will be killed.

---

### Post by Strid on 2011-07-10
Hi Karlsson,

Thanks! I am still listed as having three idle ttp logged in three idle terminals after trying that. also tried various combinations of pkill and skill, as well as different signals.


```

testuser@lando:~$ finger
Login     Name                 Tty      Idle  Login Time   Office     Office Phone
andersx   Anders Christensen  *tty2      60d  May 11 09:43
andersx   Anders Christensen  *tty3      60d  May 11 09:43
andersx   Anders Christensen  *tty1      60d  May 11 09:42
testuser  Test Testensen       pts/0          Jul 11 01:24 (soprano)
testuser@lando:~$ sudo kill -9 `ps -t tty1 | awk -F: {'print $1'}`
Killed
testuser@lando:~$ finger
Login     Name                 Tty      Idle  Login Time   Office     Office Phone
andersx   Anders Christensen  *tty2      60d  May 11 09:43
andersx   Anders Christensen  *tty3      60d  May 11 09:43
andersx   Anders Christensen  *tty1      60d  May 11 09:42
testuser  Test Testensen       pts/0          Jul 11 01:24 (soprano)
testuser@lando:~$

```

---

### Post by karlson on 2011-07-10
> **Strid said:**
> 
```

testuser@lando:~$ sudo kill -9 `ps -t tty1 | awk -F: {'print $1'}`

```

Why would you tell awk that fields are delimited by ':'?  You should drop that option.

Also just run the ```
 ps -t tty1 | awk {'print $1'} 
```

The output should produce a single column of process IDs.  The ps you are running won't do that.

Try it first before supplying to kill.  

You also might just try to runn kill manually on one of the processes running on ttyX

---

### Post by Strid on 2011-07-10
Thanks, I now know awk! Very useful indeed. Didn't catch the delimiter part before. However, it still did not seem to solve my problem. Still didn't manage to log out the 60d idle sessions.

I extended by an inverted grep to avoid the line beginning with PID. But after killing the PID, it seems like theres just a new one with a different number. If I go to "top -u andersx" there are seemingly no running processes with that owner. Very strange indeed!

```
testuser@lando:~$ ps -t tty1 | awk {'print $1'}
PID
11667
testuser@lando:~$ ps -t tty1 | awk {'print $1'} | grep -v PID
11667
testuser@lando:~$ sudo kill -9 `ps -t tty1 | awk {'print $1'} | grep -v PID`
testuser@lando:~$ finger
Login     Name                 Tty      Idle  Login Time   Office     Office Phone
andersx   Anders Christensen  *tty2      60d  May 11 09:43
andersx   Anders Christensen  *tty3      60d  May 11 09:43
andersx   Anders Christensen  *tty1      60d  May 11 09:42
testuser  Test Testensen       pts/0          Jul 11 02:04 (192.168.1.42)
testuser@lando:~$ ps -t tty1
  PID TTY          TIME CMD
11688 tty1     00:00:00 getty
testuser@lando:~$ 

```

Cheers!

---

