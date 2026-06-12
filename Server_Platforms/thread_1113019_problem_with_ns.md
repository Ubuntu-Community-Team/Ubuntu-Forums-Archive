---
title: "problem with ns"
date: 2009-04-01
forum: Server Platforms
---

### Post by Spikerok on 2009-04-01
on 123-reg.co.uk i have registered domain [www.example.com](www.example.com)
it working ok, points on my server. I have added 2 dns entries
ns1 A 1.2.3.4
ns2 A 1.2.3.5

now i have registed another domain, [www.domain.com](www.domain.com), and i want to enter nameservers to point [www.domain.com](www.domain.com) to my server.
so under primary and secondary nameservers i have entered next:
primary ns : ns1.example.com
secondary ns: ns2.example.com

the problem is that [www.domain.com](www.domain.com) can't connect to my server, some thing is wrong with my nameservers.

Please could some on help me out, on how to fix this problem. To get them nameservers to work, to point on my server.

---

### Post by BkkBonanza on 2009-04-01
I'm not sure if you're confused or if you have setup what you want but something is wrong. 

You setup example.com to act as a nameserver for your domain.com server, correct?
If not then you have gone about this the wrong way.

But assuming you know what you're doing then the next step is to verify that your nameservers on example.com are working correctly. You should be able to lookup a name on them directly using a tool like dig. (dig is installed with djbdns but there are serveral versions and also I've seen online versions before too) You need something like dig because it allows you to specify the nameserver to use,

dig @1.2.3.4 domain.com

should give you a valid result. First get it to work locally from your console, then try to update the registrar for domain.com.

If it doesn't work locally then next step is to see if it's even listening. So try,

sudo netstat -lnptu

It should show your nameserver listening on udp port 53. If not then you have problems related to nameserver install/config. Let us know what nameserver your'e using and what results you get from these tests.

---

### Post by Spikerok on 2009-04-01
I have registered domain - [www.example.com](www.example.com) to point to my server as a nameserver and as well it does a basic job as domain, finds ip address and shows web-site.

---

### Post by BkkBonanza on 2009-04-01
First, you can run nameservers but you don't need to. Unless you really feel you need to for some specific reason then I'd suggest you just use the nameserver of your domain registrar (unless you know it to be unreliable).

Second, if your domain and nameservers are on the same server then you just go to the registrar and tell it your nameservers ip. They usually want you have two nameservers for redundancy. If you are only going to server them on one server then I'd suggest backstepping and ask why you want to run nameservers when you don't need to. 

Good practice is generally to have 2 nameservers on two different machines. You can do it on one if you just want to learn but it's not considered to be reliable. Of course if you only have one server then when your names are down your site is down anyway. 

My suggestion: don't bother running a nameserver. Just go to the registrars domain control panel and add an A record point your name to your ip, and a CNAME record pointing www to your domain. 

Add an MX record if you want to handle your own mail but nowadays if often easier and more reliable to use google for email (which you can do and still have your own domain). They have something like 6 servers for redundancy. Read about google apps.

---

### Post by Spikerok on 2009-04-01
well, i would like to run nameserver, or get it sorted some how.
Thats what i have tried to do.

---

### Post by Spikerok on 2009-04-01
what i have now is that i have made using DNS interface on 123-reg.co.uk 2 records
ns1 A 92.20.120.86
ns2 A 92.20.120.86

if i'm correct it should act as a name server now?
if i enter in different domain, nameservers,
ns1.web-a.org.uk
ns2.web-a.org.uk
it will locate my server, but it doesn't do it. can some one help me on how to fix it this problem.

when i tried to use 
ns1.web-a.org.uk
ns2.web-a.org.uk
on one of my other domains i have resived an error "DNS error - cannot find server"

---

### Post by Spikerok on 2009-04-01
...

---

### Post by Spikerok on 2009-04-01
is their any article i can read to find more about nameserver of the type i need..

---

### Post by BkkBonanza on 2009-04-02
Ok. To run your own nameservers you first need to install suitable programs on your server, like Bind or TinyDNS. Many are available. That has to be configured and tested locally. Once that is working correctly then you start configuring the domain names with your registrar.

You will then set the nameserver records which are typically done in a different area of the control panel from the DNS settings. This tells your registrar not to handle your names any more. It will update the global root nameservers for you so that after this all name requests will go to your ip, your nameservers. Any records added to your registrar's control panel except the "nameserver" ones will be ignored.

At this point any requests out on the net for your names will resolve to your nameservers. If your nameservers have trouble or are down then no one can get to your site.

Your own nameservers will have to have records suitable for your domain, like an A records, CNAME and MX records. Those you will enter in the local config files or if you get fancy maybe a web control panel on your own servers.

For a basic primer on DNS read,

[http://en.wikipedia.org/wiki/Domain_name_system](http://en.wikipedia.org/wiki/Domain_name_system)

For more info you can find tons of sites with various info and explanations by googling "DNS how-to".

Just to be clear - on your domain registrar's control panel there is usually two different areas - one for dns control and another for nameserver setting. They are not the same. To set your own nameserver you have to update the nameserver settings not the DNS settings. These records release them from controlling your domain.

---

### Post by Spikerok on 2009-04-02
did my best, and gone back to the start, i have tried couple of guides, and didn't worked out..

i have DNS installed, im using ISPConfig as well.

etc/hosts/
[PHP]
127.0.0.1       localhost.localdomain   localhost
192.168.1.100   server1.web-a.org.uk    server1
92.20.120.86    ns1.web-a.org.uk        ns1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/PHP]

/etc/bind/named.conf.options
[PHP]options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        //forwarders {
        92.20.120.86;
        // };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
[/PHP]

/etc/resolv.conf
[PHP]domain web-a.org.uk
search web-a.org.uk
nameserver 192.168.1.254
[/PHP]

/etc/bind/db.local
[PHP];
; BIND data file for local loopback interface
;
$TTL    604800
//@     IN      SOA     localhost. root.localhost. (
@       IN      SOA     ns1.web-a.org.uk. hostmaster.web-a.org.uk. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
//@     IN      NS      localhost.
//@     IN      A       127.0.0.1
//@     IN      AAAA    ::1
                NS      ns1.web-a.org.uk.
1               PTR     localhost.
[/PHP]

[PHP]root@server1:/home/vladislav# netstat -lnptu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State                                                                                    PID/Program name
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN                                                                                   4210/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN                                                                                   4954/apache2
tcp        0      0 0.0.0.0:81              0.0.0.0:*               LISTEN                                                                                   4771/ispconfig_http
tcp        0      0 192.168.1.66:53         0.0.0.0:*               LISTEN                                                                                   5079/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN                                                                                   5079/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN                                                                                   4120/sshd
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN                                                                                   5079/named
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN                                                                                   5044/master
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN                                                                                   4954/apache2
tcp6       0      0 :::993                  :::*                    LISTEN                                                                                   4330/couriertcpd
tcp6       0      0 :::995                  :::*                    LISTEN                                                                                   4368/couriertcpd
tcp6       0      0 :::110                  :::*                    LISTEN                                                                                   4346/couriertcpd
tcp6       0      0 :::143                  :::*                    LISTEN                                                                                   4303/couriertcpd
tcp6       0      0 :::21                   :::*                    LISTEN                                                                                   5096/proftpd: (acce
tcp6       0      0 :::22                   :::*                    LISTEN                                                                                   4120/sshd
tcp6       0      0 ::1:953                 :::*                    LISTEN                                                                                   5079/named
tcp6       0      0 :::25                   :::*                    LISTEN                                                                                   5044/master
udp        0      0 0.0.0.0:54302           0.0.0.0:*                                                                                                        5079/named
udp        0      0 192.168.1.66:53         0.0.0.0:*                                                                                                        5079/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                                                                                                        5079/named
udp        0      0 0.0.0.0:68              0.0.0.0:*                                                                                                        3694/dhclient3
udp        0      0 192.168.1.66:123        0.0.0.0:*                                                                                                        3825/ntpd
udp        0      0 127.0.0.1:123           0.0.0.0:*                                                                                                        3825/ntpd
udp        0      0 0.0.0.0:123             0.0.0.0:*                                                                                                        3825/ntpd
udp6       0      0 :::52322                :::*                                                                                                             5079/named
udp6       0      0 fe80::224:21ff:fe55:123 :::*                                                                                                             3825/ntpd
udp6       0      0 ::1:123                 :::*                                                                                                             3825/ntpd
udp6       0      0 :::123                  :::*                                                                                                             3825/ntpd
[/PHP]

i'm not sure where are i gone wrong. Please could some one help me to solve this problem.

---

### Post by Spikerok on 2009-04-02
double post

---

### Post by BkkBonanza on 2009-04-02
Now you need someone proficient in bind. I always use tinydns - so the config details are different.

If you type,

dig @192.168.0.100 server1.web-a.org.uk

what do you get? You may need to install dig first if it's not there. It's in the package dnsutils, but also I think bind insalls it.

Using the @ symbol tells it exactly which ns to query.

I'm not certain about bind config but I don't think you want to use 92.20.120.86 as a forwarder. That woulod send you in circles. You should put your service providers ns there, or use opendns 208.67.222.222. You don't want to use an authoritative ns as they won't forward for you. Or use the same value as /etc/resolv.conf perhaps.

---

### Post by Spikerok on 2009-04-03
> **BkkBonaza said:**
> Now you need someone proficient in bind. I always use tinydns - so the config details are different.

If you type,

dig @192.168.0.100 server1.web-a.org.uk

what do you get? You may need to install dig first if it's not there. It's in the package dnsutils, but also I think bind insalls it.

Using the @ symbol tells it exactly which ns to query.

I'm not certain about bind config but I don't think you want to use 92.20.120.86 as a forwarder. That woulod send you in circles. You should put your service providers ns there, or use opendns 208.67.222.222. You don't want to use an authoritative ns as they won't forward for you. Or use the same value as /etc/resolv.conf perhaps.

my ISP ns if im correct? are
Primary DNS:	92.31.242.20
Secondary DNS:	92.31.242.21

---

### Post by BkkBonanza on 2009-04-03
Sorry, I didn't notice last time but 192.168.1.66 is where your bind is listening - so that is where you want to dig to see if it gives valid replies.

Your isp ns 92.31.242.20 can be used for forwarding in bind config as it will forward requests. Forwarding is for handling requests that bind is not authoritative on ie. all the ones not set up in it's config.

Don't get mixed up about various ns. Your bind ns is for answering questions from others about your names. Your isp ns is for forwarding/answering questions by you about everyone elses names. If you set your bind to forward it is simply to let it handle questions it doesn't know about.

---

### Post by vpsville on 2009-04-03
192.168.1.x is an internal LAN IP address, it won't resolve across the internet.

Your DNS server will need a real static IP in order to communicate with the outside world.

---

### Post by Spikerok on 2009-04-03
thats what i got after digging
[PHP]
root@server1:/home/vladislav# dig @192.168.1.66 server1.web-a.org.uk

; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 server1.web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 35195
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;server1.web-a.org.uk.          IN      A

;; AUTHORITY SECTION:
web-a.org.uk.           86400   IN      SOA     ns1.web-a.org.uk. admin.web-a.org.uk. 2009033002 28800 7200 604800 86400

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 11:55:39 2009
;; MSG SIZE  rcvd: 84
[/PHP]

now i need to find file in which i have to change my internal ip address on external ip address
where are can i find file in which i can modify ip?


ifconfig
[PHP]
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:21:55:03:ab
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe55:3ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:821484 (821.4 KB)  TX bytes:1786130 (1.7 MB)
          Interrupt:220

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1018303 (1.0 MB)  TX bytes:1018303 (1.0 MB)
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
Ok. Good. It's not complete but a start. First get your query working locally, then worry about your external ip.

This dig response gives the authority record. So it's saying you should ask ns1.web-a.org.uk for the ip for server1. But actually it should know more. So I expect you haven't added records for server1.web-a.org.uk to your bind config. Going by your earlier posts it looks like you added records for ns1 but not for server1. So do that and then dig again. It should tell you it has authority and the ip for server1.

When that workds then you need to get your external ip working so that users on the web can get into your server. This generally involves adjusting your router to forward port 53 tcp/udp to port 53 on your server1 machine (192.168.1.66). After that forwarding is happening - then you can try digging that external ip. It may not work because of router reflection issues but you can go find a web site for digging. It will allow you to test your external ip and make sure it returns a good reply.

After that is confirmed you can update your registrar with your external ip. You need two. And the world should be able to get your name resolved.

---

### Post by BkkBonanza on 2009-04-03
BTW Make your TTL values lower until you get things sorted out. That way incorrect values won't linger out there for too long in caches. Until everything is well tested I'd use 300 or 600 - that's 5-10 minutes.

---

### Post by Spikerok on 2009-04-03
i have created DNS for server1.web-a.org.uk

all files are in /etc/bind/
pri.server1.web-a.org.uk
[PHP]
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     server1.web-a.org.uk, root.web-a.org.uk. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      server1.web-a.org.uk.
@       IN      A       192.168.1.66
ns      IN      A       192.168.1.66
[/PHP]

added a zone in named.conf
[PHP]
zone "server1.web-a.org.uk
        type master;
        file "pri.server1.web-a.org.uk";
};
[/PHP]

dig
[PHP]
 dig @192.168.1.66 server1.web-a.org.uk

; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 server1.web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; connection timed out; no servers could be reached
[/PHP]

---

### Post by Spikerok on 2009-04-03
I have changed TTL value in pri.server1.web-a.org.uk
[PHP]
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     server1.web-a.org.uk, root.web-a.org.uk. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                            400 )       ; Negative Cache TTL
;
@       IN      NS      server1.web-a.org.uk.
@       IN      A       192.168.1.66
ns      IN      A       192.168.1.66
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
I don't know bind well. But it seems to say you configured that server1 record for the loopback interface. That's 127.0.0.1 - It may need to be configured for the machine's external interface 192.168.1.66. It seems like bind is listening on that ip so there must be some reason it timed out. Have you changed the listening/port config? Try netstat -lnptu to see it's still listening on 192.168.1.66

---

### Post by Spikerok on 2009-04-03
Result
[PHP]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      4211/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4955/apache2
tcp        0      0 0.0.0.0:81              0.0.0.0:*               LISTEN      4772/ispconfig_http
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      4121/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      5045/master
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      4955/apache2
tcp6       0      0 :::993                  :::*                    LISTEN      4331/couriertcpd
tcp6       0      0 :::995                  :::*                    LISTEN      4369/couriertcpd
tcp6       0      0 :::110                  :::*                    LISTEN      4347/couriertcpd
tcp6       0      0 :::143                  :::*                    LISTEN      4304/couriertcpd
tcp6       0      0 :::21                   :::*                    LISTEN      5097/proftpd: (acce
tcp6       0      0 :::22                   :::*                    LISTEN      4121/sshd
tcp6       0      0 :::25                   :::*                    LISTEN      5045/master
udp        0      0 0.0.0.0:68              0.0.0.0:*                           3693/dhclient3
udp        0      0 192.168.1.66:123        0.0.0.0:*                           3823/ntpd
udp        0      0 127.0.0.1:123           0.0.0.0:*                           3823/ntpd
udp        0      0 0.0.0.0:123             0.0.0.0:*                           3823/ntpd
udp6       0      0 fe80::224:21ff:fe55:123 :::*                                3823/ntpd
udp6       0      0 ::1:123                 :::*                                3823/ntpd
udp6       0      0 :::123                  :::*                                3823/ntpd
[/PHP]

some thing wrong with bind

---

### Post by Spikerok on 2009-04-03
rndc: connect failed: 127.0.0.1#953: connection refused

---

### Post by BkkBonanza on 2009-04-03
You'll need to figure that out. Maybe check /var/log/messages or /var/log/syslog for any messages from bind about why it's down. Also, not sure but bind may have some config check option to tell you if the config is bad. If the config has bad syntax it may stop it from starting.

---

### Post by Spikerok on 2009-04-03
fixed the problem, dig again
[PHP]
server1.web-a.org.uk

; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 server1.web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 55727
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;server1.web-a.org.uk.          IN      A

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 14:20:07 2009
;; MSG SIZE  rcvd: 38
[/PHP]

---

### Post by Spikerok on 2009-04-03
I have changed pri.server1.web-a.org.uk config slightly
[PHP]
$TTL 3D
@               IN      SOA     server1.web-a.org.uk. hostmaster.web-a.org.uk. (
                                1       ; Serial
                                8H      ; Refresh
                                2H      ; Retry
                                4W      ; Expire
                                1D)     ; Minimum TTL
                        NS      server1.web-a.org.uk.
1                       PTR     localhost.
[/PHP]
dig
[PHP]
root@server1:/etc/bind# dig @192.168.1.66 server1.web-a.org.uk

; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 server1.web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37206
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;server1.web-a.org.uk.          IN      A

;; AUTHORITY SECTION:
server1.web-a.org.uk.   86400   IN      SOA     server1.web-a.org.uk. hostmaster.web-a.org.uk. 1 28800 7200 2419200 86400

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 14:24:53 2009
;; MSG SIZE  rcvd: 85
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
I'm going to have read some bind docs coz something is wrong in your config but I can't tell. I can see the dig response has a question and authority but it needs an answer. It should say authority is ns1.web-a.org.uk and answer you whatever ip you configured for server1.

---

### Post by BkkBonanza on 2009-04-03
Here is a valid repsonse with dig from my test server here.

slurp@test:~$ dig @192.168.0.119 [www.test.com](www.test.com)

; <<>> DiG 9.4.2-P1 <<>> @192.168.0.119 [www.test.com](www.test.com)
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12526
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;[www.test.com](www.test.com).			IN	A

;; ANSWER SECTION:
[www.test.com](www.test.com).		3600	IN	CNAME	test.com.

;; AUTHORITY SECTION:
test.com.		259200	IN	NS	ns1.test.com.
test.com.		3600	IN	NS	ns2.test.com.
test.com.		3600	IN	NS	ns3.test.com.

;; ADDITIONAL SECTION:
ns1.test.com.		259200	IN	A	111.222.111.111
ns2.test.com.		3600	IN	A	111.222.111.112
ns3.test.com.		3600	IN	A	111.222.111.113

;; Query time: 5 msec
;; SERVER: 192.168.0.119#53(192.168.0.119)
;; WHEN: Fri Apr  3 20:40:11 2009
;; MSG SIZE  rcvd: 146


Notice in this case I have a CNAME record. That's why the ip is in the ADDITIONAL section but with just an A record it would answer in the ANSWER section.

Looking at bind now. Geez, tinydns is a lot easier.

---

### Post by Spikerok on 2009-04-03
i have done some thing wrong, pain in the head.

---

### Post by Spikerok on 2009-04-03
can you give me link to the doc which you have found please

---

### Post by BkkBonanza on 2009-04-03
I've taken an example zone file I found and made changes that I think are needed for your server. If this works then you will change the ips to be your public one. I'm just trying to get familiar with bind syntax. See if this helps. I also think your zone is web-a.org.uk not server1.web-a.org.uk so you should update other files to reflect this.


;
; dns zone for for web-a.org.uk
;
$ORIGIN web-a.org.uk.
$TTL 1D
; any time you make a change to the domain, bump the
; "serial" setting below. the format is easy:
; YYYYMMDDI, with the I being an iterator in case you
; make more than one change during any one day
@     IN SOA   ns1 hostmaster (
                        200405191 ; serial
                        8H        ; refresh
                        4H        ; retry
                        4W        ; expire
                        1D )      ; minimum
; ns1.web-a.org.uk serves this domain and mail just as example
                NS      ns1
                MX      10 mail

; our hostnames, in alphabetical order
ns1             A       192.168.1.66
server1         A       192.168.1.66
mail            A       192.168.1.66

---

### Post by BkkBonanza on 2009-04-03
The page I used to help here was,

[http://madboa.com/geek/soho-bind/](http://madboa.com/geek/soho-bind/)

I don't think it's better than any other. Also note that when you have both your ns going you will add a second NS record replacing the last part above as,

; ns1.web-a.org.uk serves this domain and mail just as example
NS ns1
NS ns2
MX 10 mail

; our hostnames, in alphabetical order
ns1 A 192.168.1.66
ns2 A 192.168.1.67 ; use the other ns ip here
server1 A 192.168.1.66
mail A 192.168.1.66

---

### Post by Spikerok on 2009-04-03
i will delete pri.server1.web-a.org.uk then..
and ill modify pri.web-a.org.uk
current file
[PHP]
$TTL        86400
@       IN      SOA     ns1.web-a.org.uk. admin.web-a.org.uk. (
                        2009040301       ; serial, todays date + todays serial #
                        28800              ; refresh, seconds
                        7200              ; retry, seconds
                        604800              ; expire, seconds
                        86400 )            ; minimum, seconds
;
                NS      ns1.web-a.org.uk.              ; Inet Address of name server 1
                NS      ns2.web-a.org.uk.              ; Inet Address of name server 2
;

  MX      10 secure.web-a.org.uk.

web-a.org.uk.      A        192.168.1.66
www       A       192.168.1.66
server1       A       92.20.120.86

web-a.org.uk.       TXT  "v=spf1 a mx ptr ~all"
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
Here's the same example converted for your named.conf file,

zone "web-a.org.uk" IN {
  // this is the authoritative server for
  // web-a.org.uk
  type master;
  file "zone.uk.org.web-a";
};

Place the zone info above in the file zone.org.web-a
Let me know how this works.
I didn't do the reverse pointers but they can be added later, when you set the public ips too. I don't think filename matter as long as they are match where they are referred to.

---

### Post by Spikerok on 2009-04-03
Current dig 
[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51137
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;web-a.org.uk.                  IN      A

;; ANSWER SECTION:
web-a.org.uk.           86400   IN      A       192.168.1.66

;; AUTHORITY SECTION:
web-a.org.uk.           86400   IN      NS      ns1.web-a.org.uk.

;; ADDITIONAL SECTION:
ns1.web-a.org.uk.       86400   IN      A       192.168.1.66

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 15:24:48 2009
;; MSG SIZE  rcvd: 80
[/PHP]

---

### Post by Spikerok on 2009-04-03
with ns2 dig
[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58478
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;web-a.org.uk.                  IN      A

;; ANSWER SECTION:
web-a.org.uk.           86400   IN      A       192.168.1.66

;; AUTHORITY SECTION:
web-a.org.uk.           86400   IN      NS      ns2.web-a.org.uk.
web-a.org.uk.           86400   IN      NS      ns1.web-a.org.uk.

;; ADDITIONAL SECTION:
ns1.web-a.org.uk.       86400   IN      A       192.168.1.66
ns2.web-a.org.uk.       86400   IN      A       192.168.1.66

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 15:28:51 2009
;; MSG SIZE  rcvd: 114
[/PHP]

---

### Post by Spikerok on 2009-04-03
i have changed ns ip's
[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29006
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;web-a.org.uk.                  IN      A

;; ANSWER SECTION:
web-a.org.uk.           86400   IN      A       192.168.1.66

;; AUTHORITY SECTION:
web-a.org.uk.           86400   IN      NS      ns1.web-a.org.uk.
web-a.org.uk.           86400   IN      NS      ns2.web-a.org.uk.

;; ADDITIONAL SECTION:
ns1.web-a.org.uk.       86400   IN      A       92.20.120.86
ns2.web-a.org.uk.       86400   IN      A       92.20.120.86

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 15:31:07 2009
;; MSG SIZE  rcvd: 114
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
Now you're getting there. What about dig for server1?
Replace all your ips with the public one.

---

### Post by Spikerok on 2009-04-03
server1 dig
[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 server1.web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 21149
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;server1.web-a.org.uk.          IN      A

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 16:00:58 2009
;; MSG SIZE  rcvd: 38
[/PHP]

i have have not modified pri.server1.web-a.org.uk

---

### Post by Spikerok on 2009-04-03
when i dig server1, with out domain
[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 server1
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 64843
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;server1.                       IN      A

;; AUTHORITY SECTION:
.                       10800   IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2009040300 1800 900 604800 86400

;; Query time: 141 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 16:05:00 2009
;; MSG SIZE  rcvd: 100
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
You're not getting that one and maybe all sub-domains. I think you need to use only the subdomain part in the zone file records. See my example - it doesn't have the full names for records in the zone because they are already defined as being in the zone. Bind may be appending them and being confused eg.

server1 not server1.web-a.org.uk because bind may do this,

server1.web-a.org.uk.web-a.org.uk

Not sure about that but looks like an immediate difference.

update: when you dig just server1 it says "authority is with the root ns", that just means you should ask root because I ain't got a clue.

---

### Post by Spikerok on 2009-04-03
do you mean i need to modify pri.server1.web-a.org.uk file?

---

### Post by Spikerok on 2009-04-03
this is my pri.web-a.org.uk
[PHP]
$ORIGIN web-a.org.uk.
$TTL 1D
@       IN      SOA     ns1 hostmaster (
                        200405191       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        4H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
;
                NS      ns1              ; Inet Address of name server 1
                NS      ns2              ; Inet Address of name server 2
;
;
                MX      10 mail
;out hostnames
ns1     A       92.20.120.86
ns2     A       92.20.120.86
web-a.org.uk.      A        192.168.1.66
www       A       192.168.1.66
server1       A       192.168.1.66
mail    A       192.168.1.66

web-a.org.uk.       TXT  "v=spf1 a mx ptr ~all"

;;;; MAKE MANUAL ENTRIES BELOW THIS LINE! ;;;;
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
I'm not sure what you call the file but the file containing web-a.org.uk zone info.
Inside the zone file it should only use subdomain names because bind already associates them with that zone.

---

### Post by BkkBonanza on 2009-04-03
That file looks ok. How does dig respond now?

---

### Post by Spikerok on 2009-04-03
[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 28027
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;web-a.org.uk.                  IN      A

;; ANSWER SECTION:
web-a.org.uk.           86400   IN      A       192.168.1.66

;; AUTHORITY SECTION:
web-a.org.uk.           86400   IN      NS      ns1.web-a.org.uk.
web-a.org.uk.           86400   IN      NS      ns2.web-a.org.uk.

;; ADDITIONAL SECTION:
ns1.web-a.org.uk.       86400   IN      A       92.20.120.86
ns2.web-a.org.uk.       86400   IN      A       92.20.120.86

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 16:25:22 2009
;; MSG SIZE  rcvd: 114
[/PHP]

[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 server1.web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 51973
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;server1.web-a.org.uk.          IN      A

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 16:28:20 2009
;; MSG SIZE  rcvd: 38

[/PHP][PHP]

; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 server1
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 19891
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;server1.                       IN      A

;; AUTHORITY SECTION:
.                       10800   IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2009040300 1800 900 604800 86400

;; Query time: 189 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 16:28:29 2009
;; MSG SIZE  rcvd: 100

[/PHP][PHP]

; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 server1.web-a.org.uk.web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 16028
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;server1.web-a.org.uk.web-a.org.uk. IN  A

;; AUTHORITY SECTION:
web-a.org.uk.           86400   IN      SOA     ns1.web-a.org.uk. hostmaster.web-a.org.uk. 200405191 28800 14400 2419200 86400

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 16:28:40 2009
;; MSG SIZE  rcvd: 102
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
Hmmm. That's what I suspected. It's using full names added to the zone name. Must be mixed up with which file you are using or maybe you didn't reload the config after changing the zone? Something like that. Go back to square one and check each step.

Also remove the web-a.org.uk. A record - doesn't make sense. And for now the TXT record until it works.

---

### Post by Spikerok on 2009-04-03
new zone for web-a.org.uk
[PHP]
$ORIGIN web-a.org.uk.
$TTL 1D
@       IN      SOA     ns1 hostmaster (
                        200405191       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        4H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
;
                NS      ns1              ; Inet Address of name server 1
                NS      ns2              ; Inet Address of name server 2
;
;
                MX      10 mail
;out hostnames
ns1     A       92.20.120.86
ns2     A       92.20.120.86
www       A       192.168.1.66
server1       A       192.168.1.66
mail    A       192.168.1.66

;;;; MAKE MANUAL ENTRIES BELOW THIS LINE! ;;;;
[/PHP]

dig
[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5028
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;web-a.org.uk.                  IN      A

;; AUTHORITY SECTION:
web-a.org.uk.           86400   IN      SOA     ns1.web-a.org.uk. hostmaster.web-a.org.uk. 200405191 28800 14400 2419200 86400

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 16:38:02 2009
;; MSG SIZE  rcvd: 81
[/PHP]

---

### Post by Spikerok on 2009-04-03
a have changed zone back to start with "web-a.org.uk. A 192.168.1.66"
[PHP]
$ORIGIN web-a.org.uk.
$TTL 1D
@       IN      SOA     ns1 hostmaster (
                        200405191       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        4H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
;
                NS      ns1              ; Inet Address of name server 1
                NS      ns2              ; Inet Address of name server 2
;
;
                MX      10 mail
;out hostnames
ns1     A       92.20.120.86
ns2     A       92.20.120.86
web-a.org.uk.   A       192.168.1.66
www       A       192.168.1.66
server1       A       192.168.1.66
mail    A       192.168.1.66
[/PHP]

and have made 2 more digs first one on web-a.org.uk next one on server1.web-a.org.uk
dig web-a.org.uk
[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29570
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;web-a.org.uk.                  IN      A

;; ANSWER SECTION:
web-a.org.uk.           86400   IN      A       192.168.1.66

;; AUTHORITY SECTION:
web-a.org.uk.           86400   IN      NS      ns2.web-a.org.uk.
web-a.org.uk.           86400   IN      NS      ns1.web-a.org.uk.

;; ADDITIONAL SECTION:
ns1.web-a.org.uk.       86400   IN      A       92.20.120.86
ns2.web-a.org.uk.       86400   IN      A       92.20.120.86

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 16:41:48 2009
;; MSG SIZE  rcvd: 114
[/PHP]

dig server1.web-a.org.uk
[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 server1.web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2961
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;server1.web-a.org.uk.          IN      A

;; ANSWER SECTION:
server1.web-a.org.uk.   86400   IN      A       192.168.1.66

;; AUTHORITY SECTION:
web-a.org.uk.           86400   IN      NS      ns2.web-a.org.uk.
web-a.org.uk.           86400   IN      NS      ns1.web-a.org.uk.

;; ADDITIONAL SECTION:
ns1.web-a.org.uk.       86400   IN      A       92.20.120.86
ns2.web-a.org.uk.       86400   IN      A       92.20.120.86

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 16:42:12 2009
;; MSG SIZE  rcvd: 122
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
That's ok for your root web-a.org.uk because you don't have a root record defined.
It seems like you need a blank name record if you want to use web-a.org.uk directly.
Like,

      IN A 192.168.1.66

placed just after the main SOA section, before NS. Also noticed on another site that they put IN before each A, NS or MX value. Not sure if that's an issue. Maybe not.

---

### Post by BkkBonanza on 2009-04-03
HEY. You got an answer for server1 - hooray.
Great. Finally.

---

### Post by Spikerok on 2009-04-03
what do i have to do next?

---

### Post by Spikerok on 2009-04-03
I have added IN A record in zone
[PHP]$ORIGIN web-a.org.uk.
$TTL 1D
@       IN      SOA     ns1 hostmaster (
                        200405191       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        4H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
        IN      A       192.20.120.86
;
                NS      ns1              ; Inet Address of name server 1
                NS      ns2              ; Inet Address of name server 2
;
;
                MX      10 mail
;out hostnames
ns1     A       92.20.120.86
ns2     A       92.20.120.86
web-a.org.uk.   A       192.168.1.66
www       A       192.168.1.66
server1       A       192.168.1.66
mail    A       192.168.1.66
[/PHP]

dig 
[PHP]
; <<>> DiG 9.5.0-P2 <<>> @192.168.1.66 web-a.org.uk
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31497
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;web-a.org.uk.                  IN      A

;; ANSWER SECTION:
web-a.org.uk.           86400   IN      A       192.168.1.66
web-a.org.uk.           86400   IN      A       192.20.120.86

;; AUTHORITY SECTION:
web-a.org.uk.           86400   IN      NS      ns2.web-a.org.uk.
web-a.org.uk.           86400   IN      NS      ns1.web-a.org.uk.

;; ADDITIONAL SECTION:
ns1.web-a.org.uk.       86400   IN      A       92.20.120.86
ns2.web-a.org.uk.       86400   IN      A       92.20.120.86

;; Query time: 0 msec
;; SERVER: 192.168.1.66#53(192.168.1.66)
;; WHEN: Fri Apr  3 16:53:20 2009
;; MSG SIZE  rcvd: 130
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
Change all ips to be your public one.

Make sure your port forwarding on your router/gateway is getting outside requests into your server. Let me know if this needs help.

Try to test from outside your LAN by using a dig site eg. 

[http://www.kloth.net/services/dig.php](http://www.kloth.net/services/dig.php)

You need to tell it your server ip to use (92.20.120.86) and the same name to check as you would with dig. I just checked and your ip 92.20.120.86 is definately blocked. So first you need to sort out your router port forwarding.

---

### Post by Spikerok on 2009-04-03
i can dig it from out side
[PHP]
 ; <<>> DiG 9.3.2 <<>> @92.20.120.86 web-a.org.uk A
 ; (1 server found)
 ;; global options:  printcmd
 ;; Got answer:
 ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48894
 ;; flags: qr aa rd; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 2
 
 ;; QUESTION SECTION:
 ;web-a.org.uk.			IN	A
 
 ;; ANSWER SECTION:
 web-a.org.uk.		86400	IN	A	192.168.1.66
 web-a.org.uk.		86400	IN	A	92.20.120.86
 
 ;; AUTHORITY SECTION:
 web-a.org.uk.		86400	IN	NS	ns1.web-a.org.uk.
 web-a.org.uk.		86400	IN	NS	ns2.web-a.org.uk.
 
 ;; ADDITIONAL SECTION:
 ns1.web-a.org.uk.	86400	IN	A	92.20.120.86
 ns2.web-a.org.uk.	86400	IN	A	92.20.120.86
 
 ;; Query time: 55 msec
 ;; SERVER: 92.20.120.86#53(92.20.120.86)
 ;; WHEN: Fri Apr  3 18:04:52 2009
 ;; MSG SIZE  rcvd: 130
[/PHP]

---

### Post by Spikerok on 2009-04-03
I have changed all ip's on public ones in zone file
[PHP]
$ORIGIN web-a.org.uk.
$TTL 1D
@       IN      SOA     ns1 hostmaster (
                        200405191       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        4H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
        IN      A       92.20.120.86
;
                NS      ns1              ; Inet Address of name server 1
                NS      ns2              ; Inet Address of name server 2
;
;
                MX      10 mail
;out hostnames
ns1     A       92.20.120.86
ns2     A       92.20.120.86
web-a.org.uk.   A       92.20.120.86
www       A       92.20.120.86
server1       A       92.20.120.86
mail    A       92.20.120.86
[/PHP]

dig from [http://www.kloth.net/services/dig.php](http://www.kloth.net/services/dig.php)
[PHP]
 ; <<>> DiG 9.3.2 <<>> @92.20.120.86 web-a.org.uk A
 ; (1 server found)
 ;; global options:  printcmd
 ;; Got answer:
 ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59467
 ;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2
 
 ;; QUESTION SECTION:
 ;web-a.org.uk.			IN	A
 
 ;; ANSWER SECTION:
 web-a.org.uk.		86400	IN	A	92.20.120.86
 
 ;; AUTHORITY SECTION:
 web-a.org.uk.		86400	IN	NS	ns2.web-a.org.uk.
 web-a.org.uk.		86400	IN	NS	ns1.web-a.org.uk.
 
 ;; ADDITIONAL SECTION:
 ns1.web-a.org.uk.	86400	IN	A	92.20.120.86
 ns2.web-a.org.uk.	86400	IN	A	92.20.120.86
 
 ;; Query time: 593 msec
 ;; SERVER: 92.20.120.86#53(92.20.120.86)
 ;; WHEN: Fri Apr  3 18:09:00 2009
 ;; MSG SIZE  rcvd: 114
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
Good. I was able to do it from here too.
But you have a LAN ip lingering there and don't want that sent to public queries. You will need to fix that.

Try a more extensive check at [http://www.ip-plus.net/tools/dns_check_set.en.html](http://www.ip-plus.net/tools/dns_check_set.en.html)
It gives you some more diagnostics.

You should also have a secondary ns on another ip. Maybe your registrar will let it go with only one - don't know as I always used two. 

Now that you can query it from outside you can update your domain registrar to use your nameserver at 92.20.120.86 and test it fully with the tool above or other ones out there.

update - I see you fixed ips already. Recommend you don't use long values for ttl as you have. If that goes public then the ips will sit in caches for a long time and you may want to change something. You won't see the changes until the caches update.

---

### Post by Spikerok on 2009-04-03
so i have to fix all them errors i get?

---

### Post by BkkBonanza on 2009-04-03
I didn't see any errors but there were warnings. I would try to get no or few warnings if possible. Mostly it says you need reverse pointers. Those aren't critical but they ought to be there. Lots of sites don't have their reverse points set when they are on shared hosting. Should have them for ns though. Do what you can.

---

### Post by Spikerok on 2009-04-03
ill try to fix reverse pointers. I'm unable to get nameservers to work on one of my domains, i have two domains, one is web-a.org.uk which is used as nameserver, so i have used nameservers on other domain and im still getting error, DNS error - cannot find server

---

### Post by Spikerok on 2009-04-03
in DNS nameserver i have entered for other domain
Primary - ns1.web-a.org.uk
Second  - ns2.web-a.org.uk

ah i see..

---

### Post by BkkBonanza on 2009-04-03
Did you change your zone file? When I check server1.web-a.org.uk or even ns1.web-a.org.uk it no longer has any answer.

---

### Post by Spikerok on 2009-04-03
no, zone file
[PHP]
$ORIGIN web-a.org.uk.
$TTL 1D
@       IN      SOA     ns1 hostmaster (
                        2009040350       ; serial, todays date + todays serial #
                        10800              ; refresh, seconds
                        3600              ; retry, seconds
                        604800              ; expire, seconds
                        1D )            ; minimum, seconds
        IN      A       92.20.120.86
;
                NS      ns1              ; Inet Address of name server 1
                NS      ns2              ; Inet Address of name server 2
;
;
                MX      10 mail
;out hostnames
ns1     A       92.20.120.86
ns2     A       92.20.120.86
web-a.org.uk.   A       92.20.120.86
www       A       92.20.120.86
server1       A       92.20.120.86
mail    A       92.20.120.86
[/PHP]

---

### Post by Spikerok on 2009-04-03
i have added reverse zone
[PHP]
$TTL 1D
@       IN      SOA     ns1 hostmaster (
                        2009040350       ; serial, todays date + todays serial #
                        10800              ; refresh, seconds
                        3600              ; retry, seconds
                        604800              ; expire, seconds
                        1D )            ; minimum, seconds
        IN      A       92.20.120.86
;
                NS      ns1              ; Inet Address of name server 1
                NS      ns2              ; Inet Address of name server 2
;
;
;out hostnames
ns1     A       92.20.120.86
ns2     A       92.20.120.86
[/PHP]

---

### Post by BkkBonanza on 2009-04-03
Ok. The dig tool on IP-Plus works but the DNS check doesn't for subdomains. Not sure why that is. Maybe it's trying to cross check them to your registrars dns and failing since they aren't setup over there.

I did a regular public check on your name web-a.org.uk and it worked fine.

---

### Post by Spikerok on 2009-04-03
can it be because im using ISPConfig?

---

### Post by BkkBonanza on 2009-04-03
Also working for your web server here. Your'e good!

---

### Post by Spikerok on 2009-04-03
thanks for your help!

---

### Post by BkkBonanza on 2009-04-03
Your'e welcome and good luck. 
If I were more of a bind expert it would have been quicker. 

I use tinydns because it uses much less RAM. I'm on 128 MB vps accounts so memory is tight. tinydns uses < 1MB compared to bind which is infinite... well, it has no qualms about using 70MB.

---

