---
title: "bugzilla ldap authentication integration"
date: 2010-08-09
forum: Server Platforms
---

### Post by asaturn on 2010-08-09
so I got bugzilla up and running (finally) on an ubuntu server...

but in order to use the ldap integration, you need:

Mozilla::LDAP (aka PerLDAP) Perl module
Mozilla/Netscape LDAP SDK

neither of which exist in the repositories, or anywhere on the internet. the best I could find was a request to build a package from over a year ago...

I did find source that I can build... the Perl module builds and starts to begin the setup process -- but I get stuck at the point where it requires the SDK... which I cannot find anywhere in a plain downloadable form. the one I found seems incomplete:

[http://wiki.debian.org/Teams/DebianFDSPackaging](http://wiki.debian.org/Teams/DebianFDSPackaging)

wtf?

can anyone help?

---

### Post by asaturn on 2010-08-09
well installing these two packages made it work (magic?)

libnet-ldapapi-perl
libnet-ldap-perl

---

