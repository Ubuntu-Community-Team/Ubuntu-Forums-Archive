---
title: "openVPN connection issues"
date: 2009-01-10
forum: Server Platforms
---

### Post by coffinzm on 2009-01-10
I am running openvpn 2.06 on a Dapper 6.06 - about all the computer can handle.

I have configured openvpn bridge so that I am able to log into my server from another computer on my network and am assigned a new ip address.  However, I am not able to establish a connection to the vpn server from outside my network.  I don't believe the issue has to do with router ports and forwarding because my openvpn terminal is spitting out line after line of the external client's ip address followed by "write UDPv4 Network is Unreachable (code=101)".
It also issues the error "TLS ley negotiation failed to occur within 60 seconds" and "TLS error: TLS handshake failed".

This is the output of my bridge-start.sh script:
> 
Sat Jan 10 01:13:47 2009 Note: Cannot ioctl TUNSETIFF tap0: Device or resource busy (errno=16)
Sat Jan 10 01:13:47 2009 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Sat Jan 10 01:13:47 2009 Cannot open TUN/TAP dev /dev/tap0: No such file or directory (errno=2)
Sat Jan 10 01:13:47 2009 Exiting
device br0 already exists; can't create bridge with the same name
device eth0 is already a member of a bridge; can't enslave it to bridge br0.
./bridge-start.sh: line 30: cert: command not found
./bridge-start.sh: line 31: cert: command not found
./bridge-start.sh: line 32: key: command not found
./bridge-start.sh: line 33: key: command not found

I am aware that bridge-start cannot find my certificates but I've tried pointing to them in the script and still got the error.

bridge-stop.sh freezes my ssh windows and will not let me log back in until the server is rebooted.

Copies of my server config file, bridge-start and bridge-stop are attached.  My authentication keys are stored in a folder "Keys" in the directory which contains these config files.

Update - the problem seems to have something to do with br0 taking over my server's local ip address, essentially pointing all incoming traffic to br0 and not to my eth0.  I'm still not sure how to fix this.


Thank you ahead of time for your help!

---

