---
title: "unable to access FTP remotely after installing vsFTPd"
date: 2013-08-22
forum: Server Platforms
---

### Post by John_Fuller-Root on 2013-08-22
Ubuntu server 64-Bit 12.04.2
vsftpd 2.3.5

Hi,

I was wondering if anyone could help me with an issue I am having with vsFTPd on Ubunu server. I installed Ubuntu yesterday and forwarded ports on my router for my apache webserver, ssh and ftp. I can access the server via ssh remotely without problem, I can access the webserver without problem and get the "it works page". However when I try to use smartFTP client and FreeCommander FTP client to connect to FTP I get an error. With free commander I get:

==== Connect: 8/22/2013 10:48:21 AM ====
220 (vsFTPd 2.3.5)
USER root
331 Please specify the password.
PASS *********
10038 An operation was attempted on something that is not a socket.

and in SmartFTP I get:

[10:57:21] SmartFTP v4.1.1333.0
[10:57:21] Resolving host name "[www.??????.com]("http://www./??????.com")"
[10:57:21] Connecting to ??.??.??.?? Port: 21
[10:57:22] Connected to [www.??????.com]("http://www./??????.com").
[10:57:22] 220 (vsFTPd 2.3.5)
[10:57:22] USER root
[10:57:22] 331 Please specify the password.
[10:57:22] PASS (hidden)
[10:57:22] Server closed connection
[10:57:22] Connect failed. Error=0x80043112
[10:57:22] Waiting to retry (30s)...

So here is everything I have done during and since the install of Ubuntu server:

- installed Ubuntu from DVD with a LAN cable connected (internet connection)
- selected LAMP server, ssh and SAMBA packages from the selection screen during install
- can't remember for sure if I selected FTP or not but had thought I did
- on first login I used the default user account I had created during setup to enable root and created a secure password for root (I want to use root, I like using root)
- made my router always give my Ubuntu server a static IP address on my internal network
- forwarded ports 21, 22 and 80
- tested local access to ssh and webserver
- tested external access to ssh and webserver
- loaded freecommander presuming FTP would just work like ssh did and apache but nothing happed (locally or externally)
- wondered if I had actually selected to install an FTP server
- had no idea what FTP server would have been installed by default
- google told me that the default for Ubuntu was vsFTPd so I looked for the conf file in /etc but it didn't exist
- presumed I must not have any FTP or had some other FTP that I don't know of so decided to do apt-get install vsFTPd
- It downloaded and installed so this seemed to further confirm that I didn't have FTP
- tested anonymous FTP access and that worked
- edited the .conf file to uncomment the lines: local_enable=YES, write_enable=YES so that I could authenticate FTP instead of connect anonymously
- tested FTP with the default user account that was created during Ubuntu install and got the same errors as above
- enabled root for FTP by removing root from /etc/ftpusers
- tested again as root but still got the same errors

Firstly, am I using the wrong FTP? Should I not be using vsFTPd for 12.04.2? What is the default FTP for Ubuntu server 12.04.2 and how can I check to see if I have it already installed?

If vsFTPd is the correct server to be using then does anyone have any idea why I can't login? Thanks in advance for any help.

---

### Post by John_Fuller-Root on 2013-08-22
Hi all,

I managed to resolve this by doing the following:

In the vsftpd.conf file I had the line: anonymous_enable=YES commented out so instead I uncommented it and changed it to: anonymous_enable=NO

I then kept getting a 530 Login incorrect every time I tried to connect but at least it appeared to be progress. I then changed the line: pam_service_name=svftpd to pam_service_name=**ftp**

These steps resolved the issue, I don't really understand why the pam_service_name=ftp change worked, but I am not going to complain about it :)

---

