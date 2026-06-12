---
title: "BIND9 misconfig, local lookups not working properly"
date: 2009-03-17
forum: Server Platforms
---

### Post by uberlinux on 2009-03-17
Hello All,
The home network has been growing, so I figured it was finally worth it to set up BIND on my home-server.  I've followed this [how-to]("http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html") to the 'T', and even applied the fix-edits listed in the comments below the how-to. 

This has gotten upstream-referred lookups working fine:
```

username@*****:/etc/bind$ nslookup google.com
Server:         192.168.10.226
Address:        192.168.10.226#53

Non-authoritative answer:
Name:   google.com
Address: 74.125.67.100
Name:   google.com
Address: 209.85.171.100
Name:   google.com
Address: 74.125.45.100
```

...but local lookups fail in an odd way that screams: "Dumb, careless misconfig!"  See this:
```

username@******:/etc/bind$ nslookup hostX.my-subdomain.homeunix.org
Server:         192.168.10.226
Address:        192.168.10.226#53

** server can't find hostX.my-subdomain.homeunix.org.my-subdomain.homeunix.org: SERVFAIL

```

I'm sure this is something simple involving my stupid zone files, but I don't know what to edit/update.

Here's a copy of my /etc/bind/zones/my-subdomain.homeunix.org.db file:

```

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
example.com. IN SOA ns1.example.com. admin.example.com. (
// Do not modify the following lines!
2007031001
28800
3600
604800
38400
)

// Replace the following line as necessary:
// ns1 = DNS Server name
// mail = mail server name
// example.com = domain name
my-subdomain.homeunix.org. IN NS hostN.my-subdmain.homeunix.org.
my-subdomain.homeunix.org. IN MX 10 mail.my-subdomain.homeunix.org.

// Replace the IP address with the right IP addresses.
hostA IN A 192.168.10.1
hostB IN A 192.168.10.100
hostC IN A 192.168.10.225
hostD IN A 192.168.10.226
hostE IN A 192.168.0.227
hostF IN A 192.168.10.228
hostG IN A 192.168.100.1

```

:KS halp! :KS

---

### Post by doas777 on 2009-03-17
hmmm. what I see here:```
** server can't find hostX.my-subdomain.homeunix.org.my-subdomain.homeunix.org: SERVFAIL
```

leads me to believe that you have set a default search suffix for your domain. does it work if you do:
```
nslookup hostX
```?

I'm by no means an Bind expert, but my bind conf does not include the word 'IN' in the name listings.
you may wanna try:
```
hostA A 192.168.10.1
hostB  A 192.168.10.100
hostC  A 192.168.10.225
hostD  A 192.168.10.226
hostE  A 192.168.0.227
hostF  A 192.168.10.228
hostG  A 192.168.100.1
```

---

### Post by uberlinux on 2009-03-17
> **doas777 said:**
> hmmm. what I see here:```
** server can't find hostX.my-subdomain.homeunix.org.my-subdomain.homeunix.org: SERVFAIL
```

leads me to believe that you have set a default search suffix for your domain. does it work if you do:
```
nslookup hostX
```?

LOL!  I can't believe I didn't think about that.  I'll have to figure out how to remove the search suffix later.  

I tried just the host, rather than FQDN and got an NXDOMAIN error, argh!

```
** server can't find hostX: NXDOMAIN
```

Since I suspect NXDOMAIN can mean just about anything, I did a dig on the same host:
```

$ dig hostX

; <<>> DiG 9.4.2-P2 <<>> hostX
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 46651
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;hostX.                         IN      A

;; AUTHORITY SECTION:
.                       686     IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2009031701 1800 900 604800 86400

;; Query time: 7 msec
;; SERVER: 192.168.10.226#53(192.168.10.226)
;; WHEN: Tue Mar 17 21:11:28 2009
;; MSG SIZE  rcvd: 98

```

---

### Post by doas777 on 2009-03-17
is bind running? 
```
ps -ef | grep named
```

---

### Post by doas777 on 2009-03-17
I think i edited a post after you had read the original, so I just wanted to reiterate the change.
<snip>
I'm by no means an Bind expert, but my bind conf does not include the word 'IN' in the name listings.
you may wanna try:
Code:

hostA A 192.168.10.1
hostB  A 192.168.10.100
hostC  A 192.168.10.225
hostD  A 192.168.10.226
hostE  A 192.168.0.227
hostF  A 192.168.10.228
hostG  A 192.168.100.1
</snip>

---

### Post by uberlinux on 2009-03-17
> **doas777 said:**
> is bind running? 
```
ps -ef | grep named
```

Thanks for the reply!

Bind is running:
```
bind      8360     1  0 21:03 ?        00:00:00 /usr/sbin/named -u bind
```

I'm actually using it as my DNS provider from this workstation.  The only lookups that aren't working are LAN hosts.  I'm interacting w/ this forum via the BIND instance in question.

---

### Post by uberlinux on 2009-03-17
> **doas777 said:**
> I think i edited a post after you had read the original, so I just wanted to reiterate the change.
<snip>
I'm by no means an Bind expert, but my bind conf does not include the word 'IN' in the name listings.
you may wanna try:
Code:

hostA A 192.168.10.1
hostB  A 192.168.10.100
hostC  A 192.168.10.225
hostD  A 192.168.10.226
hostE  A 192.168.0.227
hostF  A 192.168.10.228
hostG  A 192.168.100.1
</snip>

ooo good call.  I'll .bak the existing edit the orig, and restart bind.
Thanks!

---

### Post by uberlinux on 2009-03-17
> **uberlinux said:**
> ooo good call.  I'll .bak the existing edit the orig, and restart bind.
Thanks!

No luck there.  Thanks for the possibility tho!

---

### Post by doas777 on 2009-03-17
heres my zone file. it's a little differant from the one you posted:
```
$TTL 10

@ IN SOA 13of2.ABC.net. user.ABC.net. (
        20081213          ; serial
        8                 ; refresh
        2                 ; retry
        4W                ; expire
        1D                ; minimum
        )

  IN      NS  13of2.ABC.net.

localhost  A        127.0.0.1
12of5      A        192.168.xx.12
ns1        CNAME    13of5
17of5      A        192.168.xx.17
11of5      A        192.168.xx.11
13of5      A        192.168.xx.13
20of5      A        192.168.xx.20
```

good luck

---

### Post by uberlinux on 2009-03-17
If you don't mind my asking, what's your zone file called, and how does bind refer to it?  I mean, is it in the format of "/etc/bind/zones/your-domain.com.db"  ?  And does some master named.conf file refer to it?

---

### Post by doas777 on 2009-03-17
mine is db.<domain>.net I believe it expects that to be the name of the zone file. 


bind has a validation app built in. this link has some information on it:[http://www.cyberciti.biz/faq/howto-linux-unix-zone-file-validity-checking/](http://www.cyberciti.biz/faq/howto-linux-unix-zone-file-validity-checking/)

it will likely be useful. 

here is a ls of my bind dir:
```
user@13of5:~$ ls /etc/bind
db.0            db.255        db.local          named.conf.options
db.127          db.ABC.net   db.root           named.conf.options~
db.192.168.xx   db.ABC.net~  named.conf        rndc.key
db.192.168.xx~  db.empty      named.conf.local  zones.rfc1918
```

---

### Post by doas777 on 2009-03-17
what is in your named.conf.local?

mine references both my forward and reverse zones:
zone "ABC.net" {
  type master;
  notify no;
  file "/etc/bind/db.ABC.net";
};

zone "xx.168.192.in-addr.arpa" {
  type master;
  notify no;
  file "/etc/bind/db.192.168.xx";
};

---

### Post by uberlinux on 2009-03-17
Here 'tis:

```

$:/etc/bind/zones$ cat named.conf.local 
//
// Do any local configuration here
//

zone "my-subdomain.homeunix.org" {
type master;
file "/etc/bind/zones/my-subdomain.homeunix.org.db";
};

zone "10.168.192.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.10.168.192.in-addr.arpa";
};

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

```

---

### Post by doas777 on 2009-03-17
that looks right. did named -checkzone get you any info?

---

### Post by uberlinux on 2009-03-18
> **doas777 said:**
> that looks right. did named -checkzone get you any info?

I'm not sure I'm doing it right.  That doesn't return info, nor an error.

---

### Post by uberlinux on 2009-03-18
> **uberlinux said:**
> I'm not sure I'm doing it right.  That doesn't return info, nor an error.

bump?

---

### Post by doas777 on 2009-03-18
try this:
```

named-checkzone my-subdomain.homeunix.org my-subdomain.homeunix.org.db

```

it should return somthing like:
zone: my-subdomain.homeunix.org/IN loaded serial <zoneserialnumber>

---

### Post by doas777 on 2009-03-18
just to clarify, are you restarting/reloading bind each time you make a change to a config file?

---

### Post by uberlinux on 2009-03-18
Thanks for the reply.  I think this is a good lead.  It can't find the .db file, which I know exists, so somewhere there's a pointer that's not working properly.

```
$ named-checkzone blah.homeunix.org blah.homeunix.org.db
zone blah.homeunix.org/IN: loading from master file blah.homeunix.org.db failed: file not found
```

---

### Post by doas777 on 2009-03-19
have you tried adding the full path to the zone file (/etc/bind/zones/my-subdomain.homeunix.org.db) in the named-checkzone?

---

### Post by jlintz on 2009-03-21
```

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
example.com. IN SOA ns1.example.com. admin.example.com. (
// Do not modify the following lines!
2007031001
28800
3600
604800
38400
)

// Replace the following line as necessary:
// ns1 = DNS Server name
// mail = mail server name
// example.com = domain name
my-subdomain.homeunix.org. IN NS hostN.my-subdmain.homeunix.org.
my-subdomain.homeunix.org. IN MX 10 mail.my-subdomain.homeunix.org.

// Replace the IP address with the right IP addresses.
hostA IN A 192.168.10.1
hostB IN A 192.168.10.100
hostC IN A 192.168.10.225
hostD IN A 192.168.10.226
hostE IN A 192.168.0.227
hostF IN A 192.168.10.228
hostG IN A 192.168.100.1

```

[/QUOTE]


Your SOA is has example.com as the domain name and its being appended to hostA-G since you didn't use the FQDN.  Change that to homeunix.org.  You also need A records for your NS record and for your MX record.

---

