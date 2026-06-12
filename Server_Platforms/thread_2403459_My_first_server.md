---
title: "My first server"
date: 2018-10-11
forum: Server Platforms
---

### Post by no1sever on 2018-10-11
Hello,
Good evening  All,

I am about buy my first server, i prefer ubuntu  OS, I need advice on security and other things i need to know as a first timer.

Please advice

---

### Post by howefield on 2018-10-11
Thread moved to the "*Server Platforms*" forum, for the time being.

Specific questions are probably better than the vague post above.

---

### Post by SeijiSensei on 2018-10-12
Pretty much any machine you have lying around could be a server.  What matters is how many people are sharing the server, and what does it do.  Mail?  Web?  Simple file-sharing?

If you want a rugged machine for the long run, I'd suggest a Dell.  I upgraded my aged PowerEdge server to a T30 some months ago.  I got a really good deal on the machine at $400 new from someone selling off excess inventory at NewEgg.  It usually sells for more like $550.

[https://www.newegg.com/Product/Product.aspx?Item=N82E16859155537](https://www.newegg.com/Product/Product.aspx?Item=N82E16859155537)

If you just need a simple server for your home, buy a refurbished desktop machine with a decent-sized hard drive like these:

[https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100019096%2050010772%20600014652&IsNodeId=1&bop=And&SrchInDesc=1%20TB&Page=1&PageSize=36&order=PRICE](https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100019096%2050010772%20600014652&IsNodeId=1&bop=And&SrchInDesc=1%20TB&Page=1&PageSize=36&order=PRICE)

---

### Post by TheFu on 2018-10-13
> **no1sever said:**
> Hello,
Good evening  All,

I am about buy my first server, i prefer ubuntu  OS, I need advice on security and other things i need to know as a first timer.

Please advice

Security isn't a checkbox (Y/n).  It is a process with 500-50,000 decisions dependent on what the server does.  As a first-timer, the things you need to know are unlimited.  Expect to be hacked if you put it on the internet.  Plan accordingly.  Have offline, versioned, backups that are made daily, automatically.  Verify the restore works AND that you know how to do it.  Read all the server-setup and server security things you can. Follow the best practices for every service you enable.  Use multi-level security protections.  Have a secure network design with similar risk services on the same subnet and lower risk services on protected networks.  Generally, 1 service is 1 container or 1 VM.  Placing multiple services onto a single OS install is NOT a best practice.

Be careful following instructions from noobs. Learn the "why", not just the "what to type" answers.  The "why" from 1990 is just as valid today as it was then.  Just the "what to type" has changed a little.
Bob Toxen literally wrote the book: *Real World Linux Security*  There are others.  

Running a server is mostly about providing a dangerous service and trying to mitigate as many of the risks as possible. We need for the service to be available to the people who are paying for it and nobody else. Period.  If all your clients are in France, don't let people who aren't in or likely to be from France attack it all day, all night, every day of the year.  If it is a home server, there's no reason to allow anyone outside the home to have access.

And please, don't use only passwords and believe that is secure. Passwords alone are not.

As for hardware, it is smart to size the hardware correctly. Sometimes that is a $35 raspberry pi and somethings it is a $500K HP-UX server.  Most services are easily handled by a $200 PC and if you upgrade parts, you can probably spend less than $100 for a fast, new, server.  Almost always, using 2 cheap desktop computers rather than a dual-powered, dual homed, RAID disks, redundant "server" is cheaper and more available and less hassle.

---

