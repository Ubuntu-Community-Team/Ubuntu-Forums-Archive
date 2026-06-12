---
title: "why DIRECTORY SERVICE concept not rich in linux world?"
date: 2009-04-29
forum: Server Platforms
---

### Post by salim.madni on 2009-04-29
dear gurus

i have a general discussion, if you look into novell and microsft they have very strong active directory rich features,functions,roles,fmso,accounts,groups are controlled on network lan,wan,man

so being linux is so strong os now a days and everyday it becoming most popular,and strongest among all ever any os regardless. 

so why linux and ubuntu does not have similar features to above where they can interact it.

can a linux server cant control and managed user accounts,qutas,userid,password,groups,shares,permission etc on server.

kindly can someone suggest advise and any links tutorials articles videos are highly appreciated

kind regards

---

### Post by lisati on 2009-04-29
Presumably you mean something different to what many Ubuntu users can access on their System->Administration->Users and groups menu option.

---

### Post by salim.madni on 2009-04-29
i am refering to ubuntu server not desktop let me know on this where server/client relationship

---

### Post by netztier on 2009-04-29
> **salim.madni said:**
> 
can a linux server cant control and managed user accounts,qutas,userid,password,groups,shares,permission etc on server.

DHCP, DNS, NFS and Samba, LDAP, Kerberos, Radius, Certificate Handling, OpenSSL. They're all there for Linux.

On Ubuntu Server and Debian, they don't come neatly packaged "in a box", which means that you have to put these building blocks together yourself, or use a distribution that does it for you.

Suse and Redhat are probably stronger in that regard, but there's also companies like Univention that use Debian as a basis to build their "Corporate Server" product.

On launchpad.net (Ubuntu's development platform), you can find some "blueprint" documents that show plans or ideas that go into that direction, for example:
[LIST]
[*][https://blueprints.launchpad.net/ubuntu/+spec/directory-service](https://blueprints.launchpad.net/ubuntu/+spec/directory-service)
[*][https://blueprints.launchpad.net/ubuntu/+spec/opends-integration](https://blueprints.launchpad.net/ubuntu/+spec/opends-integration)
[*][https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux](https://blueprints.launchpad.net/ubuntu/+spec/domain-for-linux)
[/LIST] 
Yet, I think that (as of this writing) not too much effort has gone into building a "directory server add-on package" to the basic Ubuntu server installation - although people on forums and on launchpad see a use case for it.


regards

Marc

---

### Post by HermanAB on 2009-04-29
Howdy,

The Sun Yellow Pages, now known as NIS has been around since some time before the dinosaurs.  Every large Linux distribution has this by a different name, eg Redhat Directory Server, Novell Directory Server, Mandriva Directory Server...

It is very easy to set up and it works, which may explain why it is not in the news.  It is totally undramatic.

---

### Post by shadowfirebird on 2009-04-29
Samba 4 will allegedly interact fully with Windows Active Directories.  Of course since this is having to be reverse-engineered, there is some take-up time involved, which is why it's not here yet.

And in any case compatibility with MS and providing similar services are two different things.

---

