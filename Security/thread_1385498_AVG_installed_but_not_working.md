---
title: "AVG installed but not working"
date: 2010-01-19
forum: Security
---

### Post by spiritofelric on 2010-01-19
I installed AVG according to the Ubuntu help pages:
[https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg)

However, I learned that the interface for AVG is no longer supported:
"...we here in AVG stopped the support for GUI aimed for AVG 7.5"

I tried the command line scan, yet it doesn't seem to work either:
"
user@user-laptop:~$ gksudo avgscan /media/4DC43A7B3FDEBF/
AVG command line Anti-Virus scanner
Copyright (c) 2009 AVG Technologies CZ

user@user-laptop:~$ gksudo avgscan /media/4DC43A7B3FDEBF/Program Files/
AVG command line Anti-Virus scanner
Copyright (c) 2009 AVG Technologies CZ

user@user-laptop:~$ gksudo avgscan /media/4DC43A7B3FDEBF/Program Files
AVG command line Anti-Virus scanner
Copyright (c) 2009 AVG Technologies CZ
"

Any recommendations on Virus-scanners that are good at scanning NTFS windows installation drives?  Any ideas on how to get AVG command line working?

---

### Post by lisati on 2010-01-19
The latest AVG "free" is command-line, so the "gk" version of sudo isn't really necessary.

You need to start the avg daemon first:
```
sudo avgctl --start
```
You might then need to reboot. You can then update AVG's definitions as follows:
```
sudo avgupdate
```
Then you do your scan:
```
sudo avgscan [options] {path list}
```


edit: I see what you mean: I mounted my Vista partition & tried to scan it explicityly, nothing scanned, but when I scanned "/" it picked up the mounted drive...... Hmmmm, interesting.

edit 2: Tried again on my machine, I suspect I made a typo in the volume name of my Vista partition, the scan seems to be working now.

---

### Post by viper250 on 2010-01-19
why are you installing avg? 
linux is not affected by viruses.
The only linux computer Ive seen affected by a virus was one running a windows program through crossover and then it was only the windows program that was affected

---

### Post by lisati on 2010-01-19
> **viper250 said:**
> why are you installing avg? 
linux is not affected by viruses.
The only linux computer Ive seen affected by a virus was one running a windows program through crossover and then it was only the windows program that was affected

I have it because (a) I run a dual-boot Ubuntu & Windows, it might come in handy for repair work, and (b) my main email provider has a "thou shalt not send malware by email" clause in their terms and conditions...... I rarely use it in Ubuntu because Linux is *less* susceptible to malware.

---

### Post by spiritofelric on 2010-01-20
lisati:
Thank you so much!... you have saved me hours of searching.  Cheers!  I hope to become familiar with Ubuntu at some point.

viper250:
My vista dual boot drive is impacted with allot of Malware... it's easier to scan it from a stable OS.  Though, I hardly use Windows anymore after being on Ubuntu for a couple weeks.

---

