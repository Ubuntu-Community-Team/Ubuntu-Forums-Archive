---
title: "No permissions to /var/www"
date: 2010-04-01
forum: Server Platforms
---

### Post by davebradford on 2010-04-01
Hello guys! Small question, been racking my brians! Hope somebody can point me in the right direction.

I'm trying to SFTP to a local server and getting permissions errors from my user account, i've tried sudo chmod 777 to /var/www and not had much luck, doesn't seem to make any difference.

Is there anything else i can check?

Many thanks to you all for reading.

---

### Post by davebradford on 2010-04-01
sorry just an update, i can delete, but cannot create folders or upload files?

---

### Post by KB1JWQ on 2010-04-01
Did that sudo chmod work?

When you log into the box via ssh, does it let you write a file in that directory?

What does ls -al show on that dir?

---

### Post by davebradford on 2010-04-01
Hello thanks for your help.

I cannot create a directory via SSH using mkdir without a sudo. Maybe this is my problem, i get a permissions error.

This is my output 

user@test:/var$ ls -al www/
total 12
drwxrwxrwx  2 user user 4096 2010-04-01 23:28 .
drwxr-xr-x 17 root root 4096 2010-03-19 11:35 ..
-rw-r--r--  1 root root    7 2010-03-21 18:56 index.htm

---

### Post by Geweten on 2010-04-01
Hi guys,

Just had the same problem.

1) Fellowusers suggest that in sys>admin>groups> www-data your users should have permission so thick those first... This didn't help for me.

2) Then they suggest you should be root... Ok, I started a root window. Terminal : gksudo nautilus. But when I tried to drop a file from a usb as root to a regular window with /var/www , this didn't work either...

Finally I dropped the file in my file system and kicked it up a level at the time till I met www.
It worked, not as handy, but since these permissions entered ubuntu life became a little less easy...;)

Hope this helps cheers guys !

---

### Post by davebradford on 2010-04-01
this is very strange, I've had this working before I'm sure maybe if I enable the root account and use that but I'd rather not!

---

