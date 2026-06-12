---
title: "vsftp doesn't work"
date: 2015-01-17
forum: Server Platforms
---

### Post by ceradini on 2015-01-17
Hello everyone, i'm using a Ubuntu server 14.04 and i'm trying to create an ftp access to my web server. I have installed an apache2 and the web server work correctly. After i have installed vsftpd but it doesn't work, if i try: ftp localhost , it returns: Connection refused

This is my vsftpd.conf file:

```
    anonymous_enable=Yes    anon_upload_enable=YES
    anon_mkdir_write_enable=YES
    local_enable=YES
    write_enable=YES
    dirmessage_enable=YES
    xferlog_enable=YES
    xferlog_file=/var/log/vsftpd.log
    xferlog_std_format=YES
    listen=YES
    listen_port=21
    ftpd_banner=Benvenuto nel Server FTP
    chroot_local_user=YES
    check_shell=NO
    userlist_deny=NO
    userlist_enable=NO
    #userlist_file=/etc/vsftpd.user_list
    pam_service_name=/bin/false

```

Some commands:

```
ps aux | grep -i ftp

root      5436  0.0  0.1  19164  1532 pts/0    T    15:47   0:00 ftp localhost                                                                                                                                                                                               
root      5437  0.0  0.1  19164  1532 pts/0    T    15:48   0:00 ftp localhost 21                                                                                                                                                                                            
root      5681  0.0  0.1  23392  1624 pts/0    T    16:06   0:00 ftp :::80                                                                                                                                                                                                   
root      5682  0.0  0.1  17440  1152 pts/0    T    16:06   0:00 ftp localhost 80                                                                                                                                                                                            
root      5698  0.0  0.1  19164  1528 pts/0    S+   16:11   0:00 ftp localhost 
```

My Firewall (UFW)

```
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
21/tcp                     ALLOW       Anywhere
990/tcp                    ALLOW       Anywhere
80                         ALLOW       Anywhere
443                        ALLOW       Anywhere
22 (v6)                    ALLOW       Anywhere (v6)
21/tcp (v6)                ALLOW       Anywhere (v6)
990/tcp (v6)               ALLOW       Anywhere (v6)
80 (v6)                    ALLOW       Anywhere (v6)
443 (v6)                   ALLOW       Anywhere (v6)

```

Whati could be the problem? And how i could fix it?

**Thank you** for the help

Good bye, Matteo.

p.s. My vsftpd starts with this command: *sudo service vsftpd start* and not with this: */etc/init.d/vsftpd start*

---

### Post by nerdtron on 2015-01-17
what does the /var/log/vsftpd.log outputs when you try to log in?

---

### Post by ceradini on 2015-01-18
> **nerdtron said:**
> what does the /var/log/vsftpd.log outputs when you try to log in?

The vsftpd.log file is empty. 

It may be possible that the command *service vsftpd stop* returns *stop: Unknown istance* ?

---

### Post by Lars Noodén on 2015-01-18
You might be able to save some trouble now and in the future by avoiding [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) entirely.  There are some use cases remaining for it but not many.  

Why do you have FTP for download if you already have HTTP/HTTPS?
If it's for upload, why add FTP when (I presume) you already have SFTP via SSH?

---

### Post by ceradini on 2015-01-18
> **Lars Noodén said:**
> Why do you have FTP for download if you already have HTTP/HTTPS?
If it's for upload, why add FTP when (I presume) you already have SFTP via SSH?

Because in my server i installed an wordpress site , and for update of my wordpres, or for downloads anything i have to provide an FTP access

EDIT:

Now i can bypass the problem with a particular configuration of wordpress, but if you could help me to fix the ftp problem i would be happy, i want to know what is the problem even if the site work correctly, **Thank you**

---

### Post by Lars Noodén on 2015-01-18
ok, but you might look at this plugin and see if it saves you work:

[https://wordpress.org/plugins/ssh-sftp-updater-support/](https://wordpress.org/plugins/ssh-sftp-updater-support/)
[https://wordpress.org/support/view/plugin-reviews/ssh-sftp-updater-support](https://wordpress.org/support/view/plugin-reviews/ssh-sftp-updater-support)

---

