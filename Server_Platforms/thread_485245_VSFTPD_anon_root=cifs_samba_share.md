---
title: "VSFTPD anon_root=cifs samba share"
date: 2007-06-26
forum: Server Platforms
---

### Post by lewman on 2007-06-26
I am trying to get VSFTPD to work with a share that resides on a Windows 2003 server.  The share is mounted fine and I can aceess it from any user.  I tried setting anon_root=/home/ftp/rapport which was were I mounted the windows share but even though the files were browseable when I tried to download them I got 0 byte files and this error on the server  [ftp] FAIL DOWNLOAD: Client "10.1.1.161", "/rapport/cenac/wyse/wnos/RCA_wnos", 0.00Kbyte/sec.  If I actually copy all of the data from the windows share to the anon_root then all works fine.  I then tried just mounting the share in a local user folder and I cant even see the cifs mounted share.  Here are my configs

vsftpd -v
vsftpd: version 2.0.5

vsftpd.conf
listen=YES
anonymous_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=NO
pasv_promiscuous=YES
pasv_address=10.1.1.8
pasv_min_port=64000
pasv_max_port=65535
#anon_root=/home/ftp/rapport
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
anon_world_readable_only=NO
download_enable=YES
local_enable=YES
# Debian customization
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


cat /etc/fstab
//ccirc/CC-Rapport    /home/ltaylor/rapport        cifs    credentials=/root/.smbcredentials,ro,uid=ltaylor,gid=ltaylor,file_mode=0755,dir_mode=0755 0 0

---

### Post by lewman on 2007-06-27
No one has any clues on this one????

---

### Post by lewman on 2007-06-28
I found the answer finally.

This was fixed in all VSFTPD versions after 1.1.3. There is a
config workaround
use_sendfile=NO

---

