---
title: "User profiles w/Samba"
date: 2009-09-28
forum: Server Platforms
---

### Post by jahservant on 2009-09-28
Does anyone have any good resources for configuring Ubuntu Server as a Domain Controller with user profiles??

What I need is for users on Windows machines to log in to a domain that is controlled by an ubuntu server, and to have their "My Documents" and Desktop folders stored on the server.  And, if possible, to "push out" revisions of software when the user logs in (for example, force users to upgrade to a new version of Firefox, to install a new security program, etc.).

I believe this is possible (perhaps with Samba?)

Any good resources or advice would be appreciated!

---

### Post by openfly on 2009-09-28
You can have what is called "Roaming Profiles" on samba.  That stores their user profile on the server side and pushes them out.  Just be aware you will probably want to set some pretty strict quotas on what is stored in there.  If someone decides to put their mp3 collection and a couple of DVDs on their desktop.. next time they login at a machine that isn't their usual one it'll need to pull the umpteen gig profile before it can successfully login.

This is also where you'll probably want gigabit throughput.  

As for software updates... you'll want to use the freely available software update server that microsoft provides.

---

### Post by doas777 on 2009-09-28
roaming profiles have never worked reliably enough for my needs on any platform, once the user base got to be more than 10 or 12.

what is teh *nix approach for centralized authentication anyway? I can't believe I;ve hung arround here this long and don't know.

---

### Post by openfly on 2009-09-28
> **doas777 said:**
> roaming profiles have never worked reliably enough for my needs on any platform, once the user base got to be more than 10 or 12.

what is teh *nix approach for centralized authentication anyway? I can't believe I;ve hung arround here this long and don't know.

Kerberos + NIS/LDAP + NFS / OpenAFS

Sun One...

---

### Post by doas777 on 2009-09-28
> **openfly said:**
> Kerberos + NIS/LDAP + NFS / OpenAFS

Sun One...

thank you!

---

### Post by whoop on 2009-11-07
Complete tutorial (written for 7.10, works with 8.04):
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

Documentation on this topic needs to be updated, please **vote**:
[http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)

---

