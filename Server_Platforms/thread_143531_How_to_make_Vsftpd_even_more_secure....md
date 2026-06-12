---
title: "How to make Vsftpd even more secure..."
date: 2006-03-12
forum: Server Platforms
---

### Post by mryucky on 2006-03-12
Hello all,
I'm new to ubuntu, and I find it awesome, I did a server install and setup a no-gui based ftp/ssh server. I'm allowing anonymous users to connect, and this morning according to my /var/log auth.log file i had a user try for a couple of hours to login or take control of my box. I have vsftpd running in init mode and so I was wandering if there was a way to block this type of actions in the future, actions like port scanning and a high number of wrong logins? I found a promising looking howto:

[http://www.ubuntuforums.org/archive/index.php/t-86995.html]("http://www.ubuntuforums.org/archive/index.php/t-86995.html")
 
but it was just for proftp, because they say that vsftp doesnt handle tcp wrappers that well. 

Any tips or tricks or advice is appreciated...

mryucky

---

