---
title: "(security) is it ok to change the group of /var/www to :admin?"
date: 2008-04-29
forum: Server Platforms
---

### Post by darinwc on 2008-04-29
Is it ok security-wise to change the group ownership of the /var/www directory using these commands?

sudo chmod 775 /var/www
sudo chown -R :admin /var/www


Explanation:  I just installed ubuntu 7.10 on a fresh server that I will use as a lamp with mySQL.  I am using filezilla with FTP over SSH to upload files to the web directory root. By default, I dont have write access to /var/www except with sudo.

---

