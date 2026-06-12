---
title: "MS SBS Replacement"
date: 2008-06-06
forum: Server Platforms
---

### Post by RTucker on 2008-06-06
I know this question gets asked alot, but I haven't been able to find a decent answer anywhere.
 
I work for a company that provides IT services to small businesses. These businesses usually have a Windows Smal Business Server being used as a PDC and for Exchange, occasionally MS SQL and as an internet gateway/proxy.
 
I'm looking at replaceing SBS with some kind of linux, and if possible I'd like to go with ubuntu (as its the one I have the most experience with), possibly with ebox or the like. I need to make sure that a linux server will provide the functionallity of SBS that is needed.
 
As far as I know, the gateway/proxy side of it is fine (some clients have a separate debian server for this already), so what I'm most concerned with is the PDC, Mail/Calendar/etc. and SQL abilities of ubuntu server.
 
This really needs to be an almost drop in replacement for SBS.
 
As far as Exchange goes, the workstations need to use outlook. I think they'll be happy with IMAP if there is no way to use MAPI, though I'd like to confirm that shared calendering, etc. will still be avaliable in outlook. Also, some of them tend to have fairly large mailboxes (up to 2GB) so I'm not sure how that would go over IMAP. In the end I really would prefer a solution where the emails are stored and accessed from the server as with exchange.
 
Any and All help/suggestions/advice is greatly appreciated.

---

### Post by archmage258 on 2008-06-06
I am not sure how well this works on Ubuntu, but some of my co-workers have used a version of [this]("http://www.open-xchange.com/header/home.html") product as a replacement for MS Exchange.  So far they got it to work on CentOS as part of an open source server/desktop solution.  I would assume that it works just fine given it advertises compatibility :)  Hope this helps

---

### Post by JonRohan on 2008-06-06
I don't think you will find a "drop in replacement" for MS SBS2003. MS have developed SBS as an all in one next next finish style install with all the software needed for a small business. As most people will be using XP / Vista / Outlook it is always going to be an uphill struggle to have seamless compatability with Linux and XP PC's etc. It is possible but why create a load of extra work for yourself?

---

### Post by freebeer on 2008-06-06
I can only offer a bit of the puzzle from my experience.  I'm running Ubuntu as a PDC, but in my case, I don't have any need for Active Directory stuff, so it works just fine.  I don't know the current state of Samba with regards to AD, so if you need that, you'll need to do a bit more research.

I'm quite happy with the Ubuntu PDC.  It takes almost no maintenance (this from a guy who likes to tweak stuff).  I've never had to take it off line or have it crash, unlike the 2003 server that I also have (it's only a server for an accounting app).

I really can't help with the outlook/mail issue as I haven't run into it.

SQL *should* be ok, but if you're running apps that require a specific version of SQL, such as MS's, you might be out of luck.

Hope that helps, some.

---

### Post by HermanAB on 2010-01-16
Hmm, It is sacriledge suggesting another distro, but Mandriva Linux Small Business Server plus Citadel for email is probably the easiest solution.  The mandriva SBS includes tools for LDAP so you can replace an Active Directory domain system.

---

