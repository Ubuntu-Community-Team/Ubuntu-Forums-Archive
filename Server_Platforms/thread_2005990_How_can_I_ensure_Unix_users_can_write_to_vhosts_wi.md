---
title: "How can I ensure Unix users can write to vhosts without breaking WordPress? Need help"
date: 2012-06-18
forum: Server Platforms
---

### Post by s3w47m88 on 2012-06-18
I have a Ubuntu 10.04 LTS web server that uses Webmin/Virtualmin as the control panel interface.

Each of the domains on my server are using WordPress, and I've configured Apache/PHP to run the files in such a way so WordPress users can upload and update files and folders accordingly.

What I need to accomplish now is to provide a way for my developers to be able to SFTP into the server and modify files in /var/www/vhosts, where all of the sites are, without changing the group (and preferably the owner) so that WordPress can continue to run uploads, etc...

Can anyone explain how I can accomplish this? I presume the Unix accounts should be added to a secondary group, and that I need to confirm the /var/www/vhosts is group writeable, but I'm unsure of how to accomplish this exactly.

Thank you!

---

### Post by Cheesemill on 2012-06-18
This thread may help:
[http://ubuntuforums.org/showthread.php?t=1969248](http://ubuntuforums.org/showthread.php?t=1969248)

---

