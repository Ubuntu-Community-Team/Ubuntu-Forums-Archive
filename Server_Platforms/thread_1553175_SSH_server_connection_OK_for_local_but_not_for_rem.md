---
title: "SSH server connection OK for local but not for remote machine"
date: 2010-08-14
forum: Server Platforms
---

### Post by nid on 2010-08-14
Hi, 

I am having trouble to make my SSH server working with remote machine. I appreciate any help!
```

telnet 192.168.1.102 22

```

[PHP]
Trying 192.168.1.102...
Connected to 192.168.1.102.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
[/PHP]

There is no problem to connect the server using ssh from a different machine in the network. But when I connected from a remote machine, the server was not reachable.

```

sudo iptables -vnL

```

[PHP]

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.1          0.0.0.0/0           tcp flags:!0x17/0x02 
36454 4996K ACCEPT     udp  --  *      *       192.168.1.1          0.0.0.0/0           
  417 37360 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    9   504 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
   64 16769 DROP       all  --  eth0   *       0.0.0.0/0            255.255.255.255     
 1131  105K DROP       all  --  *      *       0.0.0.0/0            192.168.1.255       
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
 3031 91317 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
  222 97628 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
1085K 1258M INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.102        192.168.1.1         tcp dpt:53 
36611 2436K ACCEPT     udp  --  *      *       192.168.1.102        192.168.1.1         udp dpt:53 
  417 37360 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
  157 12627 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         


[/PHP]

---

### Post by Bachstelze on 2010-08-14
You can't connect from a machine outside your LAN with your local IP address. You have to setup port forwarding in your router and use your public address.

---

### Post by nid on 2010-08-15
I added SSH forwarding with the router configuration tool and now it seems to work but I need to check later with an outside machine. Great help. Thanks!

---

### Post by bilkay on 2010-08-23
Sorry to barge in here, but I have a question.

Here's the port forwarding section of my router:

Protocol:   TCP/UDP
WAN port range:   ___ to ___                     
LAN IP address:   ________________________
LAN port range:    ___ to ?
Add


$ grep ssh /etc/services
ssh             22/tcp                          # SSH Remote Login Protocol
ssh             22/udp

Do I add 22 to all port range entries, my desktop's IP address in "LAN IP address", and Add an entry for both TCP and UDP?

Trial and error isn't really much of an option.

Thanks!

---

### Post by amauk on 2010-08-23
Protocol: TCP
WAN port range: 22 to 22
LAN IP address: <Your_Machine's_Internal_IP>
LAN port range: 22 to 22

---

### Post by s1gnAl on 2010-08-23
> 
Sorry to barge in here, but I have a question.

Here's the port forwarding section of my router:

Protocol: TCP UDP (options: TCP and UDP)
WAN port range: to
LAN IP address:
LAN port range: to ?


Protocol: TCP
Wan port range: 22 to 22
LAN IP address: the ip of your machine
LAN port range: 22 to 22

Not sure of your brand of router, but those settings should work. 

Hope that helps :)

---

### Post by bilkay on 2010-08-23
> **s1gnAl said:**
> Protocol: TCP
Wan port range: 22 to 22
LAN IP address: the ip of your machine
LAN port range: 22 to 22

Not sure of your brand of router, but those settings should work. 

Hope that helps :)

Sure did!

Thanks...

---

### Post by nid on 2010-09-17
I haven't fixed the problem. Now I tried to use a machine to ssh my home ssh server, the results follow. By the way, I was able to ssh and log into a different server, so the problem is mostly likely on my home ssh server.
```
 ssh -vvv jon@internet.ip
```
[PHP]
OpenSSH_5.6p1, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /home/jonw/.ssh/config
debug1: Applying options for *
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Executing proxy command: exec /usr/local/bin/corkscrew proxy.ip 8080 ssh.home.server 22
debug1: permanently_drop_suid: 73291
debug1: identity file /home/jonw/.ssh/id_rsa type -1
debug1: identity file /home/jonw/.ssh/id_rsa-cert type -1
debug1: identity file /home/jonw/.ssh/id_dsa type -1
debug1: identity file /home/jonw/.ssh/id_dsa-cert type -1
ssh_exchange_identification: Connection closed by remote host[/PHP]

But I am not sure what to do next. I checked my server /etc/hosts.deny which has nothing there.

Thanks in advance!

---

### Post by v1ad on 2010-09-17
question is what ip are you using. if your ip starts with  192.* it will never work remotely. go to ip chicken from the computer you are trying to access and use the ip provided. 
ssh [email]username@ip_from_ipchicken...

---

### Post by nid on 2010-09-18
> **v1ad said:**
> question is what ip are you using. if your ip starts with  192.* it will never work remotely. go to ip chicken from the computer you are trying to access and use the ip provided. 
ssh [email]username@ip_from_ipchicken...

That's what I did above.

---

### Post by CharlesA on 2010-09-18
> **nid said:**
> That's what I did above.
If port forwarding is set up correctly, I would move sshd to another port to see if yer ISP is blocking port 22.

Edit this line in /etc/ssh/sshd_config:
```
# What ports, IPs and protocols we listen for
Port 22
```

Change it to something like 2222, or a higher port number and update your port forwarding.

---

### Post by nid on 2010-09-18
> **CharlesA said:**
> If port forwarding is set up correctly, I would move sshd to another port to see if yer ISP is blocking port 22.

Edit this line in /etc/ssh/sshd_config:
```
# What ports, IPs and protocols we listen for
Port 22
```

Change it to something like 2222, or a higher port number and update your port forwarding.

I wish my port forwarding was correct. To verify, should I put the ip chicken at LAN server when doing port forwarding?

Thanks!

---

### Post by v1ad on 2010-09-18
when forwarding a port you have to specify the local ip address for the computer that you are trying to access.

---

### Post by CharlesA on 2010-09-18
> **nid said:**
> I wish my port forwarding was correct. To verify, should I put the ip chicken at LAN server when doing port forwarding?

Thanks!

It's the local IP address. Check [here]("http://portforward.com/") for some info on port forwarding. :)

---

### Post by nid on 2010-09-18
> **CharlesA said:**
> If port forwarding is set up correctly, I would move sshd to another port to see if yer ISP is blocking port 22.

Edit this line in /etc/ssh/sshd_config:
```
# What ports, IPs and protocols we listen for
Port 22
```

Change it to something like 2222, or a higher port number and update your port forwarding.

For some reason, it did not work for me. I tried 2222 and 1922 but both did not work according to the results checked on [http://www.yougetsignal.com/tools/open-ports/]("http://www.yougetsignal.com/tools/open-ports/"). Indeed, port 22 works. By the way, I used internal ip address for port forwarding.

I was wondering what should I check next?

---

### Post by CharlesA on 2010-09-18
Are you trying to connect from inside the network using the external ip address?

Most of the time that won't work, since the router doesn't know what to do.

---

### Post by nid on 2010-09-18
> **CharlesA said:**
> Are you trying to connect from inside the network using the external ip address?

Most of the time that won't work, since the router doesn't know what to do.

No. I was trying to connect from outside the network.

---

### Post by CharlesA on 2010-09-18
> **nid said:**
> No. I was trying to connect from outside the network.
Hrm ok.

Try doing a scan with something like shieldsup! from your local network and see if port 22 is shown as open.

That'll confirm that the port is open and port forwarding is set up correctly.

---

### Post by nid on 2010-09-18
> **CharlesA said:**
> Hrm ok.

Try doing a scan with something like shieldsup! from your local network and see if port 22 is shown as open.

That'll confirm that the port is open and port forwarding is set up correctly.

The results from shieldsup! confirmed that the port 22 is open.

---

### Post by CharlesA on 2010-09-18
> **nid said:**
> The results from shieldsup! confirmed that the port 22 is open.

Then you should be able to connect. Are there any firewall rules enabled on the server running ssh?

---

### Post by nid on 2010-09-18
> **CharlesA said:**
> Then you should be able to connect. Are there any firewall rules enabled on the server running ssh?

The firewall rule allows ssh. The good news is that it works now somehow!:)

---

### Post by CharlesA on 2010-09-18
> **nid said:**
> The firewall rule allows ssh. The good news is that it works now somehow!:)
Glad it's working now. Don't forget to mark as solved. :)

---

