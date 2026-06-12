---
title: "best services to impliment in a small business?"
date: 2008-01-08
forum: Server Platforms
---

### Post by at0mic on 2008-01-08
Hi,

What are some of the best linux services you have ever implimented in a small business enviroment? I am personally thinking about LDAP for a global address book and a ticket system to keep track of IT tasks.

---

### Post by Pitt Stains on 2008-01-08
Samba file server.

Things I'd like to do but have yet to make time for:
[LIST]
[*]FOSS PDF printer that is shared out over the network
[*]File backups that require no software to be installed on the client (Windows) machines
[/LIST]

---

### Post by mmichalik on 2008-01-08
We have set up our entire network solely using Ubuntu servers and are thankfully Windows free.

OpenVPN on the server is an awesome tool that even works well with the windows vpn client software.  Our outside sales force uses it extensively via their Ubuntu laptops

Postfix works great.  We currently run three different domains out of it and it's seemless.  

Apache2 is as good as always.

NFS works great as well.  We use Bacula to backup our NFS mounts with out an issue.

There really isn't enough space to extol the virtues of Ubuntu servers here.

We are going to set up LDAP and NIS next on our server as well.

As far as an IT Ticketing system goes, we haven't looked into that yet. There are some great ERP programs available out there, like Adempiere but that may be a bit overkill for your purposes.

---

### Post by opportunity on 2008-01-09
Really love the idea of a network PDF printer for both windows and linux clients! 

Is there any already made how to on this process? I found one for novell... Will it work the same?

[http://www.novell.com/coolsolutions/feature/17636.html](http://www.novell.com/coolsolutions/feature/17636.html)


EDIT: 

I found a good tutorial but cups-pdf does not allow for user chosen save locations. I guess ill have to go install cutepdf on all windows machines.

TUT: [http://www.linux.com/articles/61826](http://www.linux.com/articles/61826)

---

### Post by k_grdn on 2008-01-09
Hi,

I rate RT as multiuser ticket system, good mailing list support.

[http://bestpractical.com/rt/](http://bestpractical.com/rt/)

Regards,

k_grdn

---

