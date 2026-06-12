---
title: "FTP on Ubuntu server not working"
date: 2012-12-05
forum: Server Platforms
---

### Post by jg196976 on 2012-12-05
Have an Ubuntu 11.10 server that I need to FTP files to.  I installed vsftpd, made sure the service was running.  I test connected via localhost and it seems to work just fine.  However, I cannot connect to it from any FTP client I use.  I can't use windows command prompts to connect and I can't ftp from another Ubuntu server either. Firewall (ufw) is not enabled.  Any ideas on what I have done wrong?  
 
Josh

---

### Post by chadk5utc on 2012-12-05
check your logs for errors first, what about your vsftp config? Another option if you have ssh configured? just use winscp from your windows machine it will do the same thing and without the headaches. I have ssh setup to use keys and with winscp I can transfer anything I need to without an additional service that I rarely use, and its more secure.

---

### Post by Vegan on 2012-12-05
check to be sure ports 20-21 are pointing to the ftp server

---

### Post by jg196976 on 2012-12-05
I was able to connect with winSCP!!! Thanks for mentioning that.

---

