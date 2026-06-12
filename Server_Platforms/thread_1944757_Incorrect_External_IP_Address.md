---
title: "Incorrect External IP Address"
date: 2012-03-21
forum: Server Platforms
---

### Post by ruready511 on 2012-03-21
Hey guys!
 
I'm new here at the forums, but have been using Ubuntu on and off for several years. In my quest to bring more open source software into the workplace, I've just setup and configured an Openfire 3.7.1 chat server running on my slick little Ubuntu 10.04 LTS x86 server in VMware VI3 (it's old, I know). So far I love it, but I'm stuck with a problem I just can't figure out.
 
It's pretty complicated, but I'll try to trim it down as much as possible (although I'll be happy to answer any detailed questions):
 
I have an Untangle 9.2.0 server acting as my gateway. There are 3 NICs on the gateway - 1 is for internal traffic and 2 are for external traffic. Each of the 2 external NICs are configured with a different netblock. As of right now, all of my public hosts are put online by using 1-to-1 NAT policies on my internal interface and port forwards on the external interface(s). This has been setup for a long time and has been working perfectly fine for several years.
 
**EDIT:** The method of port forwarding my internet facing hosts has worked for several years, however the addition of the second external NIC's netblock is brand-spanking new. Right now, the Ubuntu server is the only host on this newly acquired netblock (aside from the gateway itself - which is pingable from the outside world).
 
My problem is that when I use the same configuration for my newly configured Ubuntu server, I cannot connect to it from outside my network. Additionally, when I try to grab the external IP address, it returns an address that is not on any of my netblocks or my ISP's netblocks. I'm getting the external IP like so:
```

curl [http://whatismyip.org](http://whatismyip.org)

```
 
Now, this is affecting some other areas and I'm not sure if the problem is rooted in Untangle just yet, but I'm having SMTP routing issues now. If you're reading this and you're an Untangle guru, I do have the WAN Failover and WAN Balancer apps running in my rack and I do have, what I believe to be, correct source routing rules. I've also installed the WAN Balancer patch for v9.2.0. The patch *may* have fixed my SMTP routing issues, but I'm still testing that.
 
Anyway, if anyone could help me understand why I'm getting a weird address as my external IP, it would really help me.... I think.
 
Thanks guys!
-David

---

### Post by hawkmage on 2012-03-21
If you do a traceroute from your Ubuntu system does it go out the proper interface?  

Do you have any idea where the the "external" ip you are seeing is from?  If it is not your NATing interface nor your ISPs it is almost has to be a NATed interface of some other network.

---

### Post by ruready511 on 2012-03-21
When I run traceroute to google.com the first 4 hops are unavailable. But that further confuses the matter because I can still resolve google.com and ping it.
 
I did just lookup that external IP address that I'm seeing on whatismyip.org and it turns out that it does belong to my ISP. But it's like way upstream and does not show up on any of the hosts in the traceroute path. Weird.

---

### Post by ruready511 on 2012-03-21
Humm, and I can't ping that address either...
 
I'm waiting for a call back from my ISP. I'll post some more info tomorrow.

---

### Post by ruready511 on 2012-03-22
Well that was fun. Turns out that my ISP had incorrectly provisioned my netblock in their NOC.
 
Waste of time - sorry guys...

---

