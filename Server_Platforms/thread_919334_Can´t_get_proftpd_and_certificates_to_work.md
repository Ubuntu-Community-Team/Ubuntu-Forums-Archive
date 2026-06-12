---
title: "Can´t get proftpd and certificates to work"
date: 2008-09-13
forum: Server Platforms
---

### Post by Jisstus on 2008-09-13
I have installed Ubuntu 8.04 server and tried to get proftpd and ssl/tls encryption to work. I followed a guide that I found in this forum to create my cert files and added a section in my proftpd.conf. I restarted proftpd but when I try to connect to the ftp I can connect without using encryption and when I try using encryption I get an error message (don´t have access to the server right now :( )

Should I use tls.conf for the ssl/tls information or does it still work when I put it in proftpd.conf?


This is the guide I used

Create your cert file like this:

First: Make a dir for it:
mkdir /etc/proftpd/ssl

Next: Make a cert file:
openssl req -new -x509 -days 365 -nodes -out /etc/proftpd/ssl/proftpd.cert.pem -keyout /etc/proftpd/ssl/proftpd.key.pem

Next: Change proftpd config file options for TLS to this:
<IfModule mod_tls.c>
TLSEngine on
TLSLog /var/log/proftpd/tls.log
TLSProtocol SSLv23
TLSOptions NoCertRequest
TLSRSACertificateFile /etc/proftpd/ssl/proftpd.cert.pem
TLSRSACertificateKeyFile /etc/proftpd/ssl/proftpd.key.pem
TLSVerifyClient off
TLSRequired off
</IfModule>

This will allow both encrypted and non-encrypted connections. If you want only encrypted, then change TLSRequired to on.


This is my proftpd.conf

ServerName                      "xxxxxx"
ServerType                      standalone
DefaultServer                   on
Port                            21
PassivePorts                    60000 60100
MasqueradeAddress               xxxxxx.mine.nu
DefaultRoot                     /var/tmp (just a test folder)
AllowOverwrite                  on
UseFtpUsers                     on
User                            proftpd
Group                           nogroup
Umask                           022  022

UseReverseDNS                   off
IdentLookups                    off

MaxInstances                    4
MaxLoginAttempts                2
TimeoutIdle                     600
TimeoutNoTransfer               0
TimeoutStalled                  0

<Global>
  RootLogin                     off
  RequireValidShell             off
  AuthUserFile                  /etc/passwd
  AllowStoreRestart             on
</Global>

<Limit SITE_CHMOD>
  DenyAll
</Limit>

<IfModule mod_tls.c>
  TLSEngine                     on
  TLSProtocol                   SSLv23
  TLSRequired                   on
  TLSVerifyClient               off
  TLSOptions 			NoCertRequest
  TLSRSACertificateFile         /etc/proftpd/ssl/proftpd.cert.pem
  TLSRSACertificateKeyFile      /etc/proftpd/ssl/proftpd.key.pem
  TLSLog                        /var/log/proftpd/tls.log
</IfModule>

ExtendedLog                     /opt/var/proftpd/logs/ftp.log
TransferLog                     /opt/var/proftpd/logs/xferlog.log
SystemLog                       /opt/var/proftpd/logs/syslog.log

---

