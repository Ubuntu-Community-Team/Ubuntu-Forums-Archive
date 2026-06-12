---
title: "3 Servers, Bind9, and rndc"
date: 2007-10-08
forum: Server Platforms
---

### Post by crayz1 on 2007-10-08
I am really having a hard time figuring out exactly how to configure my servers.

Here is the breakdown:

Web/Mail/FTP Server managed by ISPConfig - Ubuntu Server 6.06 LTS 64bit
Name Server 1 - Ubuntu Server 6.06 LTS 32bit
Name Server 2 - Ubuntu Server 6.06 LTS 32bit

The Web/Mail/FTP Server controls everything. It is the primary/master name server as well. When creating sites on it through ISPConfig I want the name servers/slaves to be updated with the newly created zones.

I have been unable to transfer zones from the master to the slaves. Once I can I want to have it secured with rndc. 

My question about rndc is, What key am I using on the master? What key am I using on the slave?

I hope to develop a discussion from this because I have many more questions on the subject.

---

