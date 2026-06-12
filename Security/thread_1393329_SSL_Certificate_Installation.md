---
title: "SSL Certificate Installation"
date: 2010-01-29
forum: Security
---

### Post by knichel on 2010-01-29
I recently installed a fresh OS on my server in my classroom.  It has been a couple of years since I installed my SSL certificates from godaddy.  Can someone tell me or point me to an article that tells me what I need to do?  I have my old OS mounted on /OLD so I can get to all of my previous configs etc...  I have my .csr, .crt, .key files 

So I need to re-generate anything since I have a new install?  Do I simply copy the folder that has the .csr, .crt & .key files to the new install?  I have /etc/apache2/ssl  with these files.  

Thanks in advance,
Mike

---

### Post by terazen on 2010-01-29
In your old /etc/apache2/sites-available/ there should be a config file with a few lines for ssl config.  If you copied that file to the new sites-available then whatever ssl cert files it references you'll want to copy over.

Another thing you might need to check would be the old /etc/apache2/mods-enabled to see if you enabled any modules on the old server setup that need to be on the new server.

---

### Post by knichel on 2010-01-29
Thanks for the tips.  Looks like it worked.

---

