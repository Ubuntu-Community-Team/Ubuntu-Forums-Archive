---
title: "copy user accounts from one server to another"
date: 2009-06-24
forum: Server Platforms
---

### Post by billylid on 2009-06-24
I am setting up a backup email server for my main email server and I need some help writing a script that I can run automatically every day which will copy/create any new users (and passwords) from my MAIN server to my BACKUP server.
 
I don't want to just copy the over the 
 
/etc/passwd
/etc/shadow
/etc/group
/etc/gshadow
 
because this will overwrite my system accounts on the BACKUP server
 
I've sorted out copying the /home directories - its just the user accounts (and passwords) I can't seem to work out.
 
Any help would be very much appreicated.
Thanks

---

### Post by blackxored on 2009-06-24
LDAP dude what I can tell you? That's the best way. Export your POSIX accounts to an OpenLDAP server and replicate them from there. My personal choice.

---

### Post by HermanAB on 2009-06-24
I can second LDAP, but the best way is to install a mail server that doesn't create system accounts for the users and which uses a proper database to store the mail, for example Zimbra or Citadel.  Then all you do is export the database, including the email, attachments and user accounts in one swell foop.

The difference between the enormous maintenance effort required with a legacy mail system such as Postfix, versus a zero maintenance modern mail system such as Citadel, is just mind blowing.  I changed to Citadel years ago and never looked back.

The funny thing is that Citadel is actually older than Postfix!

---

