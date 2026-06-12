---
title: "Web Proxy with user names in mixed environment"
date: 2012-09-13
forum: Security
---

### Post by vidkun on 2012-09-13
First, I will describe the lab environment I have setup for testing
this. I have a Server 2008 R2 DC, a Server 2008 R2 for Cyblock/Cyfin
products, a Windows VM joined to this test domain, a MacBook Pro
running OS X Lion that is NOT joined to any directory services, a
Linux box that is NOT joined to any domain, a Windows box NOT joined
to a domain, and a Squid Proxy server running on a Linux box. This is
fairly representative of the production environment that this would be
deployed in as we have many Windows, Linux, and OS X machines on a
network with a mix of them in an AD domain, other LDAP directory
services, OpenDirectory services, and not on any central
authentication/directory services.

Second, I will describe the ultimate goal. We need to be able to, upon
request, generate a list of all web requests by a specified user name
for a given period of time. This should be accomplished with minimal
administrative overhead (i.e. not by manually configuring proxy
settings on each individual client's browser(s) ) and minimal user interaction (i.e. not having to enter credentials every time they try to load a web page).

I have been testing out some various configurations with  Squid, Websense, and CyBlock, but haven't had too much luck accomplishing this. It seems that this would be rather simple and easy if we had nothing but Windows boxes in an AD environment, but we don't. The environment is very diverse at the moment and for the foreseeable future.

Do any of you have any additional ideas/suggestions on how to best accomplish this? I'm interested in your thoughts either way.

Thanks.

---

