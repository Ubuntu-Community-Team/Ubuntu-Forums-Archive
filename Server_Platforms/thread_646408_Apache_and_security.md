---
title: "Apache and security"
date: 2007-12-21
forum: Server Platforms
---

### Post by blippy on 2007-12-21
Previously, I had a directory within my home dir which contained my website - just static stuff. I then installed proftpd, and created an account for a friend. I didn't like the idea of anyone snooping inside my homedir, though, so I did a chmod 700 on my homedir. This means that Apache now no longer worked, because it didn't have permission to access my files.

So what I did was 
sudo addgroup myname www-data
sudo chown www-data:www-data /var/www
sudo chmod g+w /var/www

Now I can access /var/www and put web content there.

So my question is: is my current setup a reasonable idea, or have a made a bad security gaff? Also, why isn't /var/www owned by www-data as default - I would have thought that to be more logical setup?

---

### Post by OoooMatron on 2007-12-21
Apache will only see the directory told in the apache config file, you don't need to fart about with chmod on other directories (as far as i know).

To stop people snooping aruond the machine you need to chroot the ftp user into a directory they cannot escape from. You better check that if you login under his name he can't check into your directory. There are various guides on doing this but its not a one command fix unfortunately.  FTP isn't as easy to control as on windows.

---

