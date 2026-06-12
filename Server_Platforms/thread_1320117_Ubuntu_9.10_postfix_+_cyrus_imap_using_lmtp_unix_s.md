---
title: "Ubuntu 9.10 postfix + cyrus imap using lmtp unix socket"
date: 2009-11-08
forum: Server Platforms
---

### Post by eclay on 2009-11-08
I've been working on setting postfix + cyrus-imap on karmic 9.10.  I have it configured correctly based on my interpritation of the readme files.  I followed README.Debian.simplinstall, README.postfix.  I also setup both postfix and cyrus-imap to use secure authentication.  I can login with no problems.  When I attempt to send an email to users mailbox I get the following error in the /var/log/mail.log

Nov  9 03:38:52 mail postfix/lmtp[3264]: 11926C0411: to=<eclay@clayeweb.org>, relay=none, delay=16983, delays=16983/0.01/0.01/0, dsn=4.4.1, status=deferred (connect to mail[/var/run/cyrus/socket/lmtp]: No such file or directory)

So I made sure to pay special attention to the lmtp stuff in the readme's.  In the README file it says to do the following so postfix will have rights to the lmtp socket file.
[B]
README.postfix[/B]
1. Create a lmtp group:
        # addgroup lmtp

2. Put user postfix in that group:
        # adduser postfix lmtp

3. Fix the socket directory permissions:
        # dpkg-statoverride --force --update --add \
          cyrus lmtp 750 /var/run/cyrus/socket

4. Restart Postfix and Cyrus IMAPd
        # /etc/init.d/postfix restart
        # /etc/init.d/cyrus2.2 restart

This has been done on my system and I still get the error that postfix can't find or see a lmtp file in /var/run/cyrus/socket/lmtp.  When I login as root and browse to this directory the file exist.  The owner and group on it are both root.

**Postfix master.cf has the following line in it for lmtp.**
lmtp      unix  -       -       -       -       -       lmtp

**main.cf has the following.**
mailbox_transport = lmtp:unix:/var/run/cyrus/socket/lmtp

**cyrus cyrus.conf**
imap            cmd="imapd -U 30" listen="imap" prefork=0 maxchild=100
imaps           cmd="imapd -s -U 30" listen="imaps" prefork=0 maxchild=100
lmtpunix        cmd="lmtpd" listen="/var/run/cyrus/socket/lmtp" prefork=0 maxchild=20

**cyrus imapd.conf**
lmtpsocket: /var/run/cyrus/socket/lmtp

**permissions on the lmtp file**
srwxrwxrwx 1 root root 0 Nov  8 23:53 /var/run/cyrus/socket/lmtp

**Permissions on /var/run/cyrus**
drwxr-xr-x 3 cyrus      mail         60 Nov  8 23:53 cyrus

**New Findings: Just found this.**
So what I am noticing is that the instructions above had me change ownership of the /var/run/cyrus directory to cyrus:lmtp.  When I start /etc/init.d/cyrus it changes the permissions back.  Postfix is a member of the mail group.  Both cyrus and postfix are memebers of postfix number 106.  This is the postfix users default group.

Because postfix is running in a chroot jail is it possible that postfix doesn't have rights or access to /var/run/cyrus?

Based on my new findings above postfix should have rights to the /var/run/cyrus directory since the mail group has permissions.  What is causing this error.

TIA

---

### Post by eclay on 2009-11-08
Seems like the problem is in the /etc/postfix/master.cf file.

I just changes this line.

lmtp      unix  -       - -       -       -       lmtp

to

lmtp      unix  -       -       n       -       -       lmtp

Basically this sets lmtp to not run in chroot.  Once I did this I could login and send and receive emails.

---

