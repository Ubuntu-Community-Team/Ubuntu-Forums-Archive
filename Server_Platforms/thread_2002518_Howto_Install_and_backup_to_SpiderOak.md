---
title: "Howto Install and backup to SpiderOak?"
date: 2012-06-12
forum: Server Platforms
---

### Post by metz80 on 2012-06-12
Hi all.

I have been using dropbox for my server backups, but reacently started to use SpiderOak for all my company backups.

As I am running a live server, with alot of clients on it, I am not to eagar to just start messing around with spideroak install procedures found using google.

So here is my question:
Ubuntu 10.04 server

- How to install spideroak client on server (terminal only)
- How to have spideroak client login and create a new device, eg: Server1
- How to backup example; /var/backup/*


Thanks for any and all help on this!

-Tom

---

### Post by LHammonds on 2012-06-12
I have always giggled at the whole "it's secure...on somebody else's machine" line of thinking. :)  It is hard enough to secure data on your own servers. hehehe.

---

### Post by trundlenut on 2012-06-13
Perhaps looking on the Spideroak website should have been the first port of call.

[https://spideroak.com/faq/questions/31/how_do_i_install_spideroak_on_a_headless_linux_server/]("https://spideroak.com/faq/questions/31/how_do_i_install_spideroak_on_a_headless_linux_server/")

@LHammonds - any form of backup will require trust of some sort if it involves a third party.

---

### Post by trundlenut on 2012-06-13
Whoops double post!

---

### Post by LHammonds on 2012-06-13
> **trundlenut said:**
> 
@LHammonds - any form of backup will require trust of some sort if it involves a third party.
Yes, but how that trust was earned is an important part of risk management.  I have seen too many times where people see a possible solution and go with it just because it is there...without ever researching if that solution is appropriate and trustworthy.

---

### Post by metz80 on 2012-06-13
> **trundlenut said:**
> Perhaps looking on the Spideroak website should have been the first port of call.

[https://spideroak.com/faq/questions/31/how_do_i_install_spideroak_on_a_headless_linux_server/]("https://spideroak.com/faq/questions/31/how_do_i_install_spideroak_on_a_headless_linux_server/")

@LHammonds - any form of backup will require trust of some sort if it involves a third party.

Actually, I have read a ton of documents regarding this, but if you read my main topic, I am looking for some pointers on how to proceed with this, as my server is live with several clients on it. 

I do not want to do the "re-search" on the live server to get this going with a trial and error approach, perhaps crashing server and whatnot (as I have read about in some pages).

So any pointers from anyone running Spideroak client on a ubuntu server, thanks for any input and pointers on how I should proceed!

-Tom

---

### Post by trundlenut on 2012-06-13
> **metz80 said:**
> Actually, I have read a ton of documents regarding this, but if you read my main topic, I am looking for some pointers on how to proceed with this, as my server is live with several clients on it. 

I do not want to do the "re-search" on the live server to get this going with a trial and error approach, perhaps crashing server and whatnot (as I have read about in some pages).

So any pointers from anyone running Spideroak client on a ubuntu server, thanks for any input and pointers on how I should proceed!

-Tom

Do you have a machine capable of running virtualbox (or similar)?  If so install unbuntu server as a VM, bung some data in, then have a go at installing SpiderOak.  VMs are my crash test dummies that I always use to try things out on before interfering with any of my production servers.

---

### Post by LHammonds on 2012-06-13
Without knowing anything about your situation, I would recommend setting up a virtual machine as your test bed.  You are right to fear "testing" things on a production server.

Use something like VirtualBox to install an Ubuntu Server and do your testing with SpiderOak in there.

Once you have gained a certain level of proficiency with it and have determined it will work, I would recommend the next step would be to backup / restore your current production server to a virtual machine, get it up-and-running (with different IP) and see if you can get it installed and working on an exact copy of your production system.  Once you are satisfied that you can do it, make sure you have a good backup of the server and then go for it in production.

**EDIT:** Got ninja'd by trundlenut saying the same thing.  lol

LHammonds

---

### Post by trundlenut on 2012-06-13
> **LHammonds said:**
> Yes, but how that trust was earned is an important part of risk management.  I have seen too many times where people see a possible solution and go with it just because it is there...without ever researching if that solution is appropriate and trustworthy.

Very true.  A little healthy paranoia is always a good thing in my view.

---

### Post by trundlenut on 2012-06-13
> **LHammonds said:**
> 

**EDIT:** Got ninja'd by trundlenut saying the same thing.  lol

LHammonds

Great minds think alike... :lolflag:

---

### Post by metz80 on 2012-06-14
Thanks guys... virtual ubuntu server in virtualbox, vmware or whatever did not even come to mind.. ](*,)

Going to install in my virtualbox here right away and test the hell out of it.. 

Thanks!

PS! if anyone have any pointers running the client on ubuntu server, let me know ;)

---

### Post by ndstate on 2013-01-19
Hey metz80, I am looking for the same thing and I was curious as to how your experience went?  Did you get it up and running well?

Thanks.

---

