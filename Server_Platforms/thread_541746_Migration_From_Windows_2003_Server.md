---
title: "Migration From Windows 2003 Server?"
date: 2007-09-03
forum: Server Platforms
---

### Post by soapytheclown on 2007-09-03
Hi all,

Ive been asked by my boss to look into an open source alternative for our current system at work since licencing costs are spiraling out of control and since i use ubuntu at home im hoping that we will be able to do the same at work too :)

the only thing is im a bit clueless as to where to start for alternatives since currently we're tied down by a whole load of microsoft products, all our servers at work currently run windows 2003 (some with AD), our backend database is an SQL 2000 one, with the frontend being through MS Access which is accessed by our clients remotely through windows terminal services we also have our internal exchange 2003 mailsever too. 

i dont have a problem with learning alot for this cause i understand it will be a massive project just wondered if someone could point me in the correct direction to get the ball rolling, 

another thing before i end this essay lol, how easy would it be to initially intergrate the ubuntu with the current system initially and then slowly phase out the windows 2003 servers

thanks in advance guys :D

---

### Post by p_quarles on 2007-09-03
I'm no expert, but I can respond to a couple of questions. 

AD: Different Linux distros have similar applications. Ubuntu's Landscape is, from what I understand, still in development, but it is being offered. Essentially it's web-based network admin tool that does all those cool things like updating specified groups, managing users, and so forth. It's only available to paying customers, so I have not used it in any capacity. 

Of course, there are dozens of SQL-based environments and front-ends for Linux. You won't be able to use MS's, but there are replacements. You'll also have to say goodbye to Exchange -- again, though, there are replacements.

I can speak best to your last question, though. Setting up one or two file and print servers using Samba would be a relatively easy first step. This would also, I imagine, be a great way of teaching yourself how to manage multiple users in Linux. It's going to be a lot different from doing so in Windows, and it's going to be a lot different from using Linux at home.

---

### Post by elst on 2007-09-03
You're right that this would be a big undertaking, so you probably need to find a source of ongoing support (i.e. a human who can answer your questions in depth, and help you are issues arise) - you are essentially talking about replacing the heart of the IT infrastructure when you replace AD and Exchange.

Probably the first place to start is your local Linux User Group, as somebody there may be able to help you or pass you on to an expert who would be willing to spend some time discussing things with you in detail. Depending on the size of your organization, you may find it useful to engage a larger consulting firm.

In the short term, the Access/SQL Server/Terminal Server arrangement can probably be replaced to good effect without disrupting the business, provided that you have the development resources. PostgreSQL provides a strong alternative to SQL Server, and you can replace the Access frontends with Web applications. Frameworks like Rails, TurboGears and Django enable you to build database Web frontends quite efficiently.

---

### Post by koenn on 2007-09-03
I agree with p_quarles. make it a gradual move, starting with leaving your current infrastructure intact and introduce Linux servers for very specific, manageable tasks, such as a file server etc. 

You will have to go hunt for replacement applications, but there's more to it than that. An MS environment is all about integration  - on Linux you might l have to create that integration yourself - or look for products / vendors / ... that can do it for you.

And yes, it's going to ba a massive project. 

Here are some thoughts of what the Linux world may look like to a Windows sysadmin :
[http://users.telenet.be/mydotcom/howto/linux/migration03.htm](http://users.telenet.be/mydotcom/howto/linux/migration03.htm)
and maybe also [http://users.telenet.be/mydotcom/howto/linux/migration02.htm](http://users.telenet.be/mydotcom/howto/linux/migration02.htm) , although you may already know most of it.

---

### Post by afljafa on 2007-09-07
To be quite honest - I wouldn`t even bother with ubuntu. Take a look at SME server on the contribs site.

All the heavy lifting has been done for you. You end up with a very secure mail, file, web and print server out of the box. The forums are very active and people have come up with plenty of good howtos on gettin various other requirements up and running.

---

### Post by Sef on 2007-09-07
> To be quite honest - I wouldn`t even bother with ubuntu. Take a look at SME server on the contribs site.


I would check out a few distros and find out what one best suites your needs.

---

### Post by Brazen on 2007-09-07
Looking at SME or other distros isn't going to do you any good.  The technologies that handle these sort of things are going to be the same across the bored.  SME sets up some neat things by default, but is not an AD/exchange replacement.  Are you wanting to replace workstations, too or just the servers?

I can tell you one quick and easy change you can make, and that is to switch out using Microsoft Access with OpenOffice's database program.  I know it can act as a frontend to MySQL and PostgreSQL, but I think it also works with MS SQL Server.  I would also agree that best thing to do here is to develop web applications for your database frontend, but that may be a little more involved.  You'll need to learn php or Ruby On Rails for that.

If you want to keep you Windows workstations but replace AD, then right now you are out of luck.  Hold off until Samba4 comes out, which will probably be at least a year, possibly 2 or more even.

For Exchange, best I've found is eGroupware, but it's complicated.

To replace the SQL server, I would suggest using MySQL.  It is the most popular open source database for good reason.

But really, you just need to pick something and take it one thing at a time.  Don't get overwhelmed by trying to do it all at once.  3 years ago the place I work at was 100% MS, but now on the server side it is more like 20% MS, but that started with a single server (an Apache webserver, in fact).

---

### Post by elst on 2007-09-08
> **Brazen said:**
> 
For Exchange, best I've found is eGroupware, but it's complicated.

To replace the SQL server, I would suggest using MySQL.  It is the most popular open source database for good reason.


There are now a couple of proprietary solutions built with OSS components for Exchange replacement (Scalix, Zimbra), but I'm not sure how easy it is to transfer mailboxes etc. out of Exchange without loss. This is really one of the tricky areas where you need access to support before you can plan a migration.

I've used MySQL, MS SQL, and PostgreSQL, and I wouldn't describe MySQL as an equivalent to, or replacement for, MS SQL or PostgreSQL. PostgreSQL follows the traditional pattern of database servers, which Oracle and MS SQL DBAs will find familiar, whilst MySQL has unusual compatibilities and weaknesses.

---

### Post by HermanAB on 2007-09-08
Active Directory and Exchange should be the last things you change, by then you should have more experience!

I'd suggest that you use a distribution with good server wizards, such as Mandriva and use rock solid virtualization, such as VMware or Xen, and then consolidate all your servers onto a handful of high power servers, each running 5 or so virtual machines.

You could Samba with WinBIND to replace Active Directory.  

Exchange can be replaced with a choice of groupware systems - I suggest Citadel, since it can handle enterprise size loads.  It is very scalable and extremely easy to set up through 'Easy Install'.

Cheers,

Herman

---

