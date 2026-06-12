---
title: "Problem with Roundcube Webmail"
date: 2012-10-09
forum: Server Platforms
---

### Post by icaka92 on 2012-10-09
Hello,

I have a problem. Now i am hosting my site on 1 server and want to transfer it to other. I transfer my site, but now i try to transfer and the mail server. I install mail server to new host from this steps:
[http://ubuntuportal.com/2012/02/an-easy-step-by-step-to-installing-and-running-roundcube-webmail-on-ubuntu-linux-mint.html](http://ubuntuportal.com/2012/02/an-easy-step-by-step-to-installing-and-running-roundcube-webmail-on-ubuntu-linux-mint.html)

But on IMAP settings i leave it blank. I test to send message from server and it is okay, but now i can't login to my roundcube mail and how to create when somebody send me a message to [EMAIL="admin@oldhost.com"]admin@oldhost.com[/EMAIL] to receive it on [EMAIL="admin@newhost.com"]admin@newhost.com[/EMAIL]

I dump my roundcube db from old server and import it to the new server and try to login with same password but "Login failed"

Any ideas ?

---

### Post by lisati on 2012-10-09
The first thing I would check is that there an "admin" user on the new system.

---

### Post by lisati on 2012-10-09
*Thread moved to **Server Platforms**.*

---

### Post by icaka92 on 2012-10-09
Yes in roundcube database in users i have the user with the domain that i will transfer to new site. But i don't know what password to use to log in. I try everything. Password from old server, new password to new server

---

### Post by lisati on 2012-10-09
It is possible that the IMAP/POP3 login is failing on your new machine.

---

### Post by icaka92 on 2012-10-09
I don't think, because i try all. 
I make this too: [http://ubuntuforums.org/showpost.php?p=11902102&postcount=16](http://ubuntuforums.org/showpost.php?p=11902102&postcount=16)
What should be the password for user in database users ?

Thanks !

---

### Post by icaka92 on 2012-10-13
Any ideas ?

---

### Post by icaka92 on 2012-10-30
Hello again,

After many tries i don't make the new mai server to work. Any ideas about my problem ?

Thanks !

---

