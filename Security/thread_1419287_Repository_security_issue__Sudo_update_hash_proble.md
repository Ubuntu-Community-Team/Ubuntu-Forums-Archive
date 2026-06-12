---
title: "Repository security issue?  Sudo update hash problem"
date: 2010-03-01
forum: Security
---

### Post by trustintrance on 2010-03-01
I'm running ubuntu 9.10 on a VPS as well as on my home box.  A few days ago I ran apt-get on the VPS and got a prompt to install a new version of sudo.  I installed it.  I noticed that my home box found no such update.  I ran rkhunter and got this message:

```
Warning: The file properties have changed:
         File: /usr/bin/sudo
         Current hash: 8ac63a420a2fa2b359777f66a35e8c86d948108c
         Stored hash : 355d1fadf50704e5c47b3072fb95f4eed83c3669
         Current inode: 172157    Stored inode: 4474
         Current size: 123504    Stored size: 123448
         Current file modification time: 1267140126 (25-Feb-2010 23:22:06)
         Stored file modification time : 1245687262 (22-Jun-2009 16:14:22)

```

sudo -V on both boxes report the version as 1.7.0.  The shasum on my home box matches the stored hash however **the server's sudo hash is indeed wrong**.  

Does this look like the work of a rootkit or some other malware or is there a good explanation?

---

### Post by FuturePilot on 2010-03-01
No, that sudo update was a legit update. It fixed a couple security vulnerabilities. [http://www.ubuntu.com/usn/USN-905-1]("http://www.ubuntu.com/usn/USN-905-1")

---

### Post by bodhi.zazen on 2010-03-01
> **trustintrance said:**
> Does this look like the work of a rootkit or some other malware or is there a good explanation?


The explanation is PEBKC =)

First, this is not windows, so tools such as rkhunter are of dubious assistance. IMO the problems are two fold.

First people run rkhunter without reading the man pages.

Second there are too many "false positives"

I suggest you start with 

```
info rkhunter
```:twisted:

So, what happened to you ?

First you did not read the man page.

Second you updated your system (sudo) without updating rkhunter.

Third, you assume you have a problem without doing your foot work.

rkhunter keeps such hashes in a database, I believe /var/lib/rkhunter/db/rkhunter.dat

To update the database, run: 

```
 sudo rkhunter --propupd
```You may be able to configure rkhunter to automatically update the database, try
 
```
sudo dpkg-reconfigure rkhunter
```and look at the options.

If you are going to run tools such as rkhunter, I advise you read the man pages and look up the warnings and what they mean. With so many false positives you need to known what is "normal" and this comes only with experience and the willingness to read.

With that said, IMO, these tools are not very helpful because:

1. Too many false positives.

2. They can only scan for known threats, not emerging threats.

IMO you are much much better off learning apparmor.

---

### Post by trustintrance on 2010-03-01
RTFM, yeah I get it.  Got the issue fixed, thanks for your help.

---

### Post by bodhi.zazen on 2010-03-01
> **trustintrance said:**
> RTFM, yeah I get it.  Got the issue fixed, thanks for your help.

Glad you got it sorted, I am not trying to give you a hard time, and I apologize if I came across as harsh, but these are things you must know if rkhunter you will use.

---

### Post by trustintrance on 2010-03-01
No worries.  It was slightly harsh but you were right I should have read up a bit more before utilizing the tool.

---

