---
title: "Problems configuring a vsftpd"
date: 2012-05-10
forum: Server Platforms
---

### Post by DiegoTc on 2012-05-10
Hi. I am having troubles when I try to upload o create a folder or file to login users. (Anonymous users can't access)

My configuration file is the following
```

# Run the server in standalone mode
listen=YES

# Allow anonymous FTP? This will enable/disable all subsequent anonymous options
anonymous_enable=NO

# Allow anonymous users to upload files?
anon_upload_enable=NO

# Allow anonymous users to create directories?
anon_mkdir_write_enable=NO

# Allow local users to log in? (Is needed even in case of a virtual setup)
local_enable=YES

# Restrict local users to their home directories
chroot_local_user=YES

# Specify a user token
user_sub_token=$USER

# Treat all non-anonymous logins as 'guest' logins
guest_enable=NO

# Specify a system user to map 'guest' logins
guest_username=vsftp

# Enable if virtual users shall use the same privileges as locals (default: NO)
virtual_use_local_privs=NO

# Hide user/group information of files and directories
hide_ids=YES

# Specify a directory to where users get chroote'd
local_root=/opt/VirtualMachines/SharedFolder/FTP

# Enable SSL, this will affect all subsequent ssl options
ssl_enable=NO

# Allow SSL for anonymous users
allow_anon_ssl=NO

# Enable to force all non-anonymous logins to use SSL in order to send and receive data
force_local_data_ssl=YES

# Enable to force all non-anonymous logins to use SSL in order to login
force_local_logins_ssl=YES

# Enable TLS v1 protocol connections
ssl_tlsv1=YES

# Enable SSL v2 protocol connections
ssl_sslv2=YES

# Enable SSL v3 protocol connections
ssl_sslv3=YES

# Specify a RSA certificate file to use for encrypted connections
#rsa_cert_file=/etc/vsftpd.d/vsftpd.pem

# Allow any form of write command?
write_enable=YES

# Enable directory messages
dirmessage_enable=YES

# Enable transfer logs, you can specify a log file and if the xferlog format shall be used
xferlog_enable=YES
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES

# Allow PORT transfer connections only from the following port (default: 20)
connect_from_port_20=YES

# Chown all created files to a specific username
chown_uploads=YES
chown_username=whoever

# When to time out an idle session? (default: 600)
#idle_session_timeout=600

# When to time out a data connection? (default: 120)
#data_connection_timeout=120

# Define a totally isolated and unprivileged user
#nopriv_user=ftpsecure

# Enable asynchronous ABOR requests for backwards compability of older clients
#async_abor_enable=YES

# Enable ASCII mangling to really happen
# Not recommended
#ascii_upload_enable=YES
#ascii_download_enable=YES

# Customize your banner
#ftpd_banner=Welcome to blah FTP service.

# Enable a anonymous e-mail blacklist
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails

# Specify a list of local users to chroot to their home directory.
# This options may become a list of users NOT to chroot if chroot_local_user is YES!
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list

# Enable recursive ls, may cause excessive I/O on large sites
# Not recommended
#ls_recurse_enable=YES

## Debian customization

# Specify an empty directory to chroot vsftpd at times it doesn't require filesystem access
secure_chroot_dir=/opt/VirtualMachines/SharedFolder/FTP

# Specify a PAM service name to use, see /etc/pam.d/ for pam services
pam_service_name=vsftpd

# Specify a RSA certificate to use for SSL encrypted connections
#rsa_cert_file=/etc/ssl/certs/vsftpd.pem


```

But I don't why it doesn't work. Login user can see the information and download it. But they can't upload it or create folders


Thanks for your time

---

