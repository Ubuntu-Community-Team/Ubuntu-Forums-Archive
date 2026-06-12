---
title: "Need help transfering files"
date: 2006-03-04
forum: Server Platforms
---

### Post by Mr. Smiley on 2006-03-04
So I followed [this]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p5") guide completely (except I set everything to server.example.com) but proftpd refuses to work for me. When I type /etc/init.d/proftpd restart I get errors saying:
Restarting ProFTPD ftp daemon..
.. - getaddrinfo 'server.exapmle.com' error: Name or service not known
 - warning: unable to determine IP address of 'server.exapmle.com'
 - getaddrinfo 'server.exapmle.com' error: Name or service not known
 - warning: unable to determine IP address of 'server.exapmle.com'
proftpd.
 done.
.. and it refuses to start. I got everything else working fine though. I would like to have a user that has complete access to the computer.
Or instead I could use SSH(I used putty on my windows comp to configure it originally, the server doesn't even have a monitor:mrgreen:) to copy files back and forth. The only problem is I have no idea how to get root access in order to create/edit/delete directories and files. Is there any way I would be able to su the entire session? I use winscp.
Thanks you for your help!

---

### Post by adwait on 2006-03-04
Maybe it is not able to reslove the server.whatever.com domain name you are giving to it. Try giving the IP address directly, if it's static.

---

### Post by Mr. Smiley on 2006-03-04
Where would I go about changing it? I dont remember telling proftpd to go to that domain so it must have gotten it from another program.
Thanks for your help again!

---

