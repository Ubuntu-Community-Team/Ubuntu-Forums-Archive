---
title: "Need help with bind9, permission denied"
date: 2012-11-13
forum: Server Platforms
---

### Post by mixwe on 2012-11-13
Hi all,
I'm installing a ubuntu 12.04 server in a test environement for DHCP and DNS purpose.
I've succesfull installed dhcp3-server ant it works. :)
after this I installed bind9 and dnsutils. 
in the next steps I created the rndc.key file and used it in the named.conf.local file using
```
include "/etc/bind/rndc.key";
```
 
I followed examples on a tutorial page to configure the other settings in named.conf.local, med.conf.options, med.conf.default-zones. 
 
The /etc/bind directory and its content have permissions 644 root:bind
 
Now the problem starts when I want to start the bind9 service.
when I run sudo service bind9 restart I get following error:
```
 * Stopping domain name service... bind9                                                                                                                   WARNING: key file (/etc/bind/rndc.key) exists, but using default configuration file (/etc/bind/rndc.conf)
rndc: connect failed: 127.0.0.1#953: connection refused
                                                                                                                                                    [ OK ]
 * Starting domain name service... bind9                                                                                                            [fail]

```
when I look at /var/log/syslog I find following message:
```
Nov 13 08:47:54 Arwen named[16605]: starting BIND 9.8.1-P1 -u bind
Nov 13 08:47:54 Arwen named[16605]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' 'CPPFLAGS=-D_FORTIFY_SOURCE=2'
Nov 13 08:47:54 Arwen named[16605]: adjusted limit on open files from 4096 to 1048576
Nov 13 08:47:54 Arwen named[16605]: found 1 CPU, using 1 worker thread
Nov 13 08:47:54 Arwen named[16605]: using up to 4096 sockets
Nov 13 08:47:54 Arwen named[16605]: loading configuration from '/etc/bind/named.conf'
Nov 13 08:47:54 Arwen named[16605]: none:0: open: /etc/bind/named.conf: permission denied
Nov 13 08:47:54 Arwen named[16605]: loading configuration: permission denied
Nov 13 08:47:54 Arwen named[16605]: exiting (due to fatal error)

```
 
I'm now confused if it is a permission issue or an rndc issue.
Please help me.

---

### Post by Doug S on 2012-11-13
Perhaps try to separate the variables. I mean, first try to get everything working without rndc, and then, if you really need it, add rndc in later as a single change to something that is already working. (I don't use rndc on my server.)

---

### Post by SeijiSensei on 2012-11-14
Apparently BIND does not think it has the permissions you think it has.  The syslog error reads: "/etc/bind/named.conf: permission denied" so BIND cannot read the named.conf file.

I agree with only adding rndc after you have gotten everything else working.  I do not use rndc on my two public DNS servers either.

---

### Post by mixwe on 2012-11-14
Thanks for reply,
After your answer I tried to remove the include rndc  from the config file. but nothings changed.
I recieve the same error messages as before. Then I tried to rename the rndc.key file and here is the output after restarting bind9
```
 * Stopping domain name service... bind9        
rndc: neither /etc/bind/rndc.conf nor /etc/bind/rndc.key was found

```
**[COLOR=red]How can I use bind without rndc?[/COLOR]** 
 
For permissions issues how can I verify with which user will bind run and how can I test if there are the correct permissions?
 
the permissions now looks so:
```
-rw-r--r-- 1 root bind 2389 Oct  9 15:06 bind.keys
-rw-r--r-- 1 root bind  237 Oct  9 15:06 db.0
-rw-r--r-- 1 root bind  271 Oct  9 15:06 db.127
-rw-r--r-- 1 root bind  423 Nov  8 16:13 db.172.20.100
-rw-r--r-- 1 root bind  237 Oct  9 15:06 db.255
-rw-r--r-- 1 root bind  353 Oct  9 15:06 db.empty
-rw-r--r-- 1 root bind  270 Oct  9 15:06 db.local
-rw-r--r-- 1 root bind  565 Nov  8 16:08 db.middle-earth.local
-rw-r--r-- 1 root bind 2994 Oct  9 15:06 db.root
-rw-r--r-- 1 root bind  707 Nov 14 15:49 named.conf
-rw-r--r-- 1 root bind  490 Oct  9 15:06 named.conf.default-zones
-rw-r--r-- 1 root bind  685 Nov 14 15:40 named.conf.local
-rw-r--r-- 1 root bind  369 Nov 12 15:50 named.conf.options
-rw-r--r-- 1 root bind   77 Nov 14 15:10 rndc.key.tmp
-rw-r--r-- 1 root bind 1317 Oct  9 15:06 zones.rfc1918

```
 
I assume that bind9 runs with user bind that is member of the group bind. In this case the permissions seems correct.

---

### Post by Doug S on 2012-11-14
I do have the default rndc.key file, which perhaps still has to be present, but I don't use rndc. My persmissions are a little different than yours:```
doug@doug-64:~$ ls -l /etc/bind
total 60
-rw-r--r-- 1 root root 2389 Jul 25 14:35 bind.keys
-rw-r--r-- 1 root root  237 Jul 25 14:35 db.0
-rw-r--r-- 1 root root  271 Jul 25 14:35 db.127
-r--r--r-- 1 root bind  933 Oct 12 10:37 db.192
-rw-r--r-- 1 root root  237 Jul 25 14:35 db.255
-rw-r--r-- 1 root root  353 Jul 25 14:35 db.empty
-rw-r--r-- 1 root root  270 Jul 25 14:35 db.local
-rw-r--r-- 1 root root 2994 Jul 25 14:35 db.root
-r--r--r-- 1 root bind  984 Oct 12 10:37 db.smythies.com
-rw-r--r-- 1 root bind  463 Jul 25 14:35 named.conf
-rw-r--r-- 1 root bind  490 Jul 25 14:35 named.conf.default-zones
-rw-r--r-- 1 root bind 3538 Oct 12 10:38 named.conf.local
-rw-r--r-- 1 root bind  762 Oct 12 11:11 named.conf.options
-rw-r----- 1 bind bind   77 Oct 12 09:29 rndc.key
-rw-r--r-- 1 root root 1317 Jul 25 14:35 zones.rfc1918

```Although named.conf is the same.
I tried a restart ( output edited to fit ):```
doug@doug-64:~$ sudo service bind9 restart
[sudo] password for doug:
 * Stopping domain name service... bind9
waiting for pid 1121 to die
[ OK ]
 * Starting domain name service... bind9
[ OK ]
doug@doug-64:~$
```

---

### Post by mixwe on 2012-11-14
hello Doug,
it seems that your permissions are more restrictive than mine... I think it should not hang on permissions related issues in this folder.
 
Altough to continue testing I would like to start bind without rndc, but I really don't know how...

---

### Post by Doug S on 2012-11-14
Wouldn't you just take out the line you said you added back in post #1?:```
include "/etc/bind/rndc.key";
```Although I do observe lo listening on port 953 on my system.
I agree about the permissions. I wonder if you have dnsmasq hanging around getting in the way of something?

---

### Post by mixwe on 2012-11-15
Thank you Doug,
This is the first thing i did
```
//include "/etc/bind/rndc.key";
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

```
But the result is still the same. Further to be sure if there could be a firewall issue I purged it, but nothings changed....
 
I will resume here the steps that I followed during installation:
 
[LIST=1]
[*]apt-get purge appmor
[*]apt-get install nscd
[*]apt-get install dhcp3-server
[*]apt-get install bind9 dnsutils
[*]rndc-confgen -a
[/LIST]I configured dhcp and it works correctly.
I configured bind, I will list here my files:
1. named.conf:
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local
//include "/etc/bind/rndc.key";
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

``` 
2. named.conf.options:
```
options {
        directory "/var/cache/bind";
        allow-transfer {
               127.0.0.1;
               172.20.100.0/24;
        };
        allow-query {
               127.0.0.1;
               172.20.100.0/24;
        };
        forwarders {
                8.8.8.8;
                172.20.100.1;
        };
        auth-nxdomain no;    # conform to RFC1035
        listen-on { any; };
        listen-on-v6 { any; };
};

```
3. named.conf.local
```
ogging {
    channel query.log {
        file "/var/log/query.log";
        severity debug 3;
    };
    category queries { query.log; };
};
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "middle-earth.local" {
  type master;
  file "/etc/bind/db.middle-earth.local";
  allow-transfer { 127.0.0.1; 172.20.100.0/24; };
  allow-update { key "rndc-key" };
  notify yes;
};
zone "100.20.172.in-addr.arpa" {
  type master;
  file "/etc/bind/db.172.20.100";
  allow-transfer { 127.0.0.1; 172.20.100.0/24; };
  allow-update { key "rndc-key" };
  notify yes;
};

```
4. named.conf.default-zones
```
// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};
// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912
zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};
zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};
zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};
zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

```
5. rndc.key
```
key "rndc-key" {
        algorithm hmac-md5;
        secret "xCDX/U9Xr/JZbuFfwyhv9Q==";
};

```
 
Using the configuration described above I get the message during start bind:
```
rndc: connect failed: 127.0.0.1#953: connection refused
[ OK ]
 * Starting domain name service... bind9  [ fail]
```
and in syslog the same message:
```
Nov 15 08:57:12 Arwen named[1388]: loading configuration from '/etc/bind/named.conf'
Nov 15 08:57:12 Arwen named[1388]: none:0: open: /etc/bind/named.conf: permission denied
Nov 15 08:57:12 Arwen named[1388]: loading configuration: permission denied
Nov 15 08:57:12 Arwen named[1388]: exiting (due to fatal error)

```
 
So I'm absolutely not an expert, but where could be here the error, is there a different conf file for rndc?
I also tried to use rndc.conf in /etc/bind but the following message is displayed:
```
WARNING: key file (/etc/bind/rndc.key) exists, but using default configuration file (/etc/bind/rndc.conf)
rndc: connect failed: 127.0.0.1#953: connection refused

```
 
I'm now out of any idea in how could I solve the problem. :confused:

---

### Post by mixwe on 2012-11-15
> **Doug S said:**
>  I wonder if you have dnsmasq hanging around getting in the way of something?
 
 I don't have dnsmasq installed.

---

### Post by Doug S on 2012-11-15
Doesn't allowing remote updates imply rndc?
I don't allow any remote updates and do not have any of these:```
  allow-update { key "rndc-key" };

```My named.local.conf:```
doug@doug-64:~/config/bind$ cat named.conf.options
options {
        directory "/var/cache/bind";
        recursion yes;
        allow-recursion {any;};
        allow-query {any;}; // this is needed to override the default
        [COLOR=red]allow-transfer {"none";[/COLOR] }; // transfer will be allowed per zone below.
        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113
        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.
        forwarders {
                75.153.176.9;
                75.153.176.1;
        };
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```Permissions: As a long shot suggestion, and just for a test, try taking out the logging stuff in named.conf.local

---

### Post by mixwe on 2012-11-15
Ok, good Idea,
This is how looks now my named.conf.local file:
```
//logging {
//    channel query.log {
//        file "/var/log/query.log";
//        severity debug 3;
//    };
//    category queries { query.log; };
//};
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
//include "/etc/bind/rndc.key";
 
zone "middle-earth.local" {
  type master;
  file "/etc/bind/db.middle-earth.local";
  //allow-transfer { 127.0.0.1; 172.20.100.0/24; };
  allow-transfer {"none";};
  //allow-update { key "rndc-key" };
  notify yes;
};
zone "100.20.172.in-addr.arpa" {
  type master;
  file "/etc/bind/db.172.20.100";
  allow-transfer {"none";}; //{ 127.0.0.1; 172.20.100.0/24; };
  //allow-update { key "rndc-key" };
  notify yes;
};

```
 
unfortunately the error is the same, permission denied and connection refused on rndc.
 
Isn't there any command to disable rndc or unlink it from bind? 
Actually there aren't any references to rndc in the named config files....
Should I try to reinstall compleetly bind9 ? purge bind9 and then reinstall?

---

### Post by Doug S on 2012-11-15
Sorry, I am out of ideas to try to help. For the port listenting part, I get this when bind starts:```
.
.
.
Nov 14 07:48:54 doug-64 named[32670]: automatic empty zone: B.E.F.IP6.ARPA
Nov 14 07:48:54 doug-64 named[32670]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
Nov 14 07:48:54 doug-64 named[32670]: command channel listening on [COLOR=red]127.0.0.1#953[/COLOR]
Nov 14 07:48:54 doug-64 named[32670]: zone 0.in-addr.arpa/IN: loaded serial 1
Nov 14 07:48:54 doug-64 named[32670]: zone 10.in-addr.arpa/IN: loaded serial 1
Nov 14 07:48:54 doug-64 named[32670]: zone 127.in-addr.arpa/IN: loaded serial 1
.
.
.
```

---

### Post by mixwe on 2012-11-16
Thank you very much for your help,
I think I will go trough the process reinstalling the machine from scratch and show if it will work, I will try to install only bind9 an see if I can make it run.

I will let you know.

---

### Post by mixwe on 2012-11-19
So, I just reinstalled the server an I began direcly to install bind and dnsutils.
 
I just configured some basic settings in named.conf.local
named.conf.options
and 2 db files.
 
The result is:
 
```
sudo service bind9 restart
 * Stopping domain name service... bind9                                                                                         rndc: connect failed: 127.0.0.1#953: connection refused
                                                                                                                          [ OK ]
 * Starting domain name service... bind9                                                                                  [ OK ]
```
 
I still get the error about rndc, but the service starts.
 
I'm trying to configure some more settings and show it it will work correctly.

---

