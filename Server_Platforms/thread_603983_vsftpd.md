---
title: "vsftpd"
date: 2007-11-05
forum: Server Platforms
---

### Post by r0ot5 on 2007-11-05
Hi, i'm new to your community and I found a lot of good tutorial but i'm stock on this one: I'm installing vsftpd on my Ubuntu 7.04 installation. Installation is ok, i've created users and they can access the FTP without any problem but here the part I dont understand, I have created an upload folder under the /home/ftp, everyone can upload in this folder but when I access my server (desktop) and browse this folder I cannot delete anything, only the user who created the folder can delete it, is there a way to fix that?


thx all for your time, 

r0ot5

---

### Post by civic_si on 2007-11-05
in the vsftpd.conf file there is a section where you can use the chown command to change the owner of the file uploaded. you can set this up to point to a user that you like and there is also a umask section that you can set the permissions for those files.

for chown look for 
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever

for umask look for
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022

I hope this is what you are looking for.

---

### Post by r0ot5 on 2007-11-06
I just try that and it dosent work. is this only for anonymous users or users that has account created? on my FTP anonymous is disable!

---

