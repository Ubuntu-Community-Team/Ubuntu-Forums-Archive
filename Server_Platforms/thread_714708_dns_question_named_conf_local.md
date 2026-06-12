---
title: "dns question named conf local"
date: 2008-03-04
forum: Server Platforms
---

### Post by paulus4605 on 2008-03-04
Dear 
I followed the tutorial found here at the forum 
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
however when I use the modifiied named.conf.local I get a failed when starting bind 
when using the non modified version I don't have any problem and everything seems to work correctly.
what am I doing wrong here 
this is the named conf local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

```
this is my version 

```

//
// Do any local configuration here
//--------Begin carrebeanpirates-----------

zone "carrebeanpirates.homedns.org" {
	type master;
	file "/etc/bind/zones/carrebeanpirates.homedns.org.db";
	};

//the next zone is for the reverse DNS entry.

zone "1.168.192.in-addr.arpa" {
	type master;
	file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
	};

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

```

this is my db

```

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
carrebeanpirates.homedns.org.      IN      SOA     ns1.carrebeanpirates.homedns.org. admin.carrebeanpirates.homedns.org. (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = carrebeanpirates.homedns.org
// mta = mail server name
// example.com = domain name
carrebeanpirates.homedns.org.      IN      NS              ns1.carrebeanpirates.homedns.org.
carrebeanpirates.homedns.org.      IN      MX     10       carrebeanpirates.homedns.org.

// Replace the IP address with the right IP addresses.
www              IN      A       192.168.1.1
mta              IN      A       192.168.1.1
ns1              IN      A       192.168.1.1


```
this is the reverse dns
```

//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA ns1.carrebeanpirates.homedns.org. admin.carrebeanpirates.homedns.org. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.carrebeanpirates.homedns.org.
10                    IN    PTR    carrebeanpirates.homedns.org


```

thanks for your help 
Paul

---

### Post by Uaine on 2008-03-04
I was following this tutorial just last night and got it working fine.  I think you may have to replace "ns1" in those conf files with the name of your server (unless your server is named "ns1")

---

### Post by paulus4605 on 2008-03-04
so if the servername is server I should put something like 
server.carrebeanpirates.homedns.org.?

---

### Post by Uaine on 2008-03-04
that's correct.  if your server was named "Server", you would replace every instance of "ns1" with "server".

---

