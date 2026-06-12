---
title: "DNS troubles"
date: 2011-05-11
forum: Server Platforms
---

### Post by shanth2600 on 2011-05-11
how's it going guys?
Im trying to set up an ubuntu DNS server on my local net.
The service is up and running and is able to do forward lookups and serve me public IP's however is not serving the IP's associated with the custom zone I created on the server. 
 
here's my named.conf.local file
 
one "home.lan" IN {
type master;
file "/etc/bind/zones/home.lan.db";
};
 
heres the /zones/home.lan.db file
 
home.lan. IN SOA ubuntu.home.lan. hostmaster.home.lan. (
2008080901 ; serial
8H ; refresh
4H ; retry
4W ; expire
1D ; minimum
)
 
home.lan. IN NS ubuntu.home.lan.
localhost IN A 127.0.0.1
shant IN A 192.168.0.55
 
 
I am doing the testing from an XP's who's dns settings have been set to point to the ubuntu machine. When i do an nslookup for shant.home.lan, i am hoping to get 192.168.0.55 (obviously) however, i get failure message.
 
Let me know if you'd like more information
and thanks in advanced!
 
ps i am editing the conf files from my XP machine using samba. I am fairly cetain I am maintaining the proper enconding, but im not 100%

---

### Post by SeijiSensei on 2011-05-12
Your first stop is the /var/log/messages file where bind will report any errors it finds.

---

### Post by terazen on 2011-05-13
Did you typo "zone" to "one" on your server or only in the forum post?  If you can open 2 cli sessions run "tail -f /var/log/syslog | grep -i named" in one window and restart bind in the other.

---

### Post by shanth2600 on 2011-05-13
> **terazen said:**
> Did you typo "zone" to "one" on your server or only in the forum post? If you can open 2 cli sessions run "tail -f /var/log/syslog | grep -i named" in one window and restart bind in the other.
 
sorry for the typo, but 'zone' was correctly spelled in the atual file. I opened up 2 SSH sessions and did what you instructed. heres the output
 
May 13 15:19:38 ns1 named[640]: received control channel command 'stop -p'
May 13 15:19:38 ns1 named[640]: shutting down: flushing changes
May 13 15:19:38 ns1 named[640]: stopping command channel on 127.0.0.1#953
May 13 15:19:38 ns1 named[640]: stopping command channel on ::1#953
May 13 15:19:38 ns1 named[640]: no longer listening on ::#53
May 13 15:19:38 ns1 named[640]: no longer listening on 127.0.0.1#53
May 13 15:19:38 ns1 named[640]: no longer listening on 192.168.0.240#53
May 13 15:19:38 ns1 named[640]: exiting
May 13 15:19:39 ns1 named[4342]: starting BIND 9.7.1-P2 -u bind
May 13 15:19:39 ns1 named[4342]: built with '--prefix=/usr' '--mandir=/usr/share                                                                                                                                /man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var                                                                                                                                ' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--                                                                                                                                enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--wit                                                                                                                                h-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesy                                                                                                                                stem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--ena                                                                                                                                ble-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbol                                                                                                                                ic-functions' 'CPPFLAGS='
May 13 15:19:39 ns1 named[4342]: adjusted limit on open files from 1024 to 10485                                                                                                                                76
May 13 15:19:39 ns1 named[4342]: found 1 CPU, using 1 worker thread
May 13 15:19:39 ns1 named[4342]: using up to 4096 sockets
May 13 15:19:39 ns1 named[4342]: loading configuration from '/etc/bind/named.con                                                                                                                                f'
May 13 15:19:39 ns1 named[4342]: reading built-in trusted keys from file '/etc/b                                                                                                                                ind/bind.keys'
May 13 15:19:39 ns1 named[4342]: using default UDP/IPv4 port range: [1024, 65535                                                                                                                                ]
May 13 15:19:39 ns1 named[4342]: using default UDP/IPv6 port range: [1024, 65535                                                                                                                                ]
May 13 15:19:39 ns1 named[4342]: listening on IPv6 interfaces, port 53
May 13 15:19:39 ns1 named[4342]: listening on IPv4 interface lo, 127.0.0.1#53
May 13 15:19:39 ns1 named[4342]: listening on IPv4 interface eth0, 192.168.0.240                                                                                                                                #53
May 13 15:19:39 ns1 named[4342]: generating session key for dynamic DNS
May 13 15:19:39 ns1 named[4342]: set up managed keys zone for view _default, fil                                                                                                                                e 'managed-keys.bind'
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 254.169.IN-ADDR.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 255.255.255.255.IN-ADDR.A                                                                                                                                RPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0                                                                                                                                .0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0                                                                                                                                .0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: D.F.IP6.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 8.E.F.IP6.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 9.E.F.IP6.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: A.E.F.IP6.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: B.E.F.IP6.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
May 13 15:19:39 ns1 named[4342]: automatic empty zone: 0.1.1.0.0.2.IP6.ARPA
May 13 15:19:39 ns1 named[4342]: command channel listening on 127.0.0.1#953
May 13 15:19:39 ns1 named[4342]: command channel listening on ::1#953
May 13 15:19:39 ns1 named[4342]: zone 0.in-addr.arpa/IN: loaded serial

---

### Post by shanth2600 on 2011-05-13
> **SeijiSensei said:**
> Your first stop is the /var/log/messages file where bind will report any errors it finds.
 
i cant make any sense of this file. I searched for anything relating to bind and the only logs i found were relating to hash tables. I could post the entirety of the file, but its pretty large.

---

### Post by eric_1982 on 2011-05-13
What is handing out your DHCP address? 
Does your Windows machine have you zone set as the dns suffix? To check you could go to Start > Run, type cmd and hit enter. Enter ipconfig /all in the dos window. Look what the suffix is set to.

---

### Post by shanth2600 on 2011-05-15
both the server and the XP machine have static IP's. And the XP is correctly configured to make dns queries to the server (as I said in the first post, the server is able to go out and grab IP's from public DNS servers but not my custom zones.)

---

### Post by terazen on 2011-05-16
You should be seeing something in the syslog similar to "zone home.lan /IN: loaded serial 2008080901".  Does /etc/bind/zones/home.lan.db exist and have permissions for bind to read?

You can check your file with "named-checkzone home.lan /etc/bind/zones/home.lan.db".  Also, you have ubuntu.home.lan as your NS, but no A record for it.  If you change something in your home.lan.db file make sure to update the serial to the current date/version.

---

### Post by shanth2600 on 2011-05-16
> **terazen said:**
> You should be seeing something in the syslog similar to "zone home.lan /IN: loaded serial 2008080901". Does /etc/bind/zones/home.lan.db exist and have permissions for bind to read?
 
You can check your file with "named-checkzone home.lan /etc/bind/zones/home.lan.db". Also, you have ubuntu.home.lan as your NS, but no A record for it. If you change something in your home.lan.db file make sure to update the serial to the current date/version.
 
wow turns that out the problem was the missing A record for the NS.
THANKS ALOT!
:P:P:P

---

