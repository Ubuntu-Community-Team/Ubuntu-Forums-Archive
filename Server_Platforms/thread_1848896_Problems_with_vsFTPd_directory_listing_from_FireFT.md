---
title: "Problems with vsFTPd directory listing from FireFTP"
date: 2011-09-23
forum: Server Platforms
---

### Post by niglas on 2011-09-23
FireFTP stalls on directory listing. What could be wrong?

It all works just fine without encrypted connection.
Since the server is not behind a firewall I used passive mode.
It also works fine with other clients than FireFTP.

This is what FireFTP tells me:
```
220 Welcome!
       AUTH TLS
234 Proceed with negotiation.
       PBSZ 0
200 PBSZ set to 0.
       USER user
331 Please specify the password.
       PASS (password not shown)
230 Login successful.
       FEAT
211-Features:
AUTH SSL
AUTH TLS
EPRT
EPSV
MDTM
PASV
PBSZ
PROT
REST STREAM
SIZE
TVFS
UTF8
211 End
       OPTS UTF8 ON
200 Always in UTF8 mode.
       PWD
257 "/"
       TYPE A
200 Switching to ASCII mode.
       PROT P
200 PROT now Private.
       PASV
227 Entering Passive Mode (111,222,333,444,185,31).
       LIST
150 Here comes the directory listing.
```This is my vsftpd.conf:
```
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome!
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd

ssl_enable=YES
rsa_cert_file=/etc/ssl/certs/cert.pem
force_local_logins_ssl=YES
force_local_data_ssl=NO
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
```

---

### Post by Lars Noodén on 2011-09-23
If you have OpenSSH already installed then you have SFTP installed already.  If so, give that a try and you might be able then to uninstall vsftp.

---

### Post by niglas on 2011-09-23
Yeah, I already have SFTP working, but I need FTPS too...

---

### Post by patryk77 on 2011-09-23
You need to specify your PASSIVE ports on the server, and make sure they are open/forwarded in the router/firewall.

[QUOTE=http://linux.web.cern.ch/linux/scientific4/docs/rhel-rg-en-4/s1-ftp-vsftpd-conf.html]pasv_max_port — Specifies the highest possible port sent to the FTP clients for passive mode connections. This setting is used to limit the port range so that firewall rules are easier to create.

The default value is 0, which does not limit the highest passive port range. The value must not exceed 65535.

pasv_min_port — Specifies the lowest possible port sent to the FTP clients for passive mode connections. This setting is used to limit the port range so that firewall rules are easier to create.

The default value is 0, which does not limit the lowest passive port range. The value must not be lower 1024.[/QUOTE]

---

### Post by niglas on 2011-09-23
Thanks for the answer. I tried specifying a pasv_min_port to 50000 and pasv_max_port to 50500, but unfortunately it didn't make any difference.

The server is directly connected to the internet, i e no NAT or (sw/hw) FW.

The fact that the server works with other clients than FireFTP in passive (and encrypted) mode makes me even more confused :S

---

### Post by patryk77 on 2011-09-23
Oops, sorry. I should read more before I post.

That definitely sounds like a problem with FireFTP rather than your server configuration. I guess you should use another client, and warn your users of potential problems with FireFTP.

If you really want to troubleshoot this further, you can try WireShark. Of course, you won't be able to read the commands as they are encrypted, but you should see a connection being opened to the port the server offers when asked to provide a passive connection:

[http://www.securitypronews.com/it/networksystems/spn-21-20030917UnderstandingtheFTPPORTCommand.html](http://www.securitypronews.com/it/networksystems/spn-21-20030917UnderstandingtheFTPPORTCommand.html)

---

