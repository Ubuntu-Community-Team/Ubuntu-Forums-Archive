---
title: "apache and dns"
date: 2012-12-07
forum: Server Platforms
---

### Post by Rakeshvijayan on 2012-12-07
Hi friends 

I am in new trouble.I have library site woking with m.com site is also available in that name .dsn and apache are configured  different systems  .My question is I want establish a new site with name c.com what should I do I am using 12.04  on both systems .c.com is only available on apache system.Both m.com and c.com are working on apache configured system ...m.com is my dns name and I pointed it  to apache server .
for c.com do I need to configure in dns system ?

Thanks Hope I will get a great answer from you all my friends

---

### Post by TheFu on 2012-12-07
> **Rakeshvijayan said:**
> Hi friends 

I am in new trouble.I have library site woking with m.com site is also available in that name .dsn and apache are configured  different systems  .My question is I want establish a new site with name c.com what should I do I am using 12.04  on both systems .c.com is only available on apache system.Both m.com and c.com are working on apache configured system ...m.com is my dns name and I pointed it  to apache server .
for c.com do I need to configure in dns system ?

Thanks Hope I will get a great answer from you all my friends

I'm having a little trouble understanding the situation.  This is what I think you have explained.

You have multiple servers on different IP addresses.
* DNS is on 1
* Apache is on another.
* m.com points to the apache server IP
* you want to have c.com also point to the apache server IP
* you have apache working with virtual servers using the VirtualHost setting.

So, if my understanding is correct, then you just need to update the DNS records to point c.com to the IP.  DNS records have A and CNAME records. It is usual that only 1 A record points Servername1 --> IP_address, then CNAME records are used to point Servername2 --> Servername1.

Since you did not say which DNS is used, I can only say that you'll need to make the changes to the DNS. If you use a hosted DNS provider, this should be easy though a panel.  

Apache needs for the DNS records to point to the IP address you want the end users to access, but Apache does not **need** for this to be there unless you only use named servers and share the IP address with other websites on the same port.

O'Reilly has a DNS book that explains everything. It is either the best bok ever written on DNS or a complete waste of money. I know that I bought it in '95 and only needed to read 1 chapter to sort out the issues I was experiencing.

There are hundreds of different ways to setup name resolution and to host multiple websites on the same IP address that will work.

If I did not get the setup correct, please try to correct it so that I or someone else might help.  Also a scanned/photographed drawing might be the easiest way to explain a complex setup.

---

### Post by SeijiSensei on 2012-12-07
You'll also need to create another VirtualHost configuration for the new domain.  Read the [Ubuntu Server Guide](https://help.ubuntu.com/12.04/serverguide/) for details.

If both domains will serve the identical content, you can add a "[ServerAlias]("http://httpd.apache.org/docs/2.2/mod/core.html#serveralias")" declaration to the definition of the existing virtual host.

---

### Post by Rakeshvijayan on 2012-12-09
> **TheFu said:**
> I'm having a little trouble understanding the situation.  This is what I think you have explained.

You have multiple servers on different IP addresses.
* DNS is on 1
* Apache is on another.
* m.com points to the apache server IP
* you want to have c.com also point to the apache server IP
* you have apache working with virtual servers using the VirtualHost setting.

So, if my understanding is correct, then you just need to update the DNS  records to point c.com to the IP.  DNS records have A and CNAME  records. It is usual that only 1 A record points Servername1 -->  IP_address, then CNAME records are used to point Servername2 -->  Servername1.

Yes you are correct my friend [TheFu]("http://ubuntuforums.org/member.php?u=1037685"),But I am using internal dns that i setup for my firm 
 this is my db.m.com file 
> 
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.m.com. root.m.com. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.m.com.
@       IN      A       192.168.1.1
@       IN      AAAA    ::1
ns      IN      A       192.168.1.1
ns1     IN      A       192.168.1.2
ns8     IN      A       192.168.1.8
rivaus  IN      A       192.168.1.77
www     IN      CNAME   ns1

do I need to create same for c.com like m.com, 192.168.1.1 is the DNS Server and apache uses 192.168.1.2 ip address ,will you explain  how the c.com will work for me I am not using paid service .This is only for my lan that why I give my IP address here 

Thanks

---

### Post by sandyd on 2012-12-10
> **Rakeshvijayan said:**
> Yes you are correct my friend [TheFu]("http://ubuntuforums.org/member.php?u=1037685"),But I am using internal dns that i setup for my firm 
 this is my db.m.com file 

**do I need to create same for c.com like m.com**, 192.168.1.1 is the DNS Server and apache uses 192.168.1.2 ip address ,will you explain  how the c.com will work for me I am not using paid service .This is only for my lan that why I give my IP address here 

Thanks
yes, and any other domain name you might want to add

---

### Post by Rakeshvijayan on 2012-12-11
> **sandyd said:**
> yes, and any other domain name you might want to add

I  use only bind files named.conf.options, named.conf.local,db.m.com ,db.c.com,db.192 is it enough for second site name in dns 
MY named.conf.options configuration 
> options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
        192.168.1.98;
         };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


MY name named.conf.local configuration 
> 
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "m.com" {
        type master;
        file "/etc/bind/db.m.com";
};

zone "c.com" {
        type master;
        file "/etc/bind/db.c.com";
};


zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192";
};


MY db.m.com configuration 
> ;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     m.com. root.m.com. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      rivaus.m.com.
@       IN      A       192.168.1.77
@       IN      AAAA    ::1
rivaus  IN      A       192.168.1.77
aswin   IN      A       192.168.1.89
lib1    IN      A       192.168.1.59
www     IN      CNAME   rivaus
My db.c.com configuration 
> ;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     c.com. root.c.com. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      rivaus.c.com.
@       IN      A       192.168.1.77
@       IN      AAAA    ::1
rivaus  IN      A       192.168.1.77
aswin   IN      A       192.168.1.89
lib1    IN      A       192.168.1.59
www     IN      CNAME   rivaus
my db.192 reverse look up configuration 
> 
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     rivaus.m.com. root.m.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      rivaus.
77      IN      PTR     ns.m.com.
89      IN      PTR     aswin.m.com.
59      IN      PTR     lib1.m.com.
_now I am using bind and apache in same meachine for the testing purpose ........._......

Here is the doubt arise .how I make reverse look up for c.com .if any body know about this problem please share your valuable information .it just only need in lan setup not out side world 

Thanks for you kind help

---

### Post by Rakeshvijayan on 2012-12-12
Here is the doubt arise .how I make reverse look up for c.com .if any  body know about this problem please share your valuable information .it  just only need in lan setup not out side world

---

### Post by Rakeshvijayan on 2012-12-12
Here is the doubt arise .how I make reverse look up for c.com .if any  body know about this problem please share your valuable information .it  just only need in lan setup not out side world

---

### Post by TheFu on 2012-12-12
O'Reilly has a few DNS books that explain everything.
[http://www.oreillynet.com/pub/a/network/excerpt/dnsbindcook_ch05/index.html](http://www.oreillynet.com/pub/a/network/excerpt/dnsbindcook_ch05/index.html)
and
[http://shop.oreilly.com/product/9780596100575.do](http://shop.oreilly.com/product/9780596100575.do)

---

### Post by Rakeshvijayan on 2012-12-14
Finally I got the answer.my m.com and c.com works fine ,but some doubt still remain .

1) why we use external ,internal and acl use in bind ?

2)client system configured in bind can only access the m.com and c.com ,is it have any possible way to get  m.com and c.com and internet in my normal pc.I configured dns and apache in lan 

I can't under stand technical word in document .will any body give your own wards

---

