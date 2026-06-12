---
title: "Trojan in system"
date: 2012-02-22
forum: Security
---

### Post by IsisBast on 2012-02-22
Hi, I am new in Ubuntu.  Today I run avast4workstation to scan my home folder (even if I have read that antivirus are rarely needed, especially for &quot;normal&quot; users), and it revealed a trojan. It was located in PSM AntiKeyLogger package (unfortunately I do not have the name of the infected file, as I removed it). I have downloaded PSM AntiKeyLogger from sourceforge.net/projects/psmantikeyloger/files/ (I think it is a reliable site), some 2 days ago. Is this a false positive, or a real threat?  Moreover, I am sure to have run PSM AntiKeyLogger in Wine, and I have used sudo in this period. How likely is my computer to be compromised? In this (unlucky) case, should i reinstall ubuntu?  Thank you

---

### Post by roelforg on 2012-02-22
I wouldn't know,
i'd say: Google it and see

---

### Post by IsisBast on 2012-02-22
Thank you roelforg,  I have googled PSM AntiKeylogger, and seems good. Even sourceforge.net seems to be reliable. But is there any way to find if some keylogger/rootkit is present?

---

### Post by roelforg on 2012-02-22
> **IsisBast said:**
> Thank you roelforg,  I have googled PSM AntiKeylogger, and seems good. Even sourceforge.net seems to be reliable. But is there any way to find if some keylogger/rootkit is present?
Given the way linux works; those are really hard to make.
There are almost no known keyloggers around.
Most virus makers focus on Windows because that's what most people have.
Also, people who use linux generally know more than the average user, making them a harder target.
The rootkits can be prevented by making sure that you know what you're executing.

Use rkhunter to scan.
The man page on [http://manpages.ubuntu.com/manpages/oneiric/man8/rkhunter.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/rkhunter.8.html) should answer your questions.

---

### Post by CharlesA on 2012-02-22
rkhunter throws a few false positives.

As a general rule of thumb, only install software you trust instead of googling something, downloading it and installing it.

If you are concerned that your machine might be compromised, back it up and reinstall.

---

### Post by haqking on 2012-02-22
> **roelforg said:**
> Given the way linux works; those are really hard to make.
[B]There are almost no known keyloggers around.
Most virus[/B] makers focus on Windows because that's what most people have.
Also, people who use linux generally know more than the average user, making them a harder target.
The rootkits can be prevented by making sure that you know what you're executing.

Use rkhunter to scan.
The man page on [http://manpages.ubuntu.com/manpages/oneiric/man8/rkhunter.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/rkhunter.8.html) should answer your questions.

there are a few keyloggers for Linux.

LKL
logkeys
uberkey

few off top of head not sure if all still active, but there there are a few out there ;-)

And a keylogger is not a Virus if thats what you meant by the sentences above, they may be seperate statements though

Just to correct your terms there.

Cheers

---

### Post by SeijiSensei on 2012-02-22
I'm suspicious that something on SourceForge could be carrying malware, but if you're concerned, I'd [learn how to compile from source]("https://help.ubuntu.com/community/CompilingEasyHowTo"), get the source code, and compile it yourself.  See what avast thinks of the binary that results.

---

### Post by emiller12345 on 2012-02-22
By any chance was the trojan called EICAR?
EICAR is a test file that checks if antivirus is working or not, and is benign.

---

### Post by IsisBast on 2012-02-23
Thank you all for replies :D I have checked with rkhunter, there was all ok, but there were 2 warnings:      Performing filesystem checks   Checking /dev for suspicious file types                  [ Warning ]        Checking for hidden files and directories                [ Warning ]       What does this mean?

---

### Post by Dangertux on 2012-02-23
> **IsisBast said:**
> Thank you all for replies :D I have checked with rkhunter, there was all ok, but there were 2 warnings:      Performing filesystem checks   Checking /dev for suspicious file types                  [ Warning ]        Checking for hidden files and directories                [ Warning ]       What does this mean?

It means you're running Ubuntu -- those are typical false positives on Ubuntu

---

