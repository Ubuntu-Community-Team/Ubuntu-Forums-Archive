---
title: "Virtual machine network adapter advice - Apache2"
date: 2022-05-25
forum: Virtualisation
---

### Post by caston101 on 2022-05-25
I've been tasked with setting up an outdated version of Ubuntu 16.04 with Apache2 webserver version 2.4 installed on a virtual machine, with the intention of discovering exploits and vulnerabilities. 
This will involve using nmap to scan the network and using metasploitable to run scripts. I am unsure on which network adapter would be most apropriate for a task like this given I will be running apache webserver.  

Should I use bridged adapter and run the ubuntu through my own network? Or should I use something like NAT? Thanks.  

Also I want to note that I will be using a seperate machine on virtualbox running Kali linux where i will be running nmap, metasploit and other tools.

---

### Post by spjackson on 2022-05-26
It sounds to me like you need bridged. NAT works if you only make outbound connections. If you want inbound connections (including ssh) it is either impossible (in my experience) or very difficult to achieve with NAT.

---

### Post by caston101 on 2022-05-26
Great thank you.

---

### Post by SeijiSensei on 2022-05-26
Or you could use NAT and run those tools on the host machine. But if you need the VM to be visible to other machines on your network, you must use a bridged adapter.

---

### Post by MAFoElffen on 2022-05-28
Or setup a Private Virtual Network with one router node on it pointing to a bridged virtual switch... For limited / outside connection to the outside, when needed. That node powered off during the testing.

Setup all your nodes (Sources and Targets) on that private network... With your own imagination and some creative networking skills, you can get wild with what you can create.

 That way you can do all the penetration and exploit testing you need to do, without any danger to your own base network. The benefit of a virtual host, is that you can create virtual networks, to keep things "contained".

I have tested networking schemes and subnets on virtual hosts... for proposed live network changes. That is what is good with Cisco Packet Tracer, to prototype, then implement on a virt host... then go live.

[s]What penetration tools do you plan to use?[/s]

---

