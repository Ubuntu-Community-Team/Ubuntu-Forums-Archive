---
title: "New to servers"
date: 2008-10-01
forum: Server Platforms
---

### Post by carbon-14 on 2008-10-01
I would like to set up a ubuntu server to
 
0. Host my web page
1. Be an email server for my web page domain
2. Be a local network file server
3. Act as my network's router using static IP 

I have a vague idea how to do this on Windows, but not a clue on Linux. Could someone point me in the direction of some howto's or other resource.

---

### Post by HermanAB on 2008-10-01
Hmm, well, if you want wizards for everything same as in Windows, then you need to use Suse or Mandriva.  If you wish to use Ubuntu, then you got to do one thing at a time and do a lot of reading.

Soooo, get your network connection sorted out first.

---

### Post by whitegourd on 2008-10-01
It does take some reading and poking around on the forums, hope these links help you out.

0. [http://httpd.apache.org/](http://httpd.apache.org/)
1. [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
2. [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
3. [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by abecus on 2008-10-01
Greetings total newbie with servers!
A friend has given me a HP Netserver LPr, 1 x p3 450Mhz, 1gb ram 2 x 9.1gb scsi hard disks loaded with Ubuntu great.
The board has room for a second CPU!
2 questions

1. Does the second CPU have to be exactly the same Mhz speed or coulkd I have the second P3 running at a faster Mhz?

2. Does anyone know or point me in the right direction for some sort of technical manual about this type of server?

I have not powered up or played with this yet saving it for the weekend!

Thanks Pete:popcorn:

---

### Post by Iowan on 2008-10-01
@carbon-14: Check the "perfect server" How-to at [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu").

@abecus: Kinda thread-hijacking... 
I thought multi-processor boxes not only needed the CPU's to be the same speed, but "matched". For info on my HP  Netserver LC II, I searched the HP support website.

---

### Post by windependence on 2008-10-02
You probably shouldn't run your box as a router if you are going to run other services on it. If you want to do this all on one box, I would suggest VMware ESXi (free). Otherwise, it's better to run your router on a separate box. take a look at pfsense (my favorite) or Untagle.

-Tim

---

### Post by carbon-14 on 2008-10-02
windependence,

Out of curiosity what are the issues with running a box as a router and a server?

---

### Post by pytrisss on 2008-10-02
really... go for pure debian. I have about 40 servers with it and you cant go better. Ubuntu and so are more of a desktop distros.
You just install vzkernel on debian. Make yourself 4 virtual machines, each of them their own hostname and IP. 
Each VM will do its job, fileserver, mailserver, webserver... and you can easily adjust the amount of RAM, disk, bandwith and so the each vm will use.

---

