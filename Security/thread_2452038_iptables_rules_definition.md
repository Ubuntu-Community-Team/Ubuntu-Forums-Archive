---
title: "iptables rules definition"
date: 2020-10-15
forum: Security
---

### Post by LeBabe on 2020-10-15
I have 2 networks like this :

Site A : 

 - Subnet 10.1.1.0/24
 - Multiple machines on this subnet.
 - 3 Servers on ip nodes : .1,.2,.3
 - A GRE box that mount a tunnel to Site B on ip node : .20
 - A CPE on ip node .254

 Site B : 

 - Subnet 10.2.1.0/24
 - Multiple machines on this subnet.
 - A GRE box that mount a tunnel to Site A on ip node : .20
 - A CPE on node ip .254
 

Between them Internet.

No issue with GRE tunnel, It mount without any issue.

GRE "A" has a tunnel interface on 10.10.10.1 and GRE "B" has a tunnel interface on 10.10.10.2

All machines on each sides of the tunnel can communicate.


I would like to allow only the three servers of side A to communicate with PCs of site B.

I made this configuration on GRE machine on site A, but I have no skill on iptables so it does not work as I would like :

    ```
-A INPUT -s 10.1.1.1/32 -i ens160 -j ACCEPT
    -A INPUT -s 10.1.1.2/32 -i ens160 -j ACCEPT
    -A INPUT -s 10.1.1.3/32 -i ens160 -j ACCEPT
    -A INPUT -s xxx.xxx.xxx.xxx/28 -i ens160 -p gre -j ACCEPT  ### xxx.xxx.xxx.xxx is Site B Pub IP
    -A INPUT -i ens160 -p gre -j DROP
    -A INPUT -i ens160 -j DROP
```

With this config,no traffic is blocked between sites, so any machine is able to contact any one elses. The only thing that is blocked is the direct access to the GRE box from a machine on Site A.

For instance : PC with ip 10.1.1.5 is able to contact any one site B whereas it should not.

Many thanks by advance to anyone that could lead me to a solution.

---

### Post by SeijiSensei on 2020-10-15
```

    -A INPUT -s 10.2.1.0/24 -d 10.1.1.1/32 -j ACCEPT
    -A INPUT -s 10.2.1.0/24 -d 10.1.1.2/32 -j ACCEPT
    -A INPUT -s 10.2.1.0/24 -d 10.1.1.3/32 -j ACCEPT

    -A INPUT -d 10.2.1.0/24 -s 10.1.1.1/32 -j ACCEPT
    -A INPUT -d 10.2.1.0/24 -s 10.1.1.2/32 -j ACCEPT
    -A INPUT -d 10.2.1.0/24 -s 10.1.1.3/32 -j ACCEPT

    -A INPUT -s 10.1.1.0/24 -d 10.2.1.0/24 -j REJECT
    -A INPUT -s 10.2.1.0/24 -d 10.1.1.0/24 -j REJECT
   
```
The first six rules permit traffic to and from the 10.2.1.0/24 subnet and the .1, .2, .3 machines. The last two block all other traffic between subnet 10.1.1.0/24 and subnet 10.2.1.0/24. You may want to make them more liberal.  

I'm not sure what the last two lines you posted are designed to accomplish.

---

### Post by LeBabe on 2020-10-16
Thanks,

I'll give a try!

---

### Post by LeBabe on 2020-10-16
Hi,

Unfortunately, result is the same, any machine on Subnet A is able to contact equipment on subnet B

---

### Post by LeBabe on 2020-10-16
Hi,

Found the solution, the issue was the rules had to be applied to FORWARD chain and not INPUT.

Works like a charm.

Thanks, you lead me to the solution!

---

### Post by SeijiSensei on 2020-10-16
You're welcome. I wondered which chain might be most appropriate. Please go to the Thread Tools drop-down at the top of this page and mark the thread [SOLVED].

---

