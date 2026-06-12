---
title: "blocking china"
date: 2009-01-14
forum: Security
---

### Post by Cr0n_J0b on 2009-01-14
I have a ubuntu server on the internet that I use for some pretty basic stuff.  Really just ssh, ftp and a very little www.  I use guarddog to setup my iptables firewall rules and that seems to work pretty well.  What I'm looking to add is a global block to all of several countries including china and india.  I know where to get the top level subnets for the countries that I want to block, but I'm struggling with effecting the change on my system.

I tried setting up a new zone called china with a simple subnet:

201.232.0.0/255.255.0.0

then i blocked every port explictly...which was a bit of a pain.  The only problem is that it didn't stop the attack, which was going on at the time.  I think I'm probably doing something wrong.

any suggestions would be appreciated.

---

### Post by HermanAB on 2009-01-15
I guess you are troubled by brute forcers.  They can be stopped very easily with a one liner in /etc/rc.d/rc.local:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit 
--limit 30/minute --limit -burst 5 -j ACCEPT

The above will make any and all brute force attacks infeasible, so they will go away and leave you alone.

Cheers,

Herman

---

### Post by hyper_ch on 2009-01-15
or you could use denyhosts or fail2ban instead

---

### Post by Cr0n_J0b on 2009-01-18
Thanks for the response.

What I will try the scripts that you suggested...but I'm also wondering if there is a simple way to just block out the entire subnet for these countries.

---

### Post by uljanow on 2009-01-18
> **Cr0n_J0b said:**
> Thanks for the response.

What I will try the scripts that you suggested...but I'm also wondering if there is a simple way to just block out the entire subnet for these countries.

You could try [ipblock]("http://iplist.sourceforge.net/") which comes with 28 pre-build country lists.

---

### Post by Cr0n_J0b on 2009-01-19
thanks,

this looks about rought.  I'll try it out and report back.

---

### Post by ferd on 2009-01-20
I have the same problem but I cannot find the rc.d file on my computer. I am using Hardy Heron and I have tried using gedit with no success. I have tried changing my password for gmail and correcting the changes the China attack makes to gmail with no success. All help much appreciated. This is the first time in my 5 years with Linux that I have been successfully attacked.

---

### Post by cariboo on 2009-01-20
In debian based distributions rcX.d is always located in /etc you are looking for rc0.d to rc6.d and rcS.d

Jim

---

### Post by ferd on 2009-01-20
Thankyou Caribo0907 but I am over my head here, so I will stop now and switch  to Yahoomail.

---

