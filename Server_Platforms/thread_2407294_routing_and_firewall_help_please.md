---
title: "routing and firewall help please"
date: 2018-12-02
forum: Server Platforms
---

### Post by lfnfan on 2018-12-02
Hello
I would really appreciate any support solving a [probably simple] network problem I am struggling with.  I suspect either routing or firewall setup is defective, but can't pinpoint the error.

I cannot get my smartphone to access the files on my home server, which is also serving as an OpenVpn server. The actual OpenVpn connection works fine.

My set up is as follows:
```

-------wan
xxx.xxx.xxx.xxx
|
|
---------  OpenVpn server
-------------172.19.14.114 / 10.8.0.1
|
|
-----------------------connected-smartphone
-----------------------------------------10.8.0.4
```

When the VPN is up, I can ping 10.8.0.4 from my OpenVpn server.  I can also ping 10.8.0.1 from my smartphone.

I have tried to check:
- configuring my nfs shares and samba shares correctly
- setting up my static route on my router/modem
- setting up my firewall rules
- /etc/sysctl has forwarding=1

I am running Ubuntu 16.04 server 4.4.0-139-generic

I would be delighted to post whatever info you think necessary to pinpoint my error.

Many thanks in advance

Paul

---

### Post by howefield on 2018-12-02
Thread moved to the "*Server Platforms*" forum.

---

### Post by volkswagner on 2018-12-02
Are you trying to access files located on the server while away from home (assuming server is at home)?
Are you able to access those files while at home?
What apps are you using on the smart phone to access the files?
Do you need both NFS and SAMBA via the VPN on your phone?
Can you ping 172.19.14.114 from your phone while connected to VPN?
Rather than getting services to work with the tun network, you may just need
routing for the VPN client to be able to connect to the regular LAN.

See [https://community.openvpn.net/openvpn/wiki/RoutedLans](https://community.openvpn.net/openvpn/wiki/RoutedLans)
You may want to add the following to your openvpn client config:
```
push "route 172.19.14.0 255.255.255.0"
```
With the above you should be able to ping 172.19.14.114 from
the VPN client and also reach services like SAMBA at 172.19.14.114 from
the vpn client.

Can you post output of:
```
testparm -s
```

---

### Post by SeijiSensei on 2018-12-02
I'll add that if you take the routing approach above, you probably also need to enable IPv4 packet forwarding.  By default, Ubuntu does not allow packets to be forwarded between interfaces.

Edit the file /etc/sysctl.conf and remove the hash mark from the beginning of this line.  
```
#net.ipv4.ip_forward=1
```

Then reboot.

---

### Post by lfnfan on 2018-12-09
> [COLOR=#000000]Are you able to access those files while at home?[/COLOR]
Now, that's a great lesson in trouble-shooting!  Back to step 1 - turns out I could not access the files even from home!

I have been all over it this past week when time permitted, and found something skewed with my samba setup.  I managed to get it working...from home.

And now it works over the VPN too.

Many thanks volkswagner
Paul

---

