---
title: "vsftp setup ubuntu server"
date: 2010-10-21
forum: Server Platforms
---

### Post by ChrisianJ on 2010-10-21
Hi,

I have had some trouble setting up my vsftpd server on my ubuntu vps. 

The ting is that I would like to access it from all browsers, but now i'm only able to access it from Chrome not IE. 

I would also like to map the ftp server in Windows 7, if that is possible. 

This is my vsftpd.conf file as it is now.
#
#
# No anonymous login
anonymous_enable=NO
# Let local users login
# If you connect from the internet with users, you should enable TLS/SSL/FTPS
local_enable=YES
# Write permissions
write_enable=YES
#All users are jailed by default

chroot_local_user=YES
chroot_list_enable=NO
chown_username=fejekosten
#chown_upload=YES

# run as standalone service
listen=YES

ascii_upload_enable=YES
ascii_download_enable=YES
pasv_enable=YES
pasv_promiscuous=NO

# ...
ftpd_banner=login til fejekosten ftp!
#
#
#


I've been trying for a couple of weeks to get is right os the file might have some lines that are not nesserary. 

I hope some one can help me set this up!

Kind regards Christian.

---

