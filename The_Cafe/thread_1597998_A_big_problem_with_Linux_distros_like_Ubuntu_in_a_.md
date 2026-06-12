---
title: "A big problem with Linux distros like Ubuntu in a business or government setting"
date: 2010-10-16
forum: The Cafe
---

### Post by .Michael on 2010-10-16
That problem is lack of the ability to authenticate users over a network so that all the systems in a building will have the same login names. (login isn't a word, Firefox?) 

Ways to solve it:

Solution 1:
> 
Run one windows server computer with an active directory installation and let the Linux clients authenticate off that. Face it- ~$500ish isn't much if you run a business and need it, while your workstation operating systems are free.


Solution 2:
> 
Run a cronjob on all the client computers to download a custom shadow and passwd file every 10 or so minutes. This would work up to ~500 users, the this would start to become sluggish or you would have to increase the propagation delay. "passwd" would have to redirect to a custom program which would update the server file.


Solution 3:
> Keep giving Bill Gates ALL your money (as opposed to some of it as in the case of solution 1.

This is not a problem I have, it is just something I wonder.

---

### Post by SeijiSensei on 2010-10-16
> **.Michael said:**
> That problem is lack of the ability to authenticate users over a network so that all the systems in a building will have the same login names.

Guess you've never heard of  [NIS]("http://en.wikipedia.org/wiki/Network_Information_Service"), [LDAP]("http://en.wikipedia.org/wiki/Ldap"), or [Kerberos]("http://en.wikipedia.org/wiki/Kerberos_%28protocol%29")?

[Active Directory]("http://en.wikipedia.org/wiki/Active_Directory") is a Microsoft implementation that relies on LDAP and Kerberos plus proprietary extensions.

Did you really think there were no large-scale *nix infrastructures in the commercial world?  Lots of high-tech companies relied on NIS and NFS for decades to manage fleets of Unix workstations from manufacturers like Sun and Silicon Graphics.

---

### Post by Khakilang on 2010-10-16
I thought Bill Gates has retired and giving away his money!

---

### Post by Megaptera on 2010-10-16
Well, some 50 places inc. US Dept. of Defense seem to have managed to overcome the "problem" that .Michael worries about.
This:
"Governments at all levels (national, state, federal and international) have opted to deploy Linux across their computer systems for a host of reasons. Some are purely technological, with the governments in question preferring the open-source benefits of the OS. Others are financial, as Linux is typically far less expensive than buying a license for Windows. Still others are political, as organizations like the World Trade Organization have actively pressured governments to shun Microsoft products. In any case, here are some of the governing bodies that now run Linux on their computers."

From here: [http://www.focus.com/fyi/information-technology/50-places-linux-running-you-might-not-expect/](http://www.focus.com/fyi/information-technology/50-places-linux-running-you-might-not-expect/)

---

### Post by HermanAB on 2010-10-16
Howdy,

Yes, I can understand that it is a problem with Ubuntu.  Ubuntu is aimed at home users.

The solution is to use Redhat, Suse or Mandriva.  They created Active Directory and LDAP wizards many years ago already.

So, you got to use the right tool for the job.

---

### Post by kio_http on 2010-10-16
> **HermanAB said:**
> Howdy,

Yes, I can understand that it is a problem with Ubuntu.  Ubuntu is aimed at home users.

The solution is to use Redhat, Suse or Mandriva.  They created Active Directory and LDAP wizards many years ago already.

So, you got to use the right tool for the job.

Ubuntu Server Edition???:confused:

---

### Post by HermanAB on 2010-10-16
Ubuntu server doesn't have decent wizards.  No, Webmin is not a decent wizard.

I use Ubuntu for fun at home and Suse, Redhat, CentOS or Mandriva at work, since at work, time=money, so Yast and MCC saves us $$$,$$$,$$$.

---

### Post by serafim on 2010-10-16
> **HermanAB said:**
> Ubuntu server doesn't have decent wizards.  No, Webmin is not a decent wizard.

I use Ubuntu for fun at home and Suse, Redhat, CentOS or Mandriva at work, since at work, time=money, so Yast and MCC saves us $$$,$$$,$$$.

At my job we use Ubuntu for employees and clients + Ubuntu server ed. for servers. We do have a couple of Solaris servers too, but mainly it's ubuntu linux. One server is hosting the AFS daemon and all the other computers are running as AFS clients. Everyone uses the same login name and password regardless of which computer they use for the moment and everything is running smoothly. Global update strategies, one for the servers and one for the desktops + local update schemes for every local computer.

Local strategies include specific installation issues like what not to update automatically at that computer and what to update that is not covered by the global strategy (if someone has specific needs, special software et.c.)

We also have a small number of MacOSX machines running, but they never constituted a problem after the upgrade to OSX.

So, don't say it's only for fun. With us computers and servers run Ubuntu successfully and, because of the global/local schemes at a minimum cost compared to the same  solution that earlier ran a mixed Solaris / a variety of Linux flavors / Mac OS / Different windows flavors.

---

### Post by TNT1 on 2010-10-16
I am the only Ubuntu/Linux user at my company. I simply told the IT people, with the blessing of the CEO, that I will not be logging onto the domain. (I guess the CEO likes me, or I am valuable to the company or something, cause I told him if they tried to put windows on my machine, I'd leave.)

---

