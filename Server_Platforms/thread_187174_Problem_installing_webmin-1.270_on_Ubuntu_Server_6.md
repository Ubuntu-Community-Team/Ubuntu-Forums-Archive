---
title: "Problem installing webmin-1.270 on Ubuntu Server 6.06"
date: 2006-06-02
forum: Server Platforms
---

### Post by SeeingEyePig on 2006-06-02
This is probably something simple, but I seem to have hit a wall.
I downloaded webmin-1.270.tar.gz from the Webmin site, and installed it on my freshly-build Ubuntu Server 6.06.  Everything went smoothly, no errors were displayed, and the message "Webmin has been installed and started successfully." was cheerfully displayed.  However, when I type in [http://myserver:10000](http://myserver:10000) on my client PC, I get "The page cannot be displayed".  I've done this same process on Ubuntu desktop 6.06 and had no problem accessing it.  What am I missing?  Anyone?  Bueller...?

---

### Post by wolf359 on 2006-06-02
Hi

You will need perl-Net_SSLeay package installed.
Open firewall ports 10000 and HTTPS ?
On the machine on which webmin is installed type the following into web browser:
[https://localhost:10000](https://localhost:10000) and accept the SSL certificate.
Log into Webmin with root password..
Set-up Access IP addresses (e.g. only from 127.0.0.1, 192.168.0.2 and 192.168.0.3). These are machines on your trusted network.
Don't forget User access only from (e.g. 127.0.0.1, 192.168.0.2 and 192.168.0.3)
Create a new webmin user ASAP.
Hope this helps.

---

### Post by wolf359 on 2006-06-02
Here's some further info regarding SSL and webmin.
[http://www.webmin.com/ssl.html](http://www.webmin.com/ssl.html)

---

### Post by SeeingEyePig on 2006-06-05
perl-Net_SSLeay was the missing piece, thanks!


[QUOTE=wolf359]Hi

You will need perl-Net_SSLeay package installed.
Open firewall ports 10000 and HTTPS ?
On the machine on which webmin is installed type the following into web browser:
[https://localhost:10000](https://localhost:10000) and accept the SSL certificate.
Log into Webmin with root password..
Set-up Access IP addresses (e.g. only from 127.0.0.1, 192.168.0.2 and 192.168.0.3). These are machines on your trusted network.
Don't forget User access only from (e.g. 127.0.0.1, 192.168.0.2 and 192.168.0.3)
Create a new webmin user ASAP.
Hope this helps.[/QUOTE]

---

### Post by SeeingEyePig on 2006-06-08
Hmmm... just built a second server and when I try to apt-get install perl-Net_SSLeay I get:  E:  Couldn't find package perl-Net_SSLeay
I've uncommented the extra repositories in /etc/apt/sources.list
It just worked the other day!  ](*,) 

[QUOTE=SeeingEyePig]perl-Net_SSLeay was the missing piece, thanks![/QUOTE]

---

### Post by SeeingEyePig on 2006-06-09
Got it!
apt-get install libnet-ssleay-perl


[QUOTE=SeeingEyePig]Hmmm... just built a second server and when I try to apt-get install perl-Net_SSLeay I get:  E:  Couldn't find package perl-Net_SSLeay
I've uncommented the extra repositories in /etc/apt/sources.list
It just worked the other day!  ](*,)[/QUOTE]

---

### Post by spo0ner on 2006-06-10
Another user encountered issues since the Webmin package is no longer available.  They wrote a quick howto on Dapper and the tgz:

[http://www.ubuntuforums.org/showthread.php?t=166276](http://www.ubuntuforums.org/showthread.php?t=166276)


Hope this helps

---

