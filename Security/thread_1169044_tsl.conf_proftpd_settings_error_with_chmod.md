---
title: "tsl.conf proftpd settings error with chmod"
date: 2009-05-24
forum: Security
---

### Post by GnubbyaBush on 2009-05-24
Hey all, I'm trying to set up ftps on my standalon ftp (proftpd) server. My tls.conf file is erroring at the following code 

# The proftpd.key file must be readable by root only. The other file can be
# readable by anyone.
#
 chmod 0600 /etc/ssl/private/proftpd.key 
 chmod 0640 /etc/ssl/private/proftpd.key

I added this corresponding code to my proftpd.conf
# This is used for FTPS connections
#
Include /etc/proftpd/tls.conf

<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired off

    # Server's certificate
    TLSRSACertificateFile /etc/ssl/certs/proftpd.crt
    TLSRSACertificateKeyFile /etc/ssl/private/proftpd.key

    # CA the server trusts
    TLSCACertificateFile /etc/ssl/certs/CA.pem

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>

the error is most deffidently in my tls.conf, all the files (certificates and such) point to files that exist, (i can't get into the etc/ssl/private folder though). anyone know how to fix the chmod fatal error?
attached is the whole tls.conf file.

---

