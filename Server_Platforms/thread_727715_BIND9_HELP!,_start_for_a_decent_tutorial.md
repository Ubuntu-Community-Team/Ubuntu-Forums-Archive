---
title: "BIND9 HELP!, start for a decent tutorial"
date: 2008-03-18
forum: Server Platforms
---

### Post by Tavorisch on 2008-03-18
Okay, So I've followed these two guides, [http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml](http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml)
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)
One thing that frusterates me is I like ubuntugeek but I cannot for the life of me figure out how to search it. So I'm going to leave my server how it is. My current network setup is cableone, isp, motorola modem plugged into a switch. port forwarding 80, 22, 53 to 192.168.0.4, I'll go over my network setup in a code to make more sense
```

Hostname, in both hosts, and hostname file:
**vpsserver**
IP Address etc.
**23.116.4.70** (outside)
**192.168.0.4** (local)
[B]23.115.1.49
23.115.1.33 [/B]
the two DNs for my ISP, 
**vpsserver.vpssolutions.com** is our name server with AIT domains, instead of the gneric ns1 or ns0
**ServerName www.vpssolutions.com** is right at the top of my /etc/apache2/apache2.conf

```
I know there has to be someone out there who has a very very simlar setup running and working. okay here it is, my outside ip address is 23.116.4.70, the local is 192.168.0.4 set to static right now,
here is my /etc/bind/named.conf.local
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "vpssolutions.com" {
type master;
file "/etc/bind/zones/vpsserver.vpssolutions.com.db";
};

zone "70.4.116.23.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.70.4.116.23.in-addr.arpa";
};

```
as far as I'm concerned looks good!
next we have. my /etc/bind/named.conf.options
```

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
                23.116.4.70;
          };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```
again, as far as I know, good to me, we won't really be needing forwarders for now, and the basic dns isn't working. next we have.
my /etc/bind/zones/vpsserver.vpssolutions.com.db
```

// replace example.com with your domain name. do not forget the . after the dom$
// Also, replace ns1 with the name of your DNS server
vpssolutions.com. IN SOA vpsserver.vpssolutions.com. admin.vpssolutions.com. (

2006081401
28800
3600
604800
38400 )

vpssolutions.com. IN NS vpsserver.vpssolutions.com.
vpssolutions.com. IN NS www.vpssolutions.com

IN A 23.116.4.70
mail.vpssolutions.com. IN MX 10 mail.vpssolutions.com.
vpssolutions.com. IN MX 10 mail.vpssolutions.com.

www IN A 23.116.4.70
mail IN A 23.116.4.70
vpsserver IN A 23.116.4.70


```
now my /etc/bind/zones/rev.70.4.116.23.in-addr.arpa
```

@ IN SOA vpssolutions.com. admin.vpssolutions.com. (
2006081401;
28800;
604800;
604800;
86400 );

IN NS vpsserver.vpssolutions.com.
70 IN PTR vpssolutions.com.

```
last but not least my /etc/resolv.conf
```

search vpssolutions.com
nameserver 23.115.1.49
nameserver 23.115.1.33 **those two keep resetting to my ISP dns server which i don't think matters because i can hit vpsserver.vpssolutions.com from the outside, just not www. mail. or just plain vpssolutions.com**

```

Like I said, I almost got it, i did something right because  I KNOW it works from the outside,(but only the FQDN, [http://vpsserver.vpssolutions.com](http://vpsserver.vpssolutions.com) will hit my default apache2 directory!! it won't for you cause i've modified it the dns name and ip for security purposes for now =)
if PM with help i'll go through the actual configs, but like I said, it works from the outside but only with the FQDN (vpsserver.vpssolutions.com)  any help would be SOO much appreciated, and i will post a BASIC, tutorial for actual internet DNS for people in the same situation as me.

---

### Post by Tavorisch on 2008-03-18
bleh I just messed around with eveyrthing and got right back to being able to hit vpsserver.vpssolutions.com from the outside, I know am certain it has something to do with my resolv.conf, I've had all of this working like 2 days ago and I had to reinstall. anyway the only way ptxserver.ptxsolutions works is if I have both of my ISP's DNS in my resolv.conf 23.115.1.50 and 23.115.1.33  must have something wrong, its really lame all these guides are for local DNS servers, if anyone knows of a guide they could justl link me too that would be awesome too! thanks for any help in advance, and no worries will definitely contribute back to the community!!

---

### Post by Cavalierdevache on 2008-03-18
The first thing you need to do is go to your registrar and change your authoritve dns servers from ns1/ns2.dns-diy.net to what you are using in your zone file. The SOA should probably not include the machine name, just the domain name you have registered. You can ignore using a reverse zone unless you can talk your isp into forwarding the reverse zones to you, otherwise it will do nothing. More then likely the reason the forwarders keep changing in resolv.conf is the use of DHCP, setup your interface with a static ip and what you type iinto resolv.conf should stay put.

The tutorials in the DNS section at the dev shed are good for getings things going. [http://forums.devshed.com/dns-36](http://forums.devshed.com/dns-36)

---

### Post by Tavorisch on 2008-03-18
alright hey thanks, but the machine name is vpsserver, as well as our registrar, is vpsserver.vpssolutions.com  in stead of ns1.vpssolutions.com

---

