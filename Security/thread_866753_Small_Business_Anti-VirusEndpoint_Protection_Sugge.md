---
title: "Small Business Anti-Virus/Endpoint Protection Suggestions"
date: 2008-07-22
forum: Security
---

### Post by Cjmovie on 2008-07-22
Hey,

I was wondering if anyone had recommendations on a software package to use in a business environment for endpoint security (similar to what McAfee and Symantec provide)... except deployable on an Ubuntu server? It needs to have at least virus and firewall protection and some sort of central management console. All the major ones seem to only support Windows Server, or at best, Netware... I've found some posts on the forums getting Netware versions of Symantec Endpoint onto Ubuntu but none have been conclusive in getting it to work.

Our network has two Linux-based servers and about 20 windows computers. Neither of the servers are an internet gateway.

It would also be nice if it provided some form of anti-spam as the email is based off of one of the linux servers, but if not I can always install an alternate program for that.

The best I've thought up so far is to run a virtual windows server on one of the machines and get the cheapest license possible for it... What do you think?

Thanks!

*edit*
Oh, and I forgot to mention. Something that has a paid route is preferable... Being a business environment, 24/7 support and someone to blame is important.

---

### Post by hyper_ch on 2008-07-22
I still don't get what you actually want to do...

---

### Post by brian_p on 2008-07-22
> **Cjmovie said:**
> Hey,

I was wondering if anyone had recommendations on a software package to use in a business environment for endpoint security (similar to what McAfee and Symantec provide)... except deployable on an Ubuntu server? It needs to have at least virus and firewall protection and some sort of central management console.

You could see what

[http://www.untangle.com](http://www.untangle.com)

has to offer you.

---

### Post by AndyCee on 2008-07-22
> **Cjmovie said:**
> Hey,

I was wondering if anyone had recommendations on a software package to use in a business environment for endpoint security (similar to what McAfee and Symantec provide)... except deployable on an Ubuntu server? It needs to have at least virus and firewall protection and some sort of central management console. All the major ones seem to only support Windows Server, or at best, Netware... I've found some posts on the forums getting Netware versions of Symantec Endpoint onto Ubuntu but none have been conclusive in getting it to work.

Our network has two Linux-based servers and about 20 windows computers. Neither of the servers are an internet gateway.

It would also be nice if it provided some form of anti-spam as the email is based off of one of the linux servers, but if not I can always install an alternate program for that.

The best I've thought up so far is to run a virtual windows server on one of the machines and get the cheapest license possible for it... What do you think?

Thanks!

*edit*
Oh, and I forgot to mention. Something that has a paid route is preferable... Being a business environment, 24/7 support and someone to blame is important.

I can't speak from an enterprise point of view, but there are many different enterprise security apps for linux. I'm not sure of any one that does everything, or with a "central management console" though.

clamav, EMP6 and ufw, for example, but this isn't centralised enough is it?

---

