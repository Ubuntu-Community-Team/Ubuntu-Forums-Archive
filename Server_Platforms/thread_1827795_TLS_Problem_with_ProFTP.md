---
title: "TLS Problem with ProFTP"
date: 2011-08-18
forum: Server Platforms
---

### Post by The Foz on 2011-08-18
Maybe someone can help solve this problem.

I have been using proftp for about 8 months. After getting the configuration right, it worked perfectly. It is only used intermittently, so I don't know for sure when the problems started, but I suspect it was triggered by a recent OS upgrade to Ubuntu 10.04 (64 bit).

I have proftp set up so that TLS is required on both the data and control channels. The problem is that, after successful login, the server seems to be terminating the session because the client (FileZilla) is attempting to renegotiate something (probably the TLS). The client settings didn't change, nor did the server settings.

I have tried switching off the TLSRequired flag, and am then able to establish a non-secure FTP session which works (but that does not meet my requirements).

I wondered whether the OS upgrade had somehow invalidated my TLS certificates, but the symptoms don't seem consistent with that cause.

The TLS part of my proftpd.conf file is:
```
<IfModule mod_tls.c>
TLSEngine on
TLSRequired on
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/server.crt
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/server.key
TLSCACertificateFile /etc/gadmin-proftpd/certs/ca.crt
TLSRenegotiate required off
</IfModule>
```

The output from FileZilla is:
```
Status:	Resolving address of ftp.xxxxxxxx.com
Status:	Connecting to XX.XX.XX.XX:21...
Status:	Connection established, waiting for welcome message...
Response:	220 xxxxxxxx.com
Command:	AUTH TLS
Response:	234 AUTH TLS successful
Status:	Initializing TLS...
Status:	Verifying certificate...
Command:	USER xxxxxxxxxx
Status:	TLS/SSL connection established.
Response:	331 Password required for xxxxxxxxx
Command:	PASS ********
Response:	230 User xxxxxxxxx logged in
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 MDTM
Response:	 MFMT
Response:	 AUTH TLS
Response:	 UTF8
Response:	 LANG en-US.utf8*
Response:	 MFF modify;UNIX.group;UNIX.mode;
Response:	 MLST modify*;perm*;size*;type*;unique*;UNIX.group*;UNIX.mode*;UNIX.owner*;
Response:	 PBSZ
Response:	 PROT
Response:	 REST STREAM
Response:	 SIZE
Response:	211 End
Command:	OPTS UTF8 ON
Response:	200 UTF8 set to on
Command:	PBSZ 0
Response:	200 PBSZ 0 successful
Command:	PROT P
Response:	200 Protection set to Private
Status:	Connected
Status:	Retrieving directory listing...
Command:	CWD /home/xxxxxxxxxxx
Response:	250 CWD command successful
Command:	PWD
Response:	257 "/home/xxxxxxxxxxx" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (46,128,253,207,255,204).
Command:	MLSD
Response:	150 Opening ASCII mode data connection for MLSD
Error:	Connection closed by server
Error:	Failed to retrieve directory listing
```

proftpd_tls.log shows:
```
Aug 18 13:45:51 mod_tls/2.2.2[11077]: TLS/TLS-C requested, starting TLS handshake
Aug 18 13:45:52 mod_tls/2.2.2[11077]: TLSv1/SSLv3 connection accepted, using cipher DHE-RSA-AES128-SHA (128 bits)
Aug 18 13:45:52 mod_tls/2.2.2[11077]: Protection set to Private
Aug 18 13:45:52 mod_tls/2.2.2[11077]: starting TLS negotiation on data connection
Aug 18 13:45:52 mod_tls/2.2.2[11077]: warning: client-initiated session renegotiation detected, aborting connection

```

and /var/log/secure shows:
```
Aug 18 13:45:51 server1 proftpd[11077] server1 (::ffff:XX.XX.XX.XX[::ffff:XX.XX.XX.XX[]): FTP session opened.
Aug 18 13:45:52 server1 proftpd[11077] server1 (::ffff:XX.XX.XX.XX[[::ffff:XX.XX.XX.XX[]): USER xxxxxx: Login successful.
Aug 18 13:45:52 server1 proftpd[11077] server1 (::ffff:XX.XX.XX.XX[[::ffff:XX.XX.XX.XX[]): mod_tls/2.2.2: client-initiated session renegotiation detected, aborting connection
Aug 18 13:45:52 server1 proftpd[11077] server1 (::ffff:XX.XX.XX.XX[[::ffff:XX.XX.XX.XX[]): FTP session closed.

```

Anyone have any ideas?

---

### Post by Sanados on 2011-08-22
proftpd(1.3.0) seems to have a bug in connection over TLS ... try use sources

---

### Post by Sanados on 2011-08-22
though first try to add 

TLSOptions AllowClientRenegotiations


in 

<IfModule mod_tls.c>

---

### Post by The Foz on 2011-08-25
HI Sanados,

Your suggestion worked. Thanks.

I noticed that, in the documentation for proftp, this option is not recommended, due to the risk of a TLS Renegotiation Attack.

It would therefore be nice if there were a safer solution.

---

### Post by gecka on 2011-08-31
Couldn't it be a client side issue? 

I mean proftp disables client regotations because of that security issue. 

But that is _your_ ftp client that asks for a regotiation on a TLS connection which it shouldn't do.

---

### Post by The Foz on 2011-09-01
Hi gecka,

I thought of that.

I am using FileZilla as the client. I looked all through the settings, and couldn't find a way to stop TLS renegotiation requests.

If anyone knows how to disable TLS renegotiation requests, the information would be much appreciated.

---

