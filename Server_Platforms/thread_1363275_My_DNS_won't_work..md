---
title: "My DNS won't work."
date: 2009-12-24
forum: Server Platforms
---

### Post by Nadzirun Hazim on 2009-12-24
Hey guys.
I've just got a problem Setting up my DNS Server.
I followed this guide below but still no luck. 
[https://help.ubuntu.com/9.04/serverguide/C/dns.html](https://help.ubuntu.com/9.04/serverguide/C/dns.html)

I'll show you what I did. First I changed the Ethernet to static.
I.P. Address: 192.168.11.20
Netmask: 255.255.255.0
Gateway: 192.168.11.1

Then I configure this file /etc/bind/named.conf.options.
This is inside:
```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

     forwarders {
         192.168.11.20;
     };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
```

As you can see, 192.168.11.20 is my Name Server.

Then I turn BIND9 into a primary Master server by editing /etc/bind/named.conf.local.
```
zone "hazim.com" {
 type master;
    file "/etc/bind/db.hazim.com" ;
}

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
```
"Hazim" is what I want to be my Domain Name.

As I followed the guide, It ask me to use an existing zone file as a template to create the /etc/bind/db.hazim.com file by doing this:

> sudo cp /etc/bind/db.local /etc/bind/db.hazim.com

After that, it ask me to edit the new zone file, /etc/bind/db.example.com.
This is inside, can you guys tell me if something was wrong in here.

```
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    ns.hazim.com. nhazimdeheritage.yahoo.com. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    ns.hazim.com.
@    IN    A    ns.hazim.com.
ns    IN    A    192.168.11.20
www    IN    A    192.168.11.22
mta    IN    A    192.168.11.23
```
After done editing the new zone file, it says to restart the Bind9 services.

This is what happen after I restart the Bind9 services.
>  * Stopping domain name service... bind9
                                       rndc: connect failed: 127.0.0.1#953: connection refused [ OK ]
 * Starting domain name service... bind9 [COLOR=Red]                                [fail] [/COLOR]


I thought this was a matter of wrong typing but when I checked all was ok. Then I tried to restart again the result is the same as above.

Thanks guys.

---

### Post by BkkBonanza on 2009-12-24
You'll need to check the log file to see why it failed. 
Post that here if it's not obvious.

---

### Post by Nadzirun Hazim on 2009-12-24
Sorry but where can I find it?

---

### Post by koenn on 2009-12-24
/var/log/syslog

---

### Post by koenn on 2009-12-24
some comments 

1-
> 
First I changed the Ethernet to static.
I.P. Address: 192.168.11.20
```

     forwarders {
         192.168.11.20;
     };


```
setting forwarders to point to the dns server itself doesn't make sense. 


2-
> ```

zone "hazim.com" {
 type master;
    file "/etc/bind/db.hazim.com" ;
}


```
After that, it ask me to edit the new zone file, /etc/bind/db.example.com.
This is inside, can you guys tell me if something was wrong in here


you should edit /etc/bind/db.hazim.com, not  /etc/bind/db.example.com

(just checking ... :) )

---

### Post by Nadzirun Hazim on 2009-12-25
Hehe, sorry, I've got confused that I type the wrong one.

Wait, I'll post the log file.

---

### Post by Nadzirun Hazim on 2009-12-25
Here is it:

```
Dec 25 18:45:35 hazim-desktop named[5320]: starting BIND 9.5.1-P2.1 -u bind
Dec 25 18:45:35 hazim-desktop named[5320]: found 1 CPU, using 1 worker thread
Dec 25 18:45:35 hazim-desktop named[5320]: using up to 4096 sockets
Dec 25 18:45:35 hazim-desktop named[5320]: loading configuration from '/etc/bind/named.conf'
Dec 25 18:45:35 hazim-desktop named[5320]: /etc/bind/named.conf:41: missing ';' before end of file
Dec 25 18:45:35 hazim-desktop named[5320]: loading configuration: failure
Dec 25 18:45:35 hazim-desktop named[5320]: exiting (due to fatal error)
```

---

### Post by BkkBonanza on 2009-12-25
Well, that kind of lays it out for you...

Dec 25 18:45:35 hazim-desktop named[5320]: /etc/bind/named.conf:41: missing ';' before end of file

Check your syntax again.

---

### Post by Nadzirun Hazim on 2009-12-25
It works now.
It's only a Syntax error. hehe. :P

Thanks guys! :popcorn:

---

### Post by KiLaHuRtZ on 2009-12-28
```
zone "hazim.com" {
 type master;
    file "/etc/bind/db.hazim.com" ;
}**[COLOR="Red"];[/COLOR]**

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
```

---

### Post by HighCommander540 on 2009-12-28
> **Nadzirun Hazim said:**
> Hey guys.
I've just got a problem Setting up my DNS Server.
I followed this guide below but still no luck. 
[https://help.ubuntu.com/9.04/serverguide/C/dns.html](https://help.ubuntu.com/9.04/serverguide/C/dns.html)

I'll show you what I did. First I changed the Ethernet to static.
I.P. Address: 192.168.11.20
Netmask: 255.255.255.0
Gateway: 192.168.11.1

Then I configure this file /etc/bind/named.conf.options.
This is inside:
```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

     forwarders {
         192.168.11.20;
     };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
```

As you can see, 192.168.11.20 is my Name Server.

Koenn was right though, you really need to get rid of the statement you have under forwarders. It might not cause a start up problem, but at certain times (during lookup) it can cause BIND to just loop to itself for a lookup forever. It would be bad. The addresses you are supposed to put in the forwarders section is only for other DNS servers. If BIND can't do the lookup itself it needs to know where to send the browser to try and look next. So you really should change that.

---

