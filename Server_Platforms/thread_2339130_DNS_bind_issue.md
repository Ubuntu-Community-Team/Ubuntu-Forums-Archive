---
title: "DNS bind issue"
date: 2016-10-05
forum: Server Platforms
---

### Post by subfire91 on 2016-10-05
Hi guys,

i need ur help in a matter i cannot find solution for. i have configured a dns server with 2 views one for internal and one for external.

when i change the serial on the internal zone i get a notify from master to slave with the new serial.

when i change the serial on the external view the zone on the slave is not updated.

 i tried everything and yet to find out what is going on.

the configuration is identical..

any ideas ?

Thank you

---

### Post by subfire91 on 2016-10-05
no one ???

---

### Post by wildmanne39 on 2016-10-05
Please wait at least 12 hours before bumping your thread, we are all volunteers that live across the globe so it is likely that the person that might have the answer has not been on line to see it yet.
Thanks

---

### Post by darkod on 2016-10-05
Please post more info of the zone files for example, because it will help understand what you did. For example I don't understand what you mean by "internal" and "external" zone. A DNS zone is a zone, full stop. There are no internal and external ones... Whether the DNS server is serving client on local (internal) network or public is another thing, but the zone is still only a zone...

Did you mean forward and reverse zone maybe?

---

### Post by subfire91 on 2016-10-06
options file of the primary

```

options {
     
	directory "/var/named";

	listen-on port 53 { 127.0.0.1; master; };

   	version "None of your business"; 
	server-id "None of your business";
	hostname "None of your business";
    blackhole {badips;};
	auth-nxdomain no;
		
	transfers-in 3;
	transfers-per-ns 3;
	transfers-out 9;
	
	recursion yes;
	allow-recursion {127.0.0.1; internals;};
		
	allow-query {any;};

	allow-transfer {127.0.0.1; slave;};
			
	max-transfer-time-in 60;

	rate-limit {
	
		responses-per-second 3;
		window 5;
		log-only yes;
		exempt-clients {mail-ad; slave; };
		
	};
};


```

domain views of the primary

```

view domain.com-external {
	
	match-clients {external;};
				
	zone "domain.com." IN {
		type master;
		file "/etc/named/db.domain.com.external.hosts";
		notify yes;
		also-notify {slave;};
	};
	
};

view domain.com-internal {

	match-clients {internals;};
				
	zone "domain.com." IN {
		type master;
		file "/etc/named/db.domain.com.internal.hosts";
		notify yes;
	};

	zone "." IN {
		type hint;
		file "/etc/named/db.root";
		
	};

	zone "localhost" IN {
		type master;
		file "/etc/named/db.local";
			
	};

	zone "127.in-addr.arpa" IN {
		type master;
		file "/etc/named/db.127";
		
	};

	zone "0.in-addr.arpa" IN {
		type master;
		file "/etc/named/db.0";
		
	};

	zone "255.in-addr.arpa" IN {
		type master;
		file "/etc/named/db.255";
			
	};

	zone "10.in-addr.arpa"      { type master; file "/etc/named/db.empty"; };
	zone "16.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "17.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "18.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "19.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "20.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "21.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "22.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "23.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "24.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "25.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "26.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "27.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "28.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "29.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "30.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "31.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "168.192.in-addr.arpa" { type master; file "/etc/named/db.empty"; };

	
};


```

options file on slave

```

options {
     
	directory "/var/named";

	listen-on port 53 { 127.0.0.1; slave; };

   	version "None of your business"; 
	server-id "None of your business";
	hostname "None of your business";
  	blackhole {badips;};
	auth-nxdomain no;
		
	transfers-in 3;
	transfers-per-ns 3;
	transfers-out 9;
	
	recursion yes;
	allow-recursion {127.0.0.1; internals;};
		
	allow-transfer {127.0.0.1; master;};
			
	max-transfer-time-in 60;
	
	allow-query {any;};

	rate-limit {
	
		responses-per-second 3;
		window 5;
		log-only yes;
		exempt-clients {mail-ad; master; };
		
	};
};

```

doamin view of the slave

```

view domain.com-external {
	
	match-clients {external;};
				
	zone "domain.com." IN {
		type slave;
		masters {master;};
		file "slaves/db.domain.com.external.hosts";
		notify yes;
	};
	
};

view domain.com-internal {

	match-clients {internals;};
				
	zone "domain.com." IN {
		type slave;
		masters {masters;};
		file "slaves/db.domain.com.internal.hosts";
		notify yes;
				
	};

	zone "." IN {
		type hint;
		file "/etc/named/db.root";
		
	};

	zone "localhost" IN {
		type master;
		file "/etc/named/db.local";
			
	};

	zone "127.in-addr.arpa" IN {
		type master;
		file "/etc/named/db.127";
		
	};

	zone "0.in-addr.arpa" IN {
		type master;
		file "/etc/named/db.0";
		
	};

	zone "255.in-addr.arpa" IN {
		type master;
		file "/etc/named/db.255";
			
	};

	zone "10.in-addr.arpa"      { type master; file "/etc/named/db.empty"; };
	zone "16.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "17.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "18.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "19.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "20.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "21.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "22.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "23.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "24.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "25.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "26.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "27.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "28.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "29.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "30.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "31.172.in-addr.arpa"  { type master; file "/etc/named/db.empty"; };
	zone "168.192.in-addr.arpa" { type master; file "/etc/named/db.empty"; };

	
};


```
the problem is that when i do rndc reload on the primary after i increase the serial of both internal and external hosts file i get serial transfers only for the internal view. Please let me know if u want to post something else

---

### Post by wildmanne39 on 2016-10-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by darkod on 2016-10-06
Can you post the content of /etc/bind/named.conf.local from both primary and secondary nameserver?

---

### Post by subfire91 on 2016-10-06
> **darkod said:**
> Can you post the content of /etc/bind/named.conf.local from both primary and secondary nameserver?

there is no such file.

zone information is in the views i posted

---

### Post by darkod on 2016-10-06
Hmmm, that is one of the basic bind files. Is your configuration similar to this: [https://help.ubuntu.com/14.04/serverguide/dns-configuration.html?](https://help.ubuntu.com/14.04/serverguide/dns-configuration.html?)

That is what bind config should look like AFAIK. If you have other type of dns config, then maybe there lies the problem.

---

### Post by subfire91 on 2016-10-06
> **darkod said:**
> Hmmm, that is one of the basic bind files. Is your configuration similar to this: [https://help.ubuntu.com/14.04/serverguide/dns-configuration.html?](https://help.ubuntu.com/14.04/serverguide/dns-configuration.html?)

That is what bind config should look like AFAIK. If you have other type of dns config, then maybe there lies the problem.

yeah thats the configuration i have..very similar. because im using views i renamed instead of named.conf.loacl to views..... Naming isnt an issue if you include the file in named.conf

---

### Post by darkod on 2016-10-06
Sorry, I can't help you with this type of setup... And since it doesn't work for you as expected, I don't understand why not trying the "simplified" version. Like for example, in your view you have two declarions of zone domain.com pointing to two different db files. Is that allowed at all?

I have done a few setups like in the Ubuntu help pages, and it works easily...

---

### Post by subfire91 on 2016-10-07
> **darkod said:**
> Sorry, I can't help you with this type of setup... And since it doesn't work for you as expected, I don't understand why not trying the "simplified" version. Like for example, in your view you have two declarions of zone domain.com pointing to two different db files. Is that allowed at all?

I have done a few setups like in the Ubuntu help pages, and it works easily...

the one view is for the internal ip addresses. internal users should get dns records with their internal ip addresses
the other view is for external ones. internet users should get dns records of the external ip addresses

---

### Post by darkod on 2016-10-07
I found this, does it help?
[https://kb.isc.org/article/AA-00851/0/Understanding-views-in-BIND-9-by-example.html](https://kb.isc.org/article/AA-00851/0/Understanding-views-in-BIND-9-by-example.html)

According to that you have few small differencies.
1. On the master you also use the 'notify' parameter they don't. They only use 'also-notify'. Have you tried it like that?
2. You don't have the also-notify on the master for the internal zone. Why?

---

