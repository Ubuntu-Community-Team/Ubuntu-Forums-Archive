---
title: "Alternatives to Active Directory and Exchange"
date: 2009-08-04
forum: Server Platforms
---

### Post by nuseryame on 2009-08-04
What do companies use as alternatives to Active Directory and Exchange? what is the most popular alternative?

I know there are many alternatives as I have looked on wikipedia, but what do companies often go with, whether another proprietary like Novell and IBM Lotus Notes or open source?

Sun have an alternative too, but their website has way too much information that it overwhelms me and I just escape before I collapse of info overload.

---

### Post by epsolon77 on 2009-08-04
I am very glad you brought this up.  I have been working on this for quite some time, and just realized I don't have an answer (wish I had thought of that 2000 words earlier.)  I know there are several LDAP servers out there that work wonderfully in place of AD, but I have not found a solid Exchange replacement, that can store emails server side.  That is not to say that it is not out there, but I have not found it.  I will by watching this thread closely.

---

### Post by cdenley on 2009-08-04
I don't think there are drop-in replacements at the moment which use the same protocols as AD and exchange. Samba3 can do the old Windows domains (with or without LDAP), but not active directory. Samba4 will be a drop-in replacement for AD, as I understand, but it is still in development.

As an alternative to exchange, there are a few all-in-one e-mail and collaboration suites. I like Zimbra. I don't like Citadel. I've heard of Kolab, but never tried it. Will you use Linux or Windows clients? Does it have to work with Microsoft Outlook like Exchange does?

---

### Post by cdunbar on 2009-08-04
Hello,

We run Zimbra to provide hosted "Exchange" functionality for a number of our customers. I am upfront with them about not actually running Exchange, but (1) they can't tell the difference and (2) they are only concerned with how Outlook functions. Since Outlook functions very well they are very pleased. Zimbra uses Open LDAP to manage the user accounts. I have not tried to tap into it for authenticating other types of access (e.g. files), but it should work. You should be able to run Zimbea on ubuntu.

Apple's OS X Server product also provides a nice alternative to AD and has a reasonably nice set of GUI tools for administration. The new enhancements coming in Snow Leopard (version 10.6) should make a compelling alternative to Exchange. Specifically I am thinking about the new or updated iCal Server, Wiki Server, and Address Book server.

Regards,
Chris

---

### Post by sixstorm on 2009-08-04
I will definitely keep an eye on this thread, I'm very curious as to the "Linux alternatives" to Exchange and AD, as I am starting my Microsoft training in the next month!  (Taking my CCENT this week, 1 milestone at a time).

---

### Post by zoomy942 on 2009-08-05
> **sixstorm said:**
> I will definitely keep an eye on this thread, I'm very curious as to the "Linux alternatives" to Exchange and AD, as I am starting my Microsoft training in the next month!  (Taking my CCENT this week, 1 milestone at a time).


Count me in as well

---

### Post by mcarrara on 2009-08-05
I was hoping to implement LDAP this summer, but it ain't going to happen.  Maybe this winter.  I have heard a lot of good things about Kerio as an exchange replacement.  It is on my todo list for this fall

Mark

---

### Post by shredkingj on 2009-08-05
From what I've seen, Zimbra and Kerios give you a good alternative to Exchange, and they are based on open source software.  The licensing/support costs and features are very good.  The AD replacement is the tricky part.  Samba3 emulates NT4 domains, but that is outdated technology, only a good idea for smallish networks in my opinion.  Samba4 has been in development for a long time, and may be outdated when it's finally stable.  There is no way for Samba3 to integrate fully with Kerberos, and even the limited integration just gives you GSSAPI, which hardly any Windows apps use.  Please don't take this as me slamming Samba, because it's a good tool that has its place, but it has its limitations.

Having said all this, once you get past Microsoft's business practices and their licensing, AD is actually one of their best products.  Microsoft's also done a very good job of making it difficult to manage a large number of Windows clients without AD.

---

### Post by windependence on 2009-08-06
+1 for Zimbra. Most of our implementations are the OSS version of Zimbra but even the paid version is good value for the money compared to Exchange, and it even has a migration tool.

-Tim

---

### Post by HermanAB on 2009-08-06
Samba domain server and Citadel or Zimbra for groupware.

---

### Post by bmathis on 2009-08-07
+1 for Zimbra. 

I have Zimbra setup with 10+ non-profits that I do work for. For an Active Directory replacement, I use eBox Platform which also has a beta client to authenticate Ubuntu clients to it.

I believe there are a few howto's out on the web that will show you how to integrate the two together, you'd just have to do a search for it or visit their forums.

---

### Post by epsolon77 on 2009-08-18
This may not be quite what your looking for, but in playing around with Citadel, as a previous post had suggested, it seems to integrate well with active directory.  I did not have a full live system to truly test against, but from what I could test it did a very fair job.  I know this doesn't help the Active Directory replacement.

---

### Post by burchakoff on 2009-08-20
And what about Group Policy Objects? Is it possible to manage domain users  using ubuntu?

---

### Post by koenn on 2009-08-20
> **burchakoff said:**
> And what about Group Policy Objects? Is it possible to manage domain users  using ubuntu?

not really. maybe. sort of. 

you might want to read this thread : [http://ubuntuforums.org/showthread.php?p=7727750](http://ubuntuforums.org/showthread.php?p=7727750)

---

### Post by midair77 on 2009-10-14
Please take a look at Zarafa as it so much easier to configure and maintain in comparison to Zimbra/OpenExchange.  

I have Zarafa in productions at 2 different companies and I am very happy with everything.  I user both Professional and Community version and both are solid.

Zarafa might not have all the bells and whistles like those of Zimbra but they are getting there.  Their updates are stable and easy to perform.  

Zarafa works with openldap and a bunch of ldap directories.

Just my 2 cents.

---

