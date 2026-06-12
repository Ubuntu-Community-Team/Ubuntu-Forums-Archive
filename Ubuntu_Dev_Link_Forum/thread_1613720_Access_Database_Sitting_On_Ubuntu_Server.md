---
title: "Access Database Sitting On Ubuntu Server"
date: 2010-11-04
forum: Ubuntu Dev Link Forum
---

### Post by xlight09x on 2010-11-04
Hello gurus. I bow to your knowledge.


I'm developing a VB.NET application for a client of mine. They want to host their Access databases on a remote server, and have the individual applications connect into it. I moved my Access database onto my /var/www folder and tried remoting into it, but I got an object/module not found error. They said to use some MSAD or something or another, but that's a Microsoft-only technology. Is there any way to have a VB.NET program remote into an Access database sitting on an Ubuntu server? Or do I have to deal the bad news that they have to buy Windows Server?



Thanks,


xLight09x

---

### Post by t4thfavor on 2010-12-30
Setup a samba share, and then access it like it was on a windows share.

Putting it in /var/www just hosts it out to whoever wants to download it from your ubuntu webserver.

Develop the application against something other than Access, and you wont regret it. You will soon see that the performance, and reliability just isn't there.

If your looking for cheap, you could go SQL Express 2008, or MySQL. If you SQL Express you can use access upsizing wizard to move the DB to the server.

---

