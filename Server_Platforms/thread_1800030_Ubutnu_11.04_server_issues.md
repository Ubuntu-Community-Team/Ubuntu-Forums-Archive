---
title: "Ubutnu 11.04 server issues"
date: 2011-07-08
forum: Server Platforms
---

### Post by trebor0926 on 2011-07-08
Thank goodness for all you Linux wizards out there. 
Been working on this server stuff (DNS) for a week, and still have no clue as to why it 
wont connect to my static registered IP :(. Been reading the Ubuntu Linux Bible for clues, 
but Von Hagen seems to setup a local DNS, which does not help me. 
Also been browsing thru the Debian server forums and info pages...
 
HERE IS THE SCENERIO:
I am trying to get my APACHE2 server connected with my registered DOMAIN name.
Registered Domain name: elementac.com
Public Static IP Address: 99.154.65.113
Server LAN IP Addr: 192.168.0.10
 
Whenever I do a ping [www.elementac.com]("http://www.elementac.com"), it times out with no response.
And of course, trying to view the index.html (IE: [http://www.elementac.com/index.html](http://www.elementac.com/index.html))
on this server is a NO-GO also.
 
I keep tinkering around with all of these settings, but still no luck. 
(This is almost as bad as trying to build a map using the COD4 Radiant tools.
PULLING YOUR HAIR OUT STUFF, you know... LOL...
At least, there is LOTS of information on doing this. Infinity Ward, and of course
Treyarch suck at posting information about doing maps, servers, etc... 
At least with Crytek, for Crysis 1 and 2, there is LOTS of info on building maps, 
servers, etc. They are AWESOME.) 
 
Anyway,
I personally think that I am getting LOCAL and PUBLIC confused, but because
I am a newby at this LINUX SERVER stuff, ??it happens... Been in computers for
30+ years, just not on the LINUX SERVER SIDE.
 
GOD BLESS you guys if you can get me on the right track with this.
Robert
 
Below is the NITTY-GRITTY...
 
[COLOR=red]**/var/log/syslog**[/COLOR]
```

[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: starting BIND 9.7.3 -u bind[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: adjusted limit on open files from 4096 to 1048576[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: found 2 CPUs, using 2 worker threads[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: using up to 4096 sockets[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: loading configuration from '/etc/bind/named.conf'[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: reading built-in trusted keys from file '/etc/bind/bind.keys'[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: using default UDP/IPv4 port range: [1024, 65535][/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: using default UDP/IPv6 port range: [1024, 65535][/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: listening on IPv6 interfaces, port 53[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: listening on IPv4 interface lo, 127.0.0.1#53[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: listening on IPv4 interface eth0, 192.168.0.10#53[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: generating session key for dynamic DNS[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: set up managed keys zone for view _default, file 'managed-keys.bind'[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: 254.169.IN-ADDR.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: 2.0.192.IN-ADDR.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: 100.51.198.IN-ADDR.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: 113.0.203.IN-ADDR.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: D.F.IP6.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: 8.E.F.IP6.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: 9.E.F.IP6.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: A.E.F.IP6.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: B.E.F.IP6.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: command channel listening on 127.0.0.1#953[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: command channel listening on ::1#953[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 0.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 10.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 127.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 16.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 17.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 18.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 19.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 20.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 21.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 22.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 23.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 24.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 25.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 26.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 27.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 28.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 29.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 30.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 31.172.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 168.192.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone 255.in-addr.arpa/IN: loaded serial 1[/FONT]
[FONT=Courier New][COLOR=red]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: /etc/bind/zones/elementac.com.db:19: ignoring out-of-zone data (dns1.sbcglobal.net)[/COLOR][/FONT]
[FONT=Courier New][COLOR=red]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: /etc/bind/zones/elementac.com.db:20: ignoring out-of-zone data (dns2.sbcglobal.net)[/COLOR][/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone elementac.com/IN: loaded serial 201106301[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone localhost/IN: loaded serial 2[/FONT]
[FONT=Courier New][COLOR=red]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: managed-keys-zone ./IN: loading from master file managed-keys.bind failed: file not found[/COLOR][/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: managed-keys-zone ./IN: loaded serial 0[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: zone elementac.com/IN: sending notifies (serial 201106301)[/FONT]
[FONT=Courier New]Jul  8 09:36:46 UbuntuAMD64x2 named[4736]: running[/FONT]

```
 
[COLOR=red]**/etc/bind/named/conf.local**[/COLOR]
```

[FONT=Courier New]// Do any local configuration here[/FONT]
[FONT=Courier New]//[/FONT]
[FONT=Courier New]zone "elementac.com" IN {[/FONT]
[FONT=Courier New]type master;[/FONT]
[FONT=Courier New]file "/etc/bind/zones/elementac.com.db";[/FONT]
[FONT=Courier New]};[/FONT]
[FONT=Courier New]//zone "0.168.192.in-addr.arpa" {[/FONT]
[FONT=Courier New]//    type master;[/FONT]
[FONT=Courier New]//    file "/etc/bind/zones/rec.0.168.192.in-addr.arpa";[/FONT]
[FONT=Courier New]//};[/FONT]
[FONT=Courier New]// Consider adding the 1918 zones here, if they are not used in your[/FONT]
[FONT=Courier New]// organization[/FONT]
[FONT=Courier New]include "/etc/bind/zones.rfc1918";[/FONT]

```
 
 
**[COLOR=red]/etc/bind/zones/elementac.com.db[/COLOR]**
```

[FONT=Courier New]; Use semicolons to add comments.[/FONT]
[FONT=Courier New]; Host-to-IP Address DNS Pointers for elementac.com[/FONT]
[FONT=Courier New]; Note: The extra "." at the end of addresses are important.[/FONT]
[FONT=Courier New]; The following parameters set when DNS records will expire, etc.[/FONT]
[FONT=Courier New]; Importantly, the serial number must always be itereted upward to [/FONT]
[FONT=Courier New]; prevent undesireable consequences. A good format to use is YYYYMMDDI where[/FONT]
[FONT=Courier New]; the I index is in case you make more that one change in the same day.[/FONT]
[FONT=Courier New]$TTL 86400[/FONT]
[FONT=Courier New]elementac.com.   IN SOA  webserver.elementac.com. hostmaster.elementac.com. ([/FONT]
[FONT=Courier New]     201106301 ; serial no. based on date[/FONT]
[FONT=Courier New]         21600 ; Refresh after 6 hours[/FONT]
[FONT=Courier New]          3600 ; Retry after 1 hour[/FONT]
[FONT=Courier New]        604800 ; Expire after 7 days[/FONT]
[FONT=Courier New]          3600 ; Minimum TTL of 1 hour[/FONT]
[FONT=Courier New])[/FONT]
[FONT=Courier New]elementac.com         IN    A       99.154.65.113[/FONT]
[FONT=Courier New]ubuntuamd64x2         IN    A       192.168.0.10[/FONT]
[FONT=Courier New]dns1.sbcglobal.net.   IN    A       68.94.156.1[/FONT]
[FONT=Courier New]dns2.sbcglobal.net.   IN    A       68.94.157.1[/FONT]
[FONT=Courier New]@                     IN    NS      dns1.sbcglobal.net.[/FONT]
[FONT=Courier New]@                     IN    NS      dns2.sbcglobal.net.[/FONT]
[FONT=Courier New]@                     IN    MX      10 ubuntuamd64x2[/FONT]
[FONT=Courier New]www                   IN    CNAME   ubuntuamd64x2[/FONT]
[FONT=Courier New]ftp                   IN    CNAME   ubuntuamd64x2[/FONT]

```
 
[COLOR=red]**[COLOR=black]$[/COLOR] host elementac.com**[/COLOR]
```

elementac.com mail is handled by 10 ubuntuamd64x2.elementac.com.

```
 
[COLOR=red]**[COLOR=black]$[/COLOR] dig elementac.com**[/COLOR]
```

[FONT=Courier New]; <<>> DiG 9.7.3 <<>> elementac.com[/FONT]
[FONT=Courier New];; global options: +cmd[/FONT]
[FONT=Courier New];; Got answer:[/FONT]
[FONT=Courier New];; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19762[/FONT]
[FONT=Courier New];; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0[/FONT]
[FONT=Courier New];; QUESTION SECTION:[/FONT]
[FONT=Courier New];elementac.com.   IN A[/FONT]
[FONT=Courier New];; AUTHORITY SECTION:[/FONT]
[FONT=Courier New]elementac.com.  3600 IN SOA webserver.elementac.com. hostmaster.elementac.com. 201106301 21600 3600 604800 3600[/FONT]
[FONT=Courier New];; Query time: 0 msec[/FONT]
[FONT=Courier New];; SERVER: 127.0.0.1#53(127.0.0.1)[/FONT]
[FONT=Courier New];; WHEN: Fri Jul  8 09:38:39 2011[/FONT]
[FONT=Courier New];; MSG SIZE  rcvd: 88[/FONT]
 

```

---

### Post by dtfinch on 2011-07-08
I don't have much bind or other self-dns hosting experience but:

I think you need a "." after "elementac.com" in you "A" record. That's just how mine looks. The "ubuntuamd64x2" in the CNAME record should maybe change to your domain name. And the "IN NS" lines should probably point to your own name servers.

And I can't ping any of your name server ip's, and they don't seem to respond to dns requests in general.

---

### Post by Gyokuro on 2011-07-08
Hi,

could you please post the output of following command:

sudo service bind9 reload

---

### Post by hawkmage on 2011-07-08
I would suggest having your elementac.com.db file like this:
```
$TTL 86400
@   IN SOA  webserver.elementac.com. hostmaster.elementac.com. (
     201106301 ; serial no. based on date
         21600 ; Refresh after 6 hours
          3600 ; Retry after 1 hour
        604800 ; Expire after 7 days
          3600 ; Minimum TTL of 1 hour
)
@                     IN    NS      dns1.sbcglobal.net.
@                     IN    NS      dns2.sbcglobal.net.
@                     IN    MX      10 ubuntuamd64x2
@                     IN    A       99.154.65.113
ubuntuamd64x2         IN    A       192.168.0.10
www                   IN    CNAME   ubuntuamd64x2
ftp                   IN    CNAME   ubuntuamd64x2
```

I like the use of the @ for the domain for the zone.  This picks up the info from the zone definition.  It makes the file more portable.  

Unless this is a DNS for users on the internet to resolve names there is no need for the SBC GLobal entries and defining their DNS servers as the domains name servers.  

If this DNS server is going to act as both an internal and external DNS you may want to look into using views to that you can have separate zones for internal and external name resolution.

---

### Post by trebor0926 on 2011-07-11
> **Gyokuro said:**
> Hi,

could you please post the output of following command:

sudo service bind9 reload
Appreciate your response. Here is the response back from the command
[EMAIL="root@UbuntAMD64x2:/"]root@UbuntAMD64x2:/[/EMAIL]# sudo service bind9 reload
* Reloading domain name service... bind9                                                                 [OK]
[EMAIL="root@UbuntuAMD64x2:/"]root@UbuntuAMD64x2:/[/EMAIL]#

---

### Post by trebor0926 on 2011-07-11
Almost there.
I can go to [http://www.elementac.com](http://www.elementac.com), on the server, using the Firefox browser, and it shows me the following:
[IMG]http://www.elementmechanicalac.com/images/Screenshot.png[/IMG]As you can see, I can get there, but it is locally. 

Below, is the SYSLOG from this:
```

Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: starting BIND 9.7.3 -u bind
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: adjusted limit on open files from 4096 to 1048576
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: found 2 CPUs, using 2 worker threads
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: using up to 4096 sockets
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: loading configuration from '/etc/bind/named.conf'
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: using default UDP/IPv4 port range: [1024, 65535]
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: using default UDP/IPv6 port range: [1024, 65535]
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: listening on IPv6 interfaces, port 53
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: listening on IPv4 interface lo, 127.0.0.1#53
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: listening on IPv4 interface eth0, 192.168.0.10#53
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: generating session key for dynamic DNS
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: set up managed keys zone for view _default, file 'managed-keys.bind'
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: 254.169.IN-ADDR.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: D.F.IP6.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: 8.E.F.IP6.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: 9.E.F.IP6.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: A.E.F.IP6.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: B.E.F.IP6.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: command channel listening on 127.0.0.1#953
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: command channel listening on ::1#953
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 0.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 10.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 127.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 16.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 17.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 18.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 19.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 20.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 21.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 22.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 23.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 24.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 25.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 26.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 27.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 28.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 29.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 30.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 31.172.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 168.192.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:33 UbuntuAMD64x2 named[3562]: zone 255.in-addr.arpa/IN: loaded serial 1
Jul 11 12:03:34 UbuntuAMD64x2 named[3562]: zone elementac.com/IN: loaded serial 201106301
Jul 11 12:03:34 UbuntuAMD64x2 named[3562]: zone localhost/IN: loaded serial 2
Jul 11 12:03:34 UbuntuAMD64x2 named[3562]: managed-keys-zone ./IN: loading from master file managed-keys.bind failed: file not found
Jul 11 12:03:34 UbuntuAMD64x2 named[3562]: managed-keys-zone ./IN: loaded serial 0
Jul 11 12:03:34 UbuntuAMD64x2 named[3562]: zone elementac.com/IN: sending notifies (serial 201106301)
Jul 11 12:03:34 UbuntuAMD64x2 named[3562]: running

```I have made changes to the following files: **[COLOR=Red]/etc/bind/named.conf.local[/COLOR]**
```

[FONT=Courier New]// /etc/bind/named.conf.local
// Do any local configuration here
//

 zone "elementac.com" IN {
     type master;
    file "/etc/bind/zones/elementac.com.db";
};

//zone "0.168.192.in-addr.arpa" {
//    type master;
//    notify no;
//    file "/etc/bind/db.192";
//};
//zone "0.168.192.in-addr.arpa" {
//    type master;
//    file "/etc/bind/zones/rec.0.168.192.in-addr.arpa";
//};
// Consider adding the 1918 zones here, if they are not used in your
// organization

include "/etc/bind/zones.rfc1918";

[/FONT]
```I have also made changes in the following:** [COLOR=Red]/etc/bind/zones/elementac.com.db[/COLOR]**
I know I am talking about the IP Address of 99.154.65.113, but I put this 99.154.65.118 in here,
because it is my IP Address used for the bridged modem and in the DLink Router, so I am thinking one DSL line, and one IP Address.
As I have said, I have never set up DNS before, and this is one helluvan experience for me, this qo round.

```

[FONT=Courier New]; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for elementac.com
; Note: The extra "." at the end of addresses are important.
; The following parameters set when DNS records will expire, etc.
; Importantly, the serial number must always be itereted upward to 
; prevent undesireable consequences. A good format to use is YYYYMMDDI where
; the I index is in case you make more that one change in the same day.

$TTL 86400
elementac.com.         IN    SOA     webserver.elementac.com. hostmaster.elementac.com. (
    201106301    ; serial no. based on date
        21600    ; Refresh after 6 hours
         3600    ; Retry after 1 hour
       604800    ; Expire after 7 days
         3600    ; Minimum TTL of 1 hour
)
@                      IN    NS    dns1.sbcglobal.net.
@                      IN    NS    dns2.sbcglobal.net.
@                      IN    MX    10 ubuntuamd64x2
@                      IN    A    99.154.65.118
ubuntuamd64x2          IN    A    192.168.0.10
www                    IN    CNAME    ubuntuamd64x2
ftp                    IN    CNAME    ubuntuamd64x2
[/FONT]

```Now, when I do**[COLOR=Red] host elementac.com[/COLOR]**, this is the result of this:
```

[FONT=Courier New]$ host www.elementac.com
www.elementac.com is an alias for ubuntuamd64x2.elementac.com
ubuntuamd64x2.com has address 192.168.0.10
[/FONT]
```The following is the result of [COLOR=Red]dig [www.elementac.com]("http://www.elementac.com")[/COLOR]
```

[FONT=Courier New]l <<>> Dig 9.7.3 <<>> www.elementac.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12548
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;www.elementac.com.            IN    A

;; ANSWER SECTION:
www.elementac.com.   86400   IN    CNAME   ubuntuamd64x2.elementac.com.
ubuntuamd64x2.elementac.com. 86400 IN   A    192.168.0.10

;; AUTHORITY SECTION:
elementac.com.       86400  IN    NS    dns2.sbcglobal.net.
elementac.com.       86400  IN    NS    dns1.sbcglobal.net.

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Jul 11 14:52:44 2011
;; MSG SIZE   rcvd: 130

[/FONT]
```And, of course, when I do an
NSLOOKUP [www.elementac.com]("http://www.elementac.com")
this is the result:
```

[FONT=Courier New]Server:        127.0.0.1
Address:       127.0.0.1#53

www.elementac.com     canonical name = ubuntu64x2.elementac.com.
Name:   ubuntuamd64x2.elementac.com
Address: 192.168.0.10
[/FONT]
```Again, what I am looking for all of this to do is EQUATE the static IP Address I have from my ISP,
of 99.154.65.113 to [www.elementac.com]("http://www.elementac.com"), and be able to serve webpages for it, over the internet.

Perhaps I need to change the 99.154.65.118 back to the 99.154.65.113. 
I will try that and see what happens, but there still seems to be something missing.

ANY HELP WILL ALLOW ME TO KEEP THE GRAY HAIR IN MY HEAD, INSTEAD OF ON THE FLOOR... LOL

---

### Post by hawkmage on 2011-07-11
Are you going to try and use the ISPs IP address from systems from your 192.168.0.0/24 network?

If so you are going to have issues unless all of you machines send all of their traffic through your route/firewall.  

If you want different IP addresses returned for internal and external clients take a look at using views.

---

### Post by trebor0926 on 2011-07-12
[COLOR=red]**Thanks for all the wonderful info**[/COLOR]. Broke down and went and bought the book :P,
**DNS and BIND**, by [COLOR=red]Cricket Liu[/COLOR] and [COLOR=red]Paul Albitz,[COLOR=black] from [/COLOR]Oreilly publishing[/COLOR]. The author 
of the Ubuntu Linux Bible, William von Hagen, strongly recommended it, so I did it. 
Browsing thru it, much good and juicy information, although I am not setting up a 
tremendously large network. It does answer alot of the questions that you start out
wondering about, with this building a network. Hopefully, I will have my network up 
and running soon, the proper way. Then, I can invite you guys over for Coffee, or 
Beer, whatever works best (LOL).

---

### Post by trebor0926 on 2011-07-13
JUST TO PUT AN END TO THIS NITEMARE...
Well, First of all, let me thank all of you for all of your help.
SECONDLY, our DSL service here at our HVAC company here in Dallas, 
ELEMENT MECHANICAL, is with AT&T, or sbcglobal.net, and 6 months ago,
we told them we wanted ONE STATIC IP address because of the custom software we 
run, called ACOWIN, and, well, they ended up giving us 5 useable's, so they told me. 
So I went and registered a domain name of elementac.com, under the STATIC IP 
address of 99.154.65.113, and set the DNS's to 99.154.65.114 and 99.154.65.115, 
which I had planned to be on my machine(s) here in my office. All of this was 
basically, PLAYING AROUND WITH kind of thing... IE: To learn from (LOL). Boy, have 
I learned a thing or two... Anyway...
 
As of yesterday, (after talking to their TIER 2's tech support, and their supervisor), it turns out 
that our STATIC IP's are what they call STICKY STATIC IP's, and because the owner
of this company, when he got the DSL service, got a RESIDENTIAL MODEM, namely 
SPEEDSTREAM 4100, AT&T does not support the DLINK ROUTER that I bought. IE: 
The modem is put in BRIDGE MODE, so all information goes into the router, and the 
modem is simply a pass-thru device. That is all fine, but last night, after talking with 
this supervisor, he assured me that when I do a TRACERT 99.154.65.113, from 
another network, I would see that the 99.154.65.113 would come up after going to 
99.154.65.118. Of course this did not happen. Since then, I have contacted 
REGISTER.COM, the company I registered our domain name with, and changed the 
IP ADDR from 99.154.65.113 to 99.154.65.118,which is the IP Address that 
Sbcglobal.net gave us, and well, I can see the Index.html on my server her in my 
office. 
 
Here, I was for the last two weeks, trying to configure a DNS server, thinking that, 
that was what was keeping me from seeing my index.html page. Little did I know...
So, now that REGISTER.COM has changed my DNS1 and DNS2 to their NameServers, 
I will approach this DNS and BIND thing down the road. Of course, after doing 
computer stuff for 30+ years, I had never worked with DNS and BIND, and tried to 
host my own website on my own computer in my office.
 
 
So, all in all, all is well, as far as trying to host my own website. Now I can upload all 
kinds of perl modules, without godaddy.com, or whoever, telling me,
"You have to rent a dedicated server, to use certain perl modules". And, of course,
I can write some CGI programs, using "C", do some programming in PERL, finally. 
This was where I was headed in the first place.
 
 
What an experience. I had forgotten just what it was like when learning new things in 
the computer world. GEEZZ...
[CENTER]:lolflag:[/CENTER]
 
Thanks again for all of your help, LINUX WIZARDS...

---

