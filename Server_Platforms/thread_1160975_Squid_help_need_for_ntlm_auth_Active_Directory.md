---
title: "Squid help need for ntlm_auth Active Directory"
date: 2009-05-16
forum: Server Platforms
---

### Post by CyberMick on 2009-05-16
I can use the (at commandline) ntlm_auth --helper-protocol=squid-2.5-basic --require-membership-of="MYDOMAIN\DOMAIN_GROUP"
then input: MYDOMAIN\USERNAME PASSWORD
if the user entered is a member I get OK if the user is not a member I get ERR.
This is how I assume it should work (I went through various documents to get to that point.

My question is: How do I implement the changes to squid.conf to take advantage of this?
I get a tonne of errors in cache.log with "You must specify at least one domain controller.
I'm assuming this is meant to be passed somehow because when i do this at the command line it asks me for it.

---

### Post by CyberMick on 2009-05-16
Oh My God,
After spending over a day on this (I mean I barely left my chair other than for the essentials) trying to set it up using ubuntu 9.04.

For fun (I use the term lightly), I used Centos 5.3 to try the same thing this morning. I was done after one coffee (or about 45 minutes) fully working with Single Sign On (for compatible browsers) and prompted for those who don't or aren't allowed access by my pre-defined AD Group.

I used this excellent article if anyone cares to go this way:
[http://wiki.squid-cache.org/ConfigExamples/Authenticate/NtlmCentOS5]("http://wiki.squid-cache.org/ConfigExamples/Authenticate/NtlmCentOS5")

Is something seriously broken in current version of ubuntu that causes this to be such a pain?

Either way. I'm happy to have a functional system and I get a day of my weekend, hurrah ;)

---

