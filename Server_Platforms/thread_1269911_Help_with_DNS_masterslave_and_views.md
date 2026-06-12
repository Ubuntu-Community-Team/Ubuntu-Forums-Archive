---
title: "Help with DNS master/slave and views"
date: 2009-09-18
forum: Server Platforms
---

### Post by Moso on 2009-09-18
Hi!

I almost get this to work...  Need a little help here.  :)

**dns-01.example.com => 192.168.1.201**

/etc/bind/named.conf.local
```
acl internals {
	127.0.0.0/8;
	192.168.1.0/24;
};

view "internal" {
	match-clients { internals; };

	zone "example.com" {
		type master;
		file "/etc/bind/internals/db.example.com";
		allow-transfer { 192.168.1.202; };
	};

	zone "1.168.192.in-addr.arpa" {
		type master;
		file "/etc/bind/internals/db.192";
		allow-transfer { 192.168.1.202; };
	};
};

view "external" {
	match-clients { any; };

	zone "example.com" {
		type master;
		file "/etc/bind/externals/db.example.com";
		allow-transfer { 192.168.1.202; };
	};

	zone "xx.xx.201.in-addr.arpa" {
		type master;
		file "/etc/bind/externals/db.201";
		allow-transfer { 192.168.1.202; };
	};
};
```



**dns-02.example.com => 192.168.1.202**

/etc/bind/named.conf.local
```
acl internals {
	127.0.0.0/8;
	192.168.1.0/24;
};

view "internal" {
	match-clients { internals; };

	zone "example.com" {
		type slave;
		file "/var/cache/bind/internals/db.example.com";
		masters { 192.168.1.201; };
	};

	zone "1.168.192.in-addr.arpa" {
		type slave;
		file "/var/cache/bind/internals/db.192";
		masters { 192.168.1.201; };
	};
};

view "external" {
	match-clients { any; };

	zone "example.com" {
		type slave;
		file "/var/cache/bind/externals/db.example.com";
		masters { 192.168.1.201; };
	};

	zone "xx.xx.201.in-addr.arpa" {
		type slave;
		file "/var/cache/bind/externals/db.201";
		masters { 192.168.1.201; };
	};
};
```


**My problem:** db.201 isn´t transferred from master to slave.  :(


Any ideas?

---

### Post by gombadi on 2009-09-19
The slave host matches the view "internal" acl's so it is only able to see and transfer domains in the internal view.

 db.201 exists in the view "external". The slave dns host is not able to see, and therefore transfer this domain.

---

### Post by Moso on 2009-09-19
Hi gombadi!

Thanks for your help!  :P

There is a way to do a setup like this work?

```
         ------------
         | internet |
         ------------
              |
              |
              | 201.xx.xx.xx/29
         ------------
         | firewall |
         ------------
              | 192.168.1.254
              |
              |
      ------------------
      |                |
      |                |
      |                |
      |                |
 ------------     ------------
 |  dns-01  |     |  dns-02  |
 ------------     ------------
 192.168.1.201    192.168.1.202
```

The firewall have 5 valid IPs and is using 2 of them with DNAT to dns-01 and dns-02.

So, dns-01 is the master and dns-02 is the slave.

Now almost everything works, just the reverse of 201.xx.xx.xx isn´t transferred to the slave...  :(

---

### Post by gombadi on 2009-09-19
This web page will do a better job of explaining the problem than I can.

Have a look at the Views in Slave Name Servers section near the bottom.

[http://www.oreillynet.com/pub/a/oreilly/networking/news/views_0501.html](http://www.oreillynet.com/pub/a/oreilly/networking/news/views_0501.html)

---

### Post by Moso on 2009-09-19
Thanks gombadi!

Very useful information in that link.  :P

I found the "correct" approach to use in BIND 9.3 and later...

I posted in [http://ubuntuforums.org/showpost.php?p=7976418&postcount=2](http://ubuntuforums.org/showpost.php?p=7976418&postcount=2)

\\:D/

---

