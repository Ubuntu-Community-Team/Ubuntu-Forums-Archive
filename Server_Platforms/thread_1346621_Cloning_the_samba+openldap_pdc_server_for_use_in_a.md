---
title: "Cloning the samba+openldap pdc server for use in another network"
date: 2009-12-05
forum: Server Platforms
---

### Post by alikthename on 2009-12-05
Hi everyone!
In the office we have an ubuntu 9.04 server which serves as pdc with samba+openldap+Mandriva Diectory Server web interface, as a file server and  as a router with squid squidguard and free-sa.The server was set up by the person who is unreacheable at the moment.
Now we have a task to clone this server for use in another office with the new domain name. At the time there are two questions we want to ask and would be very thankfull if somebody could help us.

1. Is this possible just to change the domain name of new cloned pdc? If so what is the most convinient way to do this? As I guess a lot of configuration files should be changed for the domain name parameters, but I do not know what files actually sould be changed, I edited several files in particular /etc/ldap/slapd.conf /etc/ldap/ldap.conf, /etc/ldap.conf, /etc/smb.conf, /etc/squid/squid/conf and several others and then Mandriva Management Console refused to work with error 111. So I don't know whether I'm on a right way or not. Seached on the internet but could not fond anything usefull. May be I'm using wrong terms. 
2.If we will successfully change the domain name what should we do to preserve all the users and groups and shares shares that were set up on the old pdc?

---

### Post by brettg on 2009-12-05
You can clone the server easily enough using Clonezilla or by following [these instructions]("http://tuxnetworks.blogspot.com/2008/07/backing-up-disk-over-network.html")

Changing the hostname is simple;

```
sudo vi /etc/hostname
```

You might also want to change the hosts file;

```
sudo vi /etc/hosts
```

As for all the LDAP and other stuff, you will have to look elsewhere for that level of assistance. 

I can't imagine it will be all that simple to do, what with all the OU's, CN's, DN's and FDN's involved.

Personally, I would recommend setting it up from scratch. Sometimes it is easier to start with a clean slate rather than trying to change something as complex as an LDAP server.

---

### Post by alikthename on 2009-12-06
> **brettg said:**
> 
As for all the LDAP and other stuff, you will have to look elsewhere for that level of assistance. 

I can't imagine it will be all that simple to do, what with all the OU's, CN's, DN's and FDN's involved.

Personally, I would recommend setting it up from scratch. Sometimes it is easier to start with a clean slate rather than trying to change something as complex as an LDAP server.
I had similar thoughts but what if I'll change all "olddomain" names with "newdomain" in all configuration files like

```

grep -rl matchstring somedir/ | xargs sed -i &#8217;s/olddomain/newdomain/g&#8217;

```
May be that will work?

---

### Post by brettg on 2009-12-07
Well, it certainly can't hurt to try (but it might waste some time)

---

### Post by alikthename on 2009-12-07
Yes I tried that and it did not work.(

OK now if I'll try everything from scratch, what is the fastest way to complete this task. Can I import anything from old configurtration?

---

