---
title: "LDAP Advice"
date: 2009-06-09
forum: Server Platforms
---

### Post by dave9191 on 2009-06-09
Hi, 

I apologise if this has been posted before and I have failed to find it. A little tired and exhausted after today. 

My organisation has 20 servers and 5 developers, and each developer needs their own login that will work on each server. From what I have read LDAP is the best way to do this. Please correct me if I'm wrong. Should I be looking at something like NIS+?

I've been trying to get this working with LDAP and I have an LDAP server installed. And I think it's working. I can use ldapsearch to pull out a record from the ldap server. 

On a client machine, I have installed the LDAP client and configured it. I can use ldapsearch on the client machine to pull the record out of the ldap server too. 

But what I want to be able to do is login to that client machine using ssh with the details from the ldap server. I have followed guides to set up the config files, and pam.d. But its not working. 

I don't know how to debug the problem. Where should I start looking? Is there an issue with the login to authenticate with the ldap server? Are the details in the ldap server in the wrong format or are missing something? Does the ldap client leave any logs? 

If anyone could give me some suggestions or ideas or links to similar problems I would be very grateful. 

BTW I am using Ubuntu 8.04 LTS Server install. 

Many thanks, 

Dave

---

