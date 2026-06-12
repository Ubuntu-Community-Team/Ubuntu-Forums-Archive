---
title: "vsftpd + ssl having connection issues"
date: 2012-10-17
forum: Server Platforms
---

### Post by LHammonds on 2012-10-17
I recently setup a new dedicated Ubuntu Server 12.04.1 (64-bit) server for vsftpd (2.3.5-1) + SSL.

Once I finished configuring it to require SSL, I tested it from another Ubuntu Server using ssl-ftp and it worked.  I could list the contents and it showed the text file I placed there earlier.

I then passed it off to my network guy to map an external IP/port to the internal IP/port and he added the correct rule to the hardware firewall.

Upon testing, he could not get a Windows FTP client to connect.  He tried to connect to the internal IP before going through the external.  After going through about 4 different client programs, he found one that worked (SmartFTP) and was able to connect quick-n-easy.

But after he tried to upload a test file, it failed due to insufficient write permissions.

I changed the home folder to have full write permissions on the folder.  He then could not get re-connected.  I then connected from my Ubuntu Server using ssl-ftp and was then greeted with the following error message:

```

ftp-ssl 192.168.107.1 990
Connected to 192.168.107.1.
220 Welcome to Company ABC FTP server.
Name (192.168.107.1:administrator): myftpuserid
234 Proceed with negotiation.
[SSL Cipher DES-CBC3-SHA]
331 Please specify the password.
Password:
ssl_getc: SSL_read failed -1 = 0
421 Service not available, remote server has closed connection
Login failed.
No control connection for command: Success

```I figured the change to the home folder permissions is what made it mad so I changed it back to the way it was and restarted vsftpd

It did not fix the problem.

Anyone have any ideas why it would be working (somewhat) and then refuse to login?

Thanks,
LHammonds

---

### Post by LHammonds on 2012-10-17
Here are the steps I used to install vsftpd:

Install a base copy of [Ubuntu Server 12.04]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=191")

Install vsftpd and make a backup of the original config file.
```

aptitude install vsftpd
cp /etc/vsftpd.conf /etc/vsftpd.bak

```Add the following line to /etc/shells (* This allows users to login via FTP which cannot login directly on the server *)
```

/usr/sbin/nologin

```Generate an SSL certificate.
```

openssl req -x509 -nodes -days 730 -newkey rsa:1024 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem
chown root:ftp /etc/ssl/private/vsftpd.pem
chmod 644 /etc/ssl/private/vsftpd.pem

```Edit /etc/vsftpd.conf and find/uncomment following lines:
```

local_enable=YES
write_enable=YES
local_umask=022
ftpd_banner=Welcome to our FTP server.
chroot_local_user=YES

```Find the following existing lines and change the values as follows:
```

anonymous_enable=NO
connect_from_port_20=NO
rsa_cert_file=/etc/ssl/private/vsftpd.pem

```Add the following new lines:
```

listen_port=990

# Turn on SSL
ssl_enable=YES

# Allow anonymous users to use secured SSL connections
allow_anon_ssl=NO

# All non-anonymous logins are forced to use a secure SSL connection in order to
# send and receive data on data connections.
force_local_data_ssl=YES

# All non-anonymous logins are forced to use a secure SSL connection in order to send the password.
force_local_logins_ssl=YES

# Permit TLS v1 protocol connections. TLS v1 connections are preferred
ssl_tlsv1=YES

# Permit SSL v2 protocol connections. TLS v1 connections are preferred
ssl_sslv2=YES

# permit SSL v3 protocol connections. TLS v1 connections are preferred
ssl_sslv3=YES

# Hide the info about the owner (user and group) of the files.
hide_ids=YES

# Connection limit for each IP:
max_per_ip=10

# Maximum number of clients:
max_clients=10

```Use the default ftp folder of /srv/ftp but move the default "ftp" user's home directory underneath that folder.  This will be become the base folder for all FTP users but nobody will be able to access it directly.

```

mkdir -p /srv/ftp/ftp
usermod -d /srv/ftp/ftp ftp
chmod a-w /srv/ftp

```Add an ftpusers group.
```

addgroup ftpusers

```Now add a user called "myftp" with a password of "mypass123"
```

mkdir -p /srv/ftp/myftp
useradd -g ftpusers -d /srv/ftp/myftp -s /usr/sbin/nologin myftp
 chown myftp:ftpusers /srv/ftp/myftp
passwd myftp

```Now restart the service and make sure it is running:
```

service vsftpd stop
service vsftpd start
service vsftpd status

```To test this out from another server, login to another server and type the following:
```

aptitude install ftp-ssl
ftp-ssl 192.168.107.1 990

```

---

### Post by LHammonds on 2012-10-18
Checked to see if PAM is being used:
```
ldd /usr/sbin/vsftpd
```I can see the libpam being linked to it so PAM is being used.
```
libpam.so.0 => /lib/x86_64-linux-gnu/libpam.so.0 (0x00007f29c2939000)
```There is also a vsftpd file for PAM located here: /etc/pam.d/vsftpd
```

# Standard behaviour for ftpd(8).
auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own. Do not enable pam_ftp.so.

# Standard pam includes
@include common-account
@include common-session
@include common-auth
auth    required        pam_shells.so
```When creating FTP users, their shell points to /usr/sbin/nologin and I have this added to /etc/shells.  Here is what the entry looks like in /etc/passwd:
```
myftp:x:1002:1002::/srv/ftp/myftp:/usr/sbin/nologin
```Looking in /etc/ftpusers, my ftp user accounts are not listed in there which means PAM is not blacklisting their login ability.

I'm still scratching my head wondering what silly mistake I am making.

**EDIT:** I re-install the OS from scratch, made sure apparmor was removed, installed vsftpd, added an FTP user and still get the same error message.

Also try connection from the local machine and got the same message: **ftp-ssl localhost 990**

LHammonds

---

### Post by LHammonds on 2012-10-18
I figured it out.  I had to disable the SSL options in order to see more helpful error messages.

The FTP server refuses to let you login "if" you have chroot enabled AND you have "write" permission on the users home directory (/srv/ftp/myftp).

Turning off write access allows you to login, BUT you cannot upload any files...because you don't have write access!  The solution was to create a sub-folder (such as "public") and grant write access to that.  When logging in, you have to change to the public directory in order to upload the files.

Wow, this was fun.

I'll be sure to create a how-to thread with the exact steps for creating this server (very similar to the above...but done correctly)

```

mkdir -p /srv/ftp/myftp/public
chmod 555 /srv/ftp/myftp
chmod 755 /srv/ftp/myftp/public
useradd -g ftpusers -d /srv/ftp/myftp -s /usr/sbin/nologin myftp
chown -R myftp:ftpusers /srv/ftp/myftp
passwd myftp

```LHammonds

---

### Post by sptica on 2013-01-23
> **LHammonds said:**
> I figured it out.  I had to disable the SSL options in order to see more helpful error messages.

The FTP server refuses to let you login "if" you have chroot enabled AND you have "write" permission on the users home directory (/srv/ftp/myftp).

Turning off write access allows you to login, BUT you cannot upload any files...because you don't have write access!  The solution was to create a sub-folder (such as "public") and grant write access to that.  When logging in, you have to change to the public directory in order to upload the files.


Thanks a lot!

---

