---
title: "VSFTP &amp; sFTP - How to Enable?"
date: 2008-03-13
forum: Server Platforms
---

### Post by oxsyn on 2008-03-13
I've got vsFTP running on my Ubuntu server installation.  Users can log in  without a problem using their regular username & password over standard ftp protocol.

I read in another thread that in vsFTP, sFTP is enabled by default.

I attempted to connect (using SmartFTP) using my same username and password with SmartFTP's two sFTP protocol options: FTP over SSH Explicit & FTP over SSH Implicit.  On both counts I could not connect.

Explicit:
> [07:30:27] 220 Welcome to f4rr4r.dnsdojo.org FTP service.
[07:30:27] AUTH TLS
[07:30:27] 530 Please login with USER and PASS.
[07:30:27] Cannot login waiting to retry (30s)...


Implicit:
> [07:31:26] Connected to f4rr4r.dnsdojo.org.
[07:31:26] Connected. Exchanging encryption keys...
[07:31:26] SSL/TLS client handshake failed (Error = 0x80090308).
[07:31:26] Cannot login waiting to retry (30s)...

And normal FTP:
> [07:31:50] Connected to f4rr4r.dnsdojo.org.
[07:31:50] 220 Welcome to f4rr4r.dnsdojo.org FTP service.
[07:31:50] USER ****
[07:31:50] 331 Please specify the password.
[07:31:50] PASS (hidden)
[07:31:50] 230 Login successful.

Any suggestions?

---

### Post by SpaceTeddy on 2008-03-13
as far as i know, sftp is a submodule if the ssh-server, and not of vsFTP. but then i know close to nothing about vsFTP. 

maybe you need to install the openssh-server to be able to use that feature (heavy guessing here)...

---

