---
title: "VSFTPD keeps giving me 550 Permission Denied"
date: 2008-06-18
forum: Server Platforms
---

### Post by cmetcjr on 2008-06-18
I just installed VSFTPD and made a user named ftpadmin.
I made the home folder for ftpadmin /var/www
I also gave ftpadmin ownership of /var/www

No matter what I do, I can't delete, add, or do anything in any directory even though when I log in, it goes there.

What am I doing wrong?

Thanks,
cmetcjr

---

### Post by Poleh on 2008-06-19
am I correct in assuming you created vsftpadmin user and are logging into the FTP server using that account? As opposed to that being the user the server daemon is running as.

Whichever account you use to login to the server is going to need permissions to the folders you are giong to browse.

You mention you've set the ownership on the folder, can you confirm the permissions with a screenie/dump?

I used
sudo chown -R ftpadmin /var/www 
sudo chmod -R 777 /var/www

watch out for the last line though, as this gives all users full access to the folder. But it's a good starting point, because it should allow access, and then you can start locking it down.

---

### Post by k.sangeeth on 2009-07-06
Well I also had a similar problem .. i figured out the solution.

open your vsftpd.conf file .. for me it was in /etc/vsftpd.conf.

There you will find the following line :
# Uncomment this to enable any form of FTP write command.
#write_enable=YES

Uncomment this .. it will look like this.
# Uncomment this to enable any form of FTP write command.
write_enable=YES

Restart your ftp daemon and I hope things will work as expected.

Cheers !!!!
[www.sangeek.com](www.sangeek.com)

---

### Post by pablobablo on 2011-03-12
> **k.sangeeth said:**
> Well I also had a similar problem .. i figured out the solution.

open your vsftpd.conf file .. for me it was in /etc/vsftpd.conf.

There you will find the following line :
# Uncomment this to enable any form of FTP write command.
#write_enable=YES

Uncomment this .. it will look like this.
# Uncomment this to enable any form of FTP write command.
write_enable=YES

Restart your ftp daemon and I hope things will work as expected.

Cheers !!!!
[www.sangeek.com](www.sangeek.com)

Thanks for your answer. It's helped.
After uncommend this line I used following command to restart FTP server:
```
service vsftpd restart
```

---

### Post by Sailor-Moon on 2011-04-17
I have the same issue, BUT when I try to access cd / etc/vsftpd.comf I get 
-bash cd / etc/vsftpd.comf :Not a directory

Help please :)

---

### Post by Vegan on 2011-04-17
open a terminal

```
sudo nano /etc/vsftpd.conf
```

---

