---
title: "slave DNS server doesn´t get the external reverse zone"
date: 2009-09-19
forum: Server Platforms
---

### Post by Moso on 2009-09-19
Hi everbody!  :)

I´m getting crazy with this problem, please help...

The problem is that the slave DNS server gets only *db.example.com-int*, *db.example.com-ext* and *db.192* from the master DNS server.  It doesn´t get the *db.200* file that is the reverse zone of the external view.

This is the error message that appear in /var/log/syslog of the slave DNS server:

*  Sep 19 17:24:05 dns-02 named[4598]: zone xx.xx.200.in-addr.arpa/IN/external: refresh: non-authoritative answer from master 192.168.1.201#53 (source 0.0.0.0#0)*

But:

```
user@dns-02:~$ ls -l /var/cache/bind/
total 12K
-rw-r--r-- 1 bind bind 551 2009-09-19 17:23 db.192
-rw-r--r-- 1 bind bind 617 2009-09-19 17:23 db.example.com-ext
-rw-r--r-- 1 bind bind 617 2009-09-19 17:23 db.example.com-int
```

So, the slave server gets *db.example.com-int* and *db.192* from the internal view but only gets *db.example.com-ext* from the external view...  :P


**Scenario:**

I need to setup two DNS servers (master and slave) inside my LAN, with private IPs.

In my firewall, I will have the public IPs DNATed to the inside servers.

This is the layout:

```
         ------------
         | internet |
         ------------
              |
              |
              | 200.xx.xx.xx/29
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


Content of **named.conf.local** in _dns-01_:

```
acl internals { 127.0.0.0/8; 192.168.1.0/24; };

view "internal" {
        match-clients { internals; };
        recursion yes;
        zone "example.com" {
                type master;
                file "/etc/bind/db.example.com-int";
                allow-transfer { 192.168.1.202; };
        };
        zone "1.168.192.in-addr.arpa" {
                type master;
                file "/etc/bind/db.192";
                allow-transfer { 192.168.1.202; };
        };
};

view "external" {
        match-clients { any; };
        recursion no;
        zone "example.com" {
                type master;
                file "/etc/bind/db.example.com-ext";
                allow-transfer { 192.168.1.202; };
        };
        zone "247.47.201.in-addr.arpa" {
                type master;
                file "/etc/bind/db.201";
                allow-transfer { 192.168.1.202; };
        };
};
```


Content of **named.conf.local** in _dns-02_:

```
acl internals { 127.0.0.0/8; 192.168.1.0/24; };

view "internal" {
        match-clients { internals; };
        recursion yes;
        zone "example.com" {
                type slave;
                file "db.example.com-int";
                masters { 192.168.1.201; };
        };
        zone "1.168.192.in-addr.arpa" {
                type slave;
                file "db.192";
                masters { 192.168.1.201; };
        };
};

view "external" {
        match-clients { any; };
        recursion no;
        zone "example.com" {
                type slave;
                file "db.example.com-ext";
                masters { 192.168.1.201; };
        };
        zone "247.47.201.in-addr.arpa" {
                type slave;
                file "db.201";
                masters { 192.168.1.201; };
        };
};
```


PS: I have done another post about this problem ( [http://ubuntuforums.org/showthread.php?t=1269911](http://ubuntuforums.org/showthread.php?t=1269911) ) but now I think that I explained better; would be great if any moderator delete the older post.

:lolflag:

---

### Post by Moso on 2009-09-19
Yesss!  I got it!

:guitar:

Content of **named.conf.local** in *dns-01*:

```
key "external" {
	algorithm hmac-md5;
	secret "HvJo78teh/7iyK8BlSkmAA==";
};

view "internal" {
	match-clients { !key external; 192.168.1.0/24; };
	recursion yes;
	zone "example.com" {
		type master;
		file "/etc/bind/db.example.com-int";
		allow-transfer { 192.168.1.202; };
	};
	zone "1.168.192.in-addr.arpa" {
		type master;
		file "/etc/bind/db.192";
		allow-transfer { 192.168.1.202; };
	};
};

view "external" {
	match-clients { key external; any; };
	server 192.168.1.202 { keys external; };
	recursion no;
	zone "example.com" {
		type master;
		file "/etc/bind/db.example.com-ext";
		allow-transfer { 192.168.1.202; };
	};
	zone "zz.yy.xx.in-addr.arpa" {
		type master;
		file "/etc/bind/db.xx";
		allow-transfer { 192.168.1.202; };
	};
};
```


Content of **named.conf.local** in *dns-02*:

```
key "external" {
	algorithm hmac-md5;
	secret "HvJo78teh/7iyK8BlSkmAA==";
};

view "internal" {
	match-clients { !key external; 192.168.1.0/24; };
	recursion yes;
	zone "example.com" {
		type slave;
		file "db.example.com-int";
		masters { 192.168.1.201; };
	};
	zone "1.168.192.in-addr.arpa" {
		type slave;
		file "db.192";
		masters { 192.168.1.201; };
	};
};

view "external" {
	match-clients { key external; any; };
	server 192.168.1.201 { keys external; };
	recursion no;
	zone "example.com" {
		type slave;
		file "db.example.com-ext";
		masters { 192.168.1.201; };
	};
	zone "zz.yy.xx.in-addr.arpa" {
		type slave;
		file "db.xx";
		masters { 192.168.1.201; };
	};
};
```

Only don´t forget to adjust *xx*, *yy* and *zz* to the first three octects of your external IP range.  :popcorn:

---

