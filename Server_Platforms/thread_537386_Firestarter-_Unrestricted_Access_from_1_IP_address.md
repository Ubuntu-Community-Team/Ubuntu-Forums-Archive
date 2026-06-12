---
title: "Firestarter- Unrestricted Access from 1 IP address?"
date: 2007-08-28
forum: Server Platforms
---

### Post by packersfan2010 on 2007-08-28
Hi everyone,

I've setup firestarter, and I want to basically DMZ one IP in Firestarter.

Basically, I want IP address  *foo.bar.foo.bar* to be able to access **any** IP on **any** port. 

A) Is this possible?
B) How would I do it? (I have most of it setup, such as access to any IP, I just need to know how to specify any port).

-Packersfan2010

EDIT: Also, I know this sacrifices the security of firestarter for that PC- that PC has a meticulously done software firewall that the user can be trusted to manage.

---

### Post by saphil on 2007-08-29
You are at 10.0.0.100 (your workstation with firestarter on it) you can't set firestarter to allow any ingoing and outgoing on 10.0.0.222 (the workstation with the meticulously configured firewall)  The firewall on 10.0.0.222 is doing that 
all you have to do is 
```
--pseudocode for an ACL--
ALLOW_ALL 10.0.0.100 10.0.0.222
ALLOW_ALL 10.0.0.222 10.0.0.100

```
You are right, this is going to open you up to possible monkey-in-the-middle attacks

Firestarter is a front-end for ipChains, which is the kernel-module firewall native to Linux.  
You can set Firestarter Policies 
1) incoming as allowing connections from  host 10.0.0.222
2) and the outgoing can be set to restrictive by default and then you can whitelist 10.0.0.222

Let's find out if this works.

What are you actually hoping to achieve?  There might be a safer, more sophisticated way to handle it.

It could be that you would be better off adding the rules directly to IPChains

---

