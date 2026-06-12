---
title: "Will it require a DNS server to be set up?"
date: 2012-03-26
forum: Server Platforms
---

### Post by deepakdeshp on 2012-03-26
I have an Intranet of Clients and Ubuntu 10.04 server. There is no internet connectivity from the servers and the client. I require that the clients recognize the server by name. At present they are accessing the server by  ip address. I do not want to make any changes on the client side like updating hosts file etc. Can I do this? What is the procedure to accomplish this task?

---

### Post by iiz on 2012-03-26
Hello,

Yes, it does require DNS server.

DNS is super simple to setup.

```
sudo apt-get install bind9
```Then edit the conf files:

```
sudo nano /etc/bind/named.conf.local

``````
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "domain.com" {
        type master;
        file "/etc/bind/db/db.domain.com";
};
```OR if you want just a single name like typing in "server" with no tld, like a baus :) do the following:

```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "server" {
        type master;
        file "/etc/bind/db/db.server";
};
```then you need to add the db files

create a new file:

```
sudo nano /etc/bind/db/db.server
```Inside that put:
```
$TTL    604800
@       IN      SOA     server   admin.server. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
        IN      A       10.0.1.11
        IN      NS      ns1
ns1     IN      A       10.0.1.11
www     IN      A       10.0.1.11
subdomain2     IN      A       10.0.1.11

```then you can execute sudo rndc reload to reparse the conf files and you're all set:

```
sudo rndc reload
```and as always the how-to, just in case i missed something: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
[B]
[COLOR=Red]OHH almost forgot[/COLOR][/B]
You are going to have to set each client machine to use the server as it's dns provider, you can do this easily by setting the DHCP server to serve the servers address as the DNS server. Otherwise if you configured manually, you know what you have to do :)

---

### Post by deepakdeshp on 2012-03-26
> **iiz said:**
> 

** [COLOR=Red]OHH almost forgot[/COLOR]**
You are going to have to set each client machine to use the server as it's dns provider, you can do this easily by setting the DHCP server to serve the servers address as the DNS server. Otherwise if you configured manually, you know what you have to do :)

That s great and thank you, Let me try it out. Let me setup the dhcp  server on the Ubuntu server  and it will provide the dns server name to  the clients. Let me search how to set up the dhcp server or, if you have  it ready, please provide the link.

I also need to have 2 network cards and 2 networks for the Ubuntu server. What do I need to do to accomodate the 2nd network card?

---

### Post by deepakdeshp on 2012-03-27
There is no /etc/et/etc/bind/db/db.server file or /etc/bind/db directory
Instead the files are :-

-rw-r--r-- 1 root root  237 2011-11-17 02:00 db.0
-rw-r--r-- 1 root root  271 2011-11-17 02:00 db.127
-rw-r--r-- 1 root root  237 2011-11-17 02:00 db.255
-rw-r--r-- 1 root root  353 2011-11-17 02:00 db.empty
-rw-r--r-- 1 root root  270 2011-11-17 02:00 db.local
-rw-r--r-- 1 root root 2940 2011-11-17 02:00 db.root

Which file should I use in place of /etc/bind/db/db.server

---

### Post by lykwydchykyn on 2012-03-27
A much simpler option than bind would be dnsmasq.  It simply uses the server's hosts file as the name database.  Considering you have only one name to match up, that probably makes more sense than bind.

---

### Post by deepakdeshp on 2012-03-29
> **lykwydchykyn said:**
> A much simpler option than bind would be dnsmasq.  It simply uses the server's hosts file as the name database.  Considering you have only one name to match up, that probably makes more sense than bind.

Thank you . Let me try it . I found a good article [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq) which I will try out to implement dnsmasq. It looks like it will take care of dns and dhcp both

---

### Post by lykwydchykyn on 2012-03-29
> **deepakdeshp said:**
> Thank you . Let me try it . I found a good article [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq) which I will try out to implement dnsmasq. It looks like it will take care of dns and dhcp both

Yes, and you get dynamic dns (dhcp hosts resolvable by name) in the bargain.  Setting that up under BIND is a minor headache (I have some servers at work that I had to set up like that -- not my favourite thing to configure).

---

### Post by deepakdeshp on 2012-04-08
> **lykwydchykyn said:**
> A much simpler option than bind would be dnsmasq.  It simply uses the server's hosts file as the name database.  Considering you have only one name to match up, that probably makes more sense than bind.

I installed dnsmasq and removed bind9. But the config file  /etc/dnsmasq.conf file is fully commented. 

**All my clients on the intranet  have to resolve the Ubuntu server by name .**
My router is  the dhcp host  and hence my Ubuntu 10.04 server should not be a dhcp server. In this scenario what should be the dnsmasq config file?

---

### Post by Zorael on 2012-04-08
If you could get the clients to use your Ubuntu server as DNS but keep your router as DHCP, wouldn't that accomplish what you want?

As clients query the Ubuntu server to resolve addresses, dnsmasq answers with whatever it knows from having read the hosts file. If it doesn't know a particular host it would try to look it up from an external DNS, but as it doesn't have access to the outside world it would simply reply "lolidunno NXDOMAIN".

As for configuration, the only uncommented entries I have in my dnsmasq.conf are;
```
strict-order
local=/local/
cache-size=5000
log-queries
log-async=2
```
The log bits are from when I tried figuring out why it wouldn't use my VPN's DNS. The cache because well, I'm using it solely for the cache.

So it probably works fine even with your completely commented dnsmasq.conf.

---

### Post by deepakdeshp on 2012-04-08
> **Zorael said:**
> 

If it doesn't know a particular host it would try to look it up from an external DNS, but as it doesn't have access to the outside world it would simply reply "lolidunno NXDOMAIN".



The clients in the network will want to know only the Ubuntu server name by using dnsmasq. There is no need to resolve any other name. I added the entries suggested by Zorael and restarted dnsmasq . How do I tell  the client to look at the dnsmasq server to resolve the name of the dnsmasq server?

---

### Post by Doug S on 2012-04-08
As mentioned in a previous posting, I think you would want to have your DHCP server, your router, supply the IP address of your DNS server as part of the lease information. Then your clients know what should be used for DNS lookups. If your router/DCHP server is a hardware one, then you should be able set the DNS somewhere in the local DHCP Server setup configurations.

---

### Post by Zorael on 2012-04-08
So it's enough if the clients are able to access/ping/resolve the server by its hostname, not needing to know its IP? No other features needed?

Do ridicule me if I misunderstand things, but wouldn't samba's netbios nameserver **nmbd** be enough, then?
```
$ ping -c4 **macididi**                *# netbios hostname resolve via nmbd*
PING **macididi** (**10.0.0.81**) 56(84) bytes of data.
64 bytes from **10.0.0.81**: icmp_req=1 ttl=64 time=4.37 ms
64 bytes from **10.0.0.81**: icmp_req=2 ttl=64 time=6.84 ms
64 bytes from **10.0.0.81**: icmp_req=3 ttl=64 time=4.90 ms
64 bytes from **10.0.0.81**: icmp_req=4 ttl=64 time=6.32 ms

--- macididi ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 4.370/5.612/6.847/1.009 ms

$ ping -c4 **macididi.local**         *# mDNS hostname resolve*
PING **macididi.local** (**10.0.0.81**) 56(84) bytes of data.
64 bytes from **10.0.0.81**: icmp_req=1 ttl=64 time=7.21 ms
64 bytes from **10.0.0.81**: icmp_req=2 ttl=64 time=5.81 ms
64 bytes from **10.0.0.81**: icmp_req=3 ttl=64 time=5.17 ms
64 bytes from **10.0.0.81**: icmp_req=4 ttl=64 time=11.5 ms

--- macididi.local ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 5.177/7.449/11.595/2.505 ms
```
macididi is a macbook in our local network, and its IP is not referenced to anywhere in my hosts file. If I stop the nmbd daemon the hostname no longer resolves. macididi.local keeps resolving though, probably as long as I have Avahi running.

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns **wins**
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
```
You need [**libpam-winbind**](apt://libpam-winbind), which pulls Winbind. You don't seem to need to run the winbindd daemon to just resolve stuff like this, however.

---

### Post by deepakdeshp on 2012-05-23
> **Zorael said:**
> 

Do ridicule me if I misunderstand things, but wouldn't samba's netbios nameserver **nmbd** be enough, then?
 

This is a very simple solution. Let me try it. Thank you

---

### Post by Zorael on 2012-05-23
Try.

And again, if you're running Avahi you may already be able to resolve **hostname.domain** hosts, where **domain** is *local* by default -- or perhaps your company Internet domain name. Truth be told I'm not sure where to change that. : /

No need to install extra packages that way, and no overhead from extra daemons.

---

### Post by deepakdeshp on 2012-05-23
> **Zorael said:**
> Try.

And again, if you're running Avahi you may already be able to resolve **hostname.domain** 
No need to install extra packages that way, and no overhead from extra daemons.

I am studying Avahi and how to implement it.

I do not have an internet domain name. In fact there will not be any internet connection at all . It will just be an intra net, wired and wireless connected to a router.

---

### Post by deepakdeshp on 2012-05-31
> **Zorael said:**
> Try.
You need [**libpam-winbind**]("apt://libpam-winbind"), which pulls Winbind. You don't seem to need to run the winbindd daemon to just resolve stuff like this, however.


Which package can I install to get libpam-winbind?

---

