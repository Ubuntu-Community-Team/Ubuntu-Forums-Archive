---
title: "VM-Ware Host; Ubuntu Client with static IP Not working"
date: 2010-12-15
forum: Virtualisation
---

### Post by Jense on 2010-12-15
Hi,

I have a VM-Ware on which I have several clients. Yesterday I tried to copy one of these, running with a fixed IP (original mashine), and created a new virtual mashine from the image (copied mashine). I then changed the static IP in /etc/network/interfaces.

However, I just can't ping anything other then localhost. When I try the route command, which works perfectly on the original mashine, I noticed that that on the copied mashine, the gateway is missing. 


I would love to post some info, put I can't CP from the VWM-Ware-Console, so here some facts:

- ifconfig show eth0 with the new static IP
- I can ping 127.0.0.1 
- I can't ping anything else
- It is not a private IP (so nothing like 192.168....)
- the route command doesn't show the default gateway setup in /etc/network/interfaces as it does on the original mashine
- on ```
sudo route add default gw 195.167.xyz.zxy eth0
``` I get an error: SIOCADDRT: No such procress

I am really stuck here and really need this server running. Also the VM-Ware Console ist a pain .... I would much rather configure this thing properly using ssh. So any help, please :-).

---

