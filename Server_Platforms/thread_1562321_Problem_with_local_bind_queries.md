---
title: "Problem with local bind queries"
date: 2010-08-27
forum: Server Platforms
---

### Post by grimm08 on 2010-08-27
I just set up a bind dns server, I am able to get queries for internet site.  However I am unable to get any quires for my local network, not sure what is wrong with my config files.  See my config files.

config.local.


//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# This is the zone definition. replace example.com with your domain name
zone "oberlander.local" {
        type master;
        file "/etc/bind/zones/oberlander.local.db";
        };

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "0.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};

oberlander.local.db

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
oberlander.local.       IN      SOA     homeknowledge.oberlander.local. admin.oberlander.local. (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
homeknowledge = DNS Server name
// mta = mail server name
oberlander.local = domain name
oberlander.local.      IN      NS              homeknowledge.oberlander.local.
//example.com.      IN      MX     10       mta.example.com.


// Replace the IP address with the right IP addresses.


localhost        IN      A       127.0.0.1
homeknowledge    IN      A       192.168.1.5
matthewpc-001    IN      A       192.168.1.6
gateway          IN      A       192.168.1.1
homeprinter      IN      A       192.168.1.4


rev.0.1.168.192.in-addr.arpa

//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA homeknowledge.oberlander.local. admin.oberlander.local. (
                        2006081401;
                        28800;
                        604800;
                        604800;
                        86400
)

                     IN    NS     homeknowledge.oberlander.local.
                     IN    PTR    oberlander.local

                     IN    PTR    homeknowledge.oberlander.local.
                     IN    PTR    matthewpc-001.oberlander.local.
                     IN    PTR    gateway.oberlander.local.
                     IN    PTR    homeprinter.oberlander.local.

---

