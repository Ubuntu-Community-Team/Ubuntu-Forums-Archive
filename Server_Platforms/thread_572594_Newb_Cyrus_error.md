---
title: "Newb: Cyrus error"
date: 2007-10-10
forum: Server Platforms
---

### Post by Smartin on 2007-10-10
Hi,

My OSX Mail client connects to Cyrus on my Feisty box but when I try to create a new mail folder I get

 IMAP command "CREATE" failed.

The server error encountered was: Permission denied

How do I correct this?

Thanks!

Simon

---

### Post by Smartin on 2007-10-11
Hi,

I have done:
sudo cyradm
cyradm> localhost setacl INBOX smartin lrswipcda
localhost: No such file or directory
cyradm> hostname> setacl INBOX smartin lrswipcda
cyradm> 

I'm trying to give myself proper permissions but I'm still doing something wrong... Get the same error.

Just tried:
cyradm> setaclmailbox smartin lrswipcda           
usage: setaclmailbox mailbox id rights [id rights ...]
cyradm> setaclmailbox INBOX smartin lrswipcda
setaclmailbox: no connection to server
cyradm> 



Simon

---

