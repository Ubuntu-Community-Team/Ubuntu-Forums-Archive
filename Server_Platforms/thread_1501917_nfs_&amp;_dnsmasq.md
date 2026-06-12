---
title: "nfs &amp; dnsmasq"
date: 2010-06-04
forum: Server Platforms
---

### Post by ubuntologist on 2010-06-04
Hi there,

On a Lucid server, dnsmasq is happily running DHCP together with a local DNS; although, in setting up NFS, I seem to have a small problem...

I have /etc/exports referencing the hostname of the clients but these IPs change when the DHCP lease is renewed. Unless I restart NFS or run exportfs, I cannot mount the exports on my clients.

I know that it would be good to make the all the addresses static; however, I was wondering whether there is another way to configure NFS such as possibly adding in a script to continually monitor /var/lib/misc/dnsmasq.leases and re-export accordingly?

Thanks.

---

### Post by Lucky. on 2010-06-05
I don't know of a good way to monitor the leases aside from some cron job thing, but that's no good.

One idea would be to find/manage the scope/range of IP addresses your DHCP server dishes out (like 192.168.1.1 - 192.168.1.50).  Once you know that, a few ideas:

1.  If NFS exports syntax allows for a custom range of IP addresses, use that (allow your DHCP range, deny others)

2.  If hosts.allow / hosts.deny allow for a custom range of IP addresses, use that (allow your DHCP range, deny others)

3.  If straight ranges can't be used, then some clever subnetting may work.  Create a fake subnet (I say fake because it won't be separated logically by a router), and set your DHCP server's scope to dish out addresses in this range.  When that's done, type the subnet into your exports file (exports syntax may not support custom IP address ranges, but it definitely supports subnets).  For example, 192.168.1.64/26 should allow for hosts ranging from 192.168.1.65 - 192.168.1.126.  I think this might work even though the rest of your network (including your clients) wouldn't know about the subnet (they would still have a 24 bit subnet mask instead of 26).

Of course none of this will work unless you trust *everybody* in your DHCP range, and even then somebody outside of the range could static-ip into the accepted range and successfully authenticate/break into NFS - so you might as well trust everybody on your network.  Which if you did, you probably wouldn't be asking this question.

I say this now only because I barely got it working after ages of dinking around - but have you considered Kerberos + NFSv4?  SFTP?  SSHFS?

---

### Post by Lucky. on 2010-06-05
Wait a minute, isn't there a way to have your DNS server update its tables when DHCP dishes out new IP addresses?  Oh shoot, even better - use static DHCP to dish out the same IP addresses to certain MAC addresses?  I'm not familiar with DNSMasq and its capabilities, just bringing up the idea here.

Still, none of this offers amazing protection.  NFS is only good if you trust everybody on your network.

---

### Post by ubuntologist on 2010-06-05
Thanks for your thoughts Lucky. 

Associating a MAC address to an IP is definitely do-able with dnsmasq but since I do trust everyone on the network, I might just export to a range and be done with it.

Dnsmasq does update its tables but NFS seems to reference it only when started so it's no longer relevant if it changes. 

I may try a cron job to restart NFS alongside the lease renewal schedule or indefinitely extend the lease time.

Thanks.

---

