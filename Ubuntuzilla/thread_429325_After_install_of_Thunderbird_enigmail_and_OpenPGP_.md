---
title: "After install of Thunderbird enigmail and OpenPGP now error and no longer work"
date: 2007-05-01
forum: Ubuntuzilla
---

### Post by TheReaperD on 2007-05-01
I had Thunderbird 1.5 installed with Kubuntu 7.04 Fiesty i386.  I removed that version with Adept and then ran the Thunderbird install script to install 2.0.  Everything seemed to be working fine until I relized that the inigmail plugin was no longer installed.  I downloaded it and installed the extension.  Now, anytime I try to view my keys or send a PGP signed email, I get the following error:

***
Error - encryption command failed
/usr/bin/gpg --charset utf8 --batch --no-tty --status-fd 2 --with-fingerprint --fixed-list-mode --with-colons --list-keys
gpg: can't open '/home.thereaperd/.gnupg/pubring.gpg
gpg: keydb_search_first failed: file open error
***

I confirmed that the file '/home.thereaperd/.gnupg/pubring.gpg' was still present.  Also confirmed that gnupg was installed.

Any ideas?

---

### Post by TheReaperD on 2007-05-01
I found a work around but, I don't exactly like it.  

As a test, I gave global read access to the pubring.gpg file.  Now, I'm able to view my keys and send PGP signed messages.

Better suggestions?

---

### Post by nanotube on 2007-05-01
hi
could you post the output of
```
ls -al /home.thereaperd/.gnupg/pubring.gpg
```
it should be owned by your username (not root).

also, why do you have /home.thereaperd... isn't it usually /home/thereaperd? or did you create a custom home dir?

---

### Post by TheReaperD on 2007-05-01
Interesting.  At some point, the owner must have been changed.  I didn't manually change it.

Note:  /home.thereaperd was a typo.  Should have read /home/thereaperd

Requested information:
***
[thereaperd@trd-laptop] ~/%> ls -al /home/thereaperd/.gnupg/pubring.gpg
-rw-r--r-- 1 root root 4950 2007-04-30 21:11 /home/thereaperd/.gnupg/pubring.gpg
***

I changed the owner and group permissions and now it is working properly again.  No clue what happened.

Thanks for the information.  I didn't catch that when I was trying to troubleshoot this.

*****

For anyone else with this issue, here are the 2 commands to fix it.  Open a terminal window and enter the following commands:

Note:  Replace <username> with your user/login name.

sudo chown <username> ~/.gnupg/*
sudo chgrp <username> ~/.gnupg/*

---

### Post by nanotube on 2007-05-01
> **TheReaperD said:**
> Interesting.  At some point, the owner must have been changed.  I didn't manually change it.

Note:  /home.thereaperd was a typo.  Should have read /home/thereaperd

Requested information:
***
[thereaperd@trd-laptop] ~/%> ls -al /home/thereaperd/.gnupg/pubring.gpg
-rw-r--r-- 1 root root 4950 2007-04-30 21:11 /home/thereaperd/.gnupg/pubring.gpg
***

I changed the owner and group permissions and now it is working properly again.  No clue what happened.

Thanks for the information.  I didn't catch that when I was trying to troubleshoot this.

*****

For anyone else with this issue, here are the 2 commands to fix it.  Open a terminal window and enter the following commands:

Note:  Replace <username> with your user/login name.

sudo chown <username> ~/.gnupg/*
sudo chgrp <username> ~/.gnupg/*

glad you figured it out. :)
don't forget to change the permissions back to 600, so that other users can't read your keys.
also, for your future reference, there's a faster way to change owner and group:
```
chown username:groupname ~/.gnupg/*
```

---

### Post by bitterbug on 2008-03-03
Great tip! That error was driving me bonkers.
I wonder why it makes the folder a child of root.

---

### Post by nanotube on 2008-03-03
> **bitterbug said:**
> Great tip! That error was driving me bonkers.
I wonder why it makes the folder a child of root.

heh that's the problem, i do not know /what/ is the "it" that makes the folder owned by root. i know ubuntuzilla itself always runs gpg as the user, not as root, so it shouldn't be doing this...

what were the exact steps that you performed between when your gpg folder was owned by you and everything was working, and when it got re-chowned to root and stopped working? (specifically, think if you ran anything with sudo...?)

or maybe.... tell me, did you by any chance run ubuntuzilla itself with sudo?

---

