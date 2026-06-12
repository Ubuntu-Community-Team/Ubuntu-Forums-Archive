---
title: "OpenVPN.. need help.."
date: 2010-01-05
forum: Server Platforms
---

### Post by artheus on 2010-01-05
Hi!

I've set up a simple OpenVPN connection using the guide on
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

And it's working fine. But the samba shares on the server which also holds the OpenVPN server won't show up on my remote computer.

Are there any way of getting that?

Cheers,
Artheus

---

### Post by artheus on 2010-01-05
Solved this myself.. The only problem was that I was trying to connect with the hostname, and not the ip-adresse. So now it's working.

Cheers,
Artheus

---

### Post by noway2 on 2010-02-01
Would you please elaborate on this solution, I do not understand what you mean by connecting (browsing) for it by hostname instead of ip address?

When I am physically on my LAN, the samba shares appear just fine in the network group.  When I am connected via VPN, they do not.  

I am using a TAP (bridged) connection.  I have set various dhcp-options in the openvpn configuration, including wins, which is supported and enabled in the samba configuration.  All to no avail.

---

### Post by artheus on 2010-02-02
Well my default DNS configuration is that the DNS gets the hostnames of the machines in the network. But when trying to connect to the machines by their hostnames through VPN, it wouldn't connect. So I had to config the hosts file on each computer in the network to point to the correct IP adresse.

So are you trying to connect with the machine IP's or with the hostnames of the computers?

Cheers,
Artheus

---

### Post by noway2 on 2010-02-02
My (remote) connection to the VPN server is made via the public domain name of the server.  Once connected, I have the DHCP-Option to push the DNS data to the remotely connected PC from the LAN server.  This appears to work because I can see and ping any LAN resource via the name, and I can resolve LAN names and SSH into them as resources.  The LAN uses an authoritative DNS server so I usually avoid using a hosts file.

I did a little more investigation and things are even more strange.  It turns out that on a remotely connected Linux system, I can not see the samba resources via the network explorer.  I can, however, connect to them via name if I manually mount it.  For example, if I create a directory called /mnt/shared and then use sudo smbmount //server/share /mnt/shared, the samba share on the server will appear in the shared directory under mnt.  It turns out that if I connect using a windows system (vista in this case) that I can see the samba share under the workgroup and can even map a network drive to it.

What doesn't work is seeing the samba share via Linux network explorer, which does work when I am on the LAN.  This suggests that some option or data for Linux is not being transmitted over the VPN, but windows has what it needs (a strange twist that windows works and Linux doesn't).

---

