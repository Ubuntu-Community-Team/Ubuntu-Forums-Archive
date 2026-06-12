---
title: "Postgresql allow remote hosts"
date: 2006-07-16
forum: Server Platforms
---

### Post by SigmaX on 2006-07-16
Yo;

Freshly installed Postgresql 8.1 on Dapper.  After loading my database backup and adding users with psql, I added the following to the end of the stock *pg_hba.conf* file:

```
#IPv4 remote connections
host sigmax all 0.0.0.0 0.0.0.0 md5
```

Apparently that didn't do what I thought it did, however, because when I connect via my domain name I get:

```
$ psql -U postgres -h my.domain
psql: could not connect to server: Connection refused
        Is the server running on host "my.domain" and accepting
        TCP/IP connections on port 5432?

```

*psql* to localhost works fine.  I'm certain my firewall has theport open and forwarded to my server on the NAT.  What am I doing wrong?  Got the same thing on my FreeBSD server when I installed, so I assume my *pg_hba.conf* entry is wrong?  

SigmaX

---

### Post by SigmaX on 2006-07-17
*bump*

SigmaX

---

### Post by SigmaX on 2006-07-17
Lol; I feel like an idiot now.  Got help on the #postgresql freenode channel.

All that needed done was changing the listen_addresses parameter in postgresql.conf to '*'.  Forgot I hadn't done that yet.

Cheerio all.

SigmaX

---

### Post by pelgrim on 2006-07-28
Well, I still got the same problem here.

Just changed my server from mandrake to Ubuntu,
installed postgresql and uploaded my data backup.

Postgresql.conf has 
listen_address = '*'
port = 5432

pg_hba has
host all all 192.168.0.1/32 trust

I can connect with 127.0.0.1
but not with 192.168.0.1

Someone help me out please, it's blocking my work

---

### Post by pelgrim on 2006-07-28
ok,

I just found out my database directory isn't where I 
initialized it.

Now, whatever I do, postmaster refuses to point to my data directory.

Where is the start script in ubuntu for my postgresql ?

---

### Post by SigmaX on 2006-07-28
> **pelgrim said:**
> ok,

I just found out my database directory isn't where I 
initialized it.

Now, whatever I do, postmaster refuses to point to my data directory.

Where is the start script in ubuntu for my postgresql ?

Mine has one for each version installed:  */etc/init.d/postgresql-7.4* and */etc/init.d/postgresql-8.1*

Just for the record I'm using 7.4 now instead of 8.1, 'cuz 8.1 broke some of my more crudely written client apps.

SigmaX

---

