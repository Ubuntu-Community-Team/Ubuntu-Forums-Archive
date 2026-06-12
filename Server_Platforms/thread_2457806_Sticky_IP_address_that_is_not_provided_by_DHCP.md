---
title: "Sticky IP address that is not provided by DHCP"
date: 2021-02-09
forum: Server Platforms
---

### Post by skywalkerisnull on 2021-02-09
Hello everyone,

I have been having some fun with a number of our Ubuntu Servers (20.04 LTS) that seem to be extremely sticky in holding onto an ip address that was provisioned (i.e. in one subnet such as 192.168.21.0/24) but is no longer valid in the network they are being deployed/installed in (such as 192.168.2.0/24), or they are holding onto an IP address that is not being handed out by the DHCP servers (I have checked, that there are no rouge DHCP servers on the network). These are vanilla ubuntu servers that are VM's (Hyper-V 2019) and in all cases, the MAC is static and has been provisioned with a reserved IP in the DHCP server. 

On reboot, a number of machines will start up with an incorrect IP address, and can only be resolved with:
```
sudo dhclient -r eth0
sudo dhclient eth0
```
But on reboot, they are back to using the same incorrect IP address.

Any ideas on where to go looking as to why they are so sticky with the old IP addresses? Or what I can do to force them to always go to the DHCP on boot to get their IP addresses?

---

### Post by TheFu on 2021-02-10
Well, any desktop or server can force any IP they want manually, regardless of what DHCP says.  Everywhere I've worked, DHCP stuff was for desktops, not servers.  We had over 100K servers, most with 6 NICs and at least 12 IPs on 3 networks.  These were all manually managed (well - we used devops tools, but the effect is the same).  Why?  DHCP servers fail.  Why should a dead DHCP server impact any server - ever?  They shouldn't.

So .... you'll need to log into each system and if they truly are servers check the netplan file(s) for the settings.  Some older servers that were migrated forward may still be using the *interfaces* file.  Both these systems support methods to have local files names almost anything in specific locations. You'll need to check those too.  If it were me, I'd use ansible to ask all the systems about their network config files.

Or you could just shutdown the old network and I bet whoever setup a server will eventually call to complain.  If they don't notice for a few days, then you'll know it is VM-sprawl and those systems should be shutdown and retired. Clearly they aren't business critical.  

I've had to do this.  He had a 6 month plan with deadlines signed off by the CIO. This gave everyone in the company time to hear, ask for help and take action. Still, about 2% of the system nobody claimed and when we shut their networking down, only 2 screamed.  They said, "I didn't think you were talking about my system."  That let us know which systems were not being properly maintained and were huge security risks too.  In a smaller enterprise, you can probably compress the schedule to 2-4 weeks.

---

### Post by skywalkerisnull on 2021-02-10
With the DHCP server, we have a load balanced setup (Windows AD/DC configuration) and they have never gone down (i.e. the service of DHCP has never gone down). This gives us a single pane to see all IP addresses (We also use IPAM) and we know that they are registered with the DNS servers as well. Leases are set are 21 days, so if we haven't fixed our issues within 7 days, we still have a bit of time to implement a new DHCP setup. The MAC address is always known in advance so we can add it as a reservation in the DHCP and know that it will get used, well, until these few machines.

We usually use PXE boot to install the systems, for the most part the installs are handled by custom answer files. In almost all cases, the PXE boot IP address is the one that it sticks with for the life of the machine/VM.... Except for this small handful that seem to then get a different IP and hold onto it.

Back onto the ones that are not behaving correctly have the following netplan config in '00-installer-config.yaml'
```

# This is the network config written by 'subiquity'
network:
  ethernets:
    eth0:
      dhcp4: true
  version: 2

```

None of servers are upgraded, they are always installed fresh and there are no files or directories for interfaces files. The machines that came in from a different subnet are dev machines with custom components that was configured offsite and then deployed into the rack.

---

### Post by SeijiSensei on 2021-02-10
There might be "reservations" on the DHCP server, stale mappings between MAC addresses and IP addresses. If the addresses are assigned by a Linux server running isc-dhcp-server, you can delete /var/lib/dhcp/dhcpd.leases. If the DHCP server is running on your router, you'll need to edit its configuration.

---

### Post by SeijiSensei on 2021-02-10
Having read your preceding posting, I'd examine the DHCP reservations.

---

### Post by TheFu on 2021-02-10
I'd look for another, faster, DHCP server on the LAN.  

I don't use DHCP much for computers, but I do have reservations for devices that don't have a keyboard - like network TV tuners and 1 laptop. There must be a way to get the system to say which DHCP server is providing the settings, yes?  

```
egrep dhcp-server-identifier  /var/lib/dhcp/dhclient.*
```
should provide the IP address of the DHCP server.  dhclient.leases doesn't appear to have the information.  Seems each interface gets a dhcp-file added.

```
$ ll /var/lib/dhcp/dhclient.*
dhclient.enx000ec6c76418.leases  dhclient.leases
```

---

### Post by skywalkerisnull on 2021-02-10
I just rebooted one of the misbehaving ones and ran the command that TheFu has provided for checking what DHCP server it was using and it is using a correct DHCP server. 
I am going to dive into the DHCP server logs to see if there is anything going on there.

---

### Post by TheFu on 2021-02-10
google found this: [https://superuser.com/questions/1338510/wrong-ip-address-from-dhcp-client-on-ubuntu-18-04](https://superuser.com/questions/1338510/wrong-ip-address-from-dhcp-client-on-ubuntu-18-04) with some netplan config options.

```
            dhcp-identifier: xx:xx:xx:xx:xx:xx
```

---

### Post by Doug S on 2021-02-10
+1 for the input from SeijiSensei.

I'll add that you can use tcpdump (or wireshark, if you prefer) to watch the actual request grant exchange. Example command (obviously change the interface name to yours):

```
sudo tcpdump -n -tttt -vvv -i enp1s0 port 67
```

This may not apply to you, not sure:
For several years I had a mistake in my /etc/dhcp/dhcpd.conf file having the reserved pool stuff ***BEFORE*** the mac based fixed IP assignment stuff. If the client had ever been on my LAN, which was typical for new stuff being added as i would try it first then do the MAC based stuff, no matter what I tried the client would not get the desired IP, always the old one. My revision notes:

```
# 2020.01.19 try reversing the order of the code.
#       MAC stuff first instead of second.
#       Does this cure the issue whereby I can not seem
#       to force IP via MAC, if it already has an entry from
#       the pool, no matter what I seem to delete?
#       Yes, it seems to.

``````

```

EDIT: I was typing this when TheFu last posted. That is interesting. I do not use netplan.

---

### Post by skywalkerisnull on 2021-02-11
Following the link that TheFu found, I added [FONT=Consolas]dhcp-identifier: mac[/FONT] to the netplan config, rebooted and it got the correct IP address on the one that is in the same subnet. thank you! :)

Now I just need to get back onsite before I reboot the one that decides to go on to a different subnet each time it reboots.

---

