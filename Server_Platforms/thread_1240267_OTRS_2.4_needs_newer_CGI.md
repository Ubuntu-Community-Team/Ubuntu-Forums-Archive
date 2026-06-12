---
title: "OTRS 2.4 needs newer CGI"
date: 2009-08-14
forum: Server Platforms
---

### Post by sagyvolkov on 2009-08-14
Hi,

Running 9.04, trying to install OTRS from source (since I think the Ubuntu package is only 2.2), there's a script that checks Perl module existence, one of the "fails" I get with it is:
CGI............................failed!!! Version 3.29 installed but 3.33 or higher is required!

I've tried to install CGI through MCPAN but failed.
now I'm trying to find what package exactly is the CGI/Perl in Ubuntu, so I can remove it.

Anyone?

Thanks.

---

### Post by alastair on 2009-08-14
Searching, brings me to 2 possible packages :

libcgi-pm-perl - Simple Common Gateway Interface Class
perl-modules - Core Perl modules

Looking at "libcgi-pm-perl" (apt-cache show) tells me :

"CGI.pm is included in core perl-modules. Use libcgi-pm-perl only for special
 updates like the use of POSTDATA."

The version of "libcgi-pm-perl" available to me is 3.42-1 - I am running 8.10.

So maybe all you need is "libcgi-pm-perl".

---

### Post by ponsfrilus on 2009-09-01
@sagyvolkov what have you done finally?


EDIT: ok get it with a 

> sudo cpan CGI

with FCGI as prerequisite

---

