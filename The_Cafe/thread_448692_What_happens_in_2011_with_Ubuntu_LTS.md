---
title: "What happens in 2011 with Ubuntu LTS?"
date: 2007-05-19
forum: The Cafe
---

### Post by spottraining on 2007-05-19
Hi

I have one question - maybe here someone can give very simple answer.
As we all know - Ubuntu supports the 6.06 server edition until 2011. But what happens then?

Right now its possible to upgrade only to next version of Ubuntu. From 6.06 to 6.10. From 6.10 to 7.04 etc. Its mean, that in 2011 we have Ubuntu 11.04. Ubuntu 6.10 and other older are gone - no repos any more for them. No possibility to upgrade from 6.06 to 6.10 any more. Skip versions - right now its that impossible.

Ok - maybe will be then special upgrade scripts to next LTS version. But when will shipped then next LTS version? When difference between two LTS versions are to high, then its impossible to upgrade live production servers.

Some people now ask - why I am thinking so. We have still 4 years. But time moves very fast. 4 year for servers - its nothing. My Gentoo based server works now 3 years and I think I have two or three years possibility to use this server. I have also Ubuntu based small business servers - I am using Ubuntu 6.06 LTS version. But now one costumers come to me with hes server problem. And he as Red Hat 9 based webserver! And its live production server, where is hundreds of costumers. And of course he as now problems. 

Ant then I start first think about Ubuntu LTS support. What happens in 2011. Right now I have no information - how will look the Ubuntu LTS upgrade.
Maybe someone has more information and can comment my problem.

PS: Sorry about bad English - that is not my native language.

---

### Post by aysiu on 2007-05-19
The repositories won't be gone once a release has stopped getting support--it just won't get security updates any more.

As you can see, the Warty repositories still exist:
[http://archive.ubuntu.com/ubuntu/dists/warty/](http://archive.ubuntu.com/ubuntu/dists/warty/)

Of course, you do bring up a good point--would one then have to upgrade from 6.06 to 7.04 to 7.10 to 8.04 to 8.10 to 9.04 to 9.10 to 10.04 to 10.10 to 11.04? That's a lot of releases to upgrade! Maybe in four years, Ubuntu will have found a good way to upgrade straight from 6.06 to 11.04.

---

### Post by Outrunner on 2007-05-19
I've heard that Canonical will work on this issue. I think they will make it possible to upgrade from LTS to LTS version

---

### Post by matthew on 2007-05-19
> **Outrunner said:**
> I think they will make it possible to upgrade from LTS to LTS versionI have heard that this is the intent.

---

### Post by spottraining on 2007-05-19
Direct upgrade from 6.06 to 11.04 is not good idea. Then will be very big changes. Like PHP, MySQL, PostgreSQL, Perl, GCC etc. So - to many dramatic changes. Or - is with 6.06 LTS also possible to change software versions? 
Like PHP 5 to PHP 6 when PHP 5 support is ended (this is example).
How I understand - this is not possible. Like with Firefox. Ubuntu include only security upgrades - and not new versions.

And now - when we need to upgrade databases from 6.06 to 11.04 - we skip some database versions. New database server has new functionality - and its mean, that its very painful process. With PHP and Perl - many scripts stops working then. And many other problems.

So we need soon  new LTS version - what has not so many changes. But from 6.06 is soon one year and I dont have find any information - will the next Ubuntu also LTS version or not? When next LTS version coming out 2008 or 2009 - then the software versions are absolutley new and upgrade will be very hard with working servers.

Red Hat releases every year new version. So when you have RHEL 3 then you can simply upgrade to RHEL 4 and there is not so many changes.

---

### Post by maniacmusician on 2007-05-19
> **spottraining said:**
> Direct upgrade from 6.06 to 11.04 is not good idea. Then will be very big changes. Like PHP, MySQL, PostgreSQL, Perl, GCC etc. So - to many dramatic changes. Or - is with 6.06 LTS also possible to change software versions? 
Like PHP 5 to PHP 6 when PHP 5 support is ended (this is example).
How I understand - this is not possible. Like with Firefox. Ubuntu include only security upgrades - and not new versions.

And now - when we need to upgrade databases from 6.06 to 11.04 - we skip some database versions. New database server has new functionality - and its mean, that its very painful process. With PHP and Perl - many scripts stops working then. And many other problems.

So we need soon  new LTS version - what has not so many changes. But from 6.06 is soon one year and I dont have find any information - will the next Ubuntu also LTS version or not? When next LTS version coming out 2008 or 2009 - then the software versions are absolutley new and upgrade will be very hard with working servers.

Red Hat releases every year new version. So when you have RHEL 3 then you can simply upgrade to RHEL 4 and there is not so many changes.
There will be another LTS before 2011. I think the intent is to make Gutsy+1 the next LTS, which would be released at the end of this year. I suppose you could upgrade then.

---

### Post by spottraining on 2007-05-19
8.04 will be LTS?
Is there some official information also about that. 
And still - right now I am thinking - this is to big step and it will be very hard to upgrade. Of course is that easier than to 11.04 version.

Why I am thinking about this problem also - I need to recommend to this Red Hat 9 guy new operating system. I want to recommend Ubuntu (what I am using at my home server, home PC-s and my laptops)  - but I want to be sure, that is the better solution than CentOS or Gentoo. And I don't have after some years problems with upgrading.

---

### Post by bonzodog on 2007-05-19
It seems marks original plan was to release one uber-stable LTS version every two years, or every 4th release.  So, logically, following this, the next LTS will be Gutsy +1.

---

### Post by matthew on 2007-05-19
> **bonzodog said:**
> It seems marks original plan was to release one uber-stable LTS version every two years, or every 4th release.  So, logically, following this, the next LTS will be Gutsy +1.True. It's not set in stone, but that's the general plan.

---

### Post by FuturePilot on 2007-05-19
I thought Dapper was supported for 3 years on the desktop and 5 on the server. Why would there be another one before at least 3 years? Just wondering. I'll be looking forward to the next LTS:) It would be cool if you could go from Dapper straight to the next LTS.

---

### Post by matthew on 2007-05-19
> **FuturePilot said:**
> I thought Dapper was supported for 3 years on the desktop and 5 on the server. Why would there be another one before at least 3 years?
Not everyone wants to upgrade more often than that. In some instances, it is preferable to install and let the installation sit for 3 full years with only security updates, then migrate the data and do a fresh installation.

---

### Post by FuturePilot on 2007-05-19
But I mean if Gutsy +1 is supposed to be the next LTS, it will be well before the 3 year life of Dapper is done.

---

### Post by matthew on 2007-05-19
> **FuturePilot said:**
> But I mean if Gutsy +1 is supposed to be the next LTS, it will be well before the 3 year life of Dapper is done.*Other* people like to update from stable version to stable more often, every 2 years or so, to get the latest versions of software packages and so on.

---

### Post by FuturePilot on 2007-05-19
Ah, now I see. Thanks.;)

---

### Post by Liquid Punk on 2007-05-19
> **FuturePilot said:**
> I thought Dapper was supported for 3 years on the desktop and 5 on the server. Why would there be another one before at least 3 years? Just wondering. I'll be looking forward to the next LTS:) It would be cool if you could go from Dapper straight to the next LTS.

Well, RHEL2 is supported until 2009, and RHEL5 has recently been released, so Ubuntu certainly wouldn't be alone in doing this. It gives users more flexibility about when and how to upgrade.

About the original question, you could tell him to install Debian Etch, you can count on support for that for a while to come. Plus it is extremely robust and as 'Free' as humanely possible.

---

### Post by Solicitous on 2007-05-19
This is personal opinion.  I don't think there will be major issues in upgrading from 6.06 to 11.04 when it is released.  There will probably be appropriate procedures in place to make this possible.  The area that issues will more than likely arise is custom apps, php, ???sql databases etc....anything essentially added to the system after install.  However after 6 years of running on the same box, I'd personally think of either a) time to retire the machine and replace with something new.  After 6 years the old hdd are probably worn out and coming to the end of their cycle.  I know I know, there are probably people out there who have run the same server for 10 years or more, yet if I was responsible and required reliability, the minor expense in purchasing a new server would be well worth the money,  and b) the system would more than likely wind up a bit messy ie; 6 years of applying little hacks and fixes etc for short term problems.

I can understand being worried about it now, get in early to resolve the problems.  But i think by then things would have changed for Ubuntu as a distro and yourself when it comes to requirement of business and the server.

Just my 2 cents.

---

### Post by macogw on 2007-05-19
> **FuturePilot said:**
> I thought Dapper was supported for 3 years on the desktop and 5 on the server. Why would there be another one before at least 3 years? Just wondering. I'll be looking forward to the next LTS:) It would be cool if you could go from Dapper straight to the next LTS.

So you have time to upgrade...there'll be a year of time to prepare and test (sysadmins like to run their own tests before deployment) and upgrade.  If you have a lot of servers it can take a while.

---

