---
title: "SSH and FTP Server Software"
date: 2009-06-25
forum: Server Platforms
---

### Post by Pinball Wizard on 2009-06-25
What software do you suggest to set up on my server for SSH and FTP? I would assume OpenSSH would be king in answers but I wanted to ask first and make sure there are no problems with it. FTP Server is a new subject for me and I don't know what I should use to serve. Thanks.

---

### Post by ibutho on 2009-06-25
I'd just go with openssh since most (if not all) include it by default. As for ftp, there several servers available. The ones I have used are vsftpd (very secure ftp daemon) and proftpd. Both work very well for me, but you may have to look at the feature lists to see which would suite your needs best.

---

### Post by Pinball Wizard on 2009-06-25
I figured that OpenSSH was the choice for it, as it seems to be an industry standard. VSFTPD I assume will server SFTP? If so will I need to get a SSL Cert. for my server? I will most likely be getting one anyways for customer sake (ECommerce stores, secure admin login, etc.).

---

### Post by Bachstelze on 2009-06-25
> **Pinball Wizard said:**
> VSFTPD I assume will server SFTP? If so will I need to get a SSL Cert. for my server?

If you want to do FTPS, you will need a SSL certificate, yes. However, for FTP, you probably won't need an expensive certificate signed by a CA, a self-signed certificate will work just as well.

---

### Post by Pinball Wizard on 2009-06-27
Hmmm.... You have given me plenty to consider for my server setup.

---

### Post by doogy2004 on 2009-06-29
The default installation of OpenSSH will give you SFTP by default.

This is how my server is setup.

---

