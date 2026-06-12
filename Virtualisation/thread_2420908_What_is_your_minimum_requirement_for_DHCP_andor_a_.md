---
title: "What is your minimum requirement for DHCP and/or a DNS server?"
date: 2019-06-12
forum: Virtualisation
---

### Post by webmiester on 2019-06-12
Hi guys,

I am currently designing my network. I will be virtualizing my DHCP and DNS servers.  I have the impression that the DHCP can be handled by small consumer grade products as well as computers like the RPi.  So this being said, I have the impression that it takes very little computational power to handle DHCP.

I understand that in VMs, we can specify what specs we would like the VM to have, such as how many cores, hard disk size, and memory size, right?  And I heard that in some cases, we can even emulate the kind of processor to use.  So with these being said,  If you were to make a VM for a sole DHCP server, what would be the bare minimum specs you would give it?

If you were to make a combined DHCP and DNS server, what would be your minimum specs.  Thanks so much.

I would like this device to handle only the DHCP, no firewall or other functions.  Thank you.

---

### Post by TheFu on 2019-06-12
How many clients?
How many networks?
10,000 clients needs more hardware/networking/CPU than 25.

---

### Post by kpatz on 2019-06-12
Consumer grade products have minimal OSes on them.  A VM will have a more substantial Linux kernel so it's likely going to need at least a little more RAM and CPU than that little router in the plastic box.

Ubuntu Server recommends a minimum of 2 GB disk space to install, for example.  I didn't find a RAM requirement, but 512 MB should be plenty.  With a VM you can easily change the RAM and disk sizes once you have an idea of how much it will need.  If you're just running isc-dhcp-server, and maybe BIND9 for DNS, I expect the space required will be minimal.  You'll want ssh as well, so you can log in and tweak things.

Once everything is set up (and you've uninstalled or disabled what you DON'T need), use top, htop and free to see how much RAM you're using.  Then size the RAM of the VM accordingly (leave a little buffer).

For disk space, take caching (of DNS), storage of DHCP lease info and logs into account.

If you need DHCP and DNS, you might as well put them in the same VM, unless you have specific security requirements.

Older kernels tend to be smaller than newer ones, so maybe a distro like Centos 7 that uses the 3.10 kernel would fit a tiny VM better than Ubuntu.

I don't know if any VM products can emulate an RPi's architecture or not, but if you can run the rPI OS in a VM it should be able to run in very little RAM.  But if you're going to do that, you might as well just run it on a Pi.

---

### Post by webmiester on 2019-06-12
There will be a total of 5 networks, so Ill be putting up 5VMs with a NIC attached to each one

The smallest network just has around 5 computers
The largest network has around 30 computers.  It will be the only one to use the DNS server.

As for the OS.  The host OS will be ubuntu (that's why Im here,hehehe).  But for the OSs that will host DHCPs, we can still use ubuntu, but I am also condiering lightweight alternatives such as puppy linux. 

So, what would be your minimal requirements?  An Rpi runs DHCP with an 8GB SD card, 1Gb memory, and just 1 core.  Can I go for just 2GB or less of harddisk space?  Thanks

---

### Post by webmiester on 2019-06-12
Thanks.  Yeah, I am thinking of trying out puppy linux so the space will be smaller with the host being ubuntu, although I would like to stick to ubuntu so I dont have to study new command lines and just stick to this forum for help.

yeah Centos is pretty good too, but I would like to use ubuntu as much as possible.  Ive been on ubuntu for a few years, and I dont want to learn new command lines for CentOS.  Yes, its linux, but some commands are different and I just want to stick to one for simplicity.  I think puppy is debian too , so its command lines would be closer, but if I can just sitck to ubuntu, I would.

Anyway, 2Gb of space isnt big considering that the server will have 1TB of harddisk.  Thanks so much for the inputs!

---

### Post by Tadaen_Sylvermane on 2019-06-12
I may be mistaken but i think a single isc dhcp server can handle as many networks as you want with a single instance. Shouldn't need 5 separate vms. Simpler is always better.

---

### Post by kpatz on 2019-06-13
Is this server going to host VMs for other purposes as well?  Might as well make use of that 1TB drive for more than just a DHCP server.

What are you using for an internet connection, firewall, routing (to internet as well as the 5 networks?)  Often a Linux system is set up as a firewall, router, DHCP, and DNS all on the same box.

Are these 5 networks physically separate, connected via routers?  Is your box going to have a NIC for each?  Or are they VLANs?

---

### Post by TheFu on 2019-06-13
Lost my original reply.  Abbreviated follows.

Don't use a r-pi HW for critical infrastructure. Those are the lowest priced devices as their primary goal.

1 VM can handle DNS/DHCP for 5 connected subnets, as Tadaen_Sylvermane says. Businesses do this all the time. Probably want at least 2 VMs for redundancy of critical infra.  Don't put them on the same physical machine.  If you intend to make DNS available to the outside, you'll need a master-slave setup where the master isn't on the network most of the time and slaves handle DNS.  DNS has been hacked over the years.  In 2002, I was running BIND and got hacked. Be VERY careful if you make it available on the internet.

All computers need to run a minimal firewall that allows access for only the services configured. Attacks come from inside too.  Think of the guest visiting in the conference room.  Do those LAN ports connect to the internal LAN or directly to the internet?  Any wifi there? Do you trust it or secure it?

Don't use puppy linux for critical server infrastructure. The design goals of puppy don't align with the needs of a server. There are light distros like Alpine for running 1-trick VMs and containers.  CentOS is not lighter than Ubuntu Server.

Avoid running internal-only services on WAN firewalls.  DNS is critical infrastructure since it is part of all HTTPS connections. If the DNS is hacked, all those connections can be sent anywhere, show the little green key icon, and very few people would notice.  Keep internal DNS away from the internet.

Sorry if that is all too choppy. Busy day.

---

### Post by SeijiSensei on 2019-06-13
The first server I built to provide DHCP and DNS was an i486 with 1 MB of memory.  Services like these have minimal hardware demands. Remember both dhcpd and named will be idle well over 90% of the time as they wait for requests. 

Those same i486 servers would also be running Apache, sendmail, and a few other things I can't recall now. Most the time their load averages were around zero.

---

### Post by webmiester on 2019-06-18
> **kpatz said:**
> Is this server going to host VMs for other purposes as well?  Might as well make use of that 1TB drive for more than just a DHCP server.

What are you using for an internet connection, firewall, routing (to internet as well as the 5 networks?)  Often a Linux system is set up as a firewall, router, DHCP, and DNS all on the same box.

Are these 5 networks physically separate, connected via routers?  Is your box going to have a NIC for each?  Or are they VLANs?

Yeah, I plan to virtualize some of the office computers and have the access their "computer" through remote desktop protocol.  I need to test how many we can put in before they start experiencing slowdown.  My current test server is a 7th Gen Core i7 with 16g memory.  I want to make one from xeon, but its quite pricey.

---

### Post by webmiester on 2019-06-18
> **TheFu said:**
> Lost my original reply.  Abbreviated follows.

Don't use a r-pi HW for critical infrastructure. Those are the lowest priced devices as their primary goal.

1 VM can handle DNS/DHCP for 5 connected subnets, as Tadaen_Sylvermane says. Businesses do this all the time. Probably want at least 2 VMs for redundancy of critical infra.  Don't put them on the same physical machine.  If you intend to make DNS available to the outside, you'll need a master-slave setup where the master isn't on the network most of the time and slaves handle DNS.  DNS has been hacked over the years.  In 2002, I was running BIND and got hacked. Be VERY careful if you make it available on the internet.

All computers need to run a minimal firewall that allows access for only the services configured. Attacks come from inside too.  Think of the guest visiting in the conference room.  Do those LAN ports connect to the internal LAN or directly to the internet?  Any wifi there? Do you trust it or secure it?

Don't use puppy linux for critical server infrastructure. The design goals of puppy don't align with the needs of a server. There are light distros like Alpine for running 1-trick VMs and containers.  CentOS is not lighter than Ubuntu Server.

Avoid running internal-only services on WAN firewalls.  DNS is critical infrastructure since it is part of all HTTPS connections. If the DNS is hacked, all those connections can be sent anywhere, show the little green key icon, and very few people would notice.  Keep internal DNS away from the internet.

Sorry if that is all too choppy. Busy day.

Well, none of the DHCP should be available on the internet.  Besides the DHCP, Im thinking of putting another VM to run a firewall such as PFsense (or ubuntu running squid), as well as virtualized versions of the office computers.  Computers which need internet access need to virtually pass through the firewall first.

---

### Post by webmiester on 2019-06-18
> **TheFu said:**
> Lost my original reply.  Abbreviated follows.

Don't use a r-pi HW for critical infrastructure. Those are the lowest priced devices as their primary goal.

1 VM can handle DNS/DHCP for 5 connected subnets, as Tadaen_Sylvermane says. Businesses do this all the time. Probably want at least 2 VMs for redundancy of critical infra.  Don't put them on the same physical machine.  If you intend to make DNS available to the outside, you'll need a master-slave setup where the master isn't on the network most of the time and slaves handle DNS.  DNS has been hacked over the years.  In 2002, I was running BIND and got hacked. Be VERY careful if you make it available on the internet.

All computers need to run a minimal firewall that allows access for only the services configured. Attacks come from inside too.  Think of the guest visiting in the conference room.  Do those LAN ports connect to the internal LAN or directly to the internet?  Any wifi there? Do you trust it or secure it?

Don't use puppy linux for critical server infrastructure. The design goals of puppy don't align with the needs of a server. There are light distros like Alpine for running 1-trick VMs and containers.  CentOS is not lighter than Ubuntu Server.

Avoid running internal-only services on WAN firewalls.  DNS is critical infrastructure since it is part of all HTTPS connections. If the DNS is hacked, all those connections can be sent anywhere, show the little green key icon, and very few people would notice.  Keep internal DNS away from the internet.

Sorry if that is all too choppy. Busy day.

1 VM can handle the 5 subnets, and that should be able to free up resources, but considering that DHCP consumes such a low amount of resources, will it be more secure to have them in separate VMs?  In this case if one DHCP gets hacked, it wont affect the others, right?

Thank you for the RPi thing.  We wont be using RPi for the DHCP, Ill use a heavy duty server for this.  All addresses on the LAN will be static with MAC address binding.  Only wifi will have dynamic DHCP and that will run on its own network switch (but its dhcp and radius server will be on the same physical machine as the other dhcp's).  The wifi will run on its own network and subnet so those getting into the wifi will hopefully not access the LAN, but a VM will still provide DHCP, and radius authentication for that wifi network.

The application server is a separate physical unit with IP tables to screen off devices.  I still have to figure out how to put SSL certificates on my computers so that everyone accessing the server locally needs to be SSL certified too.  If you have links on how to do the SSL certification, I will appreciate it too although it is off topic on this thread.

---

