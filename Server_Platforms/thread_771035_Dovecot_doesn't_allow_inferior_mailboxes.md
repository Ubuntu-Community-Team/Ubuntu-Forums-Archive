---
title: "Dovecot: doesn't allow inferior mailboxes"
date: 2008-04-27
forum: Server Platforms
---

### Post by stuartbh on 2008-04-27
Mail/Server Gurus:

I have downloaded and installed Ubuntu Server 8.04, and created a normal user account as was requested during installation.

I then went over to a Windows XP Workstation with Outlook 2002 installed and tried to create subordinate mailboxes and was rebuffed. It stated something like doesn't allow creating subordinate folders or the like.

What changes must I make to allow this to happen?

Stuart

---

### Post by MJN on 2008-04-28
Can you elaborate on exactly what you were trying to do? (i.e. what folder were you trying to create, and where?) Also, have you tried from a different client?

Presumably you are using IMAP, but which message storage format? mbox/maildir? (run **sudo grep "default_mail_env =" /etc/dovecot/dovecot.conf** if you're not sure)

Your mail log *may* also hold some clues...

Mathew

---

### Post by stuartbh on 2008-04-28
> **MJN said:**
> Can you elaborate on exactly what you were trying to do? (i.e. what folder were you trying to create, and where?) Also, have you tried from a different client?

Presumably you are using IMAP, but which message storage format? mbox/maildir? (run **sudo grep "default_mail_env =" /etc/dovecot/dovecot.conf** if you're not sure)

Your mail log *may* also hold some clues...

Mathew

I have a lot of email messages in Microsoft Outlook 2002, that I wish to move over to my MacOS environment. My intention was to setup Ubuntu and run an IMAP Server temporarily so I could move all the messages to the IMAP Server under Outlook and then download them using my mail client on the MacOS side.

Thus, eventually I would have tried another email client, but for now was trying to get Outlook 2002 to work, so I can get the messages moved TO the IMAP server, so first I must make Outlook 2002 work.

I did try Entourage as well, and it too was rebuffed in terms of creating subfolders.


1) A grep of default_mail_env returns nothing
2) I do not really care if it uses mbox or maildir format, since this is temporary just to transfer mail from my Windows environment to my MacOS environment. However, I am curious what (if any) advantage there is with one over the other?

Thanks for your reply!

Stuart

---

### Post by stuartbh on 2008-04-28
> **MJN said:**
> Can you elaborate on exactly what you were trying to do? (i.e. what folder were you trying to create, and where?) Also, have you tried from a different client?

Presumably you are using IMAP, but which message storage format? mbox/maildir? (run **sudo grep "default_mail_env =" /etc/dovecot/dovecot.conf** if you're not sure)

Your mail log *may* also hold some clues...

Mathew

Of course I did come up with a simple solution this morning: Fedora 8

As apparently with Fedora 8, dovecot "just works", and with Ubuntu dovecot "does not just work" with an Outlook 2002 client.

I would still like to figure this out, but the dovecot.conf file from Fedora seems to be configured out of the box to support this subfolder capability.

Stuart

---

### Post by MJN on 2008-04-28
It ought to 'just work' so I wouldn't be too quick to make any assumes re distro-specific issues.

The reason I asked about mbox/mailbox is that the former doesn't allow sub-folders of folders that already contain messages. Hence why I asked about exactly what folder you were trying to create where.

Do the logs not say anything? What is the exact error message (for both clients)?

Mathew

---

