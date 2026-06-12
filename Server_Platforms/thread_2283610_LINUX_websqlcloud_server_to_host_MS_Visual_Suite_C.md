---
title: "LINUX web/sql/cloud server to host MS Visual Suite C#, MS SQL Server .NET pages"
date: 2015-06-23
forum: Server Platforms
---

### Post by JC_Hood on 2015-06-23
Dear Ubuntu Server Pros:

     I'm a career IT professional with 30+ years using, programming & administering UNIX on high-end workstations but have done limited experience with programming or setting up a modern LINUX web or cloud server.  I have a requirement to setup a LINUX server that will replace the customer's current hosting environment, which is MS Azure.  
     Here's what I am doing and what I want to do. I'm working out of my home. I have broadband ISP but it is slow...about 1.5Mb down but I can increase that some if I need. I have been developing .NET server pages in C# under MS Visual Studio and using MS SQL Server Express under Windows 7. I have been subscribing to MS Azure to host my website and it has proven to be very costly. I just want to setup my own server here at home that will host my domain, website and everything else just like Azure does. But, I want to use Linux and its' free daemons to do this, not Microsoft.
     My database sizes aren't going to be anything especially big, so I think the standard SQL server that comes with Ubuntu Server will do OK.  I have to purchase a dedicated PC to be my server.  It will not be anything rack mounted.  I have a pretty small budget and will have to do all the setup myself.  I will need remote managment and RAID mirror capibilities.  My server workload is going to be small, not enterprise level. I won't be able to purchase paid support.  My server will be hosting 6 or less domains.
      I guess my most important question is if MS Visual Suite .Net active server pages developed mostly in C# and using MS SQL Server on my local PC, can be hosted by a dist. of Ubuntu Server without major pains.  Can I continue to develop under MS Windows 7 using MS Visual Suite or will I have to switch to LINUX for my apps to run correctly?
     I can do all of this project myself and don't require paid consultants.  I would just like to get it right the first time by getting some advise.  Thank you very much.

---

### Post by slickymaster on 2015-06-23
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by SeijiSensei on 2015-06-23
> **JC_Hood said:**
>       I guess my most important question is if MS Visual Suite .Net active server pages developed mostly in C# and using MS SQL Server on my local PC, can be hosted by a dist. of Ubuntu Server without major pains.  Can I continue to develop under MS Windows 7 using MS Visual Suite or will I have to switch to LINUX for my apps to run correctly?
"Without major pains?" I don't think so.  You could try renting a Windows virtual server somewhere.  Here's one place I found in a Google search: [https://hostek.com/hosting/windows/vps/windows-vps-hosting.html](https://hostek.com/hosting/windows/vps/windows-vps-hosting.html).  The minimum price is $35/month which includes something called "MS SQL Express" for free.  Real MS SQL is a costly add-on.

To convert entirely to an open-source model, you'd need to migrate the SQL database to something like PostgreSQL or MySQL, and rewrite the C# code into a language like Java, Ruby or something else.  You could use Eclipse for development.

The other alternative would be to set up a Linux box, then create a Windows virtual machine on it with something like VirtualBox.  I don't know what Azure offers so I can't tell you if that would be enough to host your site.  Still if you have a spare box that you can load Linux on, why not use Windows instead?

---

### Post by TheFu on 2015-06-24
+1 to what SeijiSensei says.  Drop proprietary tools and systems. Go F/LOSS. It will be harder to do this later.

For small web-apps, Ruby on Rails is extremely productive, if you follow the best practices. Takes about 3 months to *get up to speed*, assuming another OO language has been mastered.  Python is good too, but schools are teaching everyone and their dog python like they used to teach php. This means that market/skill will be less income producing for the next few years - too much supply.

Of course, if you are an "artist" in any specific language - stay with that 1 and you'll always find plenty of clients.

Part of me wants to ask why you'd start a C#/MS-SQL project on Windows planning to switch to Linux later?  Microsoft makes great tools, provided you never intend to leave their ecosystem.  While it is possible to stay 100% standards compliant with MSFT tools, I've never seen it when the developer didn't primarily code on some other platform and port to Windows constantly.

Google found this: [http://www.mono-project.com/docs/web/aspnet/](http://www.mono-project.com/docs/web/aspnet/) appears there could be hope.

---

### Post by JC_Hood on 2015-06-24
[SIZE=2]OK, thanks SeijiSensei, really didn't know how difficult it would be.  Do you know if there is a Windows Server OS that is free?  Like 2008 Server.  I don't have funds for expensive liscense fees.[/SIZE]

---

### Post by QIII on 2015-06-24
Just let me pop in to say that there are no free MS Server products and their cost would likely be absolutely prohibitive for you.

---

### Post by JC_Hood on 2015-06-24
Thanks, I guess it didn't really think it through.  Just broke my leg & on pain meds. I've been setting up alot of Linux Mint PCs for people and really love it and I guess I was thinking that a web server is a web server and that my apps would run on any of them.  I whole career has been strictly scientific.  I'm really a beginner when it comes to Website development and even newer to Server technology.  Thanks, I guess I will mark this as solved and start looking at a microsoft solution.

---

### Post by volkswagner on 2015-06-25
If you don't want to rent a Windows virtual server, you can get pretty far with Windows 7/8 and IIS web server and  SQL server Express.
There are deals on off lease workstations for the cost of a Windows 7 pro license. You'll want at least Windows 7 pro
so you can have it headless and use remote desktop.

There are open source platforms like DotNetNuke or DNN, which may be of interest with your C# background.

Good luck!

---

