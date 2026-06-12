---
title: "Pure-ftpd TLS = 3 &amp; filezilla not working"
date: 2009-12-07
forum: Server Platforms
---

### Post by emma_peel on 2009-12-07
Hello.
 

 I have noticed that the higher option of SSL/TLSencryption  in pure-ftpd is not supported by filezilla. To be honest, I don't even see what this action is supposed to do :
 

 [quote=pure-ftpd Documentation]- With "--tls=2", cleartext sessions are refused and only SSL/TLS compatible clients are accepted.
- With "--tls=3", cleartext sessions are refused and only SSL/TLS compatible  clients are accepted. Clear data connections are also refused, so private  data connections are enforced. This is an extreme setting.[/quote]  ([http://download.pureftpd.org/pub/pure-ftpd/doc/README.TLS](http://download.pureftpd.org/pub/pure-ftpd/doc/README.TLS))
 

 Does anybody know what this option is supposed to do ? Has it been successfully tester with another FTP client ?
 

 Thank you for your feedback.

---

### Post by mtron on 2009-12-08
well i dunno how much you know about ftp connections so i over - simplify it ;)

In FTP there are min. 2 Channels used, first one is the "Connection" channel on port 21. this channel is for "talking" (sending commands) to the server. E.g. list directories, exchange passwords, put file on server ect. This channel was always encrypted by pure-ftp with the tls = 3 option.

Now since version 1.0.22 pure-ftpd also supports encryption of the data channel[1] . The data channel is in the passive port range you configured and is used to pipe the actual data (files) from the client to the server or from the server to the client. 

So if you configure this (tls=3) you basically get a fully encrypted ftp server that won't allow unencrypted connections. The client that wants to connect to the server needs it's certificate in place before it's able to establish a connection.

A Client that supports TLS encryption and runs on all platforms is e.g. the fireftp addon for firefox[2]. I dunno if you can configure filezilla for it.

I use this ftp server on all of the server i manage (get the latest pure-ftp Version 1.0.27 from their website[3], because it got many bugfixes compared with the old version in the ubuntu repositories) 

Don't forget to use it in conjunction with fail2ban[4] to block automated script attacks. If you use TLS=3 the needed fail2ban filter for pure-ftpd is:
```

# Fail2Ban configuration file
#
# Author: Cyril Jaquier
# Modified: Yaroslav Halchenko for pure-ftpd
#
# $Revision: 3$
#

[Definition]

# Error message specified in multiple languages
__errmsg = (?:Authentication failed for user|Erreur d'authentification pour l'utilisateur)

#
# Option: failregex
# Notes.: regex to match the password failures messages in the logfile. The
#         host must be matched by a group named "host". The tag "<HOST>" can
#         be used for standard IP/hostname matching and is only an alias for
#         (?:::f{4,6}:)?(?P<host>\S+)
# Values: TEXT
#
failregex = .*pure-ftpd: \(.*@<HOST>\) \[WARNING\] Sorry, cleartext sessions are not accepted on this server.*


# Option:  ignoreregex
# Notes.:  regex to ignore. If this regex matches, the line is ignored.
# Values:  TEXT
#
ignoreregex =   
```

[1] [http://download.pureftpd.org/pub/pure-ftpd/doc/README.TLS](http://download.pureftpd.org/pub/pure-ftpd/doc/README.TLS)
[2] [https://addons.mozilla.org/en-US/firefox/addon/684](https://addons.mozilla.org/en-US/firefox/addon/684)
[3] [http://download.pureftpd.org/pub/pure-ftpd/releases/pure-ftpd-1.0.27.tar.gz](http://download.pureftpd.org/pub/pure-ftpd/releases/pure-ftpd-1.0.27.tar.gz)
[4] [http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)

---

### Post by emma_peel on 2009-12-14
Hello mtron.

Thank you for the explaination, that's clear.

I will try with fireftp and read carefully the documentation of filezilla, as I cannot imagine that this software could not handle it.

I have also discovered that filezilla does not support IPv6. :(

Arnaud

---

### Post by mtron on 2009-12-14
ok, good to know ;)

I've tried the filezilla Client just now and had no problems connecting to a pure-ftpd server in TLS only mode.

Only gotcha is:
> FTPS (SSL/TLS) is served up in two incompatible modes. If using explicit FTPS, the client connects to the normal FTP port and explicitly switches into secure (SSL/TLS) mode with "AUTH TLS", whereas implicit FTPS is an older style service that assumes SSL/TLS mode right from the start of the connection (and normally listens on TCP port 990, rather than 21). In a FileZilla client this means prefixing the host with "FTPES://" to connect an "explicit" FTPS server, or "FTPS://" for the legacy "implicit" server (for which you will likely also need to set the port to 990). 

So since i use explicit TLS Mode the host line in Filezilla should be in the syntax:
```
ftpes://<FTPSERVERIP> 
```

---

### Post by Lars Noodén on 2009-12-14
> **emma_peel said:**
> Hello.

 I have noticed that the higher option of SSL/TLSencryption  in pure-ftpd is not supported by filezilla.

If a pain-free, secure method of transfering files using Filezilla is what you are after, then look at using SFTP instead of trying to tack SSL onto FTP.  SFTP is built into [OpenSSH server](http://packages.ubuntu.com/karmic/openssh-server) and works out of the box securely with Filezilla.  

It is also very easy to do fine-tuning like chroot various groups of users.

---

### Post by emma_peel on 2009-12-21
Thanks Lars.

I will try SFTP also, but I would say that I really appreciate the "fortune" option of pure-ftp :

[QUOTE=doc pure-ftpd]- '-F <fortune file>': Display a fortune cookie on login. The sentence is
a random extract from the text file <fortune file>. This text file should be
formatted like standard "fortune" files (fortunes are separated by a '%'
sign on a single line) . Pure-FTPd has to be compiled with support for
cookies (--with-cookie). If you just want a simple banner displayed before
the login prompt, add the name of any text file here.[/QUOTE]

Anyway, I have changed the TLS option to 3 and it is now working, even without adding ftpes in front of the host name.

Thanks you for the support !

---

