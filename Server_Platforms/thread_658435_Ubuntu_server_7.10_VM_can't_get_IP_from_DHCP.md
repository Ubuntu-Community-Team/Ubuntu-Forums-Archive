---
title: "Ubuntu server 7.10 VM can't get IP from DHCP"
date: 2008-01-04
forum: Server Platforms
---

### Post by jaygo on 2008-01-04
Hi all,
I've setup Ubuntu server 7.10 as a VM in virtualbox (love it) but can't figure out the networking. I've created and bridged 4 tap interfaces on my host system. My Windows VMs pick up the tap connections and communicate with my router (which serves DHCP), get their IPs, and are completely visible on my local network.

However, I cannot get my ubuntu server VM to connect to my local network using dhcp or static. The virtualbox setup is identical for all my VMs (each VM has its own tap connection though) so it doesn't seem to be the problem. Therefore, I believe there is something unique to an ubuntu LAMP that may require configuration.

On the server, my /etc/network/interfaces file reads:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

Restarting /etc/init.d/networking, I see the following:
```
... 
Listening on LPF/eth0/08:00:27:81:da:7a
Sending on   LPF/eth0/08:00:27:81:da:7a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

What am I missing?

---

### Post by chadk5utc on 2008-01-04
what are you using for a DHCP Server ? router/modem/other
and have you tried to set a static ip for the server ?

---

### Post by jaygo on 2008-01-05
Yes, using a (dd-wrt) router and I do have a static IP assigned there.

---

### Post by jaygo on 2008-01-07
bump.
How does anyone setup their LAMP server to receive an IP address from a DHCP server or router?

---

### Post by p_quarles on 2008-01-07
You can't use DHCP to assign a static IP address. That's almost a direct contradiction in terms. ;)

Anyway, what you need to do is remove the "dhcp" line from the eth0 entry in /etc/network/interfaces, and setup something like so:
```
iface eth0 inet static
   address (the static address goes here)
   netmask 255.255.255.0
   gateway (router's address goes here)
```
Then, reinitialize networking:
```
sudo /etc/init.d/networking restart
```

---

### Post by jaygo on 2008-01-08
Well I had an idea and it worked. I had set up four tap connections in my /etc/network/interfaces file: tap0, tap1, tap2, tap3. They were all setup identically and all bridged to eth1, so there's no visible reason why one of them wouldn't work but that is the case, as it turns out. Tap0 simply doesn't connect, and that's the tap that I had connected to my server VM. My guess is that one of the console commands I ran while trying to get this working made changes to tap0 in some other mysterious file. So I made a tap4 and it works perfectly.

And yes, it was *almost* a direct contradiction but I use my DHCP server to assign static IPs for my network, just to centralize the management. I had tried the static setup as you recommended however it didn't make a difference; I'm sure it would work now that I have the tap crap straightened out.

Thanks for the input ppls. :)

---

