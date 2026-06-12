---
title: "vpn problem"
date: 2009-07-28
forum: Server Platforms
---

### Post by gixpaulie on 2009-07-28
hi all, 


just install openvpn using this [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN), but when i go and start it it says

tcp/udp: socket bind failed on local address xxx.xxx.xxx.xxx:1194: cannot assign requested address

what does this mean because i have tried different internal ip's and ever one comes up with the same error


any help will be great 


thanks

---

### Post by samosamo on 2009-07-29
It's really hard to help you if you don't post your openvpn config file.  You definitely specified the wrong IP. Since you hid your IP with "xxx" I have to assume you set your external IP in the config (otherwise why hide it?).  You need to use your NIC's IP address (your local IP).  If you need further help please post the output of "ifconfig" command

---

