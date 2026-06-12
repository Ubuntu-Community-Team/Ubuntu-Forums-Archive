---
title: "Squid &amp; User ACLs"
date: 2009-03-03
forum: Server Platforms
---

### Post by YaAqoB on 2009-03-03
Hello all.
Quick question.... I have setup Squid in a school environment using basic authentication so we can log students browsing. It's all working very well with great reporting etc.
Is it possible with out creating multiple SRC acls and setting static ips every where to tell Squid that User A & B are in an ACL called staff and users C & D are om an ACL called students.
I would then like to tell Squid that Staff can have full access and Students have access except the sites in my banned-sites list.
I currently have a banned sites file working fine but it obviously applies to all proxy users.
It sounds doable to me but I just cant figure out how to get the usernames into an ACL.
So basically to wrap it up I want to be able to separate out my users so I can apply the banned-sites.squid to half and then allow "some" of those via the allowed-sites.squid to the rest without having to have the staff for example on 192.168.1.10-50 and then the students on .1.60-100
The IP solution wouldn't work as staff and students share PC's.

Thanks in advance.


James

---

### Post by bodhi.zazen on 2009-03-03
Moved to the servers section as that is likely a better place then security (as you are configuring squid rather then a general security question).

Unfortunately I do not know the answer and I found the squid documentation let us say outdated in that many features have changed since the documentation was written.

IMO the squid config file is huge and, while you are waiting for a reply, you may want to read through it ;)

---

### Post by YaAqoB on 2009-03-03
Thanks for your help.
I'll sit back & have a read while waiting for a reply.:popcorn:

---

### Post by YaAqoB on 2009-03-05
I've read that you can do it when using AD integration but I still can't find any info that tells me how to group users using the basic password file.

---

