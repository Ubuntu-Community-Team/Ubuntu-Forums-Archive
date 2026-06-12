---
title: "Why does OpenVPN client fail?"
date: 2015-04-14
forum: Security
---

### Post by johnaaronrose on 2015-04-14
Not sure if this is really a Ubuntu question. I used to have OpenVPN Server with Username & Password Authentication running OK on my Desktop with OpenVPN Client running OK on my Laptop. OpenVPNServer still OK on Desktop but OpenVPN on Laptop now fails:
john@Laptop:~$ cd /etc/openvpn 
john@Laptop:/etc/openvpn$ openvpn --remote 88.97.74.226 --comp-lzo --dev tun --auth-user-pass --ca ca.crt --client 
Tue Apr 14 15:47:10 2015 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec 1 2014 
Enter Auth Username:john 
Enter Auth Password: 
Tue Apr 14 15:47:21 2015 WARNING: No server certificate verification method has been enabled. See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info. 
Tue Apr 14 15:47:21 2015 UDPv4 link local (bound): [undef] 
Tue Apr 14 15:47:21 2015 UDPv4 link remote: [AF_INET]88.97.74.226:1194 
Tue Apr 14 15:47:21 2015 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this 
Tue Apr 14 15:47:22 2015 [VPNServer] Peer Connection Initiated with [AF_INET]88.97.74.226:1194 
Tue Apr 14 15:47:24 2015 ERROR: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1) 
Tue Apr 14 15:47:24 2015 Exiting due to fatal error

Any ideas?

---

### Post by sandyd on 2015-04-14
Sudo is required to create the tun interface, just add sudo in front of the openvpn command.

---

### Post by johnaaronrose on 2015-04-14
Thanks for that. I forgot about it: the instructions that I use have 'sudo su' earlier which I forgot to do.

---

