---
title: "OpenVPN connects, but no internet (only when the server is using a specific NIC)"
date: 2019-02-17
forum: Security
---

### Post by ykchen on 2019-02-17
While there are some discussions on this topic before, I cannot figure out the root of my issue. Therefore, I am posting the question again.  Any suggestion is greatly appreciated. 


Problem:
(1) I set up an OpenVPN server on Ubuntu 18.04.2 LTS at home.  The VPN service works perfectly when the server is using the WiFi interface. However, the VPN service does not work well when the server is using the ethernet interface.   (The ethernet interface is working.  Both WiFi interface and the ethernet interface connect to the same home gateway.) 
(2) When the server is using the ethernet interface, my client can still establish the connection to the VPN server.  The client will be assigned a local IP address (10.8.0.2).  That is, OpenVPN connects.  However, there is no internet for the client.  The client can ping 10.8.0.1, but cannot reach any other device behind this point (not even my home gateway).  
(3) Disabling the firewall using "sudo ufw disable" does not make any difference.  
(4) A glance of iptables rules (using "sudo iptables -L") does not seem to have any NIC specific rules.

---

### Post by TheFu on 2019-02-17
More facts please.  Basically, show your work.  Configs, routes, interfaces and firewall rules.
It is generally a bad idea to have multiple interfaces connected to the same subnet at the same time.

---

### Post by ykchen on 2019-02-17
I am very confused why it works for one NIC, but not for the other NIC. When I am using the ethernet interface, I "turned off" the WiFi interface via "[COLOR=#000000][FONT=Menlo]sudo ifconfig wlp2s0 down[/FONT][/COLOR]". When I am using the WiFi interface, I disconnected the ethernet cable.  That is, there is only one NIC interface connected to the subnet at one time. 

Here are OpenVPN configuration file information ([COLOR=#000000][FONT=Menlo]/etc/openvpn/server.conf[/FONT][/COLOR]):

```
port 1194
proto udp
dev tun
sndbuf 0
rcvbuf 0
ca ca.crt
cert server.crt
key server.key
dh dh.pem
auth SHA512
tls-auth ta.key 0
topology subnet
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
cipher AES-256-CBC
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
crl-verify crl.pem
```

Here is the "iptables -L" output: 

```
Chain INPUT (policy DROP)
target prot opt source destination 
ACCEPT udp -- anywhere anywhere udp dpt:openvpn
ufw-before-logging-input all -- anywhere anywhere 
ufw-before-input all -- anywhere anywhere 
ufw-after-input all -- anywhere anywhere 
ufw-after-logging-input all -- anywhere anywhere 
ufw-reject-input all -- anywhere anywhere 
ufw-track-input all -- anywhere anywhere 


Chain FORWARD (policy ACCEPT)
target prot opt source destination 
ACCEPT all -- 10.8.0.0/24 anywhere 
ACCEPT all -- anywhere anywhere state RELATED,ESTABLISHED
ufw-before-logging-forward all -- anywhere anywhere 
ufw-before-forward all -- anywhere anywhere 
ufw-after-forward all -- anywhere anywhere 
ufw-after-logging-forward all -- anywhere anywhere 
ufw-reject-forward all -- anywhere anywhere 
ufw-track-forward all -- anywhere anywhere 


Chain OUTPUT (policy ACCEPT)
target prot opt source destination 
ufw-before-logging-output all -- anywhere anywhere 
ufw-before-output all -- anywhere anywhere 
ufw-after-output all -- anywhere anywhere 
ufw-after-logging-output all -- anywhere anywhere 
ufw-reject-output all -- anywhere anywhere 
ufw-track-output all -- anywhere anywhere 


Chain ufw-after-forward (1 references)
target prot opt source destination 


Chain ufw-after-input (1 references)
target prot opt source destination 
ufw-skip-to-policy-input udp -- anywhere anywhere udp dpt:netbios-ns
ufw-skip-to-policy-input udp -- anywhere anywhere udp dpt:netbios-dgm
ufw-skip-to-policy-input tcp -- anywhere anywhere tcp dpt:netbios-ssn
ufw-skip-to-policy-input tcp -- anywhere anywhere tcp dpt:microsoft-ds
ufw-skip-to-policy-input udp -- anywhere anywhere udp dpt:bootps
ufw-skip-to-policy-input udp -- anywhere anywhere udp dpt:bootpc
ufw-skip-to-policy-input all -- anywhere anywhere ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target prot opt source destination 


Chain ufw-after-logging-input (1 references)
target prot opt source destination 
LOG all -- anywhere anywhere limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target prot opt source destination 


Chain ufw-after-output (1 references)
target prot opt source destination 


Chain ufw-before-forward (1 references)
target prot opt source destination 
ACCEPT all -- anywhere anywhere ctstate RELATED,ESTABLISHED
ACCEPT icmp -- anywhere anywhere icmp destination-unreachable
ACCEPT icmp -- anywhere anywhere icmp source-quench
ACCEPT icmp -- anywhere anywhere icmp time-exceeded
ACCEPT icmp -- anywhere anywhere icmp parameter-problem
ACCEPT icmp -- anywhere anywhere icmp echo-request
ufw-user-forward all -- anywhere anywhere 


Chain ufw-before-input (1 references)
target prot opt source destination 
ACCEPT all -- anywhere anywhere 
ACCEPT all -- anywhere anywhere ctstate RELATED,ESTABLISHED
ufw-logging-deny all -- anywhere anywhere ctstate INVALID
DROP all -- anywhere anywhere ctstate INVALID
ACCEPT icmp -- anywhere anywhere icmp destination-unreachable
ACCEPT icmp -- anywhere anywhere icmp source-quench
ACCEPT icmp -- anywhere anywhere icmp time-exceeded
ACCEPT icmp -- anywhere anywhere icmp parameter-problem
ACCEPT icmp -- anywhere anywhere icmp echo-request
ACCEPT udp -- anywhere anywhere udp spt:bootps dpt:bootpc
ufw-not-local all -- anywhere anywhere 
ACCEPT udp -- anywhere 224.0.0.251 udp dpt:mdns
ACCEPT udp -- anywhere 239.255.255.250 udp dpt:1900
ufw-user-input all -- anywhere anywhere 


Chain ufw-before-logging-forward (1 references)
target prot opt source destination 


Chain ufw-before-logging-input (1 references)
target prot opt source destination 


Chain ufw-before-logging-output (1 references)
target prot opt source destination 


Chain ufw-before-output (1 references)
target prot opt source destination 
ACCEPT all -- anywhere anywhere 
ACCEPT all -- anywhere anywhere ctstate RELATED,ESTABLISHED
ufw-user-output all -- anywhere anywhere 


Chain ufw-logging-allow (0 references)
target prot opt source destination 
LOG all -- anywhere anywhere limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target prot opt source destination 
RETURN all -- anywhere anywhere ctstate INVALID limit: avg 3/min burst 10
LOG all -- anywhere anywhere limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target prot opt source destination 
RETURN all -- anywhere anywhere ADDRTYPE match dst-type LOCAL
RETURN all -- anywhere anywhere ADDRTYPE match dst-type MULTICAST
RETURN all -- anywhere anywhere ADDRTYPE match dst-type BROADCAST
ufw-logging-deny all -- anywhere anywhere limit: avg 3/min burst 10
DROP all -- anywhere anywhere 


Chain ufw-reject-forward (1 references)
target prot opt source destination 


Chain ufw-reject-input (1 references)
target prot opt source destination 


Chain ufw-reject-output (1 references)
target prot opt source destination 


Chain ufw-skip-to-policy-forward (0 references)
target prot opt source destination 
ACCEPT all -- anywhere anywhere 


Chain ufw-skip-to-policy-input (7 references)
target prot opt source destination 
DROP all -- anywhere anywhere 


Chain ufw-skip-to-policy-output (0 references)
target prot opt source destination 
ACCEPT all -- anywhere anywhere 


Chain ufw-track-forward (1 references)
target prot opt source destination 
ACCEPT tcp -- anywhere anywhere ctstate NEW
ACCEPT udp -- anywhere anywhere ctstate NEW


Chain ufw-track-input (1 references)
target prot opt source destination 


Chain ufw-track-output (1 references)
target prot opt source destination 
ACCEPT tcp -- anywhere anywhere ctstate NEW
ACCEPT udp -- anywhere anywhere ctstate NEW


Chain ufw-user-forward (1 references)
target prot opt source destination 


Chain ufw-user-input (1 references)
target prot opt source destination 
ACCEPT udp -- anywhere anywhere udp dpt:openvpn
ACCEPT tcp -- anywhere anywhere tcp dpt:ssh


Chain ufw-user-limit (0 references)
target prot opt source destination 
LOG all -- anywhere anywhere limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT all -- anywhere anywhere reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target prot opt source destination 
ACCEPT all -- anywhere anywhere 


Chain ufw-user-logging-forward (0 references)
target prot opt source destination 


Chain ufw-user-logging-input (0 references)
target prot opt source destination 


Chain ufw-user-logging-output (0 references)
target prot opt source destination 


Chain ufw-user-output (1 references)
target prot opt source destination 
```


I have turned off the firewall, but using "sudo ufw disable"

---

