---
title: "Question of ssh pub key security"
date: 2009-01-01
forum: Security
---

### Post by Dave_Connor on 2009-01-01
I was able to setup ssh keys on both my systems so I can access them without the need for a password but still has password auth enabled if anything happens to my keys. I chose the default 512bit and no password but for a server open to the net would I need to generate new keys to beef up security ? Or is it okay having so if an attack tried to get in he/she would not have the key but still need to brute my password which is secure above 12 charators (bad spelling I know) I know no system can be un-hackable but how would my system stand up to security standards ?

---

### Post by kevdog on 2009-01-01
Your questions are rather scatterbrained.  I would choose no less than 1024-bit keys, and preferrably 2048 bit keys.  Having a password enabled system is always a security risk.

---

### Post by bodhi.zazen on 2009-01-01
This wiki page might help you :

[https://wiki.ubuntu.com/AdvancedOpenSSH](https://wiki.ubuntu.com/AdvancedOpenSSH)

I am not a fan of ssh keys without a password, but there are times when it may be necessary (although this is rare).

---

### Post by euler_fan on 2009-01-04
> **kevdog said:**
> Your questions are rather scatterbrained.  I would choose no less than 1024-bit keys, and preferably 2048 bit keys.  Having a password enabled system is always a security risk.

If I may offer a quote from the [ssh man pages]("http://www.openbsd.org/cgi-bin/man.cgi?query=ssh"):

> Finally, if other authentication methods fail, ssh prompts the user for a password.  The password is sent to the remote host for checking; however, since all communications are encrypted, the password cannot be seen by someone listening on the network.


The great irony of insisting on large RSA keys is that through an ssh tunnel a good long password (e.g. a 20 character output from, say, KeePassX's password generator) should be sufficient while, perhaps, not ideal. Besides, whether you're using keys or passwords, a better logon doesn't defeat an insecure remote machine in general.

Brute forcing a password is only relevant if you haven't configured your machine to allow only a certain number of attempts per period of time from a given IP address via something like fail2ban. Once that's done the idea of brute forcing a pseudo-random 20 character password is in the realm of the ridiculous.

By all means: do use RSA keys . . . it's the better way. But let's not make a mountain out of a molehill.

EDIT: To be fair, there are issues which using RSA keys circumvents, like some of the man in the middle and server spoofing stuff. But this implies someone wants to take it to that level against the machine in question.

---

