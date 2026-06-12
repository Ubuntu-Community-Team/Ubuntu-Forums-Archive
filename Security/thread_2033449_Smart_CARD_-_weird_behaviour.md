---
title: "Smart CARD - weird behaviour"
date: 2012-07-26
forum: Security
---

### Post by CyberPingU on 2012-07-26
Hello all,
I configured my linuxbox to accept smart card authentication throuhg the opensc / pam_pkcs11 modules.
Everything is working (I get identified and so on), but a strange problem appear.
Every time I'm asked for the pin and I digit it correctly, the system echoes "*******" (which is the pin) and tries to execute the first file in the directory in which I am.
Here is the proof (in red are the command I digit on my own, others are done by system without any other input of mine):
```

matteo@darkstar:~/foo$ [COLOR="red"]ls[/COLOR]
startme
matteo@darkstar:~/foo$ sudo su
Smartcard authentification starts
Smart card found.
Welcome MATTEO (PIN CNS0)!
Enter your Smart card PIN on the pinpad
[COLOR="Red"]********[/COLOR]
verifying certificate
Checking signature
root@darkstar:/home/matteo/foo# ********
startme: command not found
root@darkstar:/home/matteo/foo#

```
As you see in the directory there is only one file called "startme". With the authentification, the system echoes again the "****" and tries to execute the first file in the directory in which I am when I run the command that involves a call to pam_auth.

Any ideas on how to avoid this?

---

