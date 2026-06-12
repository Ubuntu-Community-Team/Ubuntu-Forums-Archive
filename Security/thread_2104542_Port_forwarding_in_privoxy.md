---
title: "Port forwarding in privoxy"
date: 2013-01-13
forum: Security
---

### Post by axy_david on 2013-01-13
So all I want is to forward the https traffic to http, is this possible?

---

### Post by SeijiSensei on 2013-01-13
No.  HTTPS traffic requires a specific handshake between the client and server, and all the packets are encrypted.

Having read your earlier posting, I'll just mention that there are [efforts]("http://wiki.squid-cache.org/Features/SslBump") to enable Squid to handle SSL traffic, but they require you to generate a certificate for the proxy server and install it on all the client workstations.  You can use iptables to block or permit connections to remote HTTPS sites by IP address.

---

### Post by axy_david on 2013-01-21
can't I just deny all HTTPS acces? Tried with iptables, didn't work

---

### Post by bodhi.zazen on 2013-01-23
> **axy_david said:**
> can't I just deny all HTTPS acces? Tried with iptables, didn't work

iptables will block all https traffic. What rule did you use ?

```
sudo iptables -A OUTPUT -p tcp --dport https -j DROP
```

---

### Post by emiller12345 on 2013-01-24
.

---

### Post by axy_david on 2013-01-24
> **bodhi.zazen said:**
> iptables will block all https traffic. What rule did you use ?

```
sudo iptables -A OUTPUT -p tcp --dport https -j DROP
```
Tried your suggestion, nothing... it doesn't work.

---

### Post by axy_david on 2013-01-24
> **SeijiSensei said:**
> No.  HTTPS traffic requires a specific handshake between the client and server, and all the packets are encrypted.

Having read your earlier posting, I'll just mention that there are [efforts]("http://wiki.squid-cache.org/Features/SslBump") to enable Squid to handle SSL traffic, but they require you to generate a certificate for the proxy server and install it on all the client workstations.  You can use iptables to block or permit connections to remote HTTPS sites by IP address.
it seems that I am unnable to block https traffic using iptables, however I can open specific ports
Can I block https communication with squid, since I don't really understand squid.

---

### Post by raja.genupula on 2013-01-25
I am not sure but you can block the URL with some matching words . this URL can help you.

[http://sarg.sourceforge.net/sxcontrol.php](http://sarg.sourceforge.net/sxcontrol.php)

---

### Post by bodhi.zazen on 2013-01-25
> **axy_david said:**
> Tried your suggestion, nothing... it doesn't work.

If it is not working you need to post all your rules. With iptables, the order of the rules is important.

---

### Post by axy_david on 2013-01-25
> **raja.genupula said:**
> I am not sure but you can block the URL with some matching words . this URL can help you.

[http://sarg.sourceforge.net/sxcontrol.php](http://sarg.sourceforge.net/sxcontrol.php)

I just realised Im not using squid

---

### Post by axy_david on 2013-01-25
> **bodhi.zazen said:**
> If it is not working you need to post all your rules. With iptables, the order of the rules is important.
I got to the iptable file, changeed it, it blocks https allright, but now dansguardian stopped working and is not filtering anymore, this is so annoying!

---

### Post by axy_david on 2013-01-25
OK checked dansguardian, says it's running,
privoxy is running aswell, then why isn,t the webfiltering working?

---

### Post by axy_david on 2013-01-25
> **bodhi.zazen said:**
> If it is not working you need to post all your rules. With iptables, the order of the rules is important.
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination  
```

---

