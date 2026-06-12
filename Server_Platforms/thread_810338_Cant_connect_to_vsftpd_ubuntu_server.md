---
title: "Cant connect to vsftpd ubuntu server"
date: 2008-05-28
forum: Server Platforms
---

### Post by rado3105 on 2008-05-28
Hi could you help me i cant connect to vsftpd ubuntu server, it seems that it doesnt run:

/etc/init.d/vsftpd restart
>  * Stopping FTP server: vsftpd                                                  No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
 * Starting FTP server: vsftpd  

using /etc/init.d/vsftpd status
shows this:
 > * Usage: /etc/init.d/vsftpd {start|stop|restart|reload}


And i write: vsftpd
shows this:
> 500 OOPS: bad bool value in config file for: write_enable

Here is my /etc/fstab for that disk:

> UUID=4e3fccc3-a7ff-4e3d-b1d0-c8255a2444c7  /media/WD1TB   ext3 defaults 0  0


My vsftpd.conf
> listen=YES
listen_port=21
background=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
virtual_use_local_privs=YES
dirmessage_enable=YES
xferlog_enable=YES
xferlog_file=/var/log/vsftpd.log
connect_from_port_20=YES
chown_uploads=YES
chown_username=r-c
ftpd_banner=FTP Server
secure_chroot_dir=/var/run/vsftpd pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/media/WD1TB

I am trying to connect there like anonymous using TOTAL COMMANDER

---

### Post by windependence on 2008-05-28
What happens if you do:

```
/etc/init.d/vsftpd restart
```

"status" does not look like a valid option, that's why you got the usage hint.

-Tim

---

### Post by conjur3r on 2008-05-28
> **rado3105 said:**
>  500 OOPS: bad bool value in config file for: write_enable 


This message is hinting at the write_enable option.  Try commenting it out and restart to see if it starts up?

---

### Post by windependence on 2008-05-28
> **conjur3r said:**
> This message is hinting at the write_enable option.  Try commenting it out and restart to see if it starts up?

I am so sorry, I meant to say:

```
/etc/init.d/vsftpd start
```

Restart tries to shut down a server that isn't running before it restarts it. You will have to start the service first.

-Tim

---

### Post by rado3105 on 2008-05-28
this shows me in my ftp client:
500 OOPS: vsftpd: not found: directory given in 'secure_chroot_dir':/var/run/vsftpd pam_service_name=vsftpd 
OFFLINE

Before this I had to delete lines:

500 OOPS: bad bool value in config file for: > dirmessage_enable

500 OOPS: bad bool value in config file for: > chown_uploads

Could You help me how to change it to be that mount point: /media/WD1TB browseable for anonymous, /some folder in that disk(e.g public) readable and writable for anonymous/, /media/WD1TB writable for root and for some users I set up(eg johny). Please I solve this a few days without no results.

---

### Post by windependence on 2008-05-28
Were you able to start the service?

What is the output of:


```
sudo psauxww | grep vsftpd
```


-Tim

---

### Post by rado3105 on 2008-05-28
-bash: psauxww: command not found

It seems that it started using /etc/init.d/vsftpd start

but then after trying /etc/init.d/vsftpd restart showed this:
>  * Stopping FTP server: vsftpd                                                  No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
 * Starting FTP server: vsftpd                                           [ OK ]


---

### Post by windependence on 2008-05-28
> **rado3105 said:**
> -bash: psauxww: command not found

It seems that it started using /etc/init.d/vsftpd start

but then after trying /etc/init.d/vsftpd restart showed this:

Sorry, should have been:

```
sudo ps auxww | grep vsftpd
```

My bad!


-Tim

---

### Post by rado3105 on 2008-05-28
> root      4035  0.0  0.7   3692   888 ?        S    17:17   0:00 /usr/sbin/vsftp                                                           d
r-c       4051  0.0  0.5   2976   752 pts/0    R+   17:27   0:00 grep vsftpd

I reinstalled the vsftpd and it is not able to start when i try sudo /etc/init.d/start and then restart it doesnt show nothing.

---

### Post by rado3105 on 2008-05-28
It works now after second reinstall and changing vsftpd.conf like this:
listen=YES
anonymous_enable=YES
write_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
dirmessage_enable=YES
dirlist_enable=YES
no_anon_password=YES
file_open_mode=0777
guest_enable=YES
Could you help me how to permanently mount media/WD1TB to var/ftp?
And I created folder public in /var/ftp, I want to be that folder writable for anonymous, can you help how to set it?

---

### Post by windependence on 2008-05-28
Create a symlink for it:


sudo ln -s /media/WD1TB /var/ftp/WD1TB


-Tim

---

