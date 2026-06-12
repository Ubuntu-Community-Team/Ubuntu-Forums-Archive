---
title: "Can anyone help explain syslog error?"
date: 2008-11-07
forum: Security
---

### Post by EzraReeves on 2008-11-07
Every time I use sudo i get this in my syslog:

> Nov  7 09:44:08 skepsis sudo: Error attempting to parse .ecryptfsrc file; rc = [-5]
Nov  7 09:44:08 skepsis sudo: Unable to read salt value from user's .ecryptfsrc file; using default 
Nov  7 09:44:09 skepsis sudo: Passphrase key already in keyring 
Nov  7 09:44:09 skepsis sudo: Error attempting to add passphrase key to user session keyring; rc = [1] 
Nov  7 09:44:09 skepsis sudo: There is already a key in the user session keyring for the given passphrase. 


Ive looked trying to find an explanation but cant. Anyone know?

---

### Post by cariboo on 2008-11-07
There seems to be a bug in the Private directory packages, as I am getting the same errors. See this bug:

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/259631](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/259631)

Note: I created this bug while I was suffering a momentary lapse of reason, but I see there has been a lot more added.

Jim

---

### Post by EzraReeves on 2008-11-07
Thanks for the reply, Im not sure I have the same problem. Honestly I dont even know if I have a problem. Everything seems to be working, I just want to make sure I dont have something mis configured.

Private Directory seems to be working fine from what I can tell. I get that when I use sudo for anything. Why does Private Directory have anything to do with using sudo?

---

