---
title: "Setting a default proxy setting"
date: 2008-07-14
forum: Server Platforms
---

### Post by phaedrus on 2008-07-14
Hiya... I'm having issues with getting a server to connect to the outside world through a proxy. I've had a search around the forums, and google, and tried a number of things but nothing appears to be working... if anyone wants any further info let me know and I'll provide anything that lets someone suggest a solution to my problem :-)

I've just installed a 6.06 LAMP server, and it's currently hiding amongst a bunch of Windows servers that connect to the outside world through a WebMarshal proxy. I've created a service account in Active Directory for the server to use, and after adding proxy details into /etc/apt/apt.conf I have been able to apt-get update and apt-get upgrade using the service account and proxy details in apt.conf

My problem comes about because I now want to wget a file from the internet. No matter what I try I end up getting this back... 
> root@wlg01zen01:/etc/apt# wget [http://downloads.sourceforge.net/zenoss/zenoss-2.2.0-0.tar.gz](http://downloads.sourceforge.net/zenoss/zenoss-2.2.0-0.tar.gz)
--16:42:45--  [http://downloads.sourceforge.net/zenoss/zenoss-2.2.0-0.tar.gz](http://downloads.sourceforge.net/zenoss/zenoss-2.2.0-0.tar.gz)
           => `zenoss-2.2.0-0.tar.gz'
Resolving downloads.sourceforge.net... 216.34.181.60
Connecting to downloads.sourceforge.net|216.34.181.60|:80... failed: Connection refused.

I've tried adding proxy details in a few different ways...
1. Just from the command line, with HTTP_PROXY=http://user:pass@proxy:port and then export HTPP_PROXY
2. Adding an export HTTP_PROXY line to /etc/bash.bashrc
3. Adding it to my user profile in ~/.bashrc

All three of these options leave me in a position where I can just type export and see my HTTP_PROXY variable showing. The same credentials work with apt-get and the apt.conf file but wont work for wget. I've tried other external sites as well as the sourceforge site, and get the same error... but it works fine when grabbing stuff from a local machine (our internal web server with wget [http://www/images/logo.jpg](http://www/images/logo.jpg)). I've also tried using the --proxy flag with wget to explicitly turn on proxy use and tried passing user and password details directly to wget.

Anyone have any ideas of what I might be doing wrong? I can ping the sourceforge server, but can't wget...

If anyone is particularly interested, this is what tcpdump says about what happens when I try the wget command:> 16:17:46.699096 IP te002022.trustees.co.nz.2414 > wlg01zen01.trustees.co.nz.ssh: P 573:625(52) ack 1028 win 64040
16:17:46.699213 IP wlg01zen01.trustees.co.nz.ssh > te002022.trustees.co.nz.2414: P 1028:1080(52) ack 625 win 8576
16:17:46.705241 IP wlg01zen01.trustees.co.nz.ssh > te002022.trustees.co.nz.2414: P 1080:1244(164) ack 625 win 8576
16:17:46.705384 IP wlg01zen01.trustees.co.nz.ssh > te002022.trustees.co.nz.2414: P 1244:1328(84) ack 625 win 8576
16:17:46.705444 IP te002022.trustees.co.nz.2414 > wlg01zen01.trustees.co.nz.ssh: . ack 1244 win 63824
16:17:46.706070 IP wlg01zen01.trustees.co.nz.32772 > wlg01dc01.trustees.co.nz.domain:  1317+ AAAA? downloads.sourceforge.net. (43)
16:17:46.706320 arp who-has wlg01zen01.trustees.co.nz tell wlg01dc01.trustees.co.nz
16:17:46.706334 arp reply wlg01zen01.trustees.co.nz is-at 00:17:a4:ff:4c:42 (oui Unknown)
16:17:46.706450 IP wlg01dc01.trustees.co.nz.domain > wlg01zen01.trustees.co.nz.32772:  1317 1/1/0 (116)
16:17:46.706569 IP wlg01zen01.trustees.co.nz.32772 > wlg01dc01.trustees.co.nz.domain:  27439+ A? downloads.sourceforge.net. (43)
16:17:46.706717 IP wlg01dc01.trustees.co.nz.domain > wlg01zen01.trustees.co.nz.32772:  27439 2/0/0[|domain]
16:17:46.706825 IP wlg01zen01.trustees.co.nz.ssh > te002022.trustees.co.nz.2414: P 1328:1380(52) ack 625 win 8576
16:17:46.706876 IP wlg01zen01.trustees.co.nz.ssh > te002022.trustees.co.nz.2414: P 1380:1432(52) ack 625 win 8576
16:17:46.706944 IP wlg01zen01.trustees.co.nz.ssh > te002022.trustees.co.nz.2414: P 1432:1532(100) ack 625 win 8576
16:17:46.706985 IP te002022.trustees.co.nz.2414 > wlg01zen01.trustees.co.nz.ssh: . ack 1380 win 63688
16:17:46.707016 IP wlg01zen01.trustees.co.nz.59814 > ch3.sourceforge.net.www: S 1303429417:1303429417(0) win 5840 <mss 1460,sackOK,timestamp 977716 0,nop,wscale 2>
16:17:46.707107 IP te002022.trustees.co.nz.2414 > wlg01zen01.trustees.co.nz.ssh: . ack 1532 win 63536
16:17:46.707244 IP ch3.sourceforge.net.www > wlg01zen01.trustees.co.nz.59814: R 0:0(0) ack 1303429418 win 5840 <mss 1460,sackOK,timestamp 977716 0,nop,wscale 2>
16:17:46.707386 IP wlg01zen01.trustees.co.nz.ssh > te002022.trustees.co.nz.2414: P 1532:1600(68) ack 625 win 8576
16:17:46.707976 IP wlg01zen01.trustees.co.nz.ssh > te002022.trustees.co.nz.2414: P 1600:1668(68) ack 625 win 8576
16:17:46.708056 IP wlg01zen01.trustees.co.nz.ssh > te002022.trustees.co.nz.2414: P 1668:1736(68) ack 625 win 8576
16:17:46.708144 IP te002022.trustees.co.nz.2414 > wlg01zen01.trustees.co.nz.ssh: . ack 1668 win 63400
16:17:46.822198 IP te002022.trustees.co.nz.2414 > wlg01zen01.trustees.co.nz.ssh: . ack 1736 win 63332

In the above log, te002022 is my workstation which I ssh onto wlg01zen01 with, which is my ubuntu server, and wlg01dc01 is my Windows Server 2003 domain controller (my proxy is wlg01prx01, it doesn't appear in the log tho).

I also thought it might want me to explicitly state a domain... so have tried various combinations of DOMAIN\User (this strips the \ as bash's escape character) and DOMAIN\\User (both \'s show up)... and without a domain. None seem to help... which is annoying, as I was able to get the proxy to authenticate and work with apt-get... If anyone has any suggestions it would be greatly appreciated as I'm beginning to tear out my little remaining hair thanks to this not working.

 Simon

---

