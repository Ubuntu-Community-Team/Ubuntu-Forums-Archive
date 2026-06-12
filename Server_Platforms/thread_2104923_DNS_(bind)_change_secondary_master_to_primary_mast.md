---
title: "DNS (bind): change secondary master to primary master"
date: 2013-01-14
forum: Server Platforms
---

### Post by apohal9 on 2013-01-14
Hi,

this is a maybe to general bind question.

I've setup an Ubuntu-Server with bind successfully acting as an secondary master server for dns resolution. 

The primary one is an old Windows Server holding all the DNS records which I need to migrate to an Ubuntu bind-Server without setting up all the records "by hand".

So, how can I change the role of the secondary master to be the primary?

Thanks for your help,
apohal9

---

### Post by chadk5utc on 2013-01-14
> **apohal9 said:**
> Hi,

this is a maybe to general bind question.

I've setup an Ubuntu-Server with bind successfully acting as an secondary master server for dns resolution. 

The primary one is an old Windows Server holding all the DNS records which I need to migrate to an Ubuntu bind-Server without setting up all the records "by hand".

So, how can I change the role of the secondary master to be the primary?

Thanks for your help,
apohal9
Windows DNS is tightly integrated into Active Directory,If Active Directory is used all I have read indicates that it will be more complicated to do. If your just transferring DNS I'd think the easiest way to do this would be to:
    Set up the Linux DNS server as a slave / secondary server to the Windows box.
    Do a DNS zone transfer from Windows to Linux
    Optionally, shutdown the Windows DNS server, after you have tested and insured the transfer change its role to master.
The following article explains how to configure BIND (Linux DNS) for use with AD.
[http://support.microsoft.com/kb/275866](http://support.microsoft.com/kb/275866)

---

### Post by apohal9 on 2013-01-15
Thanks for your answer, chadk5utc[]("http://ubuntuforums.org/member.php?u=400673").

No, there is no AD-integration. AD isn't used on this machine.

The zone transfer has been successfull. And this is my question: HOW do I change its role to be the master? Editing the zone-files?!

---

### Post by chadk5utc on 2013-01-15
> **apohal9 said:**
> Thanks for your answer, chadk5utc[]("http://ubuntuforums.org/member.php?u=400673").

No, there is no AD-integration. AD isn't used on this machine.

The zone transfer has been successfull. And this is my question: HOW do I change its role to be the master? Editing the zone-files?!

Heres a link that should give enough information to reference.
[https://help.ubuntu.com/community/BIND9ServerHowto#Primary_Master_Server](https://help.ubuntu.com/community/BIND9ServerHowto#Primary_Master_Server)

---

