---
title: "Migrating Mail Server to Ubuntu Server 11.04"
date: 2011-06-19
forum: Server Platforms
---

### Post by tyelford on 2011-06-19
Hi all, 

I am looking for some advise on a migration project I have going on at the moment.

Currently I have an old Fedora 5ish (I didn't install, but around that time) installation which is my current working installation, but looking to upgrade to a Ubuntu server.

On the new server I have exim4, dovecot, and horde installed and everything seems to be working so far with the current users. I can send and receive mail via webmail (horde) and using imap and pop. 

I am just at the stage of migrating the users form the old server to the new one. I tried to move one user as a test to see if it would go and this is what I did:

Copyied for that user:

[LIST]
[*]Entry from /etc/passwd
[*]Entry from /etc/shadow
[*]Entry from /etc/group
[*]Entry from /etc/gshadow
[*]/var/mail file, old and current use this style
[*]home directory, and made sure all permissions/owner was the same
[/LIST]
After all that I cannot log in as that user, tried to restart a bunch of services (mail, networking, apache, the whole box...).

Is there something extra that Ubuntu requires for users that I have missed?

---

