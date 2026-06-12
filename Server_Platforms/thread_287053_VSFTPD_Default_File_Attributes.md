---
title: "VSFTPD Default File Attributes"
date: 2006-10-28
forum: Server Platforms
---

### Post by ztrek7 on 2006-10-28
I have installed vsftpd via apt-get. Installed fine. I enable local users and disabled anonymous. Created dir /var/www/home and created user homeweb with home dir of /var/www/home. I also chown dir to homeweb.

Problem? When I try to upload a file to overwrite something, it just doesn't do it, no error (at least with filezilla client). If I delete file, then upload, its permissions are 600, with these permissions, apache cannot read the file to serve, so I have to change the permissions manually. What's the fix? Below is my conf file.

# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES

# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES

# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO

# Uncomment this to allow local users to log in.
local_enable=YES

# Uncomment this to enable any form of FTP write command.
write_enable=YES

# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=0022
#file_open_mode=0777

# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES

# Activate logging of uploads/downloads.
xferlog_enable=YES

# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES

# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

---

### Post by ztrek7 on 2006-10-28
UPDATE:

It seems that it was the FTP client (filezilla), i don't know what part, but uncommented out the umask (I had it uncommented before and it did not work) and tried different ftp client (windows and coffeecup) and it works fine.

So this thread is not a complete waste, the above conf file (uncomment the umask line) provides a ftp server that denies anonymous log in and let's local users log on to their home directory.

---

### Post by [bigmac] on 2006-11-07
Thanks, I could use that config, so no it wasn't a waste. I assume its 100% secure?

Best regards.

---

