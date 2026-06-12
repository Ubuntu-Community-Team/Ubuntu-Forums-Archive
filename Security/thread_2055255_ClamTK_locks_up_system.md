---
title: "ClamTK locks up system"
date: 2012-09-08
forum: Security
---

### Post by RogerDavis on 2012-09-08
I installed ClamTK from the Software Center. 

Any attempt to run a scan causes a total system lock up (reset button needed) after 20 ~ 35 seconds of operation.

I can run Clam to scan from the terminal - see below
Known viruses: 1300582
Engine version: 0.97.5
Scanned directories: 33095
Scanned files: 160652
Infected files: 0
Total errors: 20030
Data scanned: 4621.96 MB
Data read: 6120.81 MB (ratio 0.76:1)
Time: 262.829 sec (4 m 22 s)
roger@roger-desktop:~$ 

However, note the 20030 errors!!!

When ClamTK is started, I note that it indicates that the GUI version is not current (now 4.38).  Since I'd rather wait for an update from the system, and thinking that as long as Clam began to run the GUI would not matter so much, I decided to wait for a regular update.

Can someone guide me to my next step(s)?

Thanks!

---

### Post by RogerDavis on 2012-09-28
BUMP !!!

I'd really like to get this working right.  

I can't run a scan from the desktop, it seizes up after about 30 seconds - keys don't work, cursor won't move, bowels won't move... nothing works.  Reset button time.

I understand there are new updates to the engine and GUI, and that they are not critical, waiting on Ubuntu to verify the new versions.

But it's ON the Sofware Center, and it DOESN"T work right at all.

I can run it from the Terminal, but with a bazillion errors - makes me think it's not really accomplishing anything.  See first message.

HELP?!?

---

### Post by Laiquendi on 2012-10-04
Read what the errors are saying. You can make a log file:
```
-l logfile.log
```
there you can read what those errors are saying. You should start there to search for problem.

---

### Post by RogerDavis on 2012-10-05
The command "-l logfile.log" gets me :
roger@roger-desktop:~$ -l logfile.log
-l: command not found
roger@roger-desktop:~$ l logfile.log
ls: cannot access logfile.log: No such file or directory
roger@roger-desktop:~$ logfile
logfile: command not found
roger@roger-desktop:~$

I did get it to complete one scan from the regular interface by clicking the "Home" button.  A repeat try and all other scan selections taking more than a few seconds got me the usual lockup.

Thanks!

---

### Post by Laiquendi on 2012-10-06
"-l" is an option that should be added after the main command. Something like:
```
clamscan -l logfile.log -r (this makes the scan recursive) /places-you-want-to-scan
```
Then paste the content of the errors here, or try to solve them by yourself :)

---

### Post by rookcifer on 2012-10-06
Why do you feel you need ClamAV on your machine?

---

### Post by RogerDavis on 2012-10-09
1) It's now not showing any errors from Terminal use.  It just STOPS from the GUI almost every time.  How do I track errors there?

2) I want to use it as a precaution against viruses and malware in Ubuntu.

---

### Post by Laiquendi on 2012-10-24
Try running the GUI version from the terminal, it should show messages and you should be able to see on which one it stuck.

There are not many viruses on Linux, although it's entirely up to you whether you want to have an antivirus :)
However, there is just no sense of getting paranoid in the case you won't be able to run clamav.

---

### Post by RogerDavis on 2012-10-24
How do I run the GUI version from the Terminal?

Clamscan -r gets me :
Known viruses: 1316729
Engine version: 0.97.6
Scanned directories: 2134
Scanned files: 9520
Infected files: 0
Data scanned: 796.04 MB
Data read: 3664.36 MB (ratio 0.22:1)

But I think this is a Terminal version.

BTW, Ubuntu updates updated the package, but it still has the same problem from the GUI.

---

