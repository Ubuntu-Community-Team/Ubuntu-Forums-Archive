---
title: "Aptitude update"
date: 2009-04-23
forum: Server Platforms
---

### Post by hamood on 2009-04-23
Hi,

 iam using ubuntu 8.04 LTS.
everything was working fine.
since last week i have problem with command "aptitude update".

when i run it it shows:
0% [waiting for headers] and gets stuck

when i run synptic package manager i can do install, remove or 
refresh.

it seems the teminal commnad is not working.internet is working fine.

why?

please help. thanks

---

### Post by yeats on 2009-04-23
Assuming your network connection is sound, it might be a repository that is entered incorrectly or is just down for maintenance (I've noticed this happen with the wine repositories from time to time).  You can look at /etc/apt/sources.list to make sure all looks well....

---

### Post by yeats on 2009-04-23
Actually, come to think of it, I think I might chalk this up to the load put on the servers because of the new release.  Many people have been downloading the RC of Jaunty for a couple of weeks now...

---

### Post by hamood on 2009-04-24
Thanks for the reply.

We are testing ubuntu for last 6 months to introduce 

linux on our corporate network.

this problem has put question mark on the deployment.

may be another solution is to update from cd or dvd.

what do u think.

where i can download latest complete repository for ub 8.04 LTS

thanks

---

