---
title: "Webmin pure-ftpd module setup"
date: 2007-12-16
forum: Server Platforms
---

### Post by AustinMarton on 2007-12-16
Hi there,

My server runs Ubuntu fiesty, pure-ftpd and webmin. I am trying to configure other users for the ftp server but am having much trouble. Pureadmin just wouldn't work for me, and I tried just the commands from the readme files and that doesn't seem to work either. Webmin has worked well for everything else so I was hoping it would help me out, I just need to configure the pure-ftpd module.

I need help filling in these fields...

Path to the binary file pure-ftpd:   
 
Path to the binary file pure-ftpwho:
 
Path to the binary file pure-quotacheck:
 
Path to the binary file pure-pw:
 
Path to the PureFTPd conf file:
 
Path to the users file pureftpd.passwd:
 
Start Xinetd command:


I have searched /bin, /sbin, /usr/bin, /usr/sbin and can only find pure-pw. The default values were /usr/local/sbin and /usr/local/bin but both of those folders are empty.

Any help appreciated. 

Thanks,
Austin.

---

### Post by starscalling on 2008-05-27
wow no one helped eh

/usr/sbin/pure-ftpd
/usr/sbin/pure-ftpwho
/usr/sbin/pure-quotacheck
/usr/bin/pure-pw
configuration file used to be at /etc/pure-ftpd.conf i think but now is in /etc/pure-ftpd/conf dir
all the pure-ftpd stuff is in there - im running the mysql one so i dont have it but its like /etc/pure-ftpd.passwd
not sure... on the xinit start command, as i use standalone so /etc/init.d/pure-ftpd stop/start/restart/force-reload

---

