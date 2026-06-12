---
title: "Questions about Linux hosted Windows Domain"
date: 2011-06-24
forum: Server Platforms
---

### Post by Jake.Debord on 2011-06-24
I would like to know what is the best way to turn Ubuntu server into a functioning Domain Controller for a small-mid range network. I have used Active directory in the past but would like to experiment with using Linux. I need to be able to force users to login on their machines to my domain and the ability to push group policies would be a huge plus.

Any suggestions, comments, dos & don'ts are all very much welcomed.

TIA

---

### Post by Dangertux on 2011-06-24
I find this makes a great reference when configuring LDAP on Linux. It should have most of the info you're looking for.

[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)

---

### Post by Jake.Debord on 2011-06-24
Are they any other options out there? OpenLdap seems like more trouble than its worth unless there is something I'm missing about it...

---

### Post by CharlesA on 2011-06-24
LDAP is one way, bit of a pain from what I've heard (and I haven't been able to successfully set it up)

The other is using Samba 4 which has features similar to AD, but still in the alpha stages.

IMHO just stick with Windows AD.

---

### Post by Jake.Debord on 2011-06-24
Well, I would but I'm with a new company and budgets aren't allowing much for AD... I've been looking at Samba 4 and it looks promising... I just need a way to push out group policies though and it would be just fine. Another plus is mapping home directories to the server, which I don't THINK will be too much of a hassle with samba but may not be fun to setup.

---

### Post by CharlesA on 2011-06-24
I haven't tried much with Samba outside of just sharing via local users, so I'm not sure how easy/hard it would be to set up centralized authentication.

Good luck if you go with Samba 4. :)

---

### Post by capscrew on 2011-06-24
> **Jake.Debord said:**
> Well, I would but I'm with a new company and budgets aren't allowing much for AD... I've been looking at Samba 4 and it looks promising... I just need a way to push out group policies though and it would be just fine. Another plus is mapping home directories to the server, which I don't THINK will be too much of a hassle with samba but may not be fun to setup.

Windows AD is an implementation of LDAP, DNS and Kerberos and Scripts to modify the registry (Group Policies).

That is a lot to chew on if you are a small company.  You could end up spending more time ($$$$) and end up failing.  It has more expense than it is worth.

Buy the license and move on.  The alternatives are [**_Novell NDS_**]("http://www.novell.com/products/edirectory/") and  [URL="http://directory.fedoraproject.org/"][B][U]Fedora 398 Directory server
[/U][/B][/URL].  Both have limitations.  Novel is very expensive and 389 is incomplete.  Windows AD is cheap and it works!  As you can see I am no Linux or even FOSS zealot.  The right tool for the specific job is how I see it.

---

### Post by HermanAB on 2011-06-25
Howdy,

Samba can do a Windows 2000 style Active Directory domain very successfully and for most applications, that is all you need.

Otherwise get a Windows Small Business Server CD and install it as a virtual machine on a Linux host.   That way, it is easy to install and easy to backup - just copy the whole VM to a DVD - and when it screws up (yes, it will sooner or later), you restore it from the DVD.

---

### Post by bab1 on 2011-06-25
> **HermanAB said:**
> Howdy,

Samba can do a Windows 2000 style Active Directory domain very successfully and for most applications, that is all you need.

Can you explain a little more?  I always thought Samba 3 could only handle old NT4 PDC domains.  There is no built in LDAP in Samba 3 as there is in Samba 4.  Samba 4 is Alpha software at this point; right?  Not what you would want to use in a business situation.

---

### Post by doas777 on 2011-06-25
> **capscrew said:**
> Windows AD is an implementation of LDAP, DNS and Kerberos and Scripts to modify the registry (Group Policies).

That is a lot to chew on if you are a small company.  You could end up spending more time ($$$$) and end up failing.  It has more expense than it is worth.

Buy the license and move on.  The alternatives are [**_Novell NDS_**]("http://www.novell.com/products/edirectory/") and  [URL="http://directory.fedoraproject.org/"][B][U]Fedora 398 Directory server
[/U][/B][/URL].  Both have limitations.  Novel is very expensive and 389 is incomplete.  Windows AD is cheap and it works!  As you can see I am no Linux or even FOSS zealot.  The right tool for the specific job is how I see it.

+1. 
of course this depends on whether you need just an unified accounts database, or if you need kreberos, ddns integration, and group policy. if you need the whole package, buy rather than build, or hire a guy who says this is easy in linux.

---

### Post by bab1 on 2011-06-26
Oops! Replied to the wrong thing.

---

### Post by HermanAB on 2011-06-26
Here you are:

[http://www.oregontechsupport.com/samba/](http://www.oregontechsupport.com/samba/)

[http://www.oregontechsupport.com/samba/domain-controller.php](http://www.oregontechsupport.com/samba/domain-controller.php)

---

### Post by bab1 on 2011-06-26
> **HermanAB said:**
> Here you are:

[http://www.oregontechsupport.com/samba/](http://www.oregontechsupport.com/samba/)

[http://www.oregontechsupport.com/samba/domain-controller.php](http://www.oregontechsupport.com/samba/domain-controller.php)

I've read these before.  The links show how set up an old style NT4 PDC Windows domain.  No LDAP, DDNS, Kerberos or GPO's.  I believe the OP was looking for those features in a FOSS setting.  I think doas777 and capscrew or more to the point.  

Thanks anyway.

---

