---
title: "rootkits and ubuntu"
date: 2014-02-06
forum: Security
---

### Post by Randy_Long on 2014-02-06
Hey all,
I'm a wannabe Ubuntu user(I'm partitioning my HD this week and will install beside XP). I'm curious about rootkits and linux. How prevalent are they? Are there certain safeguards to use when using Ubuntu/Linux? I'm just getting up to speed on rootkits, and I'd like to know if there are a lot of pitfalls with linux and the rootkit.

Thanks all,

---

### Post by ubudog on 2014-02-06
Hi Randy,

Due to the nature of Linux, it isn't likely that you'll "catch" a rootkit, as is possible in Windows (drive-by downloads, etc.)

However, if a hacker is able to compromise your system, he may install a rookit as a way of securing further access to the machine.

There are a few good rootkit scanners out there for Linux that are able to detect known rootkits that have been installed on your system, such as rkhunter, but in general, if you are an end-user, you should not be too worried about rootkits.

---

### Post by Randy_Long on 2014-02-06
thx ubudog. is rkhunter part of ubuntu? I am trying to learn more things/broaden my horizons, etc.

---

### Post by deadflowr on 2014-02-06
You have to install rkhunter, or the alternative chkrootkit.
Both are in the software center.
both are arcane command line tools, so...

---

### Post by prasys on 2014-02-09
As deadflowr pointed out , it's both command line tools. You may install it from the software centre and if you wish to try it out you may execute it with the following command in Terminal

```
sudo rkhunter --check
```

It will scan for rootkits , exploits , etc and present to you in a report

---

### Post by james_smith2 on 2014-02-09
My business got attatcked by a state of the art firmware kit - theres are known more often as ACPI BIOS ROOTKITS 

Scarily enough the code to bypass any FW has existed in public domain for years.  The code to copy / emulate and control motherboard memory areas from the BIOS writeable area and other areas including graphics memory and even CD-ROM caches has been public since 2006.

Its worrying to say the least.  What I had was infecting everything - mainly by flashing firmware roms.  Yet we were unable to remove it without losing six figures worth of IT gear as they create permenant tunnels into every machine in the network runningscripts such as stunnel4 on Kali Linux

These new breed of firmware rootkits bypass chkroot and rthunter etc

---

### Post by fugu2 on 2014-02-09
> **prasys said:**
> As deadflowr pointed out , it's both command line tools. You may install it from the software centre and if you wish to try it out you may execute it with the following command in Terminal
```
sudo rkhunter --check
```
It will scan for rootkits , exploits , etc and present to you in a report
Just a word of advice, these have given many false positives, many a times:)
For instance, i think it considers any directory that starts with a peroid to be harmful.
This is just the way linux make a folder hidden.

---

### Post by cariboo on 2014-02-09
To eliminate false positives, run:

```
sudo rkhunter --propupd
```

before doing a scan.

For more info on rkhunter options, check out:

```
man rkhunter
```

---

