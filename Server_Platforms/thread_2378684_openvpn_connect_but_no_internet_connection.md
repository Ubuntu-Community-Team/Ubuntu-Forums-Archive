---
title: "openvpn connect but no internet connection"
date: 2017-11-25
forum: Server Platforms
---

### Post by diamkil on 2017-11-25
I have an openvpn server and it connect but I don’t have internet while connected, I can still use ssh and samba but nothing other than the machine

help me please

---

### Post by darkod on 2017-11-25
Do you need the vpn tunnel to be default gateway for all traffic? Or only for some resources that you need on the vpn server and its local LAN?

---

### Post by diamkil on 2017-11-25
Need to have all trafic to go with the vpn

---

### Post by darkod on 2017-11-25
In such case you need to do the following on the vpn server:
1. Enable ipv4 forwarding in /etc/sysctl.conf on the vpn server.
2. Add a MASQUERADE rule in the POSTROUTING iptables nat table so that traffic knows to find its way back.
3. If you have the FORWARD iptables policy to DROP you also need rules in the FORWARD table to allow traffic between the tunnel interface and the NIC interface.

After that it will work.

---

### Post by diamkil on 2017-11-25
So, how I do that

---

### Post by diamkil on 2017-11-25
After I did it still doesn&#8217;t work

---

### Post by darkod on 2017-11-26
Did you reboot the server after making the changes to /etc/sysctl.conf? If you didn't try that first. If you did and it still doesn't work post the output of the following commands:
```
cat /etc/sysctl.conf | grep forward
sudo iptables -L -n -v
sudo iptables -t nat -L -n -v
```

---

### Post by diamkil on 2017-11-26
dev.diamkil.com/sources/server-output.PNG

---

### Post by darkod on 2017-11-26
You have no masquerade rule in the nat table. Try this on the server:
```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```

Do NOT reboot, the rule is temporary. Now test if vpn client access to internet is working as it should.

---

### Post by diamkil on 2017-11-26
It work! What to do for it not to be temporary

---

### Post by darkod on 2017-11-26
For a single iptables rule the best would be to add it in /etc/rc.local. At the end of the file but above the line saying 'exit 0'. The commands in there are run as root at the end of the boot process. So just add that command without sudo in front, and it will be added as root on each boot.

---

### Post by diamkil on 2017-11-26
Thx

---

