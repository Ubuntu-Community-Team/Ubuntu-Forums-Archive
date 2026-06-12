---
title: "Ubuntu Infrastructure"
date: 2011-05-23
forum: Server Platforms
---

### Post by ftornell on 2011-05-23
Hi,
I am a consultant working with Exchange Server and has been doing that for the last 6-7 years. I have always been running linux on the desktops at home and I was just wondering if/and how companies (like the french police I read somewhere) design their infrastructure.

What components are used and how? BIND for DNS? How to make that redundant?

SendMail/Postfix - Can those be clustered for high availability?

DHCP3?

Linux (Ubuntu, Fedora, Redhat, Suse? Archlinux...What ever) as a client.

Samba for fileshares?

How does it look?

---

### Post by lykwydchykyn on 2011-05-25
I'm not the most qualified to answer this question, but I have put Linux to use in a variety of tasks where I work and interacted with other Linux admins over the years.

Basically I see two approaches: build or buy.

Some people build infrastructure on Linux, and it's a mix-and-match affair.  You start with the big names, and later explore some options when you run into limitations.

The other approach is to buy big commercial packages that run on Linux (just because it's Linux doesn't mean it has to be free).  Novell, IBM, Oracle, and countless smaller companies have "enterprise grade" software that will happily run on Linux and cover the full range of infrastructural needs (identity, email, file management, backup, etc).

The biggest thing to get one's head around with Linux is that, unlike in the Microsoft universe, there isn't "THE ONE TRUE WAY" to do things (a la AD/Exchange/Office/Sharepoint/IIS/SQL Server/etc).  Instead you use the technology that works best for your situation. 

Some places have thin clients powered by something like LTSP, others have fat clients logging in via LDAP and getting home directories over NFS.  Others may do everything through the cloud.

For the components you mention:
- BIND: gets used a lot, though there are other options.  You can't go (too) wrong with bind9, though.  No idea how to make it redundant, though I'm sure the info is out there.
- Sendmail is (ought to be) deprecated.  It and postfix are pretty much low-level cogs as far as email is concerned.  If you're providing email to an organization, you want to look at a more complete solution a la zimbra, citadel, groupwise, etc.
- DHCP3 -- does what it says on the tin.  If there's more to ask from  DHCP server than what it does, I've yet to need it.
- Samba is one option.  NFS, webDAV, ssh, and many others exist.  Some situations (like thin clients or CMSes) obviate the need for a file sharing protocol.  Then of course you have commercial solutions as well.

Hope that helps.

---

### Post by Lars Noodén on 2011-05-25
If you need groupware options, then there is   [Kolab](http://www.kolab.org/),    [Citadel](http://www.citadel.org/),  [Dingo Calendar Server]( http://andrew.triumf.ca/dingo/),   [Darwin CalendarServer](http://trac.calendarserver.org/),    [Bedework](http://www.bedework.org/),   [Zimbra](http://www.zimbra.com/), or     [OpenGroupware](http://www.opengroupware.org/)
        
If you only need [mail](http://bsdly.blogspot.com/2011/02/problem-isnt-email-its-microsoft.html) then there is     [simta](http://rsug.itd.umich.edu/software/simta/),    [Dovecot](http://www.dovecot.org/),         [Postfix](http://www.postfix.org/),    [Exim](http://www.exim.org/), or     [Sendmail](http://www.sendmail.org/).  One of these will be part of the above groupware options anyway.  These can be used in multiples for failover, but are very reliable anyway.

For DHCP, I would recommend [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html).  

Samba is a good choice for file sharing.  If you're dealing with a very large number of people clustered at several different locations, then AFS might be an option.

---

