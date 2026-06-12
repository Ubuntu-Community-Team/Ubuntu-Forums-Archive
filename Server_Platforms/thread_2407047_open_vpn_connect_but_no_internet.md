---
title: "open vpn connect but no internet"
date: 2018-11-29
forum: Server Platforms
---

### Post by malberts2002 on 2018-11-29
Hey guys I'm fairly new to Ubuntu but I recently set up an OpenVpn server as per the Digital Ocean guide ([https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04)). It makes a connection but I get no internet. I read about and tried this command 
sudo iptables -t nat -A POSTROUTING -j MASQUERADE

Which worked, but i'm trying to understand why and how to make the fix permanent.

Most of this code can already be found in the ufw before.rules file as per the digital ocean guide.

Any help would be appreciated

---

### Post by SeijiSensei on 2018-11-29
Add the command to /etc/rc.local without the "sudo".

Masquerading makes all outbound traffic appear to come from the machine's public IP address.  I suggest adding 

```
iptables -t nat -A POSTROUTING -i tun0 -o eth0 -j MASQUERADE
```

to explicitly declare that traffic from the VPN is to be masqueraded. Replace "tun0" and "eth0" with the tunnel and public interface names your machine uses.

---

### Post by malberts2002 on 2018-11-30
I cant find /etc/rc.local
has it been moved or renamed for 18.04

---

### Post by SeijiSensei on 2018-11-30
I hate it when methods that we veterans have used for decades get removed for no good reason.

Just create a file called /etc/rc.local as root with sudo.  It needs to be marked executable. 

rc.local used to be an empty file in earlier releases.  Why that wasn't considered the right approach in 18.04 baffles me.

---

