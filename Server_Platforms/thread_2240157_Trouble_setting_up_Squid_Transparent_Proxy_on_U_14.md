---
title: "Trouble setting up Squid Transparent Proxy on U 14.04"
date: 2014-08-18
forum: Server Platforms
---

### Post by KishanB on 2014-08-18
Hi There

Have been trying for past few days everything I can think of to get Squid working as a transaprent proxy on my home network and am hitting my head against a brick will trying to figure out why it's not working. Any help would be greatly appreciated.

Ok so our network topology looks like so:

ISP Provided Router(192.168.1.1) <-- I have disabled the DHCP on this.
Ubuntu U.14.04(Virtual Machine,1 NIC, 192.168.1.5) <-- this box runs ISC-DHCP and BIND9 and I wanted to add Squid

NOTE:
The Ubuntu 14.04 is core, not gui


So the Ubuntu box is running ISC-DHCP which is handing out leases on the 192.168.1.X range(DHCP Scope is .30 - .80), in the dhcpd.conf file, the router option is currently set to 192.168.1.1, Bind9 is running and I have configured the forwarders to point to google's DNS.

I have installed squid3, and have tried numerous ways at trying to get this to work, including editing the iptables to forward traffic it receives on port 80 to port 3128:


_**Squid3 Config:**_
acl lan localnet src 192.168.1.0/24
http_access allow lan
http_port 3128 transaprent
cache_dir aufs /etc/squid3/cache 20000 16 256

So I saved a file with the following contents and then imported that into the iptables

*nat
-A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
COMMIT

I then ran "sudo iptables-restore < /etc/iptables.up.rules", it does import it and I beleive it does redirect traffic but something is going wrong, I flush my dns cache on my Windows PC, try go to google and it times out, I can't ping any websites either.

If I remove the "transparent" option from the squid config, restart squid and tell my browser(FireFox) to use the proxy(192.168.1.5 80) then it works, but as soon as I put the transparent option back it breaks again.


_**ISC-DHCP Config:**_

ddns-update-style interim;
update-static-leases on;
allow client-updates;
ddns-domainname "bharadia.com.";
ddns-rev-domainname "in-addr.arpa.";

option domain-name "bharadia.com";
option domain-name-servers DHCP-DNS.bharadia.com, 192.168.1.5;

default-lease-time 86400;
max-lease-time 86400;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.30 192.168.1.80;
    option routers 192.168.1.1;
    next-server 192.168.1.100;
}


_**Bind9 Config:**_

The forwarders config it setup to use Google's DNS(8.8.8.8, 8.8.4.4)

**Forward Zone:**
;
; BIND data file for local loopback interface
; Restart the bind9 service to make the changes live
;
$TTL    604800
@       IN      SOA     DHCP-DNS.bharadia.com.  admin.bharadia.com. (
                                20140817        ; Serial
                                7200            ; Refresh
                                3600            ; Retry
                                432000          ; Expire
                                86400           ; Negative Cache TTL
)
;
bharadia.com.   IN      NS      DHCP-DNS.bharadia.com.
bharadia.com.   IN      A       192.168.1.5
gateway         IN      A       192.168.1.1
www             IN      CNAME   bharadia.com.

**Reverse Zone:**

@       IN      SOA     DHCP-DNS.bharadia.com.  admin.bharadia.com. (
                                20140818        ; Serial
                                7200            ; Refresh
                                3600            ; Retry
                                432000          ; Expire
                                86400           ; Negative Cache TTL
)
;
                IN      NS      DHCP-DNS.
5               IN      PTR     DHCP-DNS.bharadia.com


Any help would be immensly appreciated, I can get it work if I set my browser to point to that proxy directly but just not in transparent mode which is what I want.

Kind Regards,

Kishan

---

### Post by JDorfler on 2014-08-18
If I remember correctly the transparent option is default and you may not have to have http_port 3128 transparent.  You may just need http_port 3128.  I know nothing of bind 9 or your DHCP server.  Also, you may want to look at using OpenDNS instead of Google DNS.  OpenDNS may be a little bit faster.

---

### Post by KishanB on 2014-08-19
Hi JDorfler,

I tried that and it didn't work, every time I browse to any webpage I just get an error saying "The following URL could not be retrieved /", I tried transparent mode again and this time, when I try go to google.com, it resolves to google.co.uk but then just get's stuck at waiting to load the page, and eventually times out, I can ping google.com and it will find the I.P but not actually ping it, so it's getting part of the way just not finishing it. I don't understand where it's getting stopped.

I researched a bit before choosing my DNS forwarder as initially I picked a local ISP which I got the fastest pings to and was rated highly but as I'm not a customer the were blocking a number of domain requests(ad's mostly), so I chose google for now as the syslog was getting spammed DNS refused log entrys. Changing to Google's is fine now, will look at that later after I get squid working.

---

### Post by KishanB on 2014-08-19
EDIT: I got Squid working finally, this thread can be closed.




Rite, some progress, so I've set the squid3 to transparent mode, I've configured the iptables to forward requests on port 80  to 3128, and I've changed my Gateway on my PC to point to the squid box(since squid/bind9/isc-dhcp) are running on the same machine, my Gateway/DNS servers all the same I.P.

So the problem is my forward lookup zone is broken somewhere down the line, in my post above the pages resolved but never loaded, if I go directly to the I.P of the page, it works fine. So for some reason my forward lookup is not working. nslookup works from I.P > HOSTNAME, but not from HOSTNAME > I.P

Will experiment now and see what I can find, any ideas ?

---

