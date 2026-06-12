---
title: "Ubuntu Default installed packages"
date: 2008-10-07
forum: Server Platforms
---

### Post by four2theizz0 on 2008-10-07
Hi,

I have ubuntu 64 installed and running Xen.  When I create an instance it installs Hardy but completely clen with no packages installed...i mena nothing, not even wget, vim, whois...etc
the stuff we jsut take for granted as being there

anywho, my problem is that I am trying to run an PHP API code suite and I am getting errors....like with a provided test page before even trying any coding.  This worked before I moived it to the xen server.  The other point is that if i install apache, php5 and the required packages for the api directly on the Parent Xen dom0, it works fine....so I have deduced this to the fact that I am missing some default packages, just wondering if there is a list of all the default packages that come installed in ubuntu hardy and I will try to see whta I am missing.

The problem has something to do with either a missing pear, xml, crypt, mcrypt, or cbc, package

I have no clue, but if i see a list of what gets installed automatically when you install from a cd versus a xen instance i will find the culprit.

Thank you

---

### Post by cdenley on 2008-10-07
> **four2theizz0 said:**
> Hi,

I have ubuntu 64 installed and running Xen.  When I create an instance it installs Hardy but completely clen with no packages installed...i mena nothing, not even wget, vim, whois...etc
the stuff we jsut take for granted as being there

anywho, my problem is that I am trying to run an PHP API code suite and I am getting errors....like with a provided test page before even trying any coding.  This worked before I moived it to the xen server.  The other point is that if i install apache, php5 and the required packages for the api directly on the Parent Xen dom0, it works fine....so I have deduced this to the fact that I am missing some default packages, just wondering if there is a list of all the default packages that come installed in ubuntu hardy and I will try to see whta I am missing.

The problem has something to do with either a missing pear, xml, crypt, mcrypt, or cbc, package

I have no clue, but if i see a list of what gets installed automatically when you install from a cd versus a xen instance i will find the culprit.

Thank you

Just take a look at the dependencies for the meta-package ubuntu-standard. You probably have ubuntu-minimal installed.

---

