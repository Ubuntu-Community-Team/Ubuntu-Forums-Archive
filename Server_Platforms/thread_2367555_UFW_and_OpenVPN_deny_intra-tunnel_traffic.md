---
title: "UFW and OpenVPN deny intra-tunnel traffic"
date: 2017-07-31
forum: Server Platforms
---

### Post by aro5000 on 2017-07-31
Hi All, 

I've read these forums for a long time, but this is my first post, so please let me know if there is a more appropriate place for this. 

I have successfully set up OpenVPN on Ubuntu server, and everything is working as expected, however I do not want the clients to be able to "see" each other. My tun0 subnet is 10.8.0.0/24 and if I have a client on 10.8.0.2 it is able to ping a client on 10.8.0.3. This is what I am trying to deny with UFW. 

I suspect the culprit is in my /etc/default/ufw 
```
DEFAULT_FORWARD_POLICY="ACCEPT"
```
[COLOR=#3A3A3A][FONT=monospace]
[/FONT][/COLOR]However, from everything I have read, this is necessary for NAT to work in /etc/ufw/before.rules (if I have the above as DROP, NAT does not work)
```
-A POSTROUTING -s 10.8.0.0/8 -o [interface] -j MASQUERADE
```

I have tried adding the following rule to UFW but no luck:
```
sudo ufw deny from 10.8.0.0/24 to 10.8.0.0/24
```

Is there a reason this shouldn't be working? Or is there a better way to block this intra-network traffic?

Thanks for your time and help! :D

---

### Post by wildmanne39 on 2017-07-31
*Thread moved to **Server Platforms**.*

---

### Post by aro5000 on 2017-08-01
I ended up figuring this out with a hint from this forum post from ServerFault [https://serverfault.com/questions/736274/openvpn-client-to-client](https://serverfault.com/questions/736274/openvpn-client-to-client)

The iptables rule needed was:
```
[COLOR=#242729][FONT=Consolas]iptables -A FORWARD -i tun0 -o tun0 -j DROP[/FONT][/COLOR]
```

However, since I was using UFW, I learned from the wiki (in the advanced functionality section) that I needed to put this rule in **/etc/ufw/before.rules**
It also apparently needed to be slightly adjusted to work with UFW. 
```
-A ufw-before-forward -i tun0 -o tun0 -j DROP
```

After putting that near the top of **/etc/ufw/before.rules** (but after the required section) it worked! I was no longer able to ping other devices on the tun0 subnet! \\:D/

Link to wiki post: [https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

---

