---
title: "vsftpd with virtual users.Want to discuss my general setup and how to storage quotas"
date: 2007-10-08
forum: Server Platforms
---

### Post by kentl on 2007-10-08
Hi!

I have roughly followed [http://www.debiansec.com/linux/services/ftp.html#introduction](http://www.debiansec.com/linux/services/ftp.html#introduction) to set up vsftpd with virtual users. It works well at the moment and I'm able to log in and upload, download and delete files.

However I do have some questions and would like to discuss my general set up. Therefore I begin by describing how my setup was created, which may very well serve as a guide if you are setting up vsftpd yourself with virtual users. If you do imitate this set up, make sure you read all the comments below so you don't imitate any bad decisions I've taken. :-)

[SIZE="5"]My setup:[/SIZE]

[LIST=1]
[*]_sudo aptitude install vsftpd_
[*] Created/edited /etc/vsftpd.conf
[*] Added all local users to the denied list, as they may not log in, I'm using virtual users only
[LIST=1]
[*] _sudo -i_
[*] _cat /etc/passwd | cut -d ":" -f 1 | sort >/etc/vsftpd/denied_users_
[*] _sudo -i_
[*] _exit_
[/LIST]
[*] Created/edited /etc/pam.d/ftp
[*] Created/edited ~/accounts.tmp
[*] _sudo aptitude install libdb3-util_
[*] _sudo db3_load -T -t hash -f ~/accounts.tmp /etc/vsftpd/accounts.db_
[*] _chmod 600 /etc/vsftpd/accounts.db_
[*] Create the virtual users folders
[LIST=1]
[*] _sudo -i_
[*] _cd /home/ftp_
[*] _mkdir user1 user2 user3_
[*] _chown ftp user1 user2 user3_
[*] _ls -ld *_ gives
```

drwxr-xr-x 2 ftp root 4096 2007-10-18 20:45 user1
drwxr-xr-x 2 ftp root 4096 2007-10-18 20:45 user2
drwxr-xr-x 2 ftp root 4096 2007-10-18 20:45 user3

```
[*] _exit_
[/LIST]
[/LIST]

**/etc/vsftpd.conf:**
```

=========================================
# base configuration
# -------------------------------------------------------------------------
anon_world_readable_only=NO
anonymous_enable=NO
chroot_local_user=YES
guest_enable=YES
guest_username=ftp
hide_ids=YES
listen=YES
# Not as in the tutorial
# listen_address=192.168.0.1
local_enable=YES
# Not as in the tutorial
max_clients=8
max_per_ip=1
nopriv_user=ftp
pam_service_name=ftp
pasv_max_port=65535
pasv_min_port=64000
session_support=NO
use_localtime=YES
user_config_dir=/etc/vsftpd/users
userlist_enable=YES
userlist_file=/etc/vsftpd/denied_users
xferlog_enable=YES
# -------------------------------------------------------------------------


# =========================================
# ftp settings
# -------------------------------------------------------------------------
anon_umask=0027
async_abor_enable=YES
connect_from_port_20=YES
dirlist_enable=NO
download_enable=NO
# =========================================

```

**/etc/pam.d/ftp**
```
auth required /lib/security/pam_userdb.so db=/etc/vsftpd/accounts
account required /lib/security/pam_userdb.so db=/etc/vsftpd/accounts
```

**~/accounts.tmp**
```
user1
password1
user2
password2
user3
password3
```

**/etc/vsftpd/users/user1** (the structure is the same for /etc/vsftpd/users/user2 and /etc/vsftpd/users/user3)
```

anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
dirlist_enable=YES
download_enable=YES
local_root=/home/user1
write_enable=YES

```

[SIZE="5"]Questions and discussion topics:[/SIZE]
[LIST=1]
[*]While this is working I would like to implement storage quotas. I suspect that user2 will try to upload a lot of stuff, and I only want to give that user 500mb of storage.  Is it possible? And if so, how do I do it?
[*]Do you see any obvious errors or things I could improve in this setup?
[*]I'm thinking about only allowing [COLOR="White"]SFTP but I learned that it's impossible so now I want to only allow[/COLOR] FTP over SSL connections. How do I add it to this configuration? (And should I?)
[*]I'm using the Berekely db and have imported my user names and passwords. What happens if I want to change one password or add/remove a user? (The link to more info on the Berkely db is broken at the vsftpd site in the EXAMPLES folder.) **[Possibly found a solution to this question, I'll come back with the answer. If you can't wait check my next post]**
[*]The install of vsftpd seems to have added the ftp user by itself? What password does it have? How can I be sure that the account is secure?
[/LIST]

---

### Post by nix4me on 2007-10-08
Did you consider using mysql for your virtual users?  This allows you to use phpmyadmin to admin the database. Here is a link to set this up:

[http://www.howtoforge.com/vsftpd_mysql_debian_etch](http://www.howtoforge.com/vsftpd_mysql_debian_etch)

It works great.

nix4me

---

### Post by kentl on 2007-10-08
I considered it, but it seemed kind of bloated to me. Using a plain text db like the Berkeley db will probably work quite well. In fact I might have found a possible solution to user management now at [http://viki.brainsware.org/?en/Virtual_Users_simple](http://viki.brainsware.org/?en/Virtual_Users_simple) , but I'll have to wait until tomorrow to try it.

---

### Post by MJN on 2007-10-09
> **kentl said:**
> 3. I'm thinking about only allowing SFTP connections. How do I add it to this configuration? (And should I?)
 
Short answer: You can't, and yes you should!
 
You are using VSFTPD which, despite how the name may sound, is not an SFTP server - it is a 'secure' FTP server which is a very different beast (insofar as FTP and SFTP are two different protocols).
 
You should indeed use something to encrypt your client connections otherwise all their credentials and data are travelling in the clear. If you wish to continue with VSFTPD then you will need to look at wrapping your FTP in an SSL/TLS tunnel (requiring server and client adjustments) however if you wish to use SFTP (hopefully only a server change depending on what (S)FTP client you're using) then you'll need to install an SFTP server (e.g that provided by openssh-server which you've already got installed).
 
This is overlapping with your other thread now so we must be careful to avoid duplication and confusion...
 
Mathew

---

### Post by kentl on 2007-10-09
Thanks for clarifying this! In this thread I continue the vsftpd branch of my thoughts. That way some people looking at vsftpd might get some help from this thread. I changed the first post to say FTP over SSL instead. If I can just get those quotas working I'll be satisfied.

---

### Post by kentl on 2007-10-09
I've decided to move to Pure-FTPd as it has virtual users with virtual quotas out of the box. I don't know how it will work out, but I have good faith in it so far.

By all means continue this thread. The above configuration of vsftpd works very well for virtual users without quotas. Perhaps it'll be of need to someone.

---

### Post by ruibernardo on 2007-11-06
Hi,

I just tried this instructions and they work very well. I had tried another thread about virtual users in vsftpd [here]("http://ubuntuforums.org/showpost.php?p=867795&postcount=9") (worked too) but this is much more clear. Thank you.

About the FTPS question with vsftpd it is easy to setup and it worked well with this setup. I just had to add this in the end of vsftpd.conf:

```


ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
listen_port=990

### The following lines are on the default vsftpd.conf in Ubuntu, 
### I've added it here for those who deleted it and started over.

# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```Sorry for this (late) reply. I hope it helps others.

---

### Post by kentl on 2007-11-06
I'm glad to hear that you liked my instructions, and thank you for adding the FTP over SSL/TLS instructions. :) Personally I'm happy with pure-ftpd as I got virtual quotas as well, which was important to me. Take care.

---

