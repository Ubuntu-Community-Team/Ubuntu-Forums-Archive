---
title: "newbie help"
date: 2008-05-09
forum: Server Platforms
---

### Post by rickyslim on 2008-05-09
Hello people.

I've always been a Windoze user (I know, I know, don't hate me :rolleyes:). I've now seen the light and want to have a play around with Ubuntu Server. I've installed Ubuntu 8.0 on VirtualBox, after a few aborted attempts. 

Anyway, I know have a command line waiting for me to type stuff. Obviously I'm used to having a GUI and have read that Webmin will help me.

However, I don't even know how to get to that point. I've installed DNS Server, LAMP, mail server and print servers during the installaion process. I've logged in as admin.

What next? I've seen a few user guides but don't actually find them particularly user-friendly for someone like me.

Any idiots guides or step-by-step to see.

Thanks in advance.

Ricky

---

### Post by ginjabunny on 2008-05-09
try this

sudo apt-get update
sudo apt-get install openssl libnet-ssleay-perl libmd5-perl libauthen-pam-perl libio-pty-perl
wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.410_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.410_all.deb)
sudo dpkg -i webmin_1.410_all.deb

assuming you have setup your virtual server to be seen on your lan then access from a browser on another system using 
[https://ipaddressofserver:10000](https://ipaddressofserver:10000)

from this thread [http://ubuntuforums.org/showthread.php?t=772796&highlight=ssleay&page=2](http://ubuntuforums.org/showthread.php?t=772796&highlight=ssleay&page=2) so thanks to natrixgli, I just added the openssl bit.

If you were wondering Webmin is not in the Ubuntu repository as it is not maintaained by them and is continually updated so you have to get it from sourceforge manually, see [www.webmin.com](www.webmin.com)

---

### Post by rickyslim on 2008-05-11
Thanks for your reply.

I need to try to find more resources to start from the beginning I think. I don't even know the ip address of the server, or how to set it manually.

---

### Post by rickyslim on 2008-05-15
Thanks for your help with this.

I got there in the end, but I have a new question I've started a new thread for.

---

