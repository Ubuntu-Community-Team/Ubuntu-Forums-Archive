---
title: "Firestarter prevents internet connection"
date: 2011-01-01
forum: Security
---

### Post by tlhodgson on 2011-01-01
Greetings everyone. I am running ubuntu 10.10. I recently enabled the  firewall and installed Firestarter to configure it. Bad decision  apparently. I can't connect to the internet using Firefox unless I first  stop the firewall using Firestarter. After I do that, Firefox connects  to the internet just fine.

Does anyone know what the problem is  here, and how to fix it? If I uninstall Firestarter, will the ubuntu  firewall function as it did originally, before I configured it? Or will  it continue to function the way it does right now, which doesn't allow  me to connect to the internet?

I appreciate any help the community can provide. Thanks

---

### Post by jgedeon on 2011-01-01
> **tlhodgson said:**
> Greetings everyone. I am running ubuntu 10.10. I recently enabled the  firewall and installed Firestarter to configure it. Bad decision  apparently. I can't connect to the internet using Firefox unless I first  stop the firewall using Firestarter. After I do that, Firefox connects  to the internet just fine.

Does anyone know what the problem is  here, and how to fix it? If I uninstall Firestarter, will the ubuntu  firewall function as it did originally, before I configured it? Or will  it continue to function the way it does right now, which doesn't allow  me to connect to the internet?

I appreciate any help the community can provide. Thanks

You need to set up your default rules.  I'm not familiar with the firestarter interface as I use a plain iptables script.  More than likely if you run iptables -nvL you will see that the output side set to drop.  Care to show the output of iptables -nvL ?

---

### Post by tlhodgson on 2011-01-02
Of course this is what my machine shows after I have turned off the firewall and have the internet running so I can see what has been posted on the forum. Do I need to run this command without turning off the firewall?  Here is what came up when I typed in sudo iptables -nvL

terry@terry-Inspiron-1564:~$ sudo iptables -nvL
[sudo] password for terry: 
Chain INPUT (policy ACCEPT 1227 packets, 1118K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1249 packets, 130K bytes)
 pkts bytes target     prot opt in     out     source               destination         
terry@terry-Inspiron-1564:~$

Does this shed any light on the matter? Thanks for your help.

---

### Post by jgedeon on 2011-01-02
> **tlhodgson said:**
> Of course this is what my machine shows after I have turned off the firewall and have the internet running so I can see what has been posted on the forum. Do I need to run this command without turning off the firewall?  Here is what came up when I typed in sudo iptables -nvL

terry@terry-Inspiron-1564:~$ sudo iptables -nvL
[sudo] password for terry: 
Chain INPUT (policy ACCEPT 1227 packets, 1118K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 1249 packets, 130K bytes)
 pkts bytes target     prot opt in     out     source               destination         
terry@terry-Inspiron-1564:~$

Does this shed any light on the matter? Thanks for your help.


Yes turn the firewall on run the command and copy it then turn the firewall off and then post the output.

---

### Post by tlhodgson on 2011-01-02
Here is what came out. 

pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       10.5.52.1            0.0.0.0/0           tcp flags:!0x17/0x02 
    2   656 ACCEPT     udp  --  *      *       10.5.52.1            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       82.206.129.20        0.0.0.0/0           tcp flags:!0x17/0x02 
    0     0 ACCEPT     udp  --  *      *       82.206.129.20        0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       69.20.9.156          0.0.0.0/0           tcp flags:!0x17/0x02 
    0     0 ACCEPT     udp  --  *      *       69.20.9.156          0.0.0.0/0           
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 LSI        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
    0     0 LSI        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    1   328 DROP       all  --  eth0   *       0.0.0.0/0            255.255.255.255     
    0     0 DROP       all  --  *      *       0.0.0.0/0            10.5.52.112         
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    8  1336 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
    0     0 INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LSI        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
    0     0 LSI        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       10.5.52.112          10.5.52.1           tcp dpt:53 
    0     0 ACCEPT     udp  --  *      *       10.5.52.112          10.5.52.1           udp dpt:53 
    0     0 ACCEPT     tcp  --  *      *       10.5.52.112          82.206.129.20       tcp dpt:53 
    0     0 ACCEPT     udp  --  *      *       10.5.52.112          82.206.129.20       udp dpt:53 
    0     0 ACCEPT     tcp  --  *      *       10.5.52.112          69.20.9.156         tcp dpt:53 
    0     0 ACCEPT     udp  --  *      *       10.5.52.112          69.20.9.156         udp dpt:53 
    0     0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:6881:6889 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:6881:6889 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:80 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:443 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:110 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:110 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:143 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:143 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:25 
    0     0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (6 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0

---

### Post by jgedeon on 2011-01-02
Yes, Looks like you need to set your default policy with Firestarter.

---

### Post by tlhodgson on 2011-01-04
I'm afraid I don't know what you mean. I ran the firestarter wizard, and did everything it asked me to do. Any advice on what I should do with firestarter?

---

### Post by bodhi.zazen on 2011-01-04
> **tlhodgson said:**
> I'm afraid I don't know what you mean. I ran the firestarter wizard, and did everything it asked me to do. Any advice on what I should do with firestarter?

A better question is what makes you think you need a firewall at all? What server are you running ? What access to you wish to allow or deny ?

As far as firestarter, it is no longer maintained and I would advise you remove it and use ufw or gufw.

```
sudo apt-get purge -y firestarter
sudo ufw enable
```

Those two commands are all 99.99% of desktop users need to know, and most do not need a firewall at all.

---

### Post by tlhodgson on 2011-01-06
Thanks bodhi. I believe you about the firewall. I was really just experimenting with it. It worked fine for a couple of weeks. I hadn't been messing with it at all until a buddy of mine started having some security concerns about his email. I'm in Iraq right now using some kind of locally contracted internet provider, so I figured it couldnt hurt to try out the firewall for security reasons. 

My question now is, if I uninstall firestarter, will that return the ubuntu firewall back to its original settings, such that it won't affect my internet service? If not, how do I return the firewall to its original configuration? I guess I can try to restore it to its original configuration by un-doing the rules I set up in firestarter. Is that correct? Should I just disable the firewall entirely?

---

### Post by bodhi.zazen on 2011-01-06
You have to purge and not remove firestarter

You can then disable ufw and that will leave you with "the defaults" which are to allow all traffic.

You can see the rules you have for ufw with 

```
sudo ufw status
```

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by tlhodgson on 2011-01-11
Thanks again bodhi. This seems to have fixed my problem. I appreciate your help.

---

### Post by bodhi.zazen on 2011-01-11
Glad you got it sorted out =)

---

