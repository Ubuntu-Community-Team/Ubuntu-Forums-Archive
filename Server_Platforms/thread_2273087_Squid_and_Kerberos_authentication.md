---
title: "Squid and Kerberos authentication"
date: 2015-04-10
forum: Server Platforms
---

### Post by jelockwood on 2015-04-10
I am in the process of building a Squid Proxy Server running under Ubuntu Server, having done this before although with a different desired end configuration I feel confident in getting Squid working, however this time I would like to setup Squid to use Kerberos authentication - previously I just used LDAP which did work.

The wrinkle here is that all the examples I have seen are based on using Kerberos Authentication to link to an Active Directory system either a real one or a SAMBA4 based one. In my case I want to link to Apple's Open Directory system which does also act as a full-blown Kerberos server.

So far I have got as far as building the Ubuntu Server, installing Squid and relevant tools and more relevantly the krb5-user software. I have been able to configure the Kerberos client and use kinit to successfully request a Kerberos ticket as then proven by running klist. So it would seem I have the basics of successfully configuring Ubuntu to talk to my Open Directory server.

As mentioned all the examples for configuring Squid are based on talking to AD so I am hoping someone can give me some pointers on how to adapt that approach to instead talk to Apple's OD. It would seem the next step is to generate a keytab file and this is where the examples I have seen stray in to talking about Active Directory.

Any suggestions from anyone?

---

