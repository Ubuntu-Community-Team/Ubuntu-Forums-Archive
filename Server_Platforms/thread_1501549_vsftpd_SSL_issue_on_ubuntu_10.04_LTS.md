---
title: "vsftpd SSL issue on ubuntu 10.04 LTS"
date: 2010-06-04
forum: Server Platforms
---

### Post by artooro on 2010-06-04
Hello all. 

I've setup a Ubuntu 10.04 instance on Amazon EC2, installed apache2, php, and vsftpd.

Will be using FTPS as I don't want users to have a shell.

So I set it all up and added these config lines:

```
ssl_enable=Yes

pasv_enable=YES
pasv_min_port=49400
pasv_max_port=49500

ca_certs_file=/path/to/ca
rsa_cert_file=/path/to/cert
rsa_private_key_file=/path/to/key

debug_ssl=yes

```

When I connect from an FTP client I see the SSL certificate just fine, but then I get a different error depending on which client I'm using.

On Transmit:
Error -157: invalid reply from server
and in the transcript log:
Could not read reply from control connection: Unknown error: 0.

On Cyberduck:
Unsupported record version Unknown-48.48.

And Filezilla on Ubuntu 10.04:
GnuTLS error -8: A record packet with illegal version was received.
Could not connect to server


Now I've enabled ssl debug as you can see from my config above, and here's what I see in vsftpd.log during a connection attempt:

```
Fri Jun  4 16:24:30 2010 [pid 2] CONNECT: Client "67.58.193.38"
Fri Jun  4 16:24:31 2010 [pid 2] DEBUG: Client "67.58.193.38", "SSL version: TLSv1/SSLv3, SSL cipher: DES-CBC3-SHA, not reused, no cert"
Fri Jun  4 16:24:31 2010 [pid 1] [arthur] OK LOGIN: Client "67.58.193.38"

```

I'm specifically concerned about the "SSL version: TLSv1/SSLv3, SSL cipher: DES-CBC3-SHA, not reused, no cert" part.

From what I can tell this means I have a problem with my SSL libraries on the server. But this is a fresh Ubuntu 10.04 install!

Does anyone per chance have any pointers on this?

Thanks.

---

### Post by artooro on 2010-06-04
And just some more information.

My FTP users have a shell of /usr/sbin/nologin and I've added that shell to /etc/shells

Those are the only modifications.

---

### Post by artooro on 2010-06-05
Here was my solution:

Uninstall vsftpd

Setup SSHD with SFTP using the ChrootDirectory functionality and /bin/false shell for a group called sftponly.

See: 
[http://www.minstrel.org.uk/papers/sftp/builtin/](http://www.minstrel.org.uk/papers/sftp/builtin/)

---

