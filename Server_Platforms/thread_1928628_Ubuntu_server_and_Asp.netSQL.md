---
title: "Ubuntu server and Asp.net/SQL"
date: 2012-02-20
forum: Server Platforms
---

### Post by ufodisko on 2012-02-20
Hello there,

We have at our company a dedicated windows server at godaddy on which we run an Asp.net 2 application with Sql database. The renewal of the server is gonna cost us 2500$ so we thought why not try ubuntu and see if it has asp.net support.

So my question is does ubuntu have an official asp.net plugin? And do you recommend the switch considering that our app is in asp?

---

### Post by arpanaut on 2012-02-20
If a moderator does not move this question  soon, you might better off asking in this part of the forum: 
[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=339](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=-1&f=339)

Good Luck!

---

### Post by nothingspecial on 2012-02-20
*Thread moved to **Server Platforms**.*

---

### Post by CivilizationII on 2012-02-20
You will find a (very) basic list of compatibility here: [http://www.mono-project.com/Compatibility](http://www.mono-project.com/Compatibility)

Obviously you will need to use mono, but despite the optimistic compatibility list the answer is: it is unlikely.

What is sure is that you _must_ first try _every_ http server setting, executable, database connection before having a little hope that could be ok in production (you will have then performance/scalability problems).

Obviously such tests will cost far more than the 2500$ requested for upgrading your Windows server, not to speak about the cost of re-writing parts that will (will, not could) be not be compatible.

Eventually this doesn't mean that mono is not a solution (*), but you need to anticipate such a move starting the design phase of your web applications, or face heavy test / re-write / re-test.

(*) on another hand many, if not all excepted the mono team, consider mono is still experimental. According to my opinion, this is a very wise consideration.

---

### Post by HavarN on 2012-02-20
Yes, check out mono-project's page about asp for different web servers:
[http://www.mono-project.com/ASP.NET](http://www.mono-project.com/ASP.NET)

From my experience with Mono, it is very good. It has full .NET 4.0 support, except for the System.Windows.Forms library, which you surely do not use for an ASP.NET application anyways. So go ahead, give it a try.

Mono is not experimental: [QUOTE=mono-project.org]Latest Stable Version: 2.10.8[/QUOTE][http://www.go-mono.com/mono-downloads/download.html](http://www.go-mono.com/mono-downloads/download.html)

---

### Post by ufodisko on 2012-02-20
Thank you guys and sorry for posting in the wrong forum.

I will definitely take a look at Mono, sounds promising.

---

### Post by CivilizationII on 2012-02-20
> **HavarN said:**
> 

(...)

From my experience with Mono, it is very good. It has full .NET 4.0 support, except for the System.Windows.Forms library, which you surely do not use for an ASP.NET application anyways. So go ahead, give it a try.

(...)



Well, i had tried to point out that mono could be a option while avoiding thoughtless enthusiasm. Not an easy task, and obviously i haven't reached my goal. 

That said *"It has full .NET 4.0 support, except for the System.Windows.Forms library" *sounds very optimistic when mono explicitly claims for "**Everything in .NET 4.0 except WPF, EntityFramework and WF, Server-side Odata, limited WCF**" ;)

---

### Post by CivilizationII on 2012-02-20
> **ufodisko said:**
> Thank you guys and sorry for posting in the wrong forum.

I will definitely take a look at Mono, sounds promising.


Of course it looks promising, in particular i use it (while still having problems for multi-core programs) with .net4 and F# programming.

What i have tried to say is that the path from Windows to Linux via mono is not the clear way of Java (even if some minor problems can arise here).

Anyway what should be interesting if you choose this way, is that you will take some time for a very little report like: needed 0%, 25%, 50%, 100% re-programming whatever will be the result.

---

### Post by directhex on 2012-02-20
> **ufodisko said:**
> Hello there,

We have at our company a dedicated windows server at godaddy on which we run an Asp.net 2 application with Sql database. The renewal of the server is gonna cost us 2500$ so we thought why not try ubuntu and see if it has asp.net support.

So my question is does ubuntu have an official asp.net plugin? And do you recommend the switch considering that our app is in asp?

The namespaced you'[re going to be using on an ASP.NET 2.0 app should damn well be there on Mono

You may need a little porting work to convert from MSSQL to a database which runs on Ubuntu (like PostgreSQL or MySQL) though

---

