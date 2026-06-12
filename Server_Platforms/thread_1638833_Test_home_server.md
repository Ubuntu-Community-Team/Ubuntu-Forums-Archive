---
title: "Test home server"
date: 2010-12-06
forum: Server Platforms
---

### Post by GSI on 2010-12-06
Hello. I plan installing ubuntu 10.10 server on an old box and I want to try shraing files over a windows network ( 3PCs all running Windows XP SP2), I don't have a static IP adress and I have some questions like : 
How do I configure samba so the linux server will work with windows PCs.

Thanks in advance :)

---

### Post by redelek on 2010-12-06
You can assign a static IP for the LAN you want
eg
10.0.1.0/24
or more pupilarny 192.168.1.0/24
This internal network is not you need a public IP

---

### Post by HugoSerrano on 2010-12-06
Hi.

You can follow this to configure the server:
[https://help.ubuntu.com/10.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.10/serverguide/C/samba-fileserver.html)

You can configure your network interface with a static IP Address.

> $sudo /etc/network/interfaces

> auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.254


Regards!

---

### Post by GSI on 2010-12-06
Thanks for the response! I will try configuring in a minute :)

---

### Post by GSI on 2010-12-06
> **redelek said:**
> You can assign a static IP for the LAN you want
eg
10.0.1.0/24
or more pupilarny 192.168.1.0/24
This internal network is not you need a public IP

Im sorry.. I dont understand Do I need to have static IP? And there's no "internal" network.. All the PCs are connected to a modem wich has 4 ports

---

### Post by trundlenut on 2010-12-06
Your modem is most likely actually a router so you do have an interal network.  Can the current pcs see each other when plugged into the modem?

---

### Post by CharlesA on 2010-12-06
Just wondering why you are running SP2, instead of SP3, as support for SP2 ended in July of 2010.

Anyway, The link to the server guide should work for you.

You can also check out a tutorial that I wrote up [here]("http://charlesa.net/tutorials/samba.php").

---

### Post by DanHorniblow on 2010-12-06
I have recently just started playing around with ubuntu server 10.10 and samba, I installed webmin on the server, it lets you manage and configure your server in a nice and easy to use web based control pannel.

[http://www.webmin.com/]("http://www.webmin.com/")

And it will be alot easier to configure your server and connect to it if you set it with a static IP.

[http://www.jonathanmoeller.com/screed/?p=2305]("http://www.jonathanmoeller.com/screed/?p=2305")

---

### Post by theozzlives on 2010-12-06
If you have a modem/router (normally called a Gateway) you'd only  be able to setup peer-to-peer letting your Ubuntu computer act as a "server". But it can be done, you'll have to setup your server shares in the SMB.CONF. Make sure your workgroup and smbpasswd are the same as your Windows boxes.

---

### Post by GSI on 2010-12-06
> **CharlesA said:**
> Just wondering why you are running SP2, instead of SP3, as support for SP2 ended in July of 2010.

Anyway, The link to the server guide should work for you.

You can also check out a tutorial that I wrote up [here]("http://charlesa.net/tutorials/samba.php").

Becouse nobody bothers to update them xD my PC will be running SP3 after I change my hard drive ;)

---

### Post by GSI on 2010-12-07
> **trundlenut said:**
> Your modem is most likely actually a router so you do have an interal network.  Can the current pcs see each other when plugged into the modem?

I cant see the other PCs from mine. It says :[B] Mshome is not accesable. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permsissions.
The list of servers for this workgroup is currently unavailable[/B].

---

### Post by CharlesA on 2010-12-07
> **GSI said:**
> I cant see the other PCs from mine. It says :[B] Mshome is not accesable. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permsissions.
The list of servers for this workgroup is currently unavailable[/B].
You'd need to add an exception for "File and Print Sharing" in the firewall on the Windows box in order for each machine to see each other.

---

### Post by GSI on 2010-12-08
Thanks.. I totaly forgot that... :lolflag:

---

