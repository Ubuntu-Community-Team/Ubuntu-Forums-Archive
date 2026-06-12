---
title: "Internet not working in newly installed ubuntu server"
date: 2012-08-17
forum: Server Platforms
---

### Post by slkamath on 2012-08-17
Hi Everyone,

Myself Lokesh Kamath.

I installed Ubuntu 12.04LTS server today. I am facing problem while installing or pinging outside LAN. i.e LAN ip's are pinging. So if i give ping [www.google.com]("http://www.google.com") that time it's shows ping: unknown host [www.google.com]("http://www.google.com"). :confused::confused::confused::confused::confused:

So please anyone help me in this regard.

Regards

Lokesh Kamath

---

### Post by darkod on 2012-08-17
Do you have the network set with dhcp or manually? If manually did you enter dns nameservers in /etc/network/interfaces?

First try to ping directly some public IP, for example:
ping 8.8.8.8

Does that work? If it works, probably you only need to enter dns nameservers, please post the content of:
cat /etc/network/interfaces

---

### Post by Catalyph on 2012-08-17
try 
```
dhclient eth0
```

---

### Post by rukiaEnix on 2012-08-17
Please post what you have in /etc/resolv.conf

---

### Post by darkod on 2012-08-17
> **rukiaEnix said:**
> Please post what you have in /etc/resolv.conf

/etc/resolv.conf is not edited manually any more in ubuntu server 12.04. It gets the nameservers from the dns-nameservers line in /etc/network/interfaces. That's why posting the content of /etc/network/interfaces should be enough. At the same time it will show the network config.

---

### Post by slkamath on 2012-08-18
> **darkod said:**
> Do you have the network set with dhcp or manually? If manually did you enter dns nameservers in /etc/network/interfaces?

First try to ping directly some public IP, for example:
ping 8.8.8.8

Does that work? If it works, probably you only need to enter dns nameservers, please post the content of:
cat /etc/network/interfaces

Thanks for your response.

It's Manual (static). Yes I did enter the DNS NAMESERVERS Manually. While pinging the public IP it's not pinging.
Please find the attachment.

I tried all these before posting into the forum. It's not working. 

Thanks once again.

Regards

Lokesh Kamath

> **Catalyph said:**
> try 
```
dhclient eth0
```


Thanks for your reply.

I tried your command. After checking the ping command it's shows nothing. please find the attachment.

Thanks once again.

Regards

Lokesh Kamath

> **rukiaEnix said:**
> Please post what you have in /etc/resolv.conf

Thanks for your reply.

Please find the attachment after typing the cat /etc/resolv.conf

Thanks once again.

Regards

Lokesh Kamath

> **darkod said:**
> /etc/resolv.conf is not edited manually any more in ubuntu server 12.04. It gets the nameservers from the dns-nameservers line in /etc/network/interfaces. That's why posting the content of /etc/network/interfaces should be enough. At the same time it will show the network config.

Thanks for your response.

I attached the output of /etc/network/interfaces.

Thanks once again.

Regards

Lokesh Kamath

---

### Post by darkod on 2012-08-18
Are you sure your network is 192.192.0.x? The private range allowed for use is 192.168.x.x and I have never seen private network starting with 192.192.x.x.

Double check your router private LAN IP, I suspect it is 192.168.0.1, not 192.192.0.1. In that case you would have to replace the 192.192 with 192.168 in /etc/network/interfaces. After you edit and save the file you need either to restart the networking service or restart the server for the new settings to work. You restart the networking with:
sudo /etc/init.d/networking restart

---

### Post by cariboo on 2012-08-18
The ip address your are using is routable, so you may have problems with others accessing your server. You also have a syntax error in the dns-nameservers line. the seperate addresses have to be separated by a space only eg:

```
dns-nameservers 203.123.176.65 203.123.128.70
```

---

### Post by slkamath on 2012-08-24
Yes I am sure. My network is 192.192.0.1/24



> **darkod said:**
> Are you sure your network is 192.192.0.x? The private range allowed for use is 192.168.x.x and I have never seen private network starting with 192.192.x.x.

Double check your router private LAN IP, I suspect it is 192.168.0.1, not 192.192.0.1. In that case you would have to replace the 192.192 with 192.168 in /etc/network/interfaces. After you edit and save the file you need either to restart the networking service or restart the server for the new settings to work. You restart the networking with:
sudo /etc/init.d/networking restart

---

### Post by darkod on 2012-08-24
> **slkamath said:**
> Yes I am sure. My network is 192.192.0.1/24

In that case talk to the administrator of the network and ask them to investigate.

The setup looks good but you don't have a ping to neither IP or domain name. Try also a ping to the gateway 192.192.0.1 but it looks like it won't work too.

I am still confused about this 192.192.0.x network, that's a very rare public range. But if you say you are sure, OK.

---

### Post by slkamath on 2012-09-06
Dear 

Thanks for your reply. Also sorry for the delayed reply. 

192.192.0.1 & 192.192.0.254 is pinging from all the system which are there on the network.

Regards

Lokesh Kamath

> **darkod said:**
> In that case talk to the administrator of the network and ask them to investigate.

The setup looks good but you don't have a ping to neither IP or domain name. Try also a ping to the gateway 192.192.0.1 but it looks like it won't work too.

I am still confused about this 192.192.0.x network, that's a very rare public range. But if you say you are sure, OK.

---

