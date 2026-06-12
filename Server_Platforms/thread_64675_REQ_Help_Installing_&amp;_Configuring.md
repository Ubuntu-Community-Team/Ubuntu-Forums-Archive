---
title: "REQ: Help Installing &amp; Configuring"
date: 2005-09-11
forum: Server Platforms
---

### Post by andril on 2005-09-11
Calling all Guru's I am a noob very fond of this forum and Ubuntu. I have converted all my PC's to Ubuntu all except my server. It currently runs M$oft WinXP Pro and uses the following apps to become my server:

DNS2GO (via paid domain)
Merak Email Server (POP3 & SMTP)
Xeno Web Server (HTTP)
Gene6 Server (FTP)

Please let me know what packages (or better) are similar within Ubuntu and help me get rid of the Windoze in my home.

Can you help me by providing step by step so I don't screw up my installation? I appreciate any help and will provide one of the biggest FTP's for linux apps to this forum upon completion. 


Thanks In Advance! \\:D/

---

### Post by bsussman on 2005-09-11
DNS - consider djbdns
email - consider qmail

go to [http://cr.yp.to](http://cr.yp.to) to study these - I know some very careful folk who have +60,000 virtual domains, using, among others, these tools.

Web - apache2 - installs in ubuntu easily, supports everything.  Others might consider apache, as more mature, better

FTP - ProFTP seems to be the server of choice these days.

There is extensive documentation available - I do not think I could do better than what is already written

---

### Post by LordHunter317 on 2005-09-11
[QUOTE=bsussman]DNS - consider djbdns
email - consider qmail[/quote]No, both are obsolete software and never should be used on new deployments.  Superior software that's actually maintained, has better licensing, and a larger default featureset is available today, so there is simply no reason to use DJB software anymore, except in legacy situations.

Use Bind9 in a chroot for DNS and postfix or exim4 for email.

> FTP - ProFTP seems to be the server of choice these days.Pure-FTPD and VSFTP are good alternatives, as well.  All are pretty comparable in feature set.

---

