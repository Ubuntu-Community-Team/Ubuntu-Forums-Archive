---
title: "Make secure connection to FTP Server with VPN Openswan"
date: 2017-07-22
forum: Server Platforms
---

### Post by ririaf on 2017-07-22
I have topology:

FTP Server (192.168.122.219) -----switch---- VPN openswan L2TPD (192.168.122.172 & 103.19.208.247) ----------------switch------------------------client (103.19.208.248)

my ipsec.conf is: 
```
 conn L2TP-PSK
    authby=secret
    auto=start
    keyingtries=3
    ikelifetime=8h
    keylife=1h
    ike=3des-md5
    keyexchange=ike
    phase2=esp
    phase2alg=3des-md5
    compress=no
    type=tunnel
    left=%defaultroute
    leftid=103.19.208.247
    leftsubnet=192.168.122.0/24
    leftnexthop=%defaultroute
    right=%any
    pfs=yes
    dpddelay=10
    dpdtimeout=90
    dpdaction=clear 
```


And when my client connect to VPN, i get IP 192.168.1.2/32 and my VPN server have local vpn ip: 192.168.1.1/32


I tried iptables -t nat -A POSTROUTING -j MASQUERADE on my VPN server and my client can ping to my FTP server but,  wireshark can capture FTP password when my client access my FTP server. How to solve this problem? Thank you

---

### Post by wildmanne39 on 2017-07-22
*Thread moved to **Server Platforms**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks

---

### Post by ririaf on 2017-07-22
> **wildmanne39 said:**
> *Thread moved to **Server Platforms**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks

Thank you :KS

---

### Post by darkod on 2017-07-22
The best solution would be: Don't use FTP.

Sending the password in plain text is one of the worst characteristics of FTP. The VPN does nothing to protect this, you simply first connect to one VPN network, and after that when connecting to the FTP server the password is still not protected.

Use something like SFTP which works on port 22 (like SSH) and is a very secure protocol for uploading/downloading files.

---

### Post by ririaf on 2017-07-22
> **darkod said:**
> The best solution would be: Don't use FTP.

Sending the password in plain text is one of the worst characteristics of FTP. The VPN does nothing to protect this, you simply first connect to one VPN network, and after that when connecting to the FTP server the password is still not protected.

Use something like SFTP which works on port 22 (like SSH) and is a very secure protocol for uploading/downloading files.

How about FTP data? Is data can encrypt if i use VPN tunnel?

Because wireshark still can capture my data when i download it

---

### Post by darkod on 2017-07-22
Where are you running the wireshark, on the client?

---

### Post by ririaf on 2017-07-22
> **darkod said:**
> Where are you running the wireshark, on the client?
 I running wireshark on other computers  with ip 103.19.208.249 ( same network with VPN server IP public and client )

---

### Post by darkod on 2017-07-22
Well, in that case I think what happens is that the client connect to the VPN server (that traffic is encrypted), but after that it is not encrypted any more. So by running wireshark there it can see the data.

If you run wireshark on the client, all traffic should be encrypted including the ftp password.

Besides, if you want traffic encrypted all the way to the ftp server, you need vpn connection directly to it. By having a vpn connection that only connects you half-way, and then you have "standard" internal traffic on your LAN, that traffic is not encrypted. But usually the danger is on the public internet, after you have connected to your LAN, even if password is seen on the local LAN, that is not high security risk.

If you want protected traffic all the way to the ftp then you need vpn connection all the way to it. Or simply use sftp... :)

---

### Post by ririaf on 2017-07-22
> **darkod said:**
> Well, in that case I think what happens is that the client connect to the VPN server (that traffic is encrypted), but after that it is not encrypted any more. So by running wireshark there it can see the data.

If you run wireshark on the client, all traffic should be encrypted including the ftp password.

Besides, if you want traffic encrypted all the way to the ftp server, you need vpn connection directly to it. By having a vpn connection that only connects you half-way, and then you have "standard" internal traffic on your LAN, that traffic is not encrypted. But usually the danger is on the public internet, after you have connected to your LAN, even if password is seen on the local LAN, that is not high security risk.

If you want protected traffic all the way to the ftp then you need vpn connection all the way to it. Or simply use sftp... :)


How to make my ftp traffic go to VPN tunnel?

---

### Post by TheFu on 2017-07-22
Use ssh/sftp instead.  That is really the best answer.  Plain FTP uses random ports which makes it harder to secure, though a properly designed and configured VPN should solve the issue.  The human interface for sftp is exactly the same as that for plain FTP.  sftp is in the ssh-family, like scp is. All 3 are considered secure enough, when ssh-keys are used, for internet traffic.  ssh is extremely firewall friendly too. It uses 1 port.

Don't use plain FTP.  That protocol should have been removed from all computing around 1995.  Knowing enough to be tested is fine.  Any use beyond that is a poor choice.

---

### Post by ririaf on 2017-07-22
> **TheFu said:**
> Use ssh/sftp instead.  That is really the best answer.  Plain FTP uses random ports which makes it harder to secure, though a properly designed and configured VPN should solve the issue.  The human interface for sftp is exactly the same as that for plain FTP.  sftp is in the ssh-family, like scp is. All 3 are considered secure enough, when ssh-keys are used, for internet traffic.  ssh is extremely firewall friendly too. It uses 1 port.

Don't use plain FTP.  That protocol should have been removed from all computing around 1995.  Knowing enough to be tested is fine.  Any use beyond that is a poor choice.
 Okay. I Will try it. Thank you for your answer. &#128516;  That's help me.

---

