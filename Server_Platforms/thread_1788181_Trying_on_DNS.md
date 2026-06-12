---
title: "Trying on DNS"
date: 2011-06-22
forum: Server Platforms
---

### Post by Rakeshvijayan on 2011-06-22
I am trying to configure DNS on my virtual meachine I got I message, will you share your 
knowledge what it is? and how to recover from there? ...

---

### Post by varunendra on 2011-06-23
Please provide more details about what you are trying to accomplish.

It seems your current dns is set to 192.168.130.128 (in /etc/resolv.conf)

Generally VMware by default configures the virtual NIC to use NAT and automatically assigns necessary network configuration to your virtual machine to make it able to connect to internet.

In your screenshot, you are trying to lookup your own virtual machine whose name may not be in the dns server's lookup table.

What happens if you try:
```
nslookup google.com
```

---

### Post by Rakeshvijayan on 2011-06-28
What happens if you try: nslookup google.com

---

### Post by varunendra on 2011-06-28
That means your virtual machine is connected to internet and the dns server is working fine.

Now in order to know what do you need help with, we need a detailed description about what are you trying to do and what is the problem you are facing. Your posts so far do not make much sense. Please provide details.

If you wanted to configure DNS just to be able to browse internet, it's already done!

If you want to configure your virtual machine as a DNS server, we need to know what have you tried so far and where are you stuck.

---

### Post by Rakeshvijayan on 2011-06-28
sorry friends I need to study system administration in ubuntu .I have installed KOHA library management package .koha is open only in browser ,I can call Koha with it ip address 192.168.1.200 .I need to give a name for calling koha .Today I took a machine and Installed koha and trying call with its my name  ....I make testing it on my system with out virtual machine this where my WHOLE CONFIGURATION screen shots ,please sagest    me the solution

---

### Post by Rakeshvijayan on 2011-06-28
remaining  files include nslookup with my computer name

---

### Post by Rakeshvijayan on 2011-06-28
nslookup google.com

---

### Post by Rakeshvijayan on 2011-06-28
I got information from a site after they show their nslookup with its name

---

### Post by varunendra on 2011-06-28
Sorry, I've no experience with this one. Must do a lot of research before answering here - not possible anytime soon I'm afraid.

Maybe some experienced guy could look at these to suggest what you need.

---

### Post by hawkmage on 2011-06-28
You have a space in the zone name in the file named.conf.local.

---

### Post by Rakeshvijayan on 2011-06-29
> **hawkmage said:**
> You have a space in the zone name in the file named.conf.local.

Do you mean this one 
zone " rakeshvijayan.com"

I delete the space between "and r....but got same answer ..... let me have a one question 

.how can I check my dns working or not ? is it have a solution?

---

### Post by Rakeshvijayan on 2011-06-29
> **varunendra said:**
> Sorry, I've no experience with this one. Must do a lot of research before answering here - not possible anytime soon I'm afraid.

Maybe some experienced guy could look at these to suggest what you need.


Is my entries are correct ? ....how You first check with  your dns is in proper configuration

---

### Post by Rakeshvijayan on 2011-06-29
please any one share your configuration file of your  DNS server .I searched enough documents but didn't got answer ...please share your knowledge I am little boy in linux so help me to walk with you all ....
your help would be more appreciate ...

---

### Post by haqking on 2011-06-29
> **Rakeshvijayan said:**
> Do you mean this one 
zone " rakeshvijayan.com"

I delete the space between "and r....but got same answer ..... let me have a one question 

.how can I check my dns working or not ? is it have a solution?


I have read this over and over a few times now and still cant quite workout what it is you are trying to achieve.

How you can check if your DNS is working is if it does its job which is to resolve host names to IP addresses and vice versa as long as the correct reverse entries exist.

You are able to perform nslookups and i assume you ping a name and it gets resolved to a name does it not ?

what entries do you have that do not resolve ?

---

### Post by hawkmage on 2011-06-30
OK, Here you go here is a sample of my DNS config.

/etc/bind/db.my.domain
```
$TTL 3D
@ 86400    IN      SOA     my.domain.com. root.my.domain.com. (
                        110127002       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        2H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
                NS    myns1
                NS    myns2
                MX    10    mailhost
_nfsv4idmapdomain    IN    TXT    "my.domain.com"
@        IN    A    192.168.100.113
@        IN    AAAA    ####:####:####:####::1
test1        IN    CNAME    @
test2        IN    CNAME    @
fw          IN    A    192.168.200.1
fw        IN    AAAA    ####:####:####:####::1
host1        IN    A    192.168.200.3
host1        IN    AAAA    ####:####:####:####::3
myns1        IN    A    192.168.200.4
myns1        IN    AAAA    ####:####:####:####::4
mtns2        IN    A    192.168.200.5
mtns2        IN    AAAA    ####:####:####:####::5
mailhost    IN    A    192.168.200.6
mailhost    IN    AAAA    ####:####:####:####::6
```

/etc/bind/db.200.168.192 
```
$TTL 3D
@ 86400         IN      SOA     my.doamin.com. root.my.doamin.com. (
                                110113000       ; Serial
                                28800   ; Refresh
                                7200    ; Retry
                                604800  ; Expire
                                86400)  ; Minimum TTL
                        NS      myns1.my.doamin.com.
;
;       Servers
;
1    PTR    fw.my.doamin.com.
3    PTR    host1.my.doamin.com.
4    PTR    myns1.my.doamin.com.
5    PTR    myns2.my.doamin.com.
6    PTR    mailhost.my.doamin.com.
```

/etc/bind/db.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.# ```

$TTL 3D
@ 86400         IN      SOA     my.domain.com. root.my.domain.com. (
                                110404000       ; Serial
                                28800   ; Refresh
                                7200    ; Retry
                                604800  ; Expire
                                86400)  ; Minimum TTL
                        NS      vaio.thekeepv6.com.
;
;       Servers
;
1.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#   14400 IN      PTR     fw.my.doamin.com.
3.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#   14400 IN      PTR     host1.my.doamin.com.
4.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#   14400 IN      PTR     myns1.my.doamin.com.
5.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#   14400 IN      PTR     myns2.my.doamin.com..
6.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#   14400 IN      PTR     mailhost.my.doamin.com.
```


/etc/bind/named.conf
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind/README.Debian for information on the 
// structure of BIND configuration files in Debian for BIND versions 8.2.1 
// and later, *BEFORE* you customize this configuration file.
//
include "/etc/bind/rndc.key";
include "/etc/bind/named.conf.acl";

controls {
    inet 127.0.0.1 port 953
    allow { 127.0.0.1; } keys { "rndc-key"; };
};

include "/etc/bind/named.conf.options";

// reduce log verbosity on issues outside our control
logging {
    category lame-servers { null; };
};

view "internal" {
    match-clients { internal_nets; };
    recursion yes;
    include "/etc/bind/named.conf.local";
};


view "external" {
    match-clients { !internal_nets; };
    recursion yes;
    include "/etc/bind/named.conf.external";
};

view "default" {
    match-clients { any; };
    zone "." {
        type hint;
        file "/etc/bind/db.root";
    };


    zone "localhost" {
        type master;
        file "/etc/bind/db.localhost";
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
};
```

/etc/bind/named.conf.local 
```
//
// Add local zone definitions here.
zone "my.domain.com" {
        type master;
        file "/etc/bind/db.my.domain";
    allow-transfer { zone_transfers ; };
};

zone "myotherdomain.com" {
        type master;
        file "/etc/bind/db.myotherdomain.com";
    allow-transfer { zone_transfers ; };
};

zone "200.168.192.in-addr.arpa" in {
        type master;
        file "/etc/bind/db.200.168.192";
    allow-transfer { zone_transfers ; };
};

zone "#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.ip6.arpa" {
        type master;
        file "/etc/bind/db.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#";
};
```

/etc/bind/named.conf.external 
```
//
// Add local zone definitions here.

zone "myotherdomain.com" {
        type master;
        file "/etc/bind/db.ext.myotherdomain.com";
    allow-transfer { zone_transfers ; };
};

zone "#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.ip6.arpa" {
        type master;
        file "/etc/bind/db.ext.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#";
};
```

/etc/bind/named.conf.acl 
```
acl "internal_nets" {
    192.168.200.0/24;
    ####:####:####:####::1/96;
};

acl "zone_transfers" {
    192.168.200.###;
    192.168.200.###;
    ####:####:####:####::11;
    192.168.200.###;
    ####:####:####:####::::1;
};
```

---

### Post by varunendra on 2011-06-30
> **Rakeshvijayan said:**
> sorry friends I need to study system administration in ubuntu .I have installed KOHA library management package .koha is open only in browser ,I can call Koha with it ip address 192.168.1.200 .I need to give a name for calling koha .Today I took a machine and Installed koha and trying call with its my name  ....I make testing it on my system with out virtual machine
Dear Rakesh,
Please correct me if I am misinterpreting you. From above post of yours, this is what I could comprehend :-

[LIST=1]
[*]You need to learn 'System Administration in Ubuntu', (clear)
[*]You have installed [KOHA]("http://www.koha.org/") on another computer, (or on a virtual machine on your computer - NOT CLEAR)
[*]You can 'open' KOHA's interface from your machine if you type its IP address in your browser (which should be the IP address of the machine on which KOHA is installed! - Not Clear)
[*]You are unable to open KOHA using 'a name' instead of IP address. (clear)
[*]You are testing this from your computer (while KOHA is on another one), and no virtual machine is involved in this process. (Not Clear)
[/LIST]
Is this correct? If not, please correct me, or simply re-state your question by first:
mentioning clearly what you need to do, or what is your target,
then step-wise details on what have you done so far,
then what is/are your current problems while doing this,
everything involved in this setup (computers, operating system, software, any other relevant details, etc.),

The solution may be very easy, or maybe a complex one, but first we need to understand it properly (which we are unable to so far). Therefore no matter how lengthy your post goes, try to provide each and every detail involved (including background if relevant), and as much clearly as possible.

Here are a couple of links you maybe interested in (although I'm sure you would have already seen them):-
[**Howto: Setup a DNS server with bind**]("http://ubuntuforums.org/showthread.php?t=236093")
[How to Setup a DNS Server in Ubuntu]("http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/")
[Koha - open source library management system]("http://townx.org/blog/elliot/koha-open-source-library-management-system")
[Community Documentation for BIND9Server Howto]("https://help.ubuntu.com/community/BIND9ServerHowto")

---

### Post by Rakeshvijayan on 2011-07-01
> **varunendra said:**
> Dear Rakesh,
Please correct me if I am misinterpreting you. From above post of yours, this is what I could comprehend :-

[LIST=1]
[*]You have installed [KOHA]("http://www.koha.org/") on another computer, (or on a virtual machine on your computer - NOT CLEAR)
[*]You can 'open' KOHA's interface from your machine if you type its IP address in your browser (which should be the IP address of the machine on which KOHA is installed! - Not Clear)
[*]You are testing this from your computer (while KOHA is on another one), and no virtual machine is involved in this process. (Not Clear)
[/LIST]

Fisrst of all I wish to thank you.finally my problem solved with question....

I DROP MY TESTING ON VIRTUAL MACHINE ... 

1. apache installed on **"lkjkkl"** named system which IP is 192.168.1.200 .koha running on this system 

2. I can call koha using the  ipaddress  192.168.1.200:8000  on networked system 

3. I am trying to install dns server on another system which name is **"talks"**

finally  I reach my destination .....and I have a question  .(please reffer on the image )

now I can call web page by [http://www.mctlib.com:8001/](http://www.mctlib.com:8001/)

[U]I want call this web page with out the specified port ?????
[/U]
I appreciating  all users on this forum and varunendra for great help ........

---

### Post by Rakeshvijayan on 2011-07-11
hello [hawkmage] I have doubt in below statements will you explane about  this "  [view "internal" ,  view "external" ,  view "external" ]" 
 
 and I need to know how can I log all dns  system activites
 



> **hawkmage said:**
> 




 /etc/bind/named.conf
 [CODE]// This is the primary configuration file for the BIND DNS server named.
 //
 // Please read /usr/share/doc/bind/README.Debian for information on the 
 // structure of BIND configuration files in Debian for BIND versions 8.2.1 
 // and later, *BEFORE* you customize this configuration file.
 //
 include "/etc/bind/rndc.key";
 include "/etc/bind/named.conf.acl";
 
 controls {
     inet 127.0.0.1 port 953
     allow { 127.0.0.1; } keys { "rndc-key"; };
 };
 
 include "/etc/bind/named.conf.options";
 
 // reduce log verbosity on issues outside our control
 logging {
     category lame-servers { null; };
 };
 
 view "internal" {                  "
     match-clients { internal_nets; };
     recursion yes;
     include "/etc/bind/named.conf.local";
 };
 
 
 view "external" {
     match-clients { !internal_nets; };
     recursion yes;
     include "/etc/bind/named.conf.external";
 };
 
 view "default" {
     match-clients { any; };
     zone "." {
         type hint;
         file "/etc/bind/db.root";
     };
 
 
     zone "localhost" {
         type master;
         file "/etc/bind/db.localhost";
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
 };  



  

[/QUOTE]

---

### Post by Rakeshvijayan on 2011-07-11
Frends with your support I can Install dns .I need to know how can I log all dns entries

---

### Post by SeijiSensei on 2011-07-11
> **Rakeshvijayan said:**
> Frends with your support I can Install dns .I need to know how can I log all dns entries

[http://www.zytrax.com/books/dns/ch7/logging.html](http://www.zytrax.com/books/dns/ch7/logging.html)

---

### Post by Rakeshvijayan on 2011-07-11
Thanks am going to check this site and test it on my server

---

### Post by Rakeshvijayan on 2012-12-14
what is external and internal network? why external entries have second name used

---

### Post by Rakeshvijayan on 2012-12-14
> **hawkmage said:**
> OK, Here you go here is a sample of my DNS config.

/etc/bind/db.my.domain
```
$TTL 3D
@ 86400    IN      SOA     my.domain.com. root.my.domain.com. (
                        110127002       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        2H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
                NS    myns1
                NS    myns2
                MX    10    mailhost
_nfsv4idmapdomain    IN    TXT    "my.domain.com"
@        IN    A    192.168.100.113
@        IN    AAAA    ####:####:####:####::1
test1        IN    CNAME    @
test2        IN    CNAME    @
fw          IN    A    192.168.200.1
fw        IN    AAAA    ####:####:####:####::1
host1        IN    A    192.168.200.3
host1        IN    AAAA    ####:####:####:####::3
myns1        IN    A    192.168.200.4
myns1        IN    AAAA    ####:####:####:####::4
mtns2        IN    A    192.168.200.5
mtns2        IN    AAAA    ####:####:####:####::5
mailhost    IN    A    192.168.200.6
mailhost    IN    AAAA    ####:####:####:####::6
```/etc/bind/db.200.168.192 
```
$TTL 3D
@ 86400         IN      SOA     my.doamin.com. root.my.doamin.com. (
                                110113000       ; Serial
                                28800   ; Refresh
                                7200    ; Retry
                                604800  ; Expire
                                86400)  ; Minimum TTL
                        NS      myns1.my.doamin.com.
;
;       Servers
;
1    PTR    fw.my.doamin.com.
3    PTR    host1.my.doamin.com.
4    PTR    myns1.my.doamin.com.
5    PTR    myns2.my.doamin.com.
6    PTR    mailhost.my.doamin.com.
```/etc/bind/db.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.# ```

$TTL 3D
@ 86400         IN      SOA     my.domain.com. root.my.domain.com. (
                                110404000       ; Serial
                                28800   ; Refresh
                                7200    ; Retry
                                604800  ; Expire
                                86400)  ; Minimum TTL
                        NS      vaio.thekeepv6.com.
;
;       Servers
;
1.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#   14400 IN      PTR     fw.my.doamin.com.
3.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#   14400 IN      PTR     host1.my.doamin.com.
4.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#   14400 IN      PTR     myns1.my.doamin.com.
5.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#   14400 IN      PTR     myns2.my.doamin.com..
6.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#   14400 IN      PTR     mailhost.my.doamin.com.
```/etc/bind/named.conf
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind/README.Debian for information on the 
// structure of BIND configuration files in Debian for BIND versions 8.2.1 
// and later, *BEFORE* you customize this configuration file.
//
include "/etc/bind/rndc.key";
include "/etc/bind/named.conf.acl";

controls {
    inet 127.0.0.1 port 953
    allow { 127.0.0.1; } keys { "rndc-key"; };
};

include "/etc/bind/named.conf.options";

// reduce log verbosity on issues outside our control
logging {
    category lame-servers { null; };
};

view "internal" {
    match-clients { internal_nets; };
    recursion yes;
    include "/etc/bind/named.conf.local";
};


view "external" {
    match-clients { !internal_nets; };
    recursion yes;
    include "/etc/bind/named.conf.external";
};

view "default" {
    match-clients { any; };
    zone "." {
        type hint;
        file "/etc/bind/db.root";
    };


    zone "localhost" {
        type master;
        file "/etc/bind/db.localhost";
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
};
```/etc/bind/named.conf.local 
```
//
// Add local zone definitions here.
zone "my.domain.com" {
        type master;
        file "/etc/bind/db.my.domain";
    allow-transfer { zone_transfers ; };
};

zone "myotherdomain.com" {
        type master;
        file "/etc/bind/db.myotherdomain.com";
    allow-transfer { zone_transfers ; };
};

zone "200.168.192.in-addr.arpa" in {
        type master;
        file "/etc/bind/db.200.168.192";
    allow-transfer { zone_transfers ; };
};

zone "#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.ip6.arpa" {
        type master;
        file "/etc/bind/db.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#";
};
```/etc/bind/named.conf.external 
```
//
// Add local zone definitions here.

zone "myotherdomain.com" {
        type master;
        file "/etc/bind/db.ext.myotherdomain.com";
    allow-transfer { zone_transfers ; };
};

zone "#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.ip6.arpa" {
        type master;
        file "/etc/bind/db.ext.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#";
};
```/etc/bind/named.conf.acl 
```
acl "internal_nets" {
    192.168.200.0/24;
    ####:####:####:####::1/96;
};

acl "zone_transfers" {
    192.168.200.###;
    192.168.200.###;
    ####:####:####:####::11;
    192.168.200.###;
    ####:####:####:####::::1;
};
```

> // // Add local zone definitions here.  zone "myotherdomain.com" {         type master;         file "/etc/bind/db.ext.myotherdomain.com";     allow-transfer { zone_transfers ; }; };  zone "#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.ip6.arpa" {         type master;         file "/etc/bind/db.ext.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#.#"; };

how db.ext.myotherdomain.com entries will come .Is this for second site ........?

---

