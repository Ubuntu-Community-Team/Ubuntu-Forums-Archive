---
title: "Redirecting selected ports to virtual machines"
date: 2012-05-20
forum: Virtualisation
---

### Post by eksbaf on 2012-05-20
I am using Ubuntu 12.04 and have set up and qemu/kvm guest acording to this very good tutorial: [https://help.ubuntu.com/community/KVM/](https://help.ubuntu.com/community/KVM/)

The client is installed (debian) and is working well. I can access the internet out of my guest and would now like to set up an web server.
For now I only have one IP adresse over my wlan device. Later I want to move the guest to another host which has several IPs and build a bridge.

So for now I have set up a "Usermode Networking" according to this: [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking) (default mode).

Now I want to reach my guest webserver out of the internet/my lan. My host IP is 192.168.0.150 and my guest IP is 192.168.122.178.

If I open the web browser on my host I can reach the apache of the guest by entering "192.168.0.150".

So I thought I just have to set the Iptables rule for redirecting the port 80 and I can reach it! But it doesnt work :(

```
iptables -t nat -A PREROUTING -d 192.168.0.150 -p tcp --dport 80 -j DNAT --to-destination 192.168.122.178:80
```

Have I done anything wrong?

---

### Post by eksbaf on 2012-05-22
Does nobody have an answer for me? My ifconfig shows the bridging-device, but I am not sure if bridging and routing is mixable?
[http://nopaste.info/fe53e46ac7.html](http://nopaste.info/fe53e46ac7.html)

---

