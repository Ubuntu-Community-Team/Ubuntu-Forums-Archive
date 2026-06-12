---
title: "Add Ubuntu Server 22 to Windows Domain"
date: 2022-08-07
forum: Server Platforms
---

### Post by Billy_Martinez on 2022-08-07
Hello Everyone,

I’m an I.T. admin and I would like to setup an Ubuntu server that can do the things below. I tried searching Google and I wasn’t able to find any help for any these topics. If you can please post links to whatever reading I can do to get this done, then I would greatly appreciate it.

1. Add an Ubuntu server to a domain so that it has a computer account in active directory.

2. Register the static IP and hostname that an Ubuntu Server has with a worksites Windows DNS server.

3. Setup Samba so that it can communicated with active directory and give windows domain users access to samba shares on an Ubuntu server.

If any of these things can’t be done, then please let me know as well.

Thanks

---

### Post by TheFu on 2022-08-08
I've never used AD. Not something we do, since we have LDAP running on Linux systems here and use that, but google found these links:
[https://ubuntu.com/server/docs/service-sssd-ad](https://ubuntu.com/server/docs/service-sssd-ad)
[https://ubuntu.com/server/docs/samba-active-directory](https://ubuntu.com/server/docs/samba-active-directory)

In theory, those links should be for the current LTS server, but definitely look through the steps provided to see if they are too old.

I do recall that adding an Ubuntu Workstation to AD became really easy (in theory) during the OS install with the 20.04 release. Again, I never tested it.

---

### Post by Billy_Martinez on 2022-08-08
Thanks &#128578;

---

### Post by Billy_Martinez on 2022-08-09
I was able to add an ubuntu server to the domain and its account showed up in active directory, but no DNS record was created on the DNS server. On a Windows Machine, when you add it to a domain, it automatically creates a DNS record on the on the DNS server.

---

### Post by TheFu on 2022-08-09
> **Billy_Martinez said:**
> I was able to add an ubuntu server to the domain and its account showed up in active directory, but no DNS record was created on the DNS server. On a Windows Machine, when you add it to a domain, it automatically creates a DNS record on the on the DNS server.

I've never seen that, but are your certain that the DNS isn't due to the DHCP server telling DNS?  Domain membership doesn't seem related to me.  In Linux, DHCP can provide a lite DNS capability through dnsmasq connections or I suppose someone may have created a bind link too.  It is possible to use NIS, NIS+ or LDAP to hold hosts. I used to do that with NIS in the mid-1990s, before security became job #1 and NIS use was removed from every corporate network.  I use DNS at home and work. These are manual entries. We only use DHCP for guest machines on a guest LAN and for portable wired devices, but those have DHCP reservations with static DNS entries.  All wifi devices are either on the untrusted or guest network. We don't trust wifi, as policy.

I've seen entire buildings at client locations go down because their DHCP servers failed.  For non-portable devices, this is why we always, always, have static IPs setup inside the OS, never from DHCP.  Plus, at work, our systems almost always have restricted access into specific systems on other LANs based on the needs of the user.  People sitting next to each other can be on multiple LANs, 1 is shared by nearly all end-users, and the other has firewall rules to allow access to specific servers in data centers around the world.  People who work in the same group, seldom work together, so they each have unique firewall rules just for their assigned system access.

---

