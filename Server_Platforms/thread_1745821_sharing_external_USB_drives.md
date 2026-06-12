---
title: "sharing external USB drives"
date: 2011-05-01
forum: Server Platforms
---

### Post by zongosaiba on 2011-05-01
Hey Guys, 

I am new to linux. Just moved my Mac Server to Ubuntu Server 10.10.  
I am stuck. I have two external USB drives that need to be shared on the network and be available on the internet for sensitive file transfer. 
What would be the most secure way to do it ? 
Some users are mobile and some not. The mobile users can access the network through a vpn running on that same server. The server is serving DNS and Proxy as well. 
I thought about creating a SAMBA share but the two disks are 1TB each. Then I went for proftpd but after reading some doc, it appears not very secure. 
Any help is much appreciated. 

Kind Regards, 

Zongo

---

### Post by gordintoronto on 2011-05-01
Samba should work fine. After you set up a share, open Accessories/Terminal and enter this command:
gksudo gedit /etc/samba/smb.conf
Scroll down to this line:
guest ok = yes
and insert a line after it:
force user = (your ubuntu user name)
Save the file, exit and enter this command:
sudo service smbd restart

If you are not using a GUI on the server, the command becomes:
sudo nano /etc/samba/smb.conf
(or your choice of text editor.)

I think the other option is SSH, but I have never set it up myself.

---

