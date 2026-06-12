---
title: "Fail2Ban adds iptable rules but they are not working?"
date: 2012-08-29
forum: Security
---

### Post by THPubs on 2012-08-29
Fail2Ban just blocked my IP for 3 SSH attempts. It added the iptables rule and I can see it using the "sudo iptables -L -n" command. But I can still access the site and login through SSH! What might be the problem? Is it because im using CloudFlare? I have set Nginx to write the real IPs to the access logs instead of the Cloud Flare IP. Isn't it enough?

---

### Post by dfreer on 2012-08-30
Please list your iptables rules with:
```
iptables -L
```

---

### Post by juanellis on 2012-08-30
Hello Guys, i've been having same problem whith iptables. Actually i configured iptables and squid3. all my clients have internet connection but can't connect to outside machine with Remote Desktop.

My iptables looks like this:

#Borrar cadenas anteriores
iptables -F
iptables -X
iptables -Z
iptables -t nat -F

#Condiciones por defecto
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

iptables -t nat -P PREROUTING ACCEPT
iptables -t nat -P POSTROUTING ACCEPT

#Desde el localhost se puede hacer todo
iptables -A INPUT -i lo -j ACCEPT

# forward all established connections to the logaccept chain
#iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j logaccept

#Desde la red local se puede acceder al servidor
iptables -A INPUT -s 172.16.20.0/24 -j ACCEPT

#Dejamos abiertos los puertos que necesitemos que se vean desde internet
#Supongamos que también tenemos un servidor web en esta PC
#iptables -A INPUT -p tcp --dport 80 -j ACCEPT
#Supongamos que queremos acceder al ssh desde internet
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

#Permitimos los puertos que pueden usar en la red local
iptables -A FORWARD -s 172.16.20.0/24 -i eth1 -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -s 172.16.20.0/24 -i eth1 -p tcp --dport 443 -j ACCEPT
iptables -A FORWARD -s 172.16.20.0/24 -i eth1 -p tcp --dport 53 -j ACCEPT
iptables -A FORWARD -s 172.16.20.0/24 -i eth1 -p udp --dport 53 -j ACCEPT
iptables -A FORWARD -s 172.16.20.0/24 -i eth1 -p tcp --dport 995 -j ACCEPT
iptables -A FORWARD -s 172.16.20.0/24 -i eth1 -p tcp --dport 110 -j ACCEPT
iptables -A FORWARD -s 172.16.20.0/24 -i eth1 -p tcp --dport 22 -j ACCEPT

#Conexion al MSN
iptables -A FORWARD -s 172.16.20.0/24 -i eth1 -p tcp --dport 1863 -j ACCEPT

#Conexion a Escritorio Remoto
iptables -A OUTPUT -s 172.16.20.101 -d <rd-server> -p tcp --dport 3389 -m state --state NEW -j ACCEPT
iptables -A OUTPUT -s 172.16.20.101 -d >rd-server> -p udp --dport 3389 -m state --state NEW -j ACCEPT

#PING
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT

#Denegamos todos los demas puertos de FORWARD
#Con esto bloqueamos todo lo que no se acepto anteriormente
#por ejemplo cualquier P2P y el msn.
#iptables -A FORWARD -s 172.16.20.0/24 -i eth1 -j DROP

#Cerramos todos los puertos de INPUT que no permitimos anteriormente
iptables -A INPUT -p tcp --dport 1:1024 -j DROP
iptables -A INPUT -p udp --dport 1:1024 -j DROP

#Con esto hacemos transparente el squid
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128

#Esta linea es muy importante, habilita el forwardeo de nuestro servidor
echo 1 > /proc/sys/net/ipv4/ip_forward

I'd appreciate any help, thank you

---

### Post by THPubs on 2012-08-31
> **dfreer said:**
> Please list your iptables rules with:
```
iptables -L
```


```
    Chain fail2ban-ssh (1 references)
     target     prot opt source               destination         
     DROP       all  --  119.235.14.8         0.0.0.0/0           
     RETURN     all  --  0.0.0.0/0            0.0.0.0/0  
```

The input chain :
```
	
	Chain INPUT (policy DROP)
	
		target     prot opt source               destination         
		fail2ban-NoAuthFailures  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:80
		fail2ban-nginx-dos  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 80,8090
		fail2ban-postfix  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 25,465
		fail2ban-ssh-ddos  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
		fail2ban-ssh  tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
		ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
		ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
		ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
		ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
		ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           
		ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           
		LOG        all  --  0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 4
```

Hope its enough :)

---

### Post by THPubs on 2012-09-03
Any clue whats going on?

---

### Post by dfreer on 2012-09-06
No, not really. Your iptables -L output looks vastly different from anything I'm use to configuring. Also you didn't post all of it, that might have helped. My guess would be that it is matching that fail2ban-ssh-ddos rule first? I'm not very good at troubleshooting the output of iptables -L, I'm better at troubleshooting the raw commands such as the other user posted above.

juenellis, try creating a new topic as your iptables issue is completely different from the OP's (has to do with routing, which I am also unfamiliar with). It will get you more help if you create a separate thread.

---

