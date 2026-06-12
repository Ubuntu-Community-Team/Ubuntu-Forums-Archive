---
title: "bind reverse zone issue"
date: 2011-06-19
forum: Server Platforms
---

### Post by vahidreza.y on 2011-06-19
H,

i have bind installed and registered my domain name servers in my registrar and is pointing to my vps server that running bind9 , the forward zone works great and apache,ftp server and mail server are working great.

i need to make my reverse zone works to pass gmail,yahoo,msn ptr record check !
i used some tutorials on this forum and elsewhere to make my forward zone , the only thing that was mysterious is that all tutorials use class c ip addressees and it seems they use their reverse zone only for local purposes !

i have a class a ip assigned and i need reverse dns query for it !

here is my configuration file and zone files :

```
named.conf.local file :
===========================
zone "example.com" {
        type master;
        file "/etc/bind/zones/example.com.db";
        };

zone "250.140.210.69.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.250.140.210.69.in-addr.arpa";
};


/etc/bind/zones/example.com.db file :
=======================
example.com.      IN      SOA     ns1.example.com. admin.example.com. (
                      2006081401
                      28800
                      3600
                      604800
                      38400
 )
example.com.      IN      NS              ns1.example.com.
example.com.      IN      MX     10       mail.example.com.

         IN     A      69.210.140.250  
www           IN      A      69.210.140.250
mail             IN      A     69.210.140.250
ns1         IN      A     69.210.140.250


/etc/bind/zones/rev.250.140.210.69.in-addr.arpa file :
=======================

@ IN SOA ns1.example.com. admin.example.com. (
                        2006081401
                        28800 
                        604800
                        604800
                        86400 
)

                    IN    NS     ns1.example.com.
                    IN    PTR    example.com.
ns1           IN    A       69.210.140.250
```if there is something wrong or you have any suggestions please let me know .

---

### Post by vahidreza.y on 2011-06-20
i am really stuck in this issue , dnslookup works when i ssh to vps but it fails in the internet! please let me know if my syntax is correct for zone files and let me know what you think is wrong here !

---

### Post by SeijiSensei on 2011-06-20
You have no control over reverse resolution; only your ISP can handle that.  If you have a business-class connection with a static IP, your ISP will probably be willing to set up reverse resolution for your address.  Some providers offer [RFC2317 delegation]("http://www.faqs.org/rfcs/rfc2317.html"), but typically only to customers who have been granted an IP subnet.  

You need to talk to your ISP about this.

---

