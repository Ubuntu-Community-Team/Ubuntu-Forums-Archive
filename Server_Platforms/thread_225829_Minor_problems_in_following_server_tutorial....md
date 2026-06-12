---
title: "Minor problems in following server tutorial..."
date: 2006-07-30
forum: Server Platforms
---

### Post by cityofdoors on 2006-07-30
Hi All,

I recently installed ubuntu server 6.06 on my computer and have been following the instructions at this link to get it working:
[URL="http://www.howtoforge.com/perfect_setup_ubuntu_6.06"]
http://www.howtoforge.com/perfect_setup_ubuntu_6.06[/URL]

Aside from the things in that guide, the only other thing I've done is install ddclient for my dynamic dns.

Naturally, I'm having a few problems and would really really appreciate some help...

Under step 5 (p3, Configuring the Network), I tried to follow the instructions, knowing that I have a dynamic dns. Thus, my /etc/hosts reads:

```
127.0.0.1       localhost.localdomain localhost
127.0.1.1   www.omniversalism.com     outlands

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I don't know if this is correct, but "hostname" and "hostname -f" do NOT give me the same result.

*

Second, in step 10 (p4, MySQL), when I tried to create a password for my site using

```
mysqladmin -h www.omniversalism.com -u root password MYPASSWORDHERE
```

I got the following error:

*"connect to server at 'www.omniversalism.com' failed error: 'Host '192.168.0.3' is not allowed to connect to this mySQL server."*

This is what I'm currently up to.

Please, any help would help! Thanks.

---

### Post by chaag on 2006-07-30
Not sure on the hosts file question, but access mysql using the mysql binary and follow the insructions here:
[http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html)

mysql, controls both which accounts are set up _and_ from where they can access the database(s). By default, only connections from localhost as "root" are allowed.

---

### Post by vanilla on 2006-08-01
If you read the comments at page 3 in the guide you see that you need to change the name in /etc/hostname also.

That did the trick for me on my second install, the first one worked without that.:confused:

---

