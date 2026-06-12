---
title: "Dual NIC: port forward with iptables"
date: 2014-09-17
forum: Security
---

### Post by kjetil-fleten on 2014-09-17
Hi 

I'm trying to port forward requests on port 56000 on eth1 (Internet) to port 80 on a webserver on LAN (eth0) with iptables. I have read a lot of guides and posts on iptables, but at the moment I'm more confused than clarified.

I ran the command:
```
sudo iptables -t nat -A PREROUTING -p tcp --dport 56000 -j DNAT --to-destination  172.16.30.59:80
```

Then, my settings look like this:
```
#sudo iptables -t nat -L -v -n

Chain PREROUTING (policy ACCEPT 1046 packets, 79021 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   21  1260 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:56000 to:172.16.30.59:80

Chain INPUT (policy ACCEPT 605 packets, 50419 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 463 packets, 36513 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 297 packets, 26128 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 8754  534K MASQUERADE  all  --  *      eth1    0.0.0.0/0            0.0.0.0/0           

```

When I try to access [public IP]:56000 with a browser from outside, nothing happens. What do I miss ?

---

### Post by Doug S on 2014-09-17
We can not comment. In addition to what you already listed, the nat table, we need to the output of> sudo iptables -L -v -nAlso is forwarding enabled? Here is a segment from my script```
#CRITICAL:  Enable IP forwarding since it is disabled by default
#
echo Enabling forwarding...
echo "1" > /proc/sys/net/ipv4/ip_forward
```You can check via:```
doug@doug-64:~/init$ [COLOR=#ff0000]cat /proc/sys/net/ipv4/ip_forward[/COLOR]
[COLOR=#ff0000]1[/COLOR]
doug@doug-64:~/init$
```EDIT: I forgot to mention: I prefer to specify the interface:```
sudo iptables -t nat -A PREROUTING -p tcp [COLOR=#ff0000]-i eth1[/COLOR] --dport 56000 -j DNAT --to-destination  172.16.30.59:80
```

---

### Post by kjetil-fleten on 2014-09-18
sudo iptables -L -v -n:
```
Chain INPUT (policy ACCEPT 1045K packets, 210M bytes)
 pkts bytes target     prot opt in     out     source               destination         
1054K  212M ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
1054K  212M ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
1046K  210M ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
1046K  210M ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
1046K  210M ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
1045K  210M ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 23 packets, 1380 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 280K   17M ACCEPT     all  --  eth0   eth1    172.16.30.0/24       0.0.0.0/0            ctstate NEW
4112K 2158M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
   23  1380 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   23  1380 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   23  1380 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   23  1380 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   23  1380 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   23  1380 ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 995K packets, 283M bytes)
 pkts bytes target     prot opt in     out     source               destination         
1004K  286M ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
1004K  286M ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 995K  283M ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 995K  283M ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 995K  283M ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 995K  283M ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination
```

Ip forwarding is enabled.

I have now specified the interface:
```
Chain PREROUTING (policy ACCEPT 6 packets, 376 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:56000 to:172.16.30.59:80

Chain INPUT (policy ACCEPT 4 packets, 256 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
20296 1238K MASQUERADE  all  --  *      eth1    0.0.0.0/0            0.0.0.0/0      

```

The specification did not solve the problem.

---

### Post by Doug S on 2014-09-18
I am not seeing what is wrong. Your default FORWARD policy is ACCEPT, so the packets should be getting through. We also see 23 packets have taken that path. Are you comfortable using tcpdump (or wireshark) to have a look at the actual packet traffic? And / Or are you comfortable adding logging rules to your iptables rules set to assist debugging? Note that I do not use ufw, and so can not comment about that part of things.
 
For tcpdump testing, I would start two session in two terminals, one looking at eth1 and one looking at eth0:```
sudo tcpdump -n -tttt -i eth1 port 56000
``````
sudo tcpdump -n -tttt -i eth0 host 172.16.30.59
```or, and depending on how much other traffic there is for 172.16.30.59:```
sudo tcpdump -n -tttt -i eth0 port 80
```Then we should at least be able to determine if the issue is on the forward path or the return path.

Of course, someone else might see whatever we are missing and chime in with the answer.

---

### Post by kjetil-fleten on 2014-09-20
I have tried the two commands, and also tried Wireshark.

Then I suddenly realized my problem: 
When I launch the web page from LAN, the browser shifts to https.

I changed my rule to:
```
sudo iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 56000 -j DNAT --to-destination  172.16.30.59:443
```

Embarrassing, but I hope it can help someone else :oops:

Thanks Doug S for helping :-)

---

