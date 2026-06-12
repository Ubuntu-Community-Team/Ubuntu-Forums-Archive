---
title: "DNS name server does not start"
date: 2006-06-26
forum: Server Platforms
---

### Post by Pelin on 2006-06-26
Hello,

I have put some new zone files in my dns server, and then restarted the name server. But so far I am not successful. Although it states that name server started, it actually does not start it up.

root@imstest:/etc/init.d# sudo /etc/init.d/bind9 start
 * Starting domain name service...
   ...done.
root@imstest:/etc/init.d# ps -ef | grep named
root       531 32760  0 13:15 pts/0    00:00:00 grep named

I have tried some other ways too. What can I be missing to check? How can I get name server up again?

Thanks,
Pelin

---

### Post by falcon15500 on 2006-06-26
Did it work with the old zone file?  I am assuming you just updated your root zone file?  Do you have backups of your old files?  Did you manually edit the files or are is a new root file out of dig?  Seems like it might be dying off straight away.

falc

---

### Post by Pelin on 2006-06-26
Hello,

it was working with my old zone files, but the thing is old ones are still there I just added two new zone files, which are exactly the same besides the IP addresses, so I dont see a reason why it does not start up. I will try to remove them and start again. I will inform you asap after lunch.
Thanks,
Pelin

---

### Post by Pelin on 2006-06-26
[QUOTE=Pelin]Hello,

it was working with my old zone files, but the thing is old ones are still there I just added two new zone files, which are exactly the same besides the IP addresses, so I dont see a reason why it does not start up. I will try to remove them and start again. I will inform you asap after lunch.
Thanks,
Pelin[/QUOTE]

OK, got the problem, my zone file name in named.conf remained the same as existing one.. Thanks a lot for your help.

---

### Post by Kurt` on 2006-06-26
[QUOTE=Pelin]I dont see a reason why it does not start up.[/QUOTE]
You can always check a program's log file (usually in /var/log) to see why it won't start up. Usually it's something silly on your part. :p

---

