---
title: "netplan issue with Ubuntu 18.04.1 Server. No network connectivity (no routes either)"
date: 2018-11-03
forum: Server Platforms
---

### Post by uufor44400aa12 on 2018-11-03
I've been using Ubuntu since inception and have recently found out  about Ubuntu's switch to using netplan vs it's traditiona /etc/network/interfaces method.  


  I'm attempting to get this to work but it simply isn't working.   Based on what I can tell, there is no default route, or possibly even a  bad netplan (though ./netplan apply runs correctly). Below is what I'm  doing:


  
[LIST]
[*]Clean/brand new 18.04.1 install on ESXi 
[*]Interface is named ens160 
[*]My IP Address 247.235.60.161 
[*]My Gateway is 247.235.38.51 
[*]My subnet mask is 255.255.255.255 
[/LIST]


 /etc/netplan/01-netcfg.yaml:


  ```
network:
  version: 2
  renderer: networkd
  ethernets:
          ens160:
                  dhcp4: no
                  addresses: [247.235.60.161/32]
                  gateway4: 247.235.38.51
                  nameservers:
                          addresses: [8.8.8.8,8.8.4.4]

```

 When I run "netplan apply" it completes successfully.  If I do with the --debug switch, nothing jumps out (see here: [https://i.imgur.com/aViBohG.png](https://i.imgur.com/aViBohG.png)  ).   "ip link" shows this:  [https://i.imgur.com/Scs7Frv.png](https://i.imgur.com/Scs7Frv.png)


  If I ping 8.8.8.8 I get a "SIOCADDRT: Network is unreachable"


  If I do a "route" to view my routing table, it returns with nothing.  No routing table.  This definitely is an issue.


  If I do an "ifconfig -a" it displays my ens160 interface, correct IP,  netmask of 255.255.255.255, no broadcast address, the mac/ether address  is correct.


  With regards to the addressing/gw/sn, I can confirm that is correct  (I have other hosts running with same/similar on this network/ESXi server). 


  Something is definitely wrong with netplan.  Any ideas?


  Thanks very much for your help!

---

### Post by cariboo on 2018-11-04
It looks like your spacing is off, a yaml file uses spaces, not tabs. Your /etc/netplan/01-netcfg.yaml should look similar to this:

```
network: 
  version: 2 
  renderer: networkd 
  ethernets: 
    enp0s3: 
      addresses: [192.168.107.2/24] 
      gateway4: 192.168.107.1 
      nameservers: 
        addresses: [192.168.107.212,192.168.107.213,1.1.1.1,8.8.8.8]
```

---

### Post by uufor44400aa12 on 2018-11-04
> **cariboo said:**
> It looks like your spacing is off, a yaml file uses spaces, not tabs. Your /etc/netplan/01-netcfg.yaml should look similar to this:


Hey there, thanks for the response!

My forum post here was hand written VS a copy paste due to it being an ESXi instance where copy/paste is not available.  

The server itself is correctly spaced (auto-spaces in vi + no errors on run).  Definitely is something other than spaces :(

---

### Post by darkod on 2018-11-04
Did you set up a static IP during installation or you let it use dhcp and then modified netplan config? I have found that selecting static IP during installation creates the correct netplan file by default.

Also, I know you say your IP and GW data is correct, but I keep wondering. A 247.235.60.161/32 address would not be able to reach the GW 247.235.38.51 in general. It is completely out of the subnet, even if you used /24 that GW would still be out of the range.

I assume you double checked the networking on ESXi level? Made sure the vSwitch/portgroup is correct?

---

### Post by Doug S on 2018-11-04
> **darkod said:**
> Also, I know you say your IP and GW data is correct, but I keep wondering. A 247.235.60.161/32 address would not be able to reach the GW 247.235.38.51 in general. It is completely out of the subnet, even if you used /24 that GW would still be out of the range.
+1 this doesn't make sense. As a test, try a subnet mask of 19.

---

### Post by joebeasley on 2018-11-04
You are using the wrong subnet mask.  Using a /32 means the default gateway is not on the same subnet.

---

### Post by uufor44400aa12 on 2018-11-05
> **darkod said:**
> Did you set up a static IP during installation or you let it use dhcp and then modified netplan config? I have found that selecting static IP during installation creates the correct netplan file by default.

Also, I know you say your IP and GW data is correct, but I keep wondering. A 247.235.60.161/32 address would not be able to reach the GW 247.235.38.51 in general. It is completely out of the subnet, even if you used /24 that GW would still be out of the range.

I assume you double checked the networking on ESXi level? Made sure the vSwitch/portgroup is correct?

Hey there, thanks again for the response!

On installation I skipped the networking portion due to the eternal bug that Ubuntu has in that it does not accept network information that has a GW not on the same subnet as the IP.  For those who are curious, you absolutely can have a GW not on the same subnet as your IP address.  So I skipped the network information and then configured it manually.  

As far as the networking on the ESXi level, that is correct, there are many VMs with the same addressing information (except the IP addy being different).

---

### Post by uufor44400aa12 on 2018-11-05
> **joebeasley said:**
> You are using the wrong subnet mask.  Using a /32 means the default gateway is not on the same subnet.

Hey there, it definitely is correct.  

The subnet has a single host hence the cidr /32.  You are correct, the gateway is not on the same subnet as the IP address (since it is a /32).  The subnet listed is correct.

For what it's worth, if I install Ubuntu 16.04 then this works correctly when I dump it into /etc/network/interfaces.  It also works with other OSes.   It only fails with netplan on Ubuntu versions that require it.

---

### Post by Doug S on 2018-11-05
> **uufor44400aa12 said:**
> For those who are curious, you absolutely can have a GW not on the same subnet as your IP address.Yes, but from what I read before replying earlier today, it isn't straight forward, and routing needs to be specifically taken care of.

If you say it worked for 16.04, I believe you. I am not a fan of netplan, and that is why my servers are still on 16.04.

---

### Post by The Cog on 2018-11-05
ESXi does some strange things with its networking/bridging, making use of its from the drivers that would not work with a real switched network. Maybe this is why your mis-configured networking works on other boxes though I am surprised that it does. It appears that netplan is doing more sanity checking and ignoring erroneous configuration. You really should correct your subnet mask, although configuring the interface as a point-to-point link instead of a normal ethernet link might possibly work, given ESXI's special knowledge.

---

### Post by darkod on 2018-11-05
I'm sorry, but it still doesn't make sense (whether or not there is a way to assign a GW outside of the subnet). I still haven't seen a provider that will assign you a GW that is outside of the subnet.

Has your internet provider given you these public IPs to use? I have seen cases where people go against all rules and use public ranges for private networks.

I cannot think of any case why a provider would give you such confusing info for IP and GW to use. They always assign a GW inside the subnet, regardless what that subnet size is.

---

### Post by mpaszek on 2019-07-12
> **uufor44400aa12 said:**
> I've been using Ubuntu since inception and have recently found out  about Ubuntu's switch to using netplan vs it's traditiona /etc/network/interfaces method.  


  I'm attempting to get this to work but it simply isn't working.   Based on what I can tell, there is no default route, or possibly even a  bad netplan (though ./netplan apply runs correctly). Below is what I'm  doing:


  
[LIST]
[*]Clean/brand new 18.04.1 install on ESXi
[*]Interface is named ens160
[*]My IP Address 247.235.60.161
[*]My Gateway is 247.235.38.51
[*]My subnet mask is 255.255.255.255
[/LIST]


 /etc/netplan/01-netcfg.yaml:


  ```
network:
  version: 2
  renderer: networkd
  ethernets:
          ens160:
                  dhcp4: no
                  addresses: [247.235.60.161/32]
                  gateway4: 247.235.38.51
                  nameservers:
                          addresses: [8.8.8.8,8.8.4.4]

```


I had the same problem, mine working yaml:
```

network:
  version: 2
  renderer: networkd
  ethernets:
          ens160:
                  dhcp4: no
                  addresses: [247.235.60.161/32]
                  gateway4: 247.235.38.51
                  nameservers:
                          addresses: [8.8.8.8,8.8.4.4]
          [B]routes:
              - to: 247.235.38.51
                scope: link[/B]

```

---

### Post by volkswagner on 2019-07-13
> **darkod said:**
> I'm sorry, but it still doesn't make sense (whether or not there is a way to assign a GW outside of the subnet). I still haven't seen a provider that will assign you a GW that is outside of the subnet.

Has your internet provider given you these public IPs to use? I have seen cases where people go against all rules and use public ranges for private networks.

I cannot think of any case why a provider would give you such confusing info for IP and GW to use. They always assign a GW inside the subnet, regardless what that subnet size is.

I'm no expert and like to learn. 

Wouldn't the act of avoiding breaking up larger networks into multiple /29 or /27, etc. free up precious IP addresses?
If the provider hands out a range of usable IP addresses and a gateway, without specifying /29 or any subnet for that matter,
avoid loosing first and last ip of all the /29s?

I'm just guessing here.

Sorry if this leads off topic, but it seems not everyone knows everything.... especially me!

---

