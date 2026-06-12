---
title: "Two IPv4 addresses in VM but only one NIC"
date: 2018-06-11
forum: Server Platforms
---

### Post by linuxnoob87 on 2018-06-11
All,

I'm stumped by this one and my google-fu hasn't turned up anything.

I have a VM running Ubuntu server 17.10. I initially set the VM up in ESXi 6.5 with a single NIC and the IP ending in .190. I later decided that I wanted to switch the IP to .139 but didn't want to incur any downtime (the machine hosts the pihole software as well as my unifi controller). To avoid downtime I added another NIC, set the static IP in /etc/network/interfaces, and was set. The issue now is that I can't seem to remove the .190 address from the system.

I've commented out the relevant sections of the interfaces file so that it's just a single interface with the .139 address. I removed the second NIC from the VM so that only one is present. I've checked my DHCP server for a reservation (which I highly doubted but figured I'd check) and nothing. I tried manually specifying a MAC address for the NIC but when I did that I lost all connectivity in or out. No matter what, I can't seem to find why .190 is still being associated with the machine. 

Anyone have any ideas as to what I can do? 

Thanks in advance.

---

### Post by darkod on 2018-06-12
You never rebooted or restarted the networking service, right? I'm not sure how exactly it works, but it might be that once the interface is up then it doesn't bring it down until you reboot/restart networking.

What you can do it bring it down yourself manually (if you are sure the other NIC is functioning correctly and all your applications can use it).

Lets say the interface you want to turn off is eth0:
```
sudo ifdown eth0
```

---

### Post by linuxnoob87 on 2018-06-12
I've rebooted the machine after making the changes. I initially didn't want down time but that went away when I couldn't figure out how/why two IP addresses are seemingly tied to the same system.

I've tried running the command you mentioned, however, it appears that my adapter is "ens160" but doesn't seem to respond to that command. Any other ideas?

Thanks

EDIT: ifconfig only shows one NIC with the correct IP. If I run a ping to both the .139 AND .190 address while rebooting the server they both stop and start responding again at the time time.

---

### Post by darkod on 2018-06-12
Another thing I didn't mention earlier. Ubuntu 17.10 started using netplan for the NIC configuration, and you mention doing changes in /etc/network/interfaces (the old way). Do you know for sure how the NIC config is controlled? Netplan or not?

If ifconfig shows only one IP, it is rare... Can you post the content of your /etc/network/interfaces please (assuming netplan is not relevant).

---

### Post by volkswagner on 2018-06-13
> **linuxnoob87 said:**
> 

EDIT: ifconfig only shows one NIC with the correct IP. If I run a ping to both the .139 AND .190 address while rebooting the server they both stop and start responding again at the time time.

If ifconfig only shows one ethernet adapter and one ip address, it's likely you are assuming
the ping result means there is a "hidden network adapter" configured.

This may be as a result of arp. Maybe a switch or the machine you are running the
ping from has arp cache pointing to the same machine or you have /etc/hosts configured
with multiple ip's pointing to the same host???

Try the ping from a different host if possible and clear any arp cache on switches.
Depending on the switch model, you may have to reboot it.

---

### Post by linuxnoob87 on 2018-06-13
Ok. 

The /etc/netplan folder on this server is completely empty. If I try a "sudo nano /etc/netplan/01-netcfg.yaml" it opens a blank file.

Here is my /etc/network/interfaces file:

```

# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
 auto ens160
iface ens160 inet static
 address 172.16.249.139
 netmask 255.255.255.0
 gateway 172.16.249.200
 dns-nameservers 172.16.249.139 172.16.249.138


# The secondary network interface - ens192
# Added for IP switchover
# auto ens192
# iface ens192 inet static
# address 172.16.249.139
# netmask 255.255.255.0
# gateway 172.16.249.200
# dns-nameservers 172.16.249.139 172.16.249.138
# dns-search xxx.global

```

I've removed the secondary NIC from the system but left the information in there commented out just incase. I can remove it as it's no longer needed.

---

### Post by linuxnoob87 on 2018-06-13
I'll try rebooting the main switch for the network and see if that works; the main switch is a 16port Unifi (not sure how to manually clear the arp - will google if a swtich reboot doesn't fix things).

I pinged both the IPs from two different hosts (one VM and one hardware switch) and both continue to ping.

---

### Post by darkod on 2018-06-13
I still haven't had chance to "play" with netplan, but I am surprised you say the folder is empty. Installing 17.10 you surely configured at least one IP or dhcp, at which point it would create the netplan configuration (because if I'm not mistaken, it is the default networking configuration tool since 17.10).

So maybe this is the reason you see both IPs. You have the original in netplan "somehow", and you have configured a new one in /etc/network/interfaces.

---

### Post by linuxnoob87 on 2018-06-15
[IMG]https://imgur.com/T3iEp2J[/IMG]Here is what I get if I do a directory listing in the netplan folder: [https://imgur.com/T3iEp2J](https://imgur.com/T3iEp2J)

And here is what happens if I try to edit the file: [https://imgur.com/vvrZ7Vz](https://imgur.com/vvrZ7Vz)

I've no idea why these are blank/empty but, unless I'm doing something very wrong (and I might be), there's nothing there.

---

### Post by linuxnoob87 on 2018-06-15
One other piece of info: If I check the MAC addresses for the .139 and .190 address they're exactly the same.

---

### Post by volkswagner on 2018-06-15
> **linuxnoob87 said:**
> One other piece of info: If I check the MAC addresses for the .139 and .190 address they're exactly the same.

I know you don't want down time, but you can prove if there is an arp issue
if you boot a live "CD/USB" and see if those addresses are still pingable.
If they are, you can rule out config on the server.

---

### Post by darkod on 2018-06-16
I am still confused how come netplan didn't create any configuration on install. Possible arp remains in the switches are valid point but I do not think it is the issue. They should be cleared after a while anyway otherwise IP changes in a network would be impossible.

I know it is difficult to play around with production servers, but because all of this is very confusing, I would try commenting out the .139 setup you did in /etc/network/interfaces and reboot. If the server starts responding only to .190 that would prove the theory that it is somewhere configured (although we can't figure out where :) ).

If that is the case, I would even try using the command line and 'ip' command to try replacing the IP like that, and to continue the investigation... Basically that command could show a lot (with correct parameters) although I have never needed to use it because I have always worked with /etc/network/interfaces and I still haven't installed my first 18.04 to start using netplan.

---

### Post by The Cog on 2018-06-16
As .190 doesn't show in ifconfig, maybe it's not an assigned address. Does it show up in the output of command "ip address list"?

I wonder if it's a NAT redirect entry somewhere. See if this command outputs anything: "sudo iptables-save | grep 190".

---

### Post by linuxnoob87 on 2018-06-21
I might be able to try this tonight; if so I'll report back with the findings.

---

### Post by linuxnoob87 on 2018-06-21
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens160: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:0c:29:d7:a8:20 brd ff:ff:ff:ff:ff:ff
    inet 172.16.249.139/24 brd 172.16.249.255 scope global ens160
       valid_lft forever preferred_lft forever
    inet 172.16.249.190/24 brd 172.16.249.255 scope global secondary ens160
       valid_lft forever preferred_lft forever
    inet6 fe80::20c:29ff:fed7:a820/64 scope link 
       valid_lft forever preferred_lft forever
```

---

### Post by linuxnoob87 on 2018-06-21
"sudo iptables-save | grep 190" doesn't output anything after entering in my admin password.

---

### Post by linuxnoob87 on 2018-06-21
> [COLOR=#000000]I know you don't want down time, but you can prove if there is an arp issue[/COLOR]
[COLOR=#000000]if you boot a live "CD/USB" and see if those addresses are still pingable.[/COLOR]
[COLOR=#000000]If they are, you can rule out config on the server.[/COLOR]

Booted up off a linux live disc. Could not ping .139 or .190. Live OS only showed one NIC in the system.

[IMG]https://imgur.com/a/bfgsH5w[/IMG]
[IMG]https://imgur.com/a/bfgsH5w[/IMG]https://imgur.com/a/bfgsH5w

---

### Post by darkod on 2018-06-21
Well the output in post #15 shows both IPs as configured on that single interface. The harder part seems to be to find how and where... The 'ip' command should also have options to delete an IP, in this case the .190. I just haven't used it before and I'm little busy to google right now. I'll try later if you don't resolve it...

---

### Post by linuxnoob87 on 2018-06-24
I'll google and report back...

---

