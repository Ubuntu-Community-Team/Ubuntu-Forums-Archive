---
title: "Enigmail stopped working - &quot; gpg: problem with the agent - disabling agent use&quot;"
date: 2013-06-23
forum: Security
---

### Post by Lars Noodén on 2013-06-23
I've got Thunderbird with Engimail on Lubuntu Saucy.  Engimail has been working fine until a few days ago when it stopped working. I  get the following message when I check "details" on a message:

[indent]
 OpenPGP Security Info

 Error - signature verification failed

 gpg command line and output:
 gpg
 gpg: problem with the agent - disabling agent use
 gpg: can't query passphrase in batch mode
 gpg: Invalid passphrase; please try again ...
 gpg: can't query passphrase in batch mode
 gpg: Invalid passphrase; please try again ...
 gpg: can't query passphrase in batch mode
 gpg: encrypted with 1024-bit ELG-E key, ID XXXXXXXX, created 2004-01-09
       "xxxx <xx@xxxxx.com>"
 gpg: encrypted with 2048-bit ELG-E key, ID XXXXXXXX, created 2008-03-04
     "xxxxx <xxxx@xxxx.com>"
 gpg: public key decryption failed: bad passphrase
 gpg: decryption failed: secret key not available
[/indent]

The same files and settings work fine with Debian wheezy and IceDove, but no longer with Thunderbird on Saucy.  I've even tried installing the system again from daily snapshot ISO image and the problem persists.  It looks like there is something wrong with the agent, but the question is what and how to fix it.

---

### Post by cariboo on 2013-06-23
I've used the same ~/.gnupg directory for the past several releases, as it gets backed up during my weekly home directory backup. The only thing I can think of is that it may be a permission issue.

[LIST]
[*]pubring.gpg
[*]trustdb.gpg
[/LIST]


both have permissions of 700, all the other directories and files have permissions set to 777.

---

### Post by Lars Noodén on 2013-06-24
Maybe 777 is a typo?  I hope.

The problem here is with Thunderbird or with something tha Thunderbird interacts with.  gpg works in the shell just fine  I think the main clue might be in this line of the error message:

```

 gpg: problem with the agent - disabling agent use

```

I'm not sure which agent or how to check it.  I looked in Menu->Preferences->Desktop Session Settings->GPG Password Agent and that box is checked.

---

### Post by Non_Forum_User on 2013-08-31
Same problem and same setup here.
Temporary fix that works for me: in a terminal window type `killall gpg-agent`
You will have to do this after every login
If you want to contribute to the solution of the problem, file a bug report, not a forum complaint.
* [https://wiki.ubuntu.com/Lubuntu/ReportingBugs](https://wiki.ubuntu.com/Lubuntu/ReportingBugs)
Possible pointers for further research:
* [http://serverfault.com/questions/481103/gpg-agent-says-agent-exists-but-gpg-says-agent-doesnt-exist](http://serverfault.com/questions/481103/gpg-agent-says-agent-exists-but-gpg-says-agent-doesnt-exist)
* [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642021](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642021)

---

### Post by spam6 on 2013-12-10
I’ve solved this issue unchecking the “Never ask for any passphrase” in the basic tab of the enigmail preferences

---

### Post by hirt on 2014-03-13
I changed the /usr/bin/pinentry from pointing to pinentry-qt4 to pointing to **pinentry-gtk-2**. This resolved the issue. 
credits for the this solution go to [http://sourceforge.net/p/enigmail/forum/support/thread/ee2a2a62/#7e11](http://sourceforge.net/p/enigmail/forum/support/thread/ee2a2a62/#7e11)

---

