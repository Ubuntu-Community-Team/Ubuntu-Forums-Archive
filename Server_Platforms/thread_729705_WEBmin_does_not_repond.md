---
title: "WEBmin does not repond"
date: 2008-03-20
forum: Server Platforms
---

### Post by HEWman on 2008-03-20
I have installed the Ubuntu Server version (7.10) for the first time.
Additionally I installed WEBmin (using the directions from: [http://sylvarwolflinux.wordpress.com/2007/10/23/installin-ubuntu-710-gutsy-on-the-fileserver/](http://sylvarwolflinux.wordpress.com/2007/10/23/installin-ubuntu-710-gutsy-on-the-fileserver/))
[LIST]
[*]apt-get install openssl libauthen-pam-erl libio-pty-perl libmd5-perl
[*]wget [http://ftp.fi.debian.org/debian/pool/main/libn/libnet-ssleay-perl/libnet-ssleay-perl_1.30-1_i386.deb](http://ftp.fi.debian.org/debian/pool/main/libn/libnet-ssleay-perl/libnet-ssleay-perl_1.30-1_i386.deb)
[*]dpkg -i libnet-ssleay-perl_1.30-1_i386.deb
[*]choose to get the 1.400 version directly:
wget [http://heanet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.400_all.deb](http://heanet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.400_all.deb)
[*]dpkg -i webmin_1.400_all.deb
[/LIST]

Every seems OK :)

Trying to connect to the WEBmin server: [https://192.168.1.11:10000/](https://192.168.1.11:10000/) 
(192.168.1.11 is the IP address of the server)
i got the browser message: Firefox can't establish a connection to the server at 192.168.1.11:10000. :(

Trouble shooting results:
Port 10000 is open
**netstat -lnp output:**
tcp        0      0 0.0.0.0:10000     0.0.0.0:*       LISTEN     - 4651/perl
udp       0      0 0.0.0.0:10000     0.0.0.0:*                        - 4651/perl
:confused: Server address is 0.0.0.0 in stead of 127.0.0.1 or 192.168.1.11 - is this normal?

Checking Perl:
**sudo ps aux |grep perl output**
root      4651  0.0  3.3  10228  6404 ?        Ss   Mar18   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/

Wat went wrong?

---

### Post by stalker145 on 2008-03-20
> **HEWman said:**
> Wat went wrong?

It may be an obvious question, but can you ping out from the server? My first thought is that it's not properly configured for the network.

---

### Post by HEWman on 2008-03-20
Other network services (Apache, SSH, FTP, SAmba) are working fine.
It is just WEBmin that doesn't respond.

---

### Post by stalker145 on 2008-03-20
> **HEWman said:**
> Other network services (Apache, SSH, FTP, SAmba) are working fine.
It is just WEBmin that doesn't respond.

Assuming that you've either restarted your computer and/or the appropriate services to make sure WebMin is running, I would suggest checking the WebMin forum. At the moment, I'm at work and they have that site (among many others) blocked.

I've never had an issue with WebMin not responding in this manner. Hopefully someone else has an idea if you can't find anything on the WebMin forum.

Sorry.

---

