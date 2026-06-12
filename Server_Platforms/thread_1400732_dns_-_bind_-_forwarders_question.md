---
title: "dns - bind - forwarders question"
date: 2010-02-07
forum: Server Platforms
---

### Post by bvidinli on 2010-02-07
Hi,

I want this scenario:

for some domains (group A) in my server, answer directly (using master zone), this is already working.
for some other domains (group B), just redirect to another dns server, such as google dns, 8.8.8.8,       i tried forwarders directive, but didnt work.
for all other domains, return nothing, refuse... this is already working.

any idea ?

i did for ex:

zone "hurriyet.com" IN {
	type forward;
	forwarders { 8.8.8.8; 8.8.4.4; };
};


but still in log:
named[20414]: client 78.187.86.112#49266: query (cache) 'hurriyet.com/A/IN' denied


how can I forward for ex, hurriyet.com to google dns ?

I do not want to do forwarding for all domains, but only a group (B) of domains.

---

### Post by Bachstelze on 2010-02-07
You need to allow recursive requests with the [font=monospace]allow-recursion[/font] directive. For example:

```
firas@iori ~ % cat /etc/bind/named.conf.options
acl "myservers" {
    88.181.14.184;
    2a01:e35:8B50:EB80::/64;
    2a01:e35:8BA7:C5B0::/64;
    88.186.124.91;
    localhost;
    ::1;
};

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

        auth-nxdomain no;    # conform to RFC1035
        //listen-on { 1; };
        listen-on-v6    { any; };
        allow-recursion { myservers; };
};

```

With this configuration, all the IPs in the "myservers" list will be allowed to ask the server about other domains. By the way, you don't need a forwarder.

---

### Post by bvidinli on 2010-02-07
Thank you for your suggestion,
but, that is not what I want,

You did allow recursion for a group of ip's/servers.

I want to do grouping NOT for people that asks/queries my dns server, 
BUT, for domains that can be queried.

Everybody should be able to query my dns server,
For some domains of mine (lets say group A) use master zones and answer as an authoritative dns.
for some other domains, not all domains, (lets say group B), just forward dns queries to 8.8.8.8 or root servers,

for all remaining domains, just refuse it (like in case allow-recursion no )


thank you for your helps.

---

### Post by bvidinli on 2010-02-08
Another way to ask same:

I have in config:
zone "s67.org" {
        type master;
        file "/etc/bind/s67.org";
};


zone "hurriyet.com" IN {
        type forward;
        forwarders { 8.8.8.8; 8.8.4.4; };
        forward only;
};



master zone works normally, as expected, 
but forward type zone does not work. 

my options has this:

forwarders { 8.8.8.8; 8.8.4.4; };
forward first;
recursion yes;

---

