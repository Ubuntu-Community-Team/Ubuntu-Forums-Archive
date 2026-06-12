---
title: "Some services not autostarting"
date: 2009-12-20
forum: Server Platforms
---

### Post by fizgig on 2009-12-20
I have two computers I use as servers but they have the regular ubuntu 9.10 version installed on them since I do have monitors connected to them and like the graphical tools on occasion.

I installed openvpn on one of them and it works great - when it's running.  I used this [tutorial]("https://help.ubuntu.com/community/OpenVPN").  I can start the service as so:  **/etc/init.d/openvpn start** and I'm off and running - can connect just fine.  If I reboot the computer, it doesn't autostart despite the fact that I see an entry in the /etc/rc2.d directory: S20openvpn.

I'm having a similar problem in the other computer:  Samba doesn't start unless I run **/etc/init.d/samba start**.  It too has an entry in the /etc/rc2.d directory.

One last thing:  both computers have virtualbox on them which has an xp client in bridge mode.  The openvpn server also has a network bridge as part of the vpn setup.  Not sure if that makes a difference but I suppose that might interfere with the network startup time or something.

Anyone have a guess why this is happening?  It's driving me nuts.

---

### Post by munky99999 on 2009-12-20
samba not starting is a known bug in karmic. Maybe openvpn suffers from the same family issue.

My current fix for this issue. Never turn the computer off. :guitar:

---

### Post by fizgig on 2009-12-21
Ah.  Found the samba bug here:  [https://bugs.launchpad.net/ubuntu/karmic/+source/samba/+bug/462169](https://bugs.launchpad.net/ubuntu/karmic/+source/samba/+bug/462169)

I imagine you're right - that openvpn might have the same issue...

---

### Post by tUrtleAE86 on 2010-01-01
For clarity, here is what is shown in /var/syslog by the init.d:
```
Jan  1 14:59:09 vostro ovpn-server[1080]: OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Jan  1 14:59:09 vostro ovpn-server[1080]: NOTE: when bridging your LAN adapter with the TAP adapter, note that the new bridge adapter will often take on its own IP address that is different from what the LAN adapter was previously set to
Jan  1 14:59:09 vostro ovpn-server[1080]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jan  1 14:59:09 vostro ovpn-server[1080]: Diffie-Hellman initialized with 1024 bit key
Jan  1 14:59:09 vostro ovpn-server[1080]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Jan  1 14:59:10 vostro ovpn-server[1080]: Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Jan  1 14:59:10 vostro ovpn-server[1080]: Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Jan  1 14:59:10 vostro ovpn-server[1080]: Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Jan  1 14:59:10 vostro ovpn-server[1080]: TLS-Auth MTU parms [ L:1576 D:168 EF:68 EB:0 ET:0 EL:0 ]
Jan  1 14:59:10 vostro ovpn-server[1080]: TCP/UDP: Socket bind failed on local address x.x.x.x:x: Cannot assign requested address
Jan  1 14:59:10 vostro ovpn-server[1080]: Exiting
```

If I manually run **/etc/init.d/openvpn start**, OpenVPN starts correctly. Indeed, it looks like the the network isn't initialized when OpenVPN is trying to start.

---

### Post by steven.jones on 2010-01-02
Do a who -r this will print out your run level, you may not be at 2.

---

### Post by fizgig on 2010-01-13
Confirmed that I'm at level 2.

The Samba issue seems to have been fixed but the openvpn server still isn't autostarting.

---

### Post by noway2 on 2010-02-09
I recently upgraded to Karmic and ran into this trouble too.  Actually, I ran into multiple problems with the same symptom that process would no longer start.

With respect to openvpn, the problem appears to be a race condition in the startup.  Initially, I found in syslog that after a boot up that it exited the start process after it couldn't resolve the (local lan) name of the server to its ip address, along with a comment that it received a temporary error response from an authoritative DNS.  This told me that Bind9 apparently wasn't up and running yet.

Next, instead of setting local server.name, I set it to the lan IP address.  This time it complained that it couldn't obtain the socket on that address or some other garbage.  

In the end, I changed the order of openvpn from S16 (Bind is at S15) to S95 to put it towards the end.  I noticed that the DHCP process is around S35, which will assign the (static) IP address to the server.  Consequently, it may be that openvpn needs to come after the DHCP?

Thankfully, I do not appear to have any problems with samba as that seems to be running.

---

### Post by Xi0N on 2010-07-27
Any solution for this?

The very same problem in here: Openvpn was working until some update today: Starting the server, but openvpn cannot start

```
TCP/UDP: Socket bind failed on local address
```

If i run it manually, it does.... any solution, please???:(

---

### Post by eldo on 2010-09-07
> **Xi0N said:**
> Any solution for this?

The very same problem in here: Openvpn was working until some update today: Starting the server, but openvpn cannot start

```
TCP/UDP: Socket bind failed on local address
```

If i run it manually, it does.... any solution, please???:(

try to use
```
bridge_maxwait 0
```
at /etc/network/interfaces

---

### Post by linuxmunky on 2010-11-11
Thanks eldo, I was experiencing the same problem and that fixed it.  Cheers!:)

---

