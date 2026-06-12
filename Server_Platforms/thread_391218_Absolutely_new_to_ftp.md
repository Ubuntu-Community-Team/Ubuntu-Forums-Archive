---
title: "Absolutely new to ftp"
date: 2007-03-22
forum: Server Platforms
---

### Post by poisonelegy on 2007-03-22
I would like to set up a ftp server in Ubuntu 6.10 to better understand them. I am a complete noob to servers in general, so please help me with this. All information is appreciated, if anyone can help me over skype (poisonelegy) or MSN (poisonelegy@hotmail.com) that would be great.

---

### Post by gepatino on 2007-03-23
Install package vsftpd, and you'll have an anonymous ftp server running.

If you want to allow local users to upload stuff (and login as themselves), edit /etc/vsftpd.conf and uncomment the following lines:

local_enable = YES
write_enable = YES

and restar the ftp service:

sudo /etc/init.d/vsftpd restart

---

