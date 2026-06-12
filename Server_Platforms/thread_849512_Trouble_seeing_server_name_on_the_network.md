---
title: "Trouble seeing server name on the network"
date: 2008-07-04
forum: Server Platforms
---

### Post by BrokenPoet on 2008-07-04
I recently set up a new headless server/raid using Hardy to replace my aging PIII server.  The server installation and raid setup went off with only one hitch: Although I can SSH into the box using the IP address, the hostname is not recognized on the network.  It is a minor annoyance, but I should be able to type 'ssh atlas' and have it work.
   I am also unsure if the problem is in my server config, my router, or my laptop (where I ssh from.)
   Any help would be appreciated.


<server Hosts file>
```
vince@atlas:/etc$ cat hosts
127.0.0.1	localhost
127.0.1.1	atlas

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

<server Hostname file>
```
vince@atlas:/etc$ cat hostname
atlas

```

---

### Post by sjwk on 2008-07-04
The problem is that although your server knows it is called atlas, nothing else on your network does...

The simple fix is to put an entry into the hosts file on your laptop.  Depending on your router, and whether your other computers are configured to use it for name lookups, there might be some way of getting it to resolve the address, but I've not seen many that do

The more complicated fix is to run a DNS service on the server.  But that's not a trivial thing to set up.  It really would be simpler to just edit the hosts files unless you have significantly more than a handful of machines.

If the laptop is a Windows machine there might be another way.  If you install samba on the server, that will by default use its hostname as the Netbios name.  Windows name resolution will try and lookup the Netbios name if it can't resolve it either from hosts or DNS.  If the laptop is a Mac or Linux box, that won't help though since they don't use Netbios name resolution.  I also don't offhand know whether with Windows that would work in 3rd party applications, or only from explorer and command prompt...

Steve.

---

### Post by BrokenPoet on 2008-07-04
Steve- Thanks for the response.  I have reserved an IP on my router for the server (atlas) and modified my laptop hosts file.  Fixed.

---

### Post by skunkbad on 2008-07-05
You might want to upload a php script with a file that uses file_get_contents(), file(), or fopen(), and check that you don't have any errors. When I had set up my static LAN IP, I had not configured DNS correctly, specifically the hosts file, and there were problems. The worst of which was that ddclient was not able to do its updates. Apache still served up web pages that I requested from the WAN and LAN, but other services couldn't "get out".

The only reason I'm saying this, is that your atlas being 127.0.1.1 looks peculiar, and I'm used to seeing LAN IPs that are more like 192.168.1.XXX.

---

