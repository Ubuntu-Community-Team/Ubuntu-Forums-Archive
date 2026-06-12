---
title: "Plesk FTP change port, passive?"
date: 2012-09-17
forum: Server Platforms
---

### Post by Gorlist on 2012-09-17
Hi, im slightly confused, im trying to change my default FTP port, so ive modified proftpd.conf and services to my new ip, e.g. 2121.

Opened ufw to match. However though I can connect to the ftp nothing is being retrieved (directory's etc)?

So bright idea, ftp-data port 20 was still closed, so ive again moved that to a new example port 2020, open a hole in ufw and again still no improvement

The guide I was following:

[http://forums.esds.co.in/f5/how-change-ftp-port-21-another-port-linux-plesk-server-4196/](http://forums.esds.co.in/f5/how-change-ftp-port-21-another-port-linux-plesk-server-4196/)


Filezilla:
> Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (87,106,247,185,149,241).
Command:	MLSD
Error:	Connection timed out
Error:	Failed to retrieve directory listing


Do I need to change and open FTP passive ports? example:

# Use the IANA registered ephemeral port range
PassivePorts 49152 65534

Or should I reset the ftp-data port back to 20?

Plesk 11.04 running ubuntu 12.04LTS.

---

### Post by Lars Noodén on 2012-09-17
If you are looking for a secure way to transfer files, then you might look at SFTP instead.  It is built in to the package OpenSSH-server so if you have that, then you already have SFTP installed and configured.  You also have SFTP client built into the file managers Dolphin and Nautilus.  It is enough to press ctrl-L and then enter the URI, [font=Courier New]sftp://xx.yy.zz.aa/[/font]

There are a few use-cases where FTP can still be useful. That is mostly centered around allowing anonymous downloads.  However, for the most part, it is time to put FTP out to pasture.  It has served its use.

[list]
[*] [http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[/list]

---

