---
title: "convincing help"
date: 2010-08-30
forum: The Cafe
---

### Post by sandyd on 2010-08-30
Im currently having a difficult issue with a friend of mine who wanted to try ubuntu.

He has a few week old laptop that has issues with IE crashing all the time, so I said he could try ubuntu.

I resized the disks using the windows partiton manager majiggy and installed it.

then, the terrible stuff began.

I began to get suspicious when the installer crashed after saying there was a problem installing GRUB.

I booted into the livecd mode, and ran cfdisk and fdisk -l

Both turned up seek errors.

How can I convince him that there are issues with his HD?

---

### Post by NightwishFan on 2010-08-30
From the live session check the SMART stats from the disk utility.

---

### Post by sandyd on 2010-08-30
> **NightwishFan said:**
> From the live session check the SMART stats from the disk utility.
tried.
It doesn't show a SMART status.

I can easily turn his computer back to normal using bootsect from the windows DVD, but im not doing it for obvious reasons. Hes just going to end up asking me to go to his university (hes going to university in sepetember) and fix his HD, since the company he bought his computer from is in the states.

---

### Post by NightwishFan on 2010-08-30
I heard of a program called badblocks, though I never used it myself. It is installed by default in lucid, its a CLI program. Check out the man page with:
```
man badblocks
```

This may help as well:
[https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia)

---

### Post by sandyd on 2010-08-30
> **NightwishFan said:**
> I heard of a program called badblocks, though I never used it myself. It is installed by default in lucid, its a CLI program. Check out the man page with:
```
man badblocks
```

This may help as well:
[https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia)
still having a seek error with badblocks (invalid argument during seek)

---

### Post by NightwishFan on 2010-08-30
I am not sure about that, however be aware of this from the man page. I apologize for not posting it sooner.
```
WARNING
       Never use the -w option on a device containing an existing file system.
       This option erases data!  If you want to do write-mode  testing  on  an
       existing  file system, use the -n option instead.  It is slower, but it
       will preserve your data.

       The -e option will cause badblocks to output a possibly incomplete list
       of  bad  blocks.  Therefore  it  is recommended to use it only when one
       wants to know if there are any bad blocks at all on the device, and not
       when the list of bad blocks is wanted.
```

---

### Post by TwoEars on 2010-08-30
Wait, let me get this right, he was having an IE problem, so you told him to install Ubuntu? You do understand that IE is a browser, right? And that Windows can run more than one browser?

Regardless, tell him it's got a problem. Something along the lines of he can go get it professionally test if he wants, but you've checked and you know there's a problem will do. He'll either trust you, or he won't.

---

### Post by sandyd on 2010-08-30
> **TwoEars said:**
> Wait, let me get this right, he was having an IE problem, so you told him to install Ubuntu? You do understand that IE is a browser, right? And that Windows can run more than one browser?

**He seems to have a habit of screwing up windows one way or another. Last time, it was getting a black screen after installing MSN messenger. I really don't know what he does to his computer. And apparently, when IE crashes, a LOT of stuff crashes along with it (explorer.exe). Im currently thinking of simply taking away his IE icon.... This is like his.... 4-5? install.**

Regardless, tell him it's got a problem. Something along the lines of he can go get it professionally test if he wants, but you've checked and you know there's a problem will do. He'll either trust you, or he won't.

**I myself am a professional.... I work as the IT manager for an unnamable company.**

> **NightwishFan said:**
> I am not sure about that, however be aware of this from the man page. I apologize for not posting it sooner.
```
WARNING
       Never use the -w option on a device containing an existing file system.
       This option erases data!  If you want to do write-mode  testing  on  an
       existing  file system, use the -n option instead.  It is slower, but it
       will preserve your data.

       The -e option will cause badblocks to output a possibly incomplete list
       of  bad  blocks.  Therefore  it  is recommended to use it only when one
       wants to know if there are any bad blocks at all on the device, and not
       when the list of bad blocks is wanted.
```
yup, I knew about it. I have a habit of using man, since that time I accidentally wiped and (as a result) desynced one of the drives in my RAID array because I didn't read the manual properly.

---

### Post by NightwishFan on 2010-08-30
If I get a chance I will fire up a virtual machine to test badblocks.

---

### Post by sandyd on 2010-08-30
> **NightwishFan said:**
> If I get a chance I will fire up a virtual machine to test badblocks.
thanks! :)

---

### Post by TwoEars on 2010-08-30
> **carlee said:**
> **I myself am a professional.... I work as the IT manager for an unnamable company.**


yup, I knew about it. I have a habit of using man, since that time I accidentally wiped and (as a result) desynced one of the drives in my RAID array because I didn't read the manual properly.

IE taking down explorer.exe? On a fairly new laptop? That sounds like a malware problem, ma'am. 

Then why do you need to convince him? Have you tried telling him yet?

---

### Post by sandyd on 2010-08-30
> **TwoEars said:**
> IE taking down explorer.exe? On a fairly new laptop? That sounds like a malware problem, ma'am. 

Then why do you need to convince him? Have you tried telling him yet?

I don't think theirs malware, because its a different weird issue each time, and ive run about 30 different antiviruses on the computer (not all at once, companies provide portable antivirus software that can be run without installing). Ive used hijackthis, ive checked in the task manager, startup programs, msconfig, and practically every single millimeter of his installation. that was the first thing I did when his IE started crashing

Ive already DBANed his HD to US military grade specifications, so there should be no malware, spyware, or anything left over.

He doesn't believe that theirs an issue with his HD, since its only a few weeks old. (even though it could have been possibly damaged in transit, or he did something to it that I havent squirmed out of him yet.)

---

### Post by TwoEars on 2010-08-30
> **carlee said:**
> I don't think theirs malware, because its a different weird issue each time, and ive run about 30 different antiviruses on the computer (not all at once, companies provide portable antivirus software that can be run without installing). Ive used hijackthis, ive checked in the task manager, startup programs, msconfig, and practically every single millimeter of his installation. that was the first thing I did when his IE started crashing

Ive already DBANed his HD to US military grade specifications, so there should be no malware, spyware, or anything left over.

He doesn't believe that theirs an issue with his HD, since its only a few weeks old. (even though it could have been possibly damaged in transit, or he did something to it that I havent squirmed out of him yet.)
Is it Windows XP? This should not happen on anything newer than XP, due to the way the explorer.exe processes are handled. Regardless, one taking down the other is all the trademarks of malware.

Well, if he doesn't believe you, there's nothing you can do about it. You've given him your professional opinion, forget it and move on, if he doesn't believe you now, he never will.

---

### Post by NightwishFan on 2010-08-30
The Ubiquity installer actually keeps a log if it fails I believe. So if you are installing Ubuntu check the log viewer or /var/log folder on the live session after the failure. Checking the logs in general might be good anyway.

---

### Post by sandyd on 2010-08-30
> **TwoEars said:**
> Is it Windows XP? This should not happen on anything newer than XP, due to the way the explorer.exe processes are handled. Regardless, one taking down the other is all the trademarks of malware.

Well, if he doesn't believe you, there's nothing you can do about it. You've given him your professional opinion, forget it and move on, if he doesn't believe you now, he never will.
well, I kind of know why its taking down each other, its part of a fix for an security issue. I had to install it to prevent his dad's computer from infecting his computer. However, turning it back to normal, and putting it back on a (safe) network still has the same IE issue.

I just finished DBANing it a few seconds ago.

Installed windows back on.

At this rate, im simply going to create a partition for DSL, and set it to run a script when it boots so that it can restore his OS from a backup image (his computer has an internal USB connector, so I can leave a USB drive in there (in fact, that is what the internal connector is for, since its a PC that I bought while my company was selling out)) and install grub, and let him restore windows as he fancies....

I wonder if thats against the EULA.
oh well. I shall go and drown my sorrows by playing some MW2....

---

### Post by TwoEars on 2010-08-30
> **carlee said:**
> well, I kind of know why its taking down each other, its part of a fix for an security issue. I had to install it to prevent his dad's computer from infecting his computer. However, turning it back to normal, and putting it back on a (safe) network still has the same IE issue.

I just finished DBANing it a few seconds ago.

Installed windows back on.

At this rate, im simply going to create a partition for DSL, and set it to run a script when it boots so that it can restore his OS from a backup image (his computer has an internal USB connector, so I can leave a USB drive in there (in fact, that is what the internal connector is for, since its a PC that I bought while my company was selling out)) and install grub, and let him restore windows as he fancies....

I wonder if thats against the EULA.
oh well. I shall go and drown my sorrows by playing some MW2....

Who wrote the "fix"? I would not trust anything that modifies core system files, let alone in such a way that means they take each other down. If his dad's computer is calling out to other devices on the network, fix his dad's computer, or block his IP address from communicating with the son's.

---

### Post by sandyd on 2010-08-30
> **TwoEars said:**
> Who wrote the "fix"? I would not trust anything that modifies core system files, let alone in such a way that means they take each other down. If his dad's computer is calling out to other devices on the network, fix his dad's computer, or block his IP address from communicating with the son's.

its a patch provided by microsoft. its not exactly supposed to take down explorer, it was simply listed as a side effect if IE crashed.

---

