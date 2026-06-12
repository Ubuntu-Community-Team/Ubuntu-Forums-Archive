---
title: "Search a local domain in 18.04?"
date: 2018-08-20
forum: Server Platforms
---

### Post by Roasted on 2018-08-20
Hi friends. In previous versions of Ubuntu Server, in an effort to get local DNS name resolution working (where I can ping the server by name from another system on my network), I'd run these commands on my server:

1. echo "search local" | sudo tee /etc/resolvconf/resolv.conf.d/tail
2. sudo resolvconf -u

This doesn't seem to be working in 18.04, which I assume is partly due to netplan taking over network duties. The catch is, my netplan config file is as follows:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses: [10.13.0.200/24]
      dhcp4: no
      dhcp6: no
      gateway4: 10.13.0.1
      nameservers:
        addresses: [10.13.0.2]
        search: [lan]
```

I have right there that my search domain is lan, yet I am unable to ping this server by name. This box hosts about 5 additional Ubuntu Server instances on top of KVM, though the virtual servers I have set to DHCP and I let my DHCP/DNS server (which is a VM running PiHole @ 10.13.0.2) dish out the IP addresses. As such, it seems as if IPs that come from the PiHole VM over DHCP work absolutely fine, as I can ping all virtual servers by name without issue, though the main host server with a static IP I cannot ping by name. It's worth noting that the PiHole is set to "lan" for the local domain as well.

According to my notes, the resolvconf text I pasted above was the ticket in years prior. Not entirely sure what the correct protocol is now. Anybody know? Would appreciate any and all insight. Thank you!

---

### Post by darkod on 2018-08-20
Is the domain .local or .lan? There is inconsistency in the two comparisons you wrote.

The netplan file looks correct to search for domain named .lan.

---

### Post by Roasted on 2018-08-20
Sorry, I wrote that late. The domain is lan. I admittedly didn't try the command from my notes with lan appended because most of the path didn't exist. With netplan being quite different I thought that was the first sign that the commands in my notes were no longer useful on new versions, then once I realized I saw I had search lan in the netplan config I felt I hit a wall as documentation online suggested that that's what I needed to make it work yet I was still unable to make it fly.

---

### Post by darkod on 2018-08-20
Hmmm, in that case it does look like you have netplan configured correctly.

To rule out DNS issues, did you try dig or nslookup by adding .lan yourself manually? Does it return the correct output? I would confirm that first before continuing the investigation why it doesn't append .lan automatically.

---

### Post by Roasted on 2018-08-20
> **darkod said:**
> Hmmm, in that case it does look like you have netplan configured correctly.

To rule out DNS issues, did you try dig or nslookup by adding .lan yourself manually? Does it return the correct output? I would confirm that first before continuing the investigation why it doesn't append .lan automatically.

Hm, so if I ping vault.lan, it doesn't work. If I ping vault.local, it responds to ping. Clearly it's somehow triggering with local appended. I dug around to see where it may be pulling from, but so far I'm not finding it.

```
administrator@vault:~$ cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
search lan

```

```
administrator@vault:~$ cat /etc/netplan/01-network-manager-all.yaml 
#Let NetworkManager manage all devices on this system network:
#network:
#  version: 2
#  renderer: NetworkManager
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses: [10.13.0.200/24]
      dhcp4: no
      dhcp6: no
      gateway4: 10.13.0.1
      nameservers:
        addresses: [10.13.0.2]
        search: [lan]
    enx00249b11e1fa:
      dhcp4: yes

```

```
administrator@vault:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	vault

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Not sure where else it would be pulling from. Any ideas?

---

### Post by darkod on 2018-08-21
What about:
```
cat /etc/hostname
```

What settings do you have on the DNS server? I assume you have some sort of DNS in your LAN because otherwise where would it get the IPs from. Maybe the .local is set on the DNS?

Try from other machines in the LAN, don't focus only on the one server. Does ping work on other machines with hostname.lan or hostname.local?

---

### Post by Roasted on 2018-08-21
> **darkod said:**
> What about:
```
cat /etc/hostname
```

What settings do you have on the DNS server? I assume you have some sort of DNS in your LAN because otherwise where would it get the IPs from. Maybe the .local is set on the DNS?

Try from other machines in the LAN, don't focus only on the one server. Does ping work on other machines with hostname.lan or hostname.local?

All systems on the network except one uses DHCP. The DHCP server has the domain set to "lan". All other systems respond to ping by their hostname without the domain. For example, my web server responds to "ping web" and "ping web.lan" but it does not respond to "ping web.local". All systems on the network behave the same way, where pinging hostname.local fails, but ping hostname works and ping hostname.lan works.

My main server, named vault, responds to "ping vault.local" only. It fails on "ping vault" and "ping vault.lan". The main 'vault' server is the only static machine on the network.

Hostname file is as follows:
```
administrator@vault:~$ cat /etc/hostname
vault

```

With my vault server having "search: [lan]" from the code blurbs pasted above in every area I'd expect it to matter I would have expected vault to respond via ping vault or ping vault.lan, but it only responds to vault.local, which tells me somehow, somewhere, 'local' is appended as the search domain somewhere on this box. I'm just not sure where. The underpinnings of netplan are new to me but if I'm doing something wrong I haven't caught on to it yet as per what documentation I've read to date.

Thanks for your assistance. Greatly appreciated!

---

### Post by darkod on 2018-08-21
Got one idea... Where is the DHCP server?

Is it on 10.13.0.1 (is that the router?) or on 10.13.0.2?

What is the DNS offered to the LAN machines by dhcp, is it .1 or .2?

PS. I'm trying to figure out if there is a difference between vault using the .2 as dns nameserver, and the other machines. Do they use .2 too, or maybe .1 if that is the router issuing dhcp and issuing itself as dns nameserver.

---

### Post by Roasted on 2018-08-21
.1 is my unifi usg. Basically my router. DHCP and dns disabled there. 

.2 is PiHole, serving DHCP and dns for the network. 

Recently the usg had been employing DHCP with dns being on the PiHole but I moved both to PiHole so it was easier to maintain internal hostname resolution. Previously when the usg was used for dhcp I still used lan as the domain. Perhaps there's something buried in between those two network devices though.... Nothing comes to mind as I've looked into their settings quite a bit but I'll do another scrub of the settings in case. 

Thanks again.

---

### Post by darkod on 2018-08-21
Can this offer some ideas to you? [https://askubuntu.com/questions/1027255/having-problems-resolving-a-fqdn-on-my-local-network-from-ubuntu-18-04](https://askubuntu.com/questions/1027255/having-problems-resolving-a-fqdn-on-my-local-network-from-ubuntu-18-04)

Even though the owner of that thread was actually using .local as domain which isn't your case. But still, playing with the file he mentioned might help you.

And another thing, after changes to the netplan yaml, you are using 'sudo netplan apply' to apply the settings, right?

I still don't have 18.04 server so it is difficult for me to look around inside it...

---

### Post by Roasted on 2018-08-21
Thanks for the suggestion. I tried the above and restarted the server for good measure. Once it came back up, no change.

ping vault          = name or service not known
ping vault.lan    = name or service not known
ping vault.local = works

Not sure what to think of it at this point. :(

And yes, to confirm I *am* using sudo netplan apply after making changes.

---

### Post by darkod on 2018-08-22
Was this an upgrade or clean install of 18.04 LTS? With an upgrade you might have some remains to how it was done before...

Also, even though the paths are not identical to before, I would still look around /etc/resolvconf/... in subfolders and files, to check if the culprit is there. Something similar to the command you posted that you were using in 16.04 and that puts the value in /etc/resolvconf/...

I'm out of other ideas too...

---

### Post by Roasted on 2018-08-22
Tried that, but no change. :(

Think this is the last time I hop on board with a newer server version. My buddy upgrades to the 2nd latest once the latest comes out (i.e. once 18.04 came out, he would have upgraded to 16.04). Might be time to follow suit. I'm just not feeling good about the documentation out there on bigger changes like this netplan approach.

I also decided to remove my pihole from the mix temporarily and gave all DNS and DHCP duties to my Unifi USG entirely. It acted identically. It's something with this server, and this server is pretty much a brand new install with libvirt and a few VMs running on it. It's not anything complex or crazy, and yet despite my configs matching up to what little documentation I can find, it still doesn't fly.

Perhaps I'll just get used to memorizing IP addresses at this point. :P

---

### Post by darkod on 2018-08-23
If this is a libvirt host, is the problem observed on both host and VMs or only on host/VMs? Is there a ubuntu version difference between the host and the VMs?

---

### Post by Roasted on 2018-08-23
> **darkod said:**
> If this is a libvirt host, is the problem observed on both host and VMs or only on host/VMs? Is there a ubuntu version difference between the host and the VMs?

Yes. Host is 18.04. VMs are a mixture between 16.04 and 18.04. All guest VMs do not have issues. I can:

ping web (18.04)
ping irc (18.04)
ping seafile (16.04)
ping unifi (16.04)

without issue, but "ping vault" as mentioned prior fails.

Think something is up with libvirt host? All along I was suspecting it was due to the host being the only static system in the household. Maybe for kicks it'll be in my interest to spin up a 2nd 18.04 system, static it, and see how it does?

---

### Post by darkod on 2018-08-23
Hold on, just got an idea. Looking back at your posts I see that /etc/hosts does not include the IP and FQDN of the server itself.

I would modify the line '127.0.1.1 vault' in /etc/hosts to be:
```
10.13.0.200   vault.lan   vault
```

Then try again. No reboot is necessary i think but if it doesn't help, try again after rebooting it.

Basically on almost all servers I do the above to make sure it responds to it's FQDN, etc... And using its private LAN IP.

---

### Post by Roasted on 2018-08-23
> **darkod said:**
> Hold on, just got an idea. Looking back at your posts I see that /etc/hosts does not include the IP and FQDN of the server itself.

I would modify the line '127.0.1.1 vault' in /etc/hosts to be:
```
10.13.0.200   vault.lan   vault
```

Then try again. No reboot is necessary i think but if it doesn't help, try again after rebooting it.

Basically on almost all servers I do the above to make sure it responds to it's FQDN, etc... And using its private LAN IP.

No dice. :( I tried everything you suggested, including rebooting, however I'm still striking out.

I'm finding this more strange than anything else. Kind of at a loss on what else it could possibly be.

---

### Post by Roasted on 2018-08-23
Not sure why I didn't think of this sooner, but I decided to take a closer look at seeing if I could leverage my hosts file on the pihole server itself. Even though pihole is serving DHCP to the LAN and the vault server is static, I figured the DNS portion would still bear some weight.

I added an entry and tested it out. Now, pinging vault works!

(This is from my desktop computer)
```
jason@JSLNXDT01:~$ ping vault
PING vault.lan (10.13.0.200) 56(84) bytes of data.
64 bytes from vault.lan (10.13.0.200): icmp_seq=1 ttl=64 time=0.140 ms
64 bytes from vault.lan (10.13.0.200): icmp_seq=2 ttl=64 time=0.193 ms
```

```
administrator@pihole:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	pihole
10.13.0.200	vault.lan

```

For some reason, despite the hosts file being in my mind, I kept thinking of it as a client file, like something that if I wanted to use I'd have to change all hosts files on all clients to make work. Added that 3rd line in the above code block to it, restarted pihole dns, and ping vault from all client machines seems to work now.

Appreciate your help! Thank you for consistently throwing your 2c in the ring. :)

---

### Post by CharlesA on 2018-08-23
Isn't the Pihole running DNSMASQ? That should pick up anything in the hosts file and serve it as DNS entries, as you have found out.

---

### Post by volkswagner on 2018-08-23
I'm still on 16.04.4 and have zero experience with netplan.

I didn't see your response to Darkod's request for "dig" and "nslookup" (these are key to proper diagnosis).
I think you are relying on "ping" a little too much as a troubleshooting tool.
I'm not sure how setting search = lan will tell your DNS server how to resolve vault.lan to 10.13.0.200.
I know nothing of pi-hole, but if your server's IP is static, you need to manually add it's ip address to the DNS server with hostname.

Have you seen [this]("https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/netplan-how-to-configure-static-ip-address-in-ubuntu-18-04-using-netplan.html")?

I'm not sure if "dns-search" and "search" are equal, but worth trying.

Also you network interfaces file has multiple addresses, perhaps try moving up your "search" or "dns-search" above your secondary address??

Sometimes workarounds can help with sanity.
Have you tried:

/etc/hostname:
```
vault.lan
```
/etc/hosts:
```
10.13.0.200 vault.lan vault
```

/etc/resolvconf/resolv.conf.d/tail:
```
Domain lan
```

---

