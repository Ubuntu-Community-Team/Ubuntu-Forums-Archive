---
title: "FTP directory is open???"
date: 2010-04-13
forum: Security
---

### Post by extacy1 on 2010-04-13
Hey all
I have question if you dont mind me ask.
I have apache, ftp and mysql installed in our server and they all working fine
however I have a security problem.
lets say you have ftp server name called linuxftp. com
and
when you type http: //linuxftp. com , page is opening and asking for user and password which has been created before by admin
so far that is controlled by apache and mysql I guess.
if user enters right password, new page opening for user and user getting able to download or upload data to server.This can be either and ftp software or directly browser.
that is working fine so far

however, if I type http: //linuxftp. com /ftp/ , without any user and password,
I am seeing all others user contents which is basically I am seeing var/www/ftp directory.

                                                                         
                                                                                    I think I am missing somethings.
 Do you guys have any idea about that?
 all suggestions are more than welcome.
 please kindly let me know, if you have any questions about the architecture
thank you in advance

---

### Post by cdenley on 2010-04-13
So apache's root directory is /var/www. What is the root directory for FTP? Which FTP server are you using? How is it configured? How did you configure apache? How did you require authentication? What directory should users be able to download from? What directory should users be able to upload to? Should they be able to download files uploaded by other users?

---

### Post by extacy1 on 2010-04-13
firstly thank you for reply.
let me answer your questions as much as I can.
ftp root directory =/var/www/ftp/$user
ftp server =vsftpd
vsftpd.conf ```
 chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
pam_service_name=vsftpd
#userlist_enable=YES
#enable for standalone mode
listen=YES
#tcp_wrappers=YES
user_sub_token=$USER
local_root=/var/www/ftp/$USER
virtual_use_local_privs=YES
user_config_dir=/etc/vsftpd/vsftpd_user_conf
```authentication= there is database in mysql which holds user and pass,after typing user and password to php web page,it is checking with the mysql database and if it matches user can login otherwise he cant.

user directory=as soon as user logs in, it is directed to its own named subfolder in var/www/ftp/~
user can only upload and download to its own space in server,no interactions between users.

any ideas?
I appreciate

---

### Post by cdenley on 2010-04-13
> **extacy1 said:**
> 
any ideas?

To accomplish what exactly? Are you trying to make it so if they login as user1, they can download from /var/www/ftp/user1 but not /var/www/ftp/user2? Or should /var/www/ftp not be accessible via apache?

---

### Post by extacy1 on 2010-04-13
thats correct user 1 can only download from /var/www/ftp/user1 
and user 2 can only download from /var/www/ftp/user2 and user 3 so on...
system is working great actually
but  I realize there is a security lack, when I type http: //ipaddress/ftp/ apache is showing all Index of /ftp which means all the user1/user2/user3/... folders and data inside.
we do not want a file publically accesible like that right.
any idea?
thanks

---

### Post by cdenley on 2010-04-13
Well, since you're authenticating with PHP, you would need to restrict access with PHP as well. Either move that directory outside of /var/www, or configure apache to disallow all access to that directory. Then you would need to write a PHP script to browse directories and download files if they are authenticated as the appropriate user.

Another option would be to use built-in apache authentication, but I think you would have to configure each inidividual user directory. I don't know of any apache authentication module managing access based on ownership or a directory name matching the user's.

---

### Post by extacy1 on 2010-04-14
thank you
problem was with apache disabling directory listing/browsing
httpd.conf
To disable directory listing
Options Indexes FollowSymLinks
I just removed ‘Indexes’ from the line.
I appreciate for your replies guys

---

### Post by cdenley on 2010-04-14
> **extacy1 said:**
> thank you
problem was with apache disabling directory listing/browsing
httpd.conf
To disable directory listing
Options Indexes FollowSymLinks
I just removed ‘Indexes’ from the line.
I appreciate for your replies guys

That will disable the listing of directories, but not the downloading of content. If they know or can guess the URL's of files, they can download them. Something like this would completely disable access:
```

<Directory "/var/www/ftp/">
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>

```
Then you would have to create a php script outside that directory to retrieve the file if the user is permitted to.

By the way, you shouldn't be using httpd.conf. That type of configuration belongs in /etc/apache2/sites-available/default, or another site configuration in the same directory.

---

