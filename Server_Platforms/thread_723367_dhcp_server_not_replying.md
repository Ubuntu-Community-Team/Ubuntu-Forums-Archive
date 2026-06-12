---
title: "dhcp server not replying"
date: 2008-03-13
forum: Server Platforms
---

### Post by shahansudu on 2008-03-13
Hi,
   I have ubuntu 6.06 server installed and running dhcpd on interface eth1. I use the dhcp server to pxe boot my client. Server was working fine but suddenly stopped serving. I still see dhcpd as running on eth1 but my client wont get served. I tried a regular dhcp reques (not pxe) and still its not serving.

My interface is up and I see the server running when I do 'ps ax | grep dhcpd' 

I tried restarting dhcpd but still dont work. can someone help me with this? I'm confused.... :confused:

---

### Post by shahansudu on 2008-03-13
Hi,
    I think I found the problem. I checked the syslog and according to it server ran out of IP addresses. so I'm going to set the lease time to a very low time or increase the address range. Hopefully this will work.;-)

---

### Post by shahansudu on 2008-03-13
I know I said I solved the problem but I have a small question. Does anyone know how to release all the leased ip addresses from the server?

---

### Post by koenn on 2008-03-13
> **shahansudu said:**
> I know I said I solved the problem but I have a small question. Does anyone know how to release all the leased ip addresses from the server?

find the file where the leases are recorded, and delete the lease records

---

### Post by {BzF}~JOKesTER on 2008-03-13
Try These Codes In The Terminal:

sudo /etc/init.d/networking restart

Or

sudo dhclient


Hope This Helps - Let Me Know!!!:):)

---

### Post by shahansudu on 2008-03-13
I want to release them from the server not the client. Is there a command for dhcpd to release the leases. I can delete the dhcpd.leases file but dont want to do so if there a proper way of doing it

---

### Post by koenn on 2008-03-13
> **shahansudu said:**
> I want to release them from the server not the client. Is there a command for dhcpd to release the leases. I can delete the dhcpd.leases file but dont want to do so if there a proper way of doing it

don't delete the file, delete the leases in it.
see 3 posts up.

---

### Post by {BzF}~JOKesTER on 2008-03-13
Have You Tried This:

sudo /etc/init.d/dhcp3-server stop

---

### Post by pana.corbului on 2008-03-13
You could try a ```
 cat /dev/null > /var/lib/dhcp3/dhcpd.leases 
``` to empty leases file

---

### Post by shahansudu on 2008-03-14
Thank you all,
    deleting the entries from the dhcpd.leses and restarting dhcpd worked....:)

---

