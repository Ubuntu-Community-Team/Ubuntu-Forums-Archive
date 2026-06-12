---
title: "Need Help Please"
date: 2005-06-12
forum: Server Platforms
---

### Post by stuffradio on 2005-06-12
Hi, I'd like to run an ssh server, ftp server, have apache running and host websites and give out shell accounts. I currently have the ssh server and apache installed but I don't know how to configure them, can you help me please? I also need to know how to install the ftp server and configure it so I can give people accounts and have them able to upload stuff to there folders.


Thanks

---

### Post by desdinova on 2005-06-12
[QUOTE=stuffradio]Hi, I'd like to run an ssh server, ftp server, have apache running and host websites and give out shell accounts. I currently have the ssh server and apache installed but I don't know how to configure them, can you help me please? I also need to know how to install the ftp server and configure it so I can give people accounts and have them able to upload stuff to there folders.


Thanks[/QUOTE]
 [http://www.openssh.org/manual.html](http://www.openssh.org/manual.html) is a full manual on Open SSH  - I'd spend some time reading up before opening up your box in this way - a misconfiguration leaves you wide open....

---

### Post by stuffradio on 2005-06-12
Thanks so much! :D, Now all I need is a ftp server, and I need to know how to configure apache to work, thanks again :)

---

### Post by desdinova on 2005-06-12
[QUOTE=stuffradio]Thanks so much! :D, Now all I need is a ftp server, and I need to know how to configure apache to work, thanks again :)[/QUOTE]
 [http://httpd.apache.org/docs-project/](http://httpd.apache.org/docs-project/)

---

### Post by stuffradio on 2005-06-12
thanks! :D Also how do I add users for the ssh and set the permissions for them?

---

### Post by desdinova on 2005-06-12
[QUOTE=stuffradio]thanks! :D Also how do I add users for the ssh and set the permissions for them?[/QUOTE]
 That's set as normal users permissions - I think you need to Google for RUTE and read up a little on it - I'd exercise REAL caution on opening up your box to others without a good understanding of all this

---

### Post by stuffradio on 2005-06-12
It's me again :D, I need one more thing then I think I'm done with questions for now! I need to know how to execute vsftpd, I have it unzipped I also edited the config file, so all I need now is the commands to build it or execute it or something.




Thanks

---

### Post by LordHunter317 on 2005-06-12
Well if you unzipped it, you're doing the wrong thing.

You sohuld have installed it via apt-get.

Not to be mean, but you should google for and read several guides on basic Linux system adminstration before continuing on this root.  Otherwise, you're just going to get yourself in trouble.

---

### Post by desdinova on 2005-06-12
[QUOTE=LordHunter317]Well if you unzipped it, you're doing the wrong thing.

You sohuld have installed it via apt-get.

Not to be mean, but you should google for and read several guides on basic Linux system adminstration before continuing on this root.  Otherwise, you're just going to get yourself in trouble.[/QUOTE]
 At the risk of sounding like "me too" I must also add I feel the same

---

