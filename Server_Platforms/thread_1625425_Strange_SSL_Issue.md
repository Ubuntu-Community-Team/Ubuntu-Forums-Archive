---
title: "Strange SSL Issue"
date: 2010-11-19
forum: Server Platforms
---

### Post by mrmark on 2010-11-19
I have just moved a website from one server to another and am now having SSL issues.

The SSL certificate installed ok and works when I access my virtualmin control panel (which doesn't use apache)

When I access https on the shared IP ([https://ppcnseo.com](https://ppcnseo.com)) I get the error below in chrome, while Safari tries to download a page.
The only certificate on this IP is issued to ppcnseo.com and has some other domains as SAN

> SSL connection error.

Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.

When I try and access a site on a private IP on this server ([https://www2.thelondonminibuscompany.com](https://www2.thelondonminibuscompany.com)) I get a name mismatch (expected, this is the backup server) and then the file is downloaded instead of displayed.

A check on ppcnseo at digicert.com/help implies that apache is not serving a certificate at all.
> Output from 'openssl s_client' command:
CONNECTED(00000003) --- no peer certificate available --- No client certificate CA names sent --- SSL handshake has read 7 bytes and written 211 bytes --- New, (NONE), Cipher is (NONE) Secure Renegotiation IS NOT supported Compression: NONE Expansion: NONE ---

Running a test locally displays the following
> #openssl s_client -connect localhost:443 -debug -state
CONNECTED(00000003)
SSL_connect:before/connect initialization
write to 0x1a39300 [0x1a3aa00] (121 bytes => 121 (0x79))
0000 - 80 77 01 03 01 00 4e 00-00 00 20 00 00 39 00 00   .w....N... ..9..
0010 - 38 00 00 35 00 00 16 00-00 13 00 00 0a 07 00 c0   8..5............
0020 - 00 00 33 00 00 32 00 00-2f 03 00 80 00 00 05 00   ..3..2../.......
0030 - 00 04 01 00 80 00 00 15-00 00 12 00 00 09 06 00   ................
0040 - 40 00 00 14 00 00 11 00-00 08 00 00 06 04 00 80   @...............
0050 - 00 00 03 02 00 80 00 00-ff eb 5f d4 1b 4e 60 38   .........._..N`8
0060 - b4 c9 f3 e8 a1 15 9e d1-32 2b e8 1c e6 d2 ef f9   ........2+......
0070 - a0 bd b7 3e e8 58 b8 d1-1a                        ...>.X...
SSL_connect:SSLv2/v3 write client hello A
read from 0x1a39300 [0x1a3ff60] (7 bytes => 7 (0x7))
0000 - 3c 21 44 4f 43 54 59                              <!DOCTY
SSL_connect:error in SSLv2/v3 read server hello A
23073:error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol:s23_clnt.c:601:


The only SSL related error in my apache error.log is below
> [Fri Nov 19 08:11:07 2010] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Fri Nov 19 08:11:07 2010] [notice] Apache/2.2.14 (Ubuntu) DAV/2 SVN/1.6.6 mod_fastcgi/2.4.6 mod_fcgid/2.3.4 mod_ruby/1.2.6 Ruby/1.8.7(2010-01-10) mod_ssl/2.2.14 OpenSSL/0.9.8k mod_perl/2.0.4 Perl/v5.10.1 configured -- resuming normal operations

Any ideas?

---

### Post by SeijiSensei on 2010-11-19
> [Fri Nov 19 08:11:07 2010] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)

How are the virtual hosts defined?  In the past, you needed to have each secure host on a separate IP address.  (Apparently RFC 4366 might change that; haven't looked into it yet, but support for it sounds browser-specific.)  I presume the certificates match the server's fully-qualified domain name, or you're using a wildcard cert.

---

