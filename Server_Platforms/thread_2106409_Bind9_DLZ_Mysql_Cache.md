---
title: "Bind9 DLZ Mysql Cache"
date: 2013-01-19
forum: Server Platforms
---

### Post by fromberg100 on 2013-01-19
HI All,

I just finished setting up my server with Bind9 + DLZ + MySQL.  I have just a simple question.  Every time any particular domain is queried, the mysql database is being checked to resolve the queried domain.  Here my question is if it is my possible when a new address is queried and resolved, can it be store in a cache somehow?

Please find below my named.conf:

include "/etc/bind/named.conf.options";
#include "/etc/bind/named.conf.local";
#include "/etc/bind/named.conf.default-zones";

dlz "Mysql" {

   database "mysql
   {host=127.0.0.1 port=3306 dbname=bind9_dlz user=root pass=perseo}
   {SELECT zone FROM records WHERE zone = '$zone$'}
   {SELECT ttl, type, mx_priority, IF(type = 'TXT', CONCAT('\"',data,'\"'), data) AS data
    FROM records
    WHERE zone = '$zone$' AND host = '$record$' AND type <> 'SOA' AND type <> 'NS'}
   {SELECT ttl, type, data, primary_ns, resp_contact, serial, refresh, retry, expire, minimum
    FROM records
    WHERE zone = '$zone$' AND (type = 'SOA' OR type='NS')}
   {SELECT ttl, type, host, mx_priority, IF(type = 'TXT', CONCAT('\"',data,'\"'), data) AS data, resp_contact, serial, refresh, retry, expire, minimum
    FROM records
    WHERE zone = '$zone$' AND type <> 'SOA' AND type <> 'NS'}
   {SELECT zone FROM xfr where zone='$zone$' AND client = '$client$'}";
};


Below my named.conf.options:

acl internals { 192.168.2.0/24; };


options {

    listen-on-v6            { none; };



    allow-query             { internals;};

    allow-recursion            { internals;};



    forwarders {

    200.63.192.1;
    200.63.212.1;
    };

};

---

