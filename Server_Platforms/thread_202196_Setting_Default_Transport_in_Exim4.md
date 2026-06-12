---
title: "Setting Default Transport in Exim4"
date: 2006-06-23
forum: Server Platforms
---

### Post by herald on 2006-06-23
Greetings.  I'm an old hat to Debian, but new to Ubuntu.  I have to say I'm really impressed with how slick Ubuntu is.  I am frustrated, however, that the update-exim4.conf.conf file does not have a place to override the mail_spool option for the LOCAL_DELIVERY option in Exim4.  I've searched, IRC'd and blogged my way to no avail.  Anyone know how you can edit the update-exim4.conf.conf file to specify the LOCAL_DELIVERY to point to $home/maildir instead of the default of  mail_spool?

The reason I'm trying to do this is so that I can similarly configure Dovecot to pop from the same place...I'm kinda stuck here until I can figure this out.  Thanks in advance for your help!

---

### Post by nagilum on 2006-06-25
The LOCAL_DELIVERY option may not be mentioned in the update-exim4.conf.conf file but it is checked in exim4.conf.template nonetheless. Search for LOCAL_DELIVERY in the last file and you will find the .ifndef-construct. Just add a line

```
dc_localdelivery='maildir_home'
``` to the update-exim4.conf.conf file and it should work.

---

