---
title: "Using ftp to upload"
date: 2007-03-03
forum: Server Platforms
---

### Post by jamiehd on 2007-03-03
How do I change the persmissions of /vav/www so that I can upload files to it?

Thanks in advance,

Jamie

Sorry, forgot to add that I installed from the server disk, so I just have the terminal.

---

### Post by Mr. C. on 2007-03-03
It depends on your ftp server and how its configured.

Is it running now?  vsftpd?

Are you trying to configure it for your own uploads, or for others?

A little more info please...

MrC

---

### Post by jamiehd on 2007-03-04
I'm running pure-ftpd and I want to configure it so I can upload using the account I use to log in. I basically want to change it, so that people who aren't root can change the folder.

---

### Post by Mr. C. on 2007-03-04
"People who aren't root" means "everyone".  Therefore, it sounds like you want:

chmod 777 /var/www

Does that solve your problem?

MrC

---

### Post by jamiehd on 2007-03-04
Yes. Thank you very much!

---

