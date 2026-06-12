---
title: "make apache2 public again"
date: 2009-09-12
forum: Server Platforms
---

### Post by jrcramer on 2009-09-12
I have apache2 with php working, but only in a localhost setting. using my external IP adres I get an error message "Failed to Connect; Firefox can't establish a connection to the server at ..."

I am behind an router and forwarded to port 80, and I hae apache listengening to *:80
It once worked, but I dnt know what broke it.

How do I restore this? What obvious steps do I have to take. 
tnx in advance

---

### Post by paulisdead on 2009-09-12
There's more than one way you could have done this.  Check the apache2.conf file, look in your webroot directory for any hidden files, like .htaccess, and check your /etc/hosts.deny and /etc/hosts.allow files.  Also check your firewall rules with "iptables -L" to make sure that's not being blocked.

---

### Post by jrcramer on 2009-09-12
Thanks for the quick reply. My hosts.allow and .deny are both empty. I guess this is good?
This is my output of sudo iptables -L

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
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

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

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
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination   
```

I dont understand this output. Is this good?
Any help is appreciated... :(

---

### Post by paulisdead on 2009-09-14
Looks like you're using UFW, which I don't really know anything about, but glancing through that output I don't see anything to allow port 80 in from anywhere.  Looks like you just need to run "sudo ufw allow 80/tcp"

---

### Post by jrcramer on 2009-09-14
Thanks for the quick respons. I added those rules, but has no effect.
I do not know why the output is so difficult. I only want port 80 to redirect the site, and another port (1412) for se of a DC client, thats all.

How do I clean this mess?

---

### Post by paulisdead on 2009-09-14
Try disabling UFW, and test to see if it works without it.  If it doesn't, that at least rules it out.  If it does, you can research the right way to open up the port with UFW.  I'm not much help with that, since I've never used it.  Either that, or you can get rid of it and go with another frontend for iptables, or just delve into the rules yourself and write your own script.  Firestarter's alright for a GUI for iptables.

---

### Post by dmizer on 2009-09-14
I think your problem is more basic.

Are you trying to access your server's public IP from a computer on the same network as the server? If so, then you're router probably isn't capable of loopback requests.

To verify this, try accessing the server via it's external IP from a remote location (ask a friend to try to visit it, or try visiting it from work)

---

