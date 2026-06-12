---
title: "ssh server help"
date: 2019-12-13
forum: Windows
---

### Post by matt18 on 2019-12-13
Ok, so my ISP blocks ssh at the protocol level, not just the port, but the actual service at their edge routers right before it hits my home router.  I have confirmed this with them. 

I have a windows 10 machine at home as the sftp server. My goal was to be able to access my pdf's, school files, etc while using a random PC at school or the library.

How do i achieve this now?

thanks

I need to be able to use portable, USB apps since i do not have rights at the library or school to install any software:)

---

### Post by TheFu on 2019-12-13
You cannot using any ssh/scp/sftp method.

Which protocols does the ISP not block?  Will a UDP-based VPN work?
You can try a few of these:
* openvpn
* wireguard
* HTTPS (which is fine for privacy but not really security).

It also might be that the ISP is not providing public IPs. If that is the case, the only way around this is to get a VPS and setup a VPN or reverse ssh tunnel between your home and the VPS.

VPS - virtual private server
VPN - virtual private network

---

### Post by matt18 on 2019-12-14
thanks for the repl;y:) i can uise hamachi VPN just fine and open VPN, only problem is, that if i go to a pc at the school or library i do not own, i cant use either of the vpn options since it requires admion rights to install the driver.

I do have a public IP, they just want more money and block protocols that have to do with servers. They block http and ssh from comming into the network so home users cant have a web site at home, unless they pay the ISP for a business line

I do have an amazon EC2 ubuntu instance. maybe have a reverse ssh from my home server to the vps, then any remote connection to the vps will be forwarded?

---

### Post by SeijiSensei on 2019-12-14
You might be able to set up an [OpenVPN tunnel]("https://openvpn.net/community-resources/static-key-mini-howto/") between your computer at home and the EC2 instance.  Then you could use iptables to forward port 22 on the instance back to port 22 on the machine at home. Make the computer at home the OpenVPN client and the instance be the OpenVPN server.

---

### Post by matt18 on 2019-12-14
> **SeijiSensei said:**
> You might be able to set up an [OpenVPN tunnel]("https://openvpn.net/community-resources/static-key-mini-howto/") between your computer at home and the EC2 instance.  Then you could use iptables to forward port 22 on the instance back to port 22 on the machine at home. Make the computer at home the OpenVPN client and the instance be the OpenVPN server.

Since i am new to vpn tunnels, i want to make sure i am understanding  you. If i make the EC2 instance the openvpn server, then my home windows  10 machine the client, i can go to a random PC that i do not own in my  university, library, friends house, etc, sftp to the EC2 server, which  in turn will forward the sftp traffic to my home windows 10 machine,  which in turn will respond with the sftp server and allow me to access  my files?

thanks

---

### Post by QIII on 2019-12-14
We are getting dangerously close to a discussion of circumvention of ToS/Policy here.

You should discuss with both your school and your ISP what protocols/technologies would be acceptable with them and use those.

Closed.

---

