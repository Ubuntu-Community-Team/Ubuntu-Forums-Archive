---
title: "SSH Tunnel connections fails"
date: 2012-02-26
forum: Server Platforms
---

### Post by Hell's Chicken on 2012-02-26
I'm trying to make a tunnel to my master mySQL server, so I can replicate the data on the slave. But I have a problem opening the SSH tunnel. I'm testing it in a local environment. 

I use the following command: 

```
sudo ssh -f ssht@192.168.2.205 -L 3307:192.168.2.205:3306 -N -v
```

With the following result: 

```
Authenticated to 192.168.2.205 ([192.168.2.205]:22).
debug1: Local connections to LOCALHOST:3307 forwarded to remote address 192.168.2.205:3306
debug1: Local forwarding listening on ::1 port 3307.
debug1: channel 0: new [port listener]
debug1: Local forwarding listening on 127.0.0.1 port 3307.
debug1: channel 1: new [port listener]
debug1: Requesting tun unit 2147483647 in mode 1
debug1: sys_tun_open: tunnel mode 1 fd 6
[B]debug1: channel 2: new [tun]
debug1: Requesting no-more-sessions@openssh.com
debug1: forking to background
server@dns2:~$ debug1: Entering interactive session.
debug1: Remote: Failed to open the tunnel device.
channel 2: open failed: administratively prohibited: open failed
debug1: channel 2: free: tun, nchannels 3[/B]

```

I've already tried to fix it, unfortunately with no results. Can anyone push me in the right direction?

---

### Post by Hell's Chicken on 2012-02-27
On google most suggestions I find is to place the following on the server sshd_config: 

```
AllowTCPForwarding yes
```

And to enable ipv4 forwarding on the server: 

```
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
echo 1 | sudo tee /proc/sys/net/ipv4/ip_nonlocal_bind
```

I've already done this, but I keep getting the same error. I'm at a total loss here at this moment :confused: . Is there anyone who can push me in the right direction?

---

### Post by Lars Noodén on 2012-02-27
> **Hell's Chicken said:**
> I use the following command: 

```
sudo ssh -f ssht@192.168.2.205 -L 3307:192.168.2.205:3306 -N -v
```


What about this instead?  Sudo is not needed in this case.

```

ssh -f ssht@192.168.2.205 -L 3307:localhost:3306 -N -v

```

Then try connecting the the MySQL server on port 3307 on the localhost.

---

### Post by Hell's Chicken on 2012-02-27
That worked for me! But it's a little bit weird. Everywhere I look they tell me that I need to connect with the receiving server, not Localhost. 

BTW: I used 127.0.0.1 to prevent mysql from using socks in stead of TCP. 

Thanks for your help :)

---

### Post by Lars Noodén on 2012-02-27
Glad it worked.  I've only ever used 127.0.0.1 or localhost when tunneling between only two hosts.

---

