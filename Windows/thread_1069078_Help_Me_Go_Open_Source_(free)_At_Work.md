---
title: "Help Me Go Open Source (free) At Work"
date: 2009-02-13
forum: Windows
---

### Post by Maheriano on 2009-02-13
We use Microsoft for everything but I'm hoping to cut the costs here in the office by switching things to open source.....or more importantly, free.

Right now we use Microsoft Office, I'm already bringing up Open Office as an alternative but does it have the same capabilities as an Exchange server and a Blackberry Enterprise Server (BES)?

We also use ArcGIS as a mapping application but I'm wondering if there are many more free but powerful mapping tools out there. We don't use everything ArcGIS has and the licenses are about $10,000 which we charge our clients for.

Also our servers are running IIS, I'm attempting to get over to Linux, especially since we run Oracle which is made more for it.

And we develop primarily in .NET so for an environment we use Visual Studio along with Visual Sourcesafe for code organization and version control. Is there any combination that will work as well as these but are free? We also do a little bit of VB6 and C# work but not much.

---

### Post by Simian Man on 2009-02-13
[QUOTE=Maheriano]Right now we use Microsoft Office, I'm already bringing up Open Office as an alternative but does it have the same capabilities as an Exchange server and a Blackberry Enterprise Server (BES)?[/QUOTE]
There is Exchange support coming for Linux in the for of [Open Change]("http://www.openchange.org/").  It was only recently announced though, so I don't know how well this will work for you.  I also don't know about Blackberry but I really suspect not.  How exactly do you use these services?

[QUOTE=Maheriano]We also use ArcGIS as a mapping application but I'm wondering if there are many more free but powerful mapping tools out there. We don't use everything ArcGIS has and the licenses are about $10,000 which we charge our clients for.[/QUOTE]
My wife is a geography student and uses ArcGIS in her studies.  Apparently the best free GIS software is [Geoda]("http://geodacenter.asu.edu/").  According to my wife it is OK but not as good as Arc (though she got Arc through school, so maybe if she had to pay for it, it would be another story :)).

[QUOTE=Maheriano]Also our servers are running IIS, I'm attempting to get over to Linux, especially since we run Oracle which is made more for it.[/QUOTE]
That is an easy one.  Linux is great for servers :).

[QUOTE=Maheriano]And we develop primarily in .NET so for an environment we use Visual Studio along with Visual Sourcesafe for code organization and version control. Is there any combination that will work as well as these but are free? We also do a little bit of VB6 and C# work but not much.[/QUOTE]
There is the Mono project that provides a C# compiler and .Net runtime for Linux.  It is supposed to be very complete, though I haven't used it.  Mondevelop is an IDE developed for it.  For source control, there are plenty available in Linux.  The most popular is probably SVN.  I use it and it's powerful and easy to use.

Overall I'd suggest migrating to FOSS little by little.  Don't change everything at once and piss everybody off!  Migrate the server to Linux.  Then look at running another email server in place of exchange.  Then move from Office to OpenOffice and so on.

---

### Post by Maheriano on 2009-02-13
Oops sorry, I need to keep Windows as the operating system, just looking for free applications to use on it. GeoDa looks pretty good though, installed it and going to play with it over the next few days.

---

### Post by donkyhotay on 2009-02-15
As mentioned above make the transition slowly, change to much at once and people will get confused. Probably a good idea (if you can) to take a spare machine and simply have one person test each open source program you are considering for awhile. Be aware that it *will* be different and most people hate changes to software regardless of what capabilities become available so make certain you choose someone with an open mind and give them plenty of time to transition. If they stick with it for awhile that will give you a good idea for whether it really meets your business needs or not. If it does then start implementing it for the entire company, if it doesn't then scrap it and find something else (or stick with your MS products). Eventually you'll find what programs can be converted to open source alternatives and which ones can't.

---

### Post by cmat on 2009-02-15
I managed to get all the mail clients, browsers and spreadsheet apps moved over to open source. Windows dominates the business world and it's nearly impossible to change over since our work applications are written exclusively to run on Windows systems. There are a few isolated businesses that can go completely open but it's next to impossible where I am.

---

