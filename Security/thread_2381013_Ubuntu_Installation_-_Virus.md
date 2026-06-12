---
title: "Ubuntu Installation - Virus"
date: 2017-12-25
forum: Security
---

### Post by Richiegs on 2017-12-25
Everytime I want to install Ubuntu 12.x, 14.x or 17.x on my old Dell Inspiron laptop, it acts strangely as such the first screen will usually not appear and the time will change incorrectly. I think the computer is infected with a virus or malware. I used DBAN to erase my entire harddrive or to update the BIOS. But this problem never seems to go away. Can anyone tell me if this sounds like a problem caused by a virus and how do I proceed to fix it. By the way I have been using Windows to download Ubuntu OS. Thank you very much for your help.

---

### Post by mörgæs on 2017-12-25
Decades ago computer vira destroyed the way programs were working but today one rarely notices them. They are created for being invisible and the purpose is spying. 

Point for using DBAN. 

Please begin with a complete hardware description.

---

### Post by coffeecat on 2017-12-25
No, I doubt this is a virus. But...

> **Richiegs said:**
> ... old Dell Inspiron laptop ... the time will change incorrectly.

That bit, at least, could be a failing CMOS battery. How old is the laptop? What model?

---

### Post by tripp98 on 2017-12-25
The time change is probably using gmt time.  This is normal behavior.

please tell us the make/model of laptop.

---

### Post by Richiegs on 2017-12-26
> **mörgæs said:**
> Decades ago computer vira destroyed the way programs were working but today one rarely notices them. They are created for being invisible and the purpose is spying. 

Point for using DBAN. 

Please begin with a complete hardware description.

My Dell Inspiron 1420 has 1.5GHz Core 2 Duo processor, 2MB and 120GB in hard drive currently running both Windows 10 English language only version and Vista.

---

### Post by Richiegs on 2017-12-26
> **coffeecat said:**
> No, I doubt this is a virus. But...



That bit, at least, could be a failing CMOS battery. How old is the laptop? What model? Definitely not CMOS battery because I already replaced with a new CMOS battery. 10 Years laptop.

---

### Post by Richiegs on 2017-12-26
> **tripp98 said:**
> The time change is probably using gmt time.  This is normal behavior.

please tell us the make/model of laptop.


If the time is incorrect, I have to go into BIOS setup to change it back to the correct time.

---

### Post by mörgæs on 2017-12-26
Are you able to run a live boot using 16.04.3?

---

### Post by Richiegs on 2017-12-26
> **mörgæs said:**
> Are you able to run a live boot using 16.04.3?

Is a live boot of 16.04.3 same as installation disc of Ubuntu 16.04.3? If so, this is what will happen as soon as I insert the Ubuntu disc into computer. Sometimes the first screen of Ubuntu will appear without the "TRY UBUNTU and INSTALL UBUNTU" or the computer screen will become blank. If I hit space bar, the first screen will appear on the monitor. It sounds really strange.

---

### Post by TheFu on 2017-12-29
Time - Unix systems use GMT internally and use the TZ variable to choose how to display the output at request time.  Windows has used local time historically.  I've been out of the Windows world about 10 yrs, so that may have changed.  What does this mean?  If the time problem happens only after booting from 1 OS into the other and by a difference in GMT-to-local amount, then that is likely the issue.

CMOS batteries have different lifetimes.  Sometimes they last multiple decades and other times, they barely last a year.  For example, my mind remembers changing the car battery last year, but when I look at my payment records, it turns out that was 6 yrs ago.  Time flies, the older we get. ;)

Virus?  Probably not.  More likely some marginal hardware problems that Linux notices but Windows ignores.  Windows seems to ignore about 80% of all HW issues, until it is so bad that the HW can't be used.  Corrupting data all the along the way.
There are a few Linux viruses, but usually if anyone gets a virus, then they were using some Windows program with the WINE Linux subsystem.  It is good enough for some windows viruses to infect Linux.  A "virus" is a specific type of malware. There are others.  On linux systems, a "virus" isn't very likely, but other sorts of malware and attacks are very common if you run any services that are available from the internet.  Be very careful running a web server or any web-apps, for example.  If you run a normal Linux desktop, stay patched and don't run any services available from the internet, it is very difficult to get any malware without clicking something bad - usually on a javascript-running website with Adobe flash media or hacked PDF files. Most of those attacks are not targeted at Linux, so they don't do much, but that doesn't mean someone couldn't target Linux.  Nothing replaces a smart end-user, not doing foolish things, when it comes to security.

Yes, a live boot 16.04.3 is the same (close enough) as a 16.04.3 installation.  The reason to run this off the flash drive or DVD/optical drive is to determine if there is a disk subsystem issue or if it is a corrupted config file somewhere.  That can be a bad cable, failing SATA controller or just data corruption due to disk sectors failing.  Creating a new userid and logging in with that is a way to see if the issue is across the entire system or just for your normal userid.

Have you checked the system log files for issues?  Always start there when there are issues.  Look for warnings and errors in all of them.

---

### Post by HermanAB on 2017-12-31
The time difference is likely due to Windows using local time and Linux using UTC with time zones.

A virus on Linux?  I have only ever seen one about 20 years ago and it didn't work...

---

