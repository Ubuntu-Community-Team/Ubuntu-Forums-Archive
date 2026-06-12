---
title: "Cant login  to ftp as virtual user"
date: 2011-07-07
forum: Server Platforms
---

### Post by Genta on 2011-07-07
I have created virtual user with following Steps
but still i cant login.



1)To create a `db’ format file, first create a plain text file  `virtual-users.txt’ with the usernames and passwords on alternating  lines:[INDENT]mary
123456
jack
654321
[/INDENT]Then execute the following command to create the actual database:[INDENT]# db_load -T -t hash -f virtual-users.txt /etc/vsftpd/virtual-users.db
[/INDENT]2)Now, create a PAM file /etc/pam.d/vsftpd-virtual which uses your database:[INDENT]auth required pam_userdb.so db=/etc/vsftpd/virtual-users
account required pam_userdb.so db=/etc/vsftpd/virtual-users
[/INDENT]**3. Configuration of VSFTPD**
 Create a configuration file /etc/vsftpd/vsftpd-virtual.conf,[INDENT]# disables anonymous FTP
anonymous_enable=NO
# enables non-anonymous FTP
local_enable=YES
# activates virtual users
guest_enable=YES
# virtual users to use local privs, not anon privs
virtual_use_local_privs=YES
# enables uploads and new directories
write_enable=YES
# the PAM file used by authentication of virtual uses
pam_service_name=vsftpd-virtual
# in conjunction with 'local_root',
# specifies a [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important]home [/FONT][/FONT][/COLOR][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important]directory[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://linuxforfun.net/2008/04/05/vsftpd-virtual-users/#") for each virtual user
user_sub_token=$USER
local_root=/var/www/virtual/$USER
# the virtual user is restricted to the virtual FTP area
chroot_local_user=YES
# hides the FTP server user IDs and just display "ftp" in directory listings
hide_ids=YES
# runs vsftpd in standalone mode
listen=YES
# listens on this port for incoming FTP connections
listen_port=60021
# the minimum port to allocate for PASV style data connections
pasv_min_port=62222
# the maximum port to allocate for PASV style data connections
pasv_max_port=63333
# controls whether PORT style data connections use port 20 (ftp-data)
connect_from_port_20=YES
# the umask for file creation
local_umask=022
[/INDENT]**4. Creation of home directories**
 Create each user’s home directory in /var/www/virtual, and change the owner of the directory to the user `ftp’:[INDENT]# mkdir /var/www/virtual/mary
# [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important]chown[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://linuxforfun.net/2008/04/05/vsftpd-virtual-users/#") ftp:ftp /var/www/virtual/mary
[/INDENT]**5. Startup of VSFTPD and test**
Now we can start VSFTPD by the command:[INDENT]# /usr/sbin/vsftpd /etc/vsftpd/vsftpd-virtual.conf
[/INDENT]and test the FTP access of a virtual user:[INDENT]# lftp -u mary -p 60021 192.168.1.101
[/INDENT]The virtual user should have full access to his directory.

---

