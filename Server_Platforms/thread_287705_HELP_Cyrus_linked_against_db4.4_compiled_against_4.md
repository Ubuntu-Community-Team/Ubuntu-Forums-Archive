---
title: "HELP: Cyrus linked against db4.4 compiled against 4.3?"
date: 2006-10-29
forum: Server Platforms
---

### Post by Sir-Archimedes on 2006-10-29
Hey Folks,

I just upgraded my server from Dapper to Edgy. Now I've got severe problems with cyrus: It's not starting and in the logs I find:

> Oct 29 00:53:32 server cyrus/master[4030]: process 15520 exited, signaled to death by 11
Oct 29 00:53:32 server cyrus/master[4030]: service lmtpunix pid 15520 in READY state: terminated abnormally
Oct 29 00:53:32 server cyrus/notify[15519]: Fatal error: wrong db version
Oct 29 00:53:32 server cyrus/master[4030]: process 15519 exited, signaled to death by 11
Oct 29 00:53:32 server cyrus/master[4030]: service notify pid 15519 in READY state: terminated abnormally
Oct 29 00:53:32 server cyrus/notify[15522]: incorrect version of Berkeley db: compiled against 4.3.29, linked against 4.4.20
Oct 29 00:53:32 server cyrus/notify[15522]: Fatal error: wrong db version
Oct 29 00:53:32 server cyrus/lmtpunix[15521]: incorrect version of Berkeley db: compiled against 4.3.29, linked against 4.4.20 

I already tried to compile cyrus by myself, but it isn't working either. What can I do? Is it a bug, I can fix by myself?

I hope, you'll help me (fast - as it's my primary mail server)...

Regards and thanks in advance
Dominik

---

### Post by hguerreiro on 2006-10-31
I am in the same situation. Re-compiled the packages but to no avail.

Has anyone solved this???

---

### Post by hguerreiro on 2006-10-31
I've "solved" the problem by installing the dapper packages of cyrus 2.2.12. It's not a final solution but it will have to do!

There is an open bug about this issue:

[https://launchpad.net/distros/ubuntu/+source/cyrus-imapd-2.2/+bug/67111](https://launchpad.net/distros/ubuntu/+source/cyrus-imapd-2.2/+bug/67111)

---

### Post by prescor on 2006-11-11
Just adding my fuel to the fire.  I'm following the VERY nice setup instructions here: [https://help.ubuntu.com/community/Cyrus](https://help.ubuntu.com/community/Cyrus)

and getting the same errors when testing.  :-(

---

### Post by ramram29 on 2007-01-25
FOR THOSE STUCK WITH THE SAME PROBLEM. There's an easy (5 minutes) solution.

I have the same problem with the default version of Cyrus IMAP for Ubuntu 6.10 - cyrus-imapd-2.2 (2.2.13-4ununtu1). It returns "compiled against 4.3.29, linked against 4.4.20" in /var/log/mail.err. Here's what I did:

Deinstalled all of cyrus:

apt-get remove --purge cyrus-imapd-2.2 cyrus-admin-2.2 cyrus-common-2.2 cyrus-doc-2.2 libcyrus-imap-perl22 websieve

Edit '/etc/apt/sources.list' comment all the repositories; add only the Debian Testing repository (my favorite):

deb [ftp://ftp.us.debian.org/debian/](ftp://ftp.us.debian.org/debian/) testing main

Run 'apt-get update'

Reinstall cyrus imap:

apt-get install cyrus-imapd-2.2 cyrus-admin-2.2 cyrus-common-2.2 cyrus-doc-2.2 libcyrus-imap-perl22

It may also update your postfix, postfix-mysql and perl, which is good.

The following where updated to the latest so far:

From - To

cyrus-imapd-2.2 (2.2.13-4) to (2.2.13-10)
postfix (2.3.3-1) to (2.3.6-1)

Afterward I restarted cyrus2.2 and it worked with no errors showing in the logs.

---

### Post by wdla on 2007-01-26
Thanks RamRam ... exactly what was needed.

---

### Post by ekoontz on 2007-01-29
Hi RamRam, thanks for the tip, however I get a problem with GPG key authentication:

```

W: GPG error: http://wine.budgetdedicated.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: ftp://ftp.us.debian.org testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F NO_PUBKEY A70DAF536070D3A1
W: You may want to run apt-get update to correct these problems


```

Anyone know how can I import the debian public key?

---

### Post by ekoontz on 2007-01-29
(replying to myself)
actually, I don't need to verify the GPG key : updating works without it.

---

