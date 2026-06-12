---
title: "Cant log into ftp server, &quot;530 login incorrect&quot;? Please help???"
date: 2011-06-15
forum: Server Platforms
---

### Post by friendlybacon on 2011-06-15
I have been trying to figure this out FOREVER.
i have googled it profusely and i have found nothing that has fixed it.

EVERY time i attempt to login to the ftp server with any user, i am  prompted for my login info. I enter my login info (  the same username  and password required to logon everytime i boot up my system, right?)

everytime i do this, it spts back the following message:

``````````````````````````````````````````````````  `````````````````````````````````````

chris@chris-Satellite-L300D:~$ ftp 192.168.0.1
Connected to 192.168.0.1.
220 (vsFTPd 2.3.0)
Name (192.168.0.1:chris): chris
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.
ftp> 

``````````````````````````````````````````````````  ``````````````````````````````````````````````

Please help, i have been trying to get this to work forever, yet i get  the feeling that this is some obvious thing i have missed.... so  frustrating....

I can post vsftpd.conf if it helps, let me know.


THANKS.

---

### Post by falko on 2011-06-16
> **friendlybacon said:**
> (  the same username  and password required to logon everytime i boot up my system, right?)
Yes, if your FTP server is configured to use system users; no, if it uses virtual users.

Did you try both active and passive connections in your FTP client?

---

