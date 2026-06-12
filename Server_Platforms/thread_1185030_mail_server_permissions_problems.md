---
title: "mail server permissions problems"
date: 2009-06-11
forum: Server Platforms
---

### Post by clownschoolphd on 2009-06-11
I have a postfix/courier mail server on a Ubuntu server 9.04 box.  It works fine for a period of time then fails out of the blue with permissions issues in Maildir/.

I can't tell if the problem is with postfix or courier.

/etc/init.d/courier-imap-ssl restart

will fix the issue temporarily but the logs seem to indicate a postfix problem first.

this is where the bad news starts:
Jun 11 10:13:14 domain postfix/local[4291]: warning: maildir access problem for UID/GID=1000/1000: create maildir file /home/username/Maildir/tmp/1244733194.P4291.domain.net: Permission denied
Jun 11 10:13:14 domain postfix/local[4291]: warning: perhaps you need to create the maildirs in advance
Jun 11 10:13:14 domain postfix/local[4291]: 286BA3D12: to=<username@domain.net>, relay=local, delay=0.36, delays=0.25/0.01/0/0.1, dsn=5.2.0, status=bounced (maildir delivery failed: create maildir file /home/username/Maildir/tmp/1244733194.P4291.domain.net: Permission denied)
Jun 11 10:13:14 domain postfix/cleanup[4239]: 863AF46E9: message-id=<20090611151314.863AF46E9@mail.domain.net>
Jun 11 10:13:14 domain postfix/bounce[4292]: 286BA3D12: sender non-delivery notification: 863AF46E9
Jun 11 10:13:14 domain postfix/qmgr[3185]: 863AF46E9: from=<>, size=5179, nrcpt=1 (queue active)
Jun 11 10:13:14 domain postfix/qmgr[3185]: 286BA3D12: removed
Jun 11 10:13:16 domain imapd-ssl: chdir Maildir: No such file or directory
Jun 11 10:13:19 domain imapd-ssl: Connection, ip=[::ffff:66.251.226.2]
Jun 11 10:13:21 domain imapd-ssl: chdir Maildir: No such file or directory
Jun 11 10:13:22 domain imapd-ssl: Connection, ip=[::ffff:66.251.226.2]
Jun 11 10:13:24 domain imapd-ssl: chdir Maildir: No such file or directory
Jun 11 10:13:24 domain imapd-ssl: Connection, ip=[::ffff:66.251.226.2]
Jun 11 10:13:27 domain imapd-ssl: chdir Maildir: No such file or directory

So to recap, my mail server is up and functioning properly.  Then all of a sudden any mail sent to me is bounced back to the sender with this error:

/home/user/Maildir/tmp/1244734481.P2935.domain.net: Permission denied

I've doubled checked permissions both while the server is passing mail and when it's acting funky.  No difference between the two states.  

Does anyone have any idea how this can happen?

Appreciate the assistance.

---

### Post by clownschoolphd on 2009-06-12
As a heads up to any future Googlers, I figured out why this is happening.

Upon install, I opted to encrypt my home directory with Jaunties cool new Private directory feature. When I'm logged in to the server postfix can deliver mail to ~/Maildir without issue.  When I'm not logged in, *nothing* has access to to anything in ~/

Looks like the options at this point are:
[INDENT]see if I can roll back the encrypted private directory setup[/INDENT]
[INDENT]see if postfix/courier will allow me to place Maildir outside of a users /home[/INDENT]
[INDENT]reinstall...[/INDENT]

Big thanks to the nice people in the postfix irc room.

---

### Post by defaria on 2009-11-14
I have this same problem. What did you do to resolve it? I looked at some instructions about unencrypting the home dir but they looks a little worrisome. I tried to tell Postfix to use some other directory than my home dir but that didn't work either.

---

### Post by defaria on 2009-11-14
I ended up unencyrpting my home directory as per [http://ubuntuforums.org/showthread.php?t=1135796](http://ubuntuforums.org/showthread.php?t=1135796). Worked relatively easily.

---

