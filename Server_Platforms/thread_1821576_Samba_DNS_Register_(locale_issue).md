---
title: "Samba DNS Register (locale issue?)"
date: 2011-08-09
forum: Server Platforms
---

### Post by remmargorp on 2011-08-09
I'm running into an issue with registering an Ubuntu 10.04 (same issue in 10.10) system to a Windows 2008 R2 DNS

Joining the domain is no problem, but it will not update DNS, which means configuring a static IP and adding a DNS A record, or a DHCP reserve and a static DNS record, these options are not acceptable for me

Command:
sudo net ads dns register -I [IP] -U [domain admin] -d 10

Parsing through the output I don't see anything too alarming except at the end where the process abruptly stops

```

[2011/08/08 17:10:27, 10] lib/util.c:2626(name_to_fqdn)
  name_to_fqdn: lookup for UBUNTU-TEST -> ubuntu-test.[DOMAIN].com.
[2011/08/08 17:10:27,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=[HEX IP]%eth0 bcast=[HEX BCAST]%eth0 netmask=[HEX NETMASK]
[2011/08/08 17:10:27,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=[DOT IP] bcast=[DOT BCAST] netmask=[DOT MASK]
[2011/08/08 17:10:27,  4] libads/dns.c:620(ads_dns_lookup_ns)
  ads_dns_lookup_ns: 17 records returned in the answer section.
[2011/08/08 17:10:28, 10] intl/lang_tdb.c:138(lang_tdb_init)
  lang_tdb_init: /usr/share/samba/en_US.UTF-8.msg: No such file or directory
DNS update failed!
[2011/08/08 17:10:28,  2] utils/net.c:779(main)
  return code = -1

```* I masked certain properties with text in []

No logs on the DNS server (Windows DHCP server allows dynamic dns update when the client requests)

From the output the only thing outstanding at this point is "lang_tdb_init: /usr/share/samba/en_US.UTF-8.msg: No such file or directory", immediately after the process fails/stops

I'm not familiar with locale's but that file does not exist in the /usr/share/samba directory and I can't find that file on the system (sudo find / -name *en_US*)



I can't seem to find information about en_US.UTF-8.msg anywhere (all search results in the error line when people are talking about joining AD, no reference to that error specifically)

Seems like if I could put en_US.UTF-8.msg in that directory I could at-least run the process again and check the results


Anyone know how to get en_US.UTF-8.msg?

---

### Post by remmargorp on 2011-08-09
I have a solution to my issue

My initial intent with this process was to get these Ubuntu clients registered in DNS. Going through the domain join process I noticed the "DNS update failed!" message and began troubleshooting that

From debug output and looking through the source code for Samba (starting at lang_tdb.c and then to net.c then to net_ads.c) it led me to a function DoDNSUpdate

A quick Google search led me to research further dynamic dns updates on a Windows DNS server and the process in which dynamic DNS updates occur


The DHCP client is responsible for sending DHCP option 81 (a FQDN) to the DHCP server.

The DHCP server needs to have enabled the "DNS dynamic updates" option (so that is can update the DNS servers when a client registers)

For Ubuntu 10.04, I needed to add the following config lines to /etc/dhcp3/dhclient.conf
 send fqdn.encoded on;
 send fqdn.server-update off;

After "sudo /etc/init.d/networking restart" I checked the DNS server and did not find an entry in my forward lookup zone, I looked at the reverse lookup zone and found an entry for the Ubuntu client

A little more research led me to re-configure dynamic DNS settings on the DHCP, under "Enable DNS dynamic updates" I chose "Always dynamically update DNS A and PTR records"

After "sudo /etc/init.d/networking restart" I checked the DNS server and there was an entry in the forward lookup zone and reverse lookup zone




EDIT:

I read through the documentation for dhclient-options ([http://linux.die.net/man/5/dhclient-options](http://linux.die.net/man/5/dhclient-options) - see section "The Client Fqdn Suboptions")

If I change send fqdn.server-update from off to on then the A record will update itself, this allows us to avoid enabling the "Always dynamically update DNS A and PTR records" on the DHCP server

---

### Post by cybrosh on 2012-02-08
Hi,

Trying to follow your instructions. Added the 2 lines to hclient.conf just under 'send-hostname <"hostname"> but it doesn't seem to work. Both of my DNS servers aren't updated(a record). Do you qualify FQDN somewhere in your conf file?

Can you publish your conf' file for comparison? did you do any changes to the conf file except the 2 lines you mentioned?

Cheers

---

### Post by teriyaki-89 on 2012-04-13
hi i added too lines to my /etc/dhcp/dhclient


send fqdn.encoded on;
send fqdn.server-update off;

but the error is still present

---

