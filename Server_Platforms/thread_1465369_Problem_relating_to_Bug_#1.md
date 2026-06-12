---
title: "Problem relating to Bug #1"
date: 2010-04-29
forum: Server Platforms
---

### Post by Aquaseafoam on 2010-04-29
[The Bug in question.]("https://bugs.launchpad.net/ubuntu/+bug/1")

So, I have, after climbing the IT Hierarchy for the past 5 years, ended up as Network administrator for my company. About 3 years ago, I started playing with Ubuntu, merely as a hobby at first. Now, there isn't a computer I own without it. I then took the next logical leap, servers. With the permission of our CIO, began investigating the use of Ubuntu within my corporation.

Thanks to likewise, myself and a like-minded webadmin now use Ubuntu Desktops at work. However, I'm looking to the future, Linux on every desktop and every server.

But first I need to break Microsoft's stranglehold on my server room. What I'm looking for is clean upgrade paths away from Microsoft products. Things that can be dropped in with as little downtime as possible. So, here's my situation:

The network is a mish-mash of mostly XP, some Windows 7 and 2k, with a few legacy NT machines here and there. We have close to 200 users + machines internally with about 20 remote users. We have 12 Windows Servers, which are Server 2003 R2, save for one 2k server soon to be phased out. We currently have 4 Ubuntu servers mixed in with them, two web servers, a file server, and a Nagios server.

Domain Controllers:
We have two Server 2003 AD Domain controllers. These, I believe should be the first to go. I've been eyeing [389 Directory server]("http://directory.fedoraproject.org/") as a replacement, though this is not set in stone. The ability to replicate over the Accounts and information is definitely a plus. A gui of some form is also important. However, my big problem then becomes my windows clients. I've heard that samba can be used for this, but I'm sceptical about security and stability.

E-mail:
This is the one I am stumbling over most, I have no idea what to replace our exchange 2003 server with. Also, relating to the Domain Controllers entry, I'm wondering if exchange can authenticate to a 389/Samba combo. If so, the switch could be done gradually and cleanly.

Web Servers:
DONE! We no longer have any IIS servers, all ours are now Apache/Ubuntu servers.

File Servers:
We already have one Ubuntu File server (Using Likewise) in place, but there is still one server 2003 file server. My only question here is, how reliable is a file server if there are windows clients authenticating via samba?

Other Servers:
All our other servers will fall into place very easily once the above three hurdles are conquered. There are a few Oracle servers and some odd servers here and there, largely unimportant. 

I'm looking for the advice of anyone who has gone through such a migration. What you used, what you tried, what worked, what didn't work.

---

### Post by CharlesA on 2010-04-29
I don't think there is anything that equals AD in the Linux world. I know of LDAP servers, but I don't think they have the same options and scalibility as AD.

Just my 0.02 cents.

---

### Post by koenn on 2010-04-29
> **CharlesA said:**
> I don't think there is anything that equals AD in the Linux world. I know of LDAP servers, but I don't think they have the same options and scalibility as AD.

Just my 0.02 cents.
It's not really 'options and scalability'.
AD is built out of Kerberos and LDAP, but has added quite a bit af functionality on top of that, mainly geared towards remote administration of and software distribution to windows desktop clients. But it's all tighly integrated, and the kerberos and ldap implementation isn't copmpletely following standard protocol. That makes it extremely hard to replace. As intended, no doubt.

---

### Post by cdenley on 2010-04-29
I believe samba4 is supposed to implement AD features, but I don't think it is production-ready yet. For exchange, Zimbra Network Edition (not free) isn't quite a drop-in replacement for Exchange, but it is as close as you will get. It has an Outlook connector so you get all the Exchange functionality with contacts and calendars, and it supports activesync for mobile devices.

---

### Post by koenn on 2010-04-29
@Aquaseafoam  

If this was my problem, I'd probably reverse the order, and tackle the DCs last.
Web and file servers are easy, and the can co-exist with windows servers and integrate into an AD domain. 

Exchange is so integrated into AD that I doubt you can get rid of your DCs without getting rid of Exchange at the same time. And even if you can, it's probably not a supported configuration so if you ever run into trouble, you're on your own.

I'd try to get rid of Exchange first, eg replace it with something that can do mail, calendars, etc (Zimbra ? Zarafa  ? Lotus Domino ? [http://www.linuxlinks.com/article/20090921133533625/Groupware.html](http://www.linuxlinks.com/article/20090921133533625/Groupware.html) ...)

Then see if you have alternatives for AD functionality such as GPO and the likes, then get rid of the DCs - or just keep them, AD is pretty useful for managing windows desktops, maybe you'll want to get rid of those first :) )

---

### Post by koenn on 2010-04-29
> **cdenley said:**
> For exchange, Zimbra Network Edition (not free) isn't quite a drop-in replacement for Exchange, but it is as close as you will get. 
Zarafa, on the other hand, is deliberately marketed as an Exchange replacement, and development aims to match it feature for feature (including Outlook compatibility + all sorts of proprietary mobile devices)
 [http://www.zarafa.com/content/benefits](http://www.zarafa.com/content/benefits)



It's not as well known as Zimbra, although it has quite some following and corporate support in western europe.

---

### Post by terazen on 2010-04-29
I don't think there is a good replacement for AD/Exchange/Outlook yet.

What functionality of email and AD are you looking to use in your new network solution?

---

### Post by Aquaseafoam on 2010-04-29
We only really use the basic functionality of AD, Authenticating users. There are a couple of Group policy changes we've made, but nothing we couldn't live without if it meant never having to pay for Microsoft again.

I'll give Zimbra and Zarafa a look. If AD/Exchange is ties as closely as you say, then it probably is best to do the DCs last. We can work with them fairly well using likewise. But what I'm concerned about is passwords. Specifically how my users are awful at remembering them (I think we've been too nice to them). Single Sign-on is important to us.

A 389 Ldap server can sync back and forth between AD, so it may be worthwhile to keep at least one on hand for some time.

---

### Post by P4man on 2010-04-29
Not an answer to your question, but I really think you should reconsider your approach. Your goal (at this point) should not be to replace windows with ubuntu, it should be find out what product mix best matches your organization's needs.

If that turns out to be ubuntu desktops and/or servers then great! but trying to force a conversion  just because you are ah.. well, "ubuntu fanboy" (dont take that as an insult, I am one too), is not gonna help your career, nor your organization, nor your end users. Its not even gonna help ubuntu, because a bad conversion is going to do a whole lot more harm to ubuntu than no conversion. End users dont like change, if you are gong to take away their windows and outlook, you  better make really sure they get something in return that works better for **them.**

/end rant.

---

### Post by Aquaseafoam on 2010-04-29
I am excited about switching our servers to Ubuntu, because I am, as you pointed out, an Ubuntu fanboy.

But that is not why we are doing it. That is not why our executives wish to do it, and it is not why it is good for our users.

We want Ubuntu, because the cost of being a Microsoft shop in these economic times is simply too high. I've seen the size of this department dwindle due to budgetary reasons, I've seen our budget for purchasing vitally needed new servers dwindle. Every time a microsoft server fails around here, it is an emergency. We haven't been able to justify the price of the Hardware + Software for some time now. Our users have started to notice that.

We want our users to be unaware that any change has been made whatsoever. No user right now has any idea that our web servers are not running on Windows. They are happy that way. What they may have noticed is, our Web sites are not down nearly as often as they once were. For free, we are able to run a cutting edge webserver, backed by a cutting edge OS. Had we stuck with Microsoft, it would have been a insecure 7 year old web server on a buggy 7 year old OS, and I'd still be trying to plead my case as to why we need to spend the money to upgrade. (There is a serious problem of "But it still works" around here.)

I want every one of our servers to be like that.

That is merely the most prominent example why we want Linux.

I could continue on listing all the reasons as far as security, malware resistance, and the like goes. But I think you get the gist of it.

---

