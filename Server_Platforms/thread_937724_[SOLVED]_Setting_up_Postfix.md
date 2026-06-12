---
title: "[SOLVED] Setting up Postfix"
date: 2008-10-04
forum: Server Platforms
---

### Post by botfish on 2008-10-04
Hi,

I've installed Ubuntu Server 8.04 and I'm trying to setup Postfix so I can send and receive mail on my local network. I've been following a tutorial

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

I skipped "Install Postfix" as it was already installed.
I tested my default setup, with Telnet I was able to send an email and verified that it was in my box with the mail command.

After following the instructions in "Setting Postfix Support for Maildir-style Mailboxes" I send a test mail but did not receive it with the mail command.

Files are appearing in ~/Maildir/new but for some reason I do not receive them with the mail program.

Help appreciated.

---

### Post by windependence on 2008-10-04
Well what folks don't tell you is you only have about half of what you need with Postfix. Postfix is an MTA (mail transfer agent). You already have outgoing smtp working the way it looks so you now need a POP3 or IMAP mail client. You can use something like Dovecot, or Courier-IMAP if you want.

Personallym I like to use a complete package that has everything I need from the beginning like Zimbra or Citadel. Setup is MUCH easier and you won't spend several days configuring things pulling your hair out.

Some resources:

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

[http://www.breezy.ca:8000/?q=node/271](http://www.breezy.ca:8000/?q=node/271)

-Tim

---

### Post by schettj on 2008-10-04
Or install dovecott to do the pop/imap side.

---

### Post by botfish on 2008-10-04
Thanks windependence!

I installed courier-pop and its working!

---

