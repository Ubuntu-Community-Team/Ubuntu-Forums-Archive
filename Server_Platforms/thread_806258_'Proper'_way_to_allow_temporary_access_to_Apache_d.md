---
title: "'Proper' way to allow temporary access to Apache domain files"
date: 2008-05-24
forum: Server Platforms
---

### Post by opus_az on 2008-05-24
Still a bit of a novice but I'm hoping to do things the 'proper' way. 

I have a few virtual hosts and for one of them I'll allow **temporary** SSH/SFTP access to one of the domains.

Right now I have /var/www/domain001 /var/www/domain002 etc. Then I created a user "tempuser" with home in /home/tempuser and I created a symbolic link in tempuser's home directory pointing to /var/www/domain001, then chown-ed the link to testuser.

Would this be 'proper' for temporary access?

---

