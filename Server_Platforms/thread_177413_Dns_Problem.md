---
title: "Dns Problem"
date: 2006-05-16
forum: Server Platforms
---

### Post by soon82 on 2006-05-16
when i try to restart bind9 services

root@Linux:~# /etc/init.d/bind9 restart
 * Stopping domain name service... rndc: connect failed: connection refused
                                                                       [ ok ]
 * Starting domain name service...                                     [ ok ]
root@Linux:~#


the rndc: connect failed: connection refused...

What is the problem...

---

### Post by cvmiller on 2006-05-16
[QUOTE=soon82]when i try to restart bind9 services

root@Linux:~# /etc/init.d/bind9 restart
 * Stopping domain name service... rndc: connect failed: connection refused
                                                                       [ ok ]
 * Starting domain name service...                                     [ ok ]
root@Linux:~#


the rndc: connect failed: connection refused...

What is the problem...[/QUOTE]

Could be lots of things, bind is pretty complicated. But I would look at your /etc/named.conf and your /etc/rndc.conf and ensure that the "secrets" are the same (you should see the note in the file to this effect).

I found quite a bit of help in the bind docs, on my mandrake system they were installed at: /usr/share/doc/bind-9.3.1/

I hope this helps,

Craig...

---

### Post by soon82 on 2006-05-17
This is my /etc/bind/named.conf.


options {
        directory "/etc/bind";

};

controls {
        inet 127.0.0.1; 172.95.10.3 allow { localhost; } keys { rndc_key; };
};

key "rndc-key" {
	algorithm hmac-md5;
	secret "JEwBeUTwWKTBBwV6yYf+Qw==";
};


zone "." {
        type hint;
        file "/etc/bind/db.root";
};

zone "0.0.127.in-addr.arpa" {
        type master;
        file "/etc/bind/127.0.0";
};

zone "nexgenoffice.dyndns.org" {
        type master;
        file "/etc/bind/nexgenoffice";
};

zone "10.95.172.in-addr.arpa" {
        type master;
        file "/etc/bind/172.95.10";
};


and below is my /etc/bind/rndc.key

key "rndc-key" {
	algorithm hmac-md5;
	secret "JEwBeUTwWKTBBwV6yYf+Qw==";
};

---

### Post by cvmiller on 2006-05-17
Hmm, Nothing jumps out at me. I do see that my pointers to the zone do include reference to my key:
zone "1.1.10.in-addr.arpa" {
        type master;
        file "internal.reversed";
        allow-update { key mykey; };
};

zone "internal.net" {
        type master;
        file "internal.zone";
        allow-update { key mykey; };
};

---

### Post by soon82 on 2006-05-17
So, what should i do now.... do you have any comment.

---

