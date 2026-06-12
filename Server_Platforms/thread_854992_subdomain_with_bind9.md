---
title: "subdomain with bind9"
date: 2008-07-10
forum: Server Platforms
---

### Post by angelochen168 on 2008-07-10
Hi,

I have a server which has bind9 installed, it runs ubuntu 9. I'd like to add some sub domains, example:

domain is: myexample.com
and I like to have a subdomain which points to myexample.com too like: test.myexample.com,
possible? thanks.

Angelo

---

### Post by qrwe on 2008-07-10
> **angelochen168 said:**
> 

it runs ubuntu 9.



Huh?

It's both possible and easy. You'll have to configure named.conf, the best way is to read the configuration specifications by running 'man named.conf', it will tell you all you need to know. Good luck!

---

### Post by angelochen168 on 2008-07-10
thanks, i did as you told, but it's really complicated, any hints to get started quickly? i just want to add a subdomain to my domain.

---

### Post by qrwe on 2008-07-10
> **angelochen168 said:**
> thanks, i did as you told, but it's really complicated, any hints to get started quickly? i just want to add a subdomain to my domain.

I'll try. Supposing you are on net '192.168.1.0/24'. Your own server has '192.168.1.50'.

Edit named.conf:
```

// GENERAL OPTIONS
options {
        directory "/etc/bind/zones"; // Or where the zones are living
        datasize 20M;
        notify yes;
        recursion no;
        zone-statistics yes;
        statistics-file "/var/stats/named.stats";
        allow-transfer { 192.168.1.100; }; // A made up slave server, if there is any. All changes will also happen there. Remove line if you have only one server.
        listen-on { 192.168.1.50; 127.0.0.1; };
        allow-query { any; };
};

//MASTER ZONES
zone "example.com" {
        type master;
        file "example_com.zone";
};

```

Then you need to create a zone file for this domain, where you provide host names (sub domains).
Create a file /etc/bind/zones/example_com.zone and edit it:
```

; $Id:
;       Authoritative data for example.com
;
$TTL 43200
@               IN      SOA     ns.example.com. hostmaster.example.com. (
                                2008071000; Serial, ALWAYS update with date of today + eventual serial number when new changes are made. You have been warned.
                                10800   ; Refresh 3 hours
                                3600    ; Retry   1 hour
                                604800  ; Expire  1 week
                                86400 ) ; Minimum 24 hours
;
;    Nameservers
;
                IN      NS              ns1.example.com.
                IN      NS              ns2.example.com.
                IN      MX      10      smtp.example.com.
;
www             IN      A               192.168.1.200; Assumed web server

```

There may be some other configurations to be made, but with this you should now have a published domain with subdomain.

And one more thing, named must be restarted (or reloaded) after every change you make.
```

/etc/init.d/named restart
# or
/etc/init.d/named reload

```

---

### Post by dgohn on 2010-03-29
I am running Bind9 on Ubuntu Server 8.04.  Currently I have it set up and working and mydomain.com points to my ip address of my server but to the /var/www like it should.  How would I go about setting up a subdomain such as userx.mydomain.com and have it point to /home/userx/public_html/ ?

Thanks in advance for any help!

---

### Post by dgohn on 2010-03-29
*bump*  Really need to get this working so if anyone knows how to do this please help.  I am at a loss.

---

### Post by roachmmflhyr on 2010-07-02
I'm assuming that you're using Apache web server.  If so, check out this link about configuring Apache and vhosts: [https://help.ubuntu.com/10.04/serverguide/C/httpd.html]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html")  Pay special attention to sites-available and sites-enabled directories.  If you have any question let me know.

---

