---
title: "DNS moved to non routable network"
date: 2009-03-22
forum: Server Platforms
---

### Post by th3 mant1s on 2009-03-22
Hi Community,

I need some help understanding what might have went wrong here.

I just moved a DNS Server off of a public IP address that had forwarders enabled to a closed network that is shut off from the outside world at a 10.0.0.0 network address (not actual address). All I am trying to do is dig the machine at its address aka dig @10.0.23.2 . However It displays the error 

; <<>> DiG 9.4.2-P2 <<>> @10.0.23.2
; (1 server found)
;; global options:  printcmd
;; connection timed out; no servers could be reached

Basically I am trying to make this a DNS Server on a non routable network. 

Can someone please help me?

Thanks!

---

### Post by netztier on 2009-03-22
> **th3 mant1s said:**
> 
Basically I am trying to make this a DNS Server on a non routable network. 



Checked the "allow-recursion" option?

[http://ubuntuforums.org/showthread.php?t=1089748](http://ubuntuforums.org/showthread.php?t=1089748)

Make sure you have the address ranges where your DNS clients are listed in allow-recursion {...}

regards

Marc

---

### Post by th3 mant1s on 2009-03-22
Hi netizer,

Thanks for the reply. I actually did not have that in my options so I added it. I then proceeded to try and dig my server at localhost and @ my ip address. However I am getting not response (same message as last time). 

The ultimate goal is to at least respond to a dig using 

dig @ipaddress

I checked and don't have any firewall rules blocking the service. Please let me know if you need more.  

-J

---

### Post by Xipher on 2009-03-22
on the DNS server run this command
```

netstat -lntup | grep named

```
you'll want to make sure it's listening on your bound IP addresses and not just localhost. If you're not seeing your IP addresses listed you should check the config for the listen directive and change it to
```

listen-on    { any; };

```

---

### Post by th3 mant1s on 2009-03-23
Hi Xipher. 

I issued the netstat command you wanted and got the following reply:

tcp        0      0 10.0.23.2:53            0.0.0.0:*               LISTEN      18808/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      18808/named
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      18808/named
tcp6       0      0 :::53                   :::*                    LISTEN      18808/named
tcp6       0      0 ::1:953                 :::*                    LISTEN      18808/named
udp        0      0 0.0.0.0:50817           0.0.0.0:*                           18808/named
udp        0      0 10.0.23.2:53            0.0.0.0:*                           18808/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           18808/named
udp6       0      0 :::58883                :::*                                18808/named
udp6       0      0 :::53                   :::*                                18808/named


So it seems to be listening... However I noticed the "udp 0 0 10.0.23.2:53 0.0.0.0:* 18808/named" doesn't exclusively have LISTEN next to it. How can I remedy this?

How can I get the DNS service to listen on UDP Port 53 and then respond to the dig command? Do I need to edit the named.conf.options to allow this? If so could someone please show me how?

---

### Post by Xipher on 2009-03-23
UDP sockets don't have a "LISTEN" state so you won't see them but if they are listed that's all that matters.
As for not responding, did you do an rndc reload or service named restart after you made the change to your configuration file for the allow-recursion?

---

### Post by th3 mant1s on 2009-03-23
Xipher, 

Yes I performed both: rndc reload and /etc/init.d/bind9 restart|reload. All were successful. I gave my iptables a check and it had nothing special:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Maybe I should be more explicit in them however I still feel it's a configuration issue. What do you think? anyone?

---

### Post by netztier on 2009-03-23
> **th3 mant1s said:**
> Thanks for the reply. I actually did not have that in my options so I added it. 

Hm. If that is Ubuntu's default install of BIND 9, the allow-recursion section should be in /etc/bind/named.conf.local by default, and /etc/bind/named.conf defines /etc/bind/named.conf.local to be included.

[COLOR="Red"]*Edit: D'OH! of course, allow-recursion should be in /etc/bind/named.conf.**options** by default, not in /etc/bind/named.conf.**local**, sorry for any confusion caused by this.*
[/COLOR] 
Double-check that you don't have multiple **allow-recursion{...}** sections that might be conflicting.

regards

Marc

---

### Post by th3 mant1s on 2009-03-23
Hi Netztier,

here is my named.conf.options configuration:
=======================================================================
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        // query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

         forwarders {
                10.0.23.2;
         };

        allow-recursion {
                localnets;
                10.0.0.0/8;
        };


        //auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
        allow-query {any; };
};

===================================================================

and here is my named.conf.local file..

===================================================================

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "linux.lan" {
type master;
file "/etc/bind/zones/linux.lan.db";
};

zone "23.0.10.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.23.0.10.in-addr.arpa";
};
==================================================================

Do you think it might have something to do with my /etc/hosts file?

[/etc/hosts]

127.0.0.1       localhost       Cybersec1
10.0.23.2       Cybersec1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Thanks again for helping!

-J

---

### Post by netztier on 2009-03-23
> **th3 mant1s said:**
> 
here is my named.conf.options configuration:
=======================================================================
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        // query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

         forwarders {
                10.0.23.2;
         };

        allow-recursion {
                localnets;
                10.0.0.0/8;
        };


        //auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
        allow-query {any; };
};

===================================================================

and here is my named.conf.local file..

===================================================================

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "linux.lan" {
type master;
file "/etc/bind/zones/linux.lan.db";
};

zone "23.0.10.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.23.0.10.in-addr.arpa";
};
==================================================================


Suggestion: when showing command line output or config file excerpts, use the [ CODE][/CODE ] tags for your text. Just highlight the text and use the **#** button from the toolbar above the edit box.

> 
Do you think it might have something to do with my /etc/hosts file?


Nope. The **/etc/hosts** file is only relevant to the local resolver (aka "DNS client"), even if that DNS client is on the same system that runs your DNS server. In fact, the OS that runs your BIND can use an entirely different DNS infrastructure from the one it hosts. 

Of course, it does make some sense to configure /etc/resolv.conf on the DNS machine to have 127.0.0.1 ("myself") as first entry, but there is no obligation to. This being said ... what does **/etc/resolv.conf** look like on your server?

Can you show us the output of

```
user@dnsserver:~$ **dig @localhost -x 10.0.23.2**
```

(assuming 10.0.23.2 is the address of this machine and there is a proper PTR record for this address in /etc/bind/zones/rev.23.0.10.in-addr.arpa .)

regards

Marc

---

