---
title: "DHCP not pushing internal DNS unless static"
date: 2010-01-13
forum: Server Platforms
---

### Post by R.Bucky on 2010-01-13
I operate Server v.8.04 with Bind9 configured for my internal sites. I installed DHCP3 the other day and assigned static addresses for certain boxes on my network. However, only those static assigned boxes can view my websites internally. In other words, DHCP appears to block my DNS. Is there a setting that I missed or is there something else?

---

### Post by noway2 on 2010-01-14
Are you sure that the non static devices are getting assigned to your network?  If you haven't run ifconfig and make sure that the IP address, mask, and gateway are all assigned.  It may be necessary to reboot and flush some DNS queues or something after making the changes.

If you haven't you might also want to consider linking your DHCP and BIND so that they are aware of each other, which the more I think about it may be the problem.  When you link them, you can access devices on the LAN by way of the host name rather than IP address.  I would provide you a link to a good how-to, but I don't have access to it at the moment.

---

### Post by NIT006.5 on 2010-01-14
Is DHCP providing the clients with the correct DNS server address? Have you got DNS manually configured on the static machines or are they also getting the DNS server address from DHCP? Try a standard nslookup of your server on both the static and dynamic clients and see if the results are the same.

Is the server doing any reverse lookups on incoming connections? (This normally only applies to smtp though I'm sure). If it is somehow blocking clients whose IP's don't resolve, then going with dynamic DNS, as suggested, would solve that. And is the server using "itself" for internal name resolution? If it's trying to do reverse resolution on local clients via Internet name servers, that's also obviously not going to work. So in /etc/resolv.conf your server should be using itself to resolve addresses, and then bind should be forwarding queries to Internet servers for records that it is not responsible for. However, if you're not using dynamic DNS then it still wouldn't be able to resolve the local clients anyway.

---

### Post by R.Bucky on 2010-01-14
I am pushing internal DNS first, then Google's public DNS. My /etc/resolv.conf appropriately reflects the DNS entries in DHCP. I have checked all of the statically assigned boxes on the network, both Windows and Linux boxes, and they all have the assigned internal static. 

I will research linking Bind and DHCP. If there are any recommended articles, I am happy to receive the input.

---

### Post by NIT006.5 on 2010-01-14
Your best bet is to look at the Ubuntu Server Guide for the version you're running, which documents how to implement dynamic DNS (should be available on help.ubuntu.com if I remember correctly). Since you've got both services running already, it's just a matter of telling DHCP to update DNS, and configuring the security between the two. It also means that zone files will need to be located elsewhere, otherwise apparmor won't allow them to be updated. (Although some people disable this protection in apparmor, it's not the right way to do it as it makes bind vulnerable to attacks). All of this should be covered in the server guide document though.

---

### Post by noway2 on 2010-01-14
I THINK that this is the one I used: lani78.wordpress.com/2008/.../dhcp-server-update-dns-records/

I used it when I was an absolute beginner and it worked the first time.

---

