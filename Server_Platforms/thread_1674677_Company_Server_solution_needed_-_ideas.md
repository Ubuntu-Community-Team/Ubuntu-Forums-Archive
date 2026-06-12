---
title: "Company Server solution needed - ideas?"
date: 2011-01-24
forum: Server Platforms
---

### Post by garfonzo on 2011-01-24
Hey Folks:

I have a situation which I need a solution to and I think I need to consider a solution that is beyond the typical setup. I thought I would get some feedback here. 

I am part of a small company that has a handful of employees that all use computers which run various versions of Windows. The company currently pays for a hosting service which holds all their company data and website. In order to access that data, every computer must remotely log in to the hosting service's Windows server and use all the software and data within that remote session (no files are stored locally on any computer). 

This works well for the company since employees often head out of the office with a laptop but still need access to both data and specific software while in the field (this "specific software" is just the MS Office Suite"). They simply log in over a wireless network and, bam, they have all the same software and files. 

The company wants to move away from paying for this service and wants me to set something up to provide similar access to their files (ie: not necessarily through a remote log in setup). Their basic needs are:

- Have access to company files and work on them from anywhere (not just within the office) without file duplication or upload/download (like ftp).

They are not in any way tied to the remote login system, but just need to have access to all their files out in the field and are open to any solution (which is great!). 

I was thinking of setting up a Ubuntu box with something similar to a mapped network drive, but have the drive available over the internet for employees in the field. I was also thinking of setting up a virtual Windows system in Ubuntu and having remote logins as before. I was even thinking, maybe I should buy a new server and a copy of Windows Small Business Server and replicate what the hosting service was doing.

One relatively minor point is that I am about 1,800 KM (1,110 miles) away from the office that all the employees work from. Thus, I need to set this all up at MY location, and have it available to them (hence the mapped network drive over the internet idea). 

I like the idea of doing this all with Ubuntu because it is cheap and I know it. However, if a Windows SBS is the better option, then that is not out of the question. 

Does anyone have any ideas or suggestions?

---

### Post by SeijiSensei on 2011-01-24
[Google Docs]("http://docs.google.com/"), perhaps?

---

### Post by garfonzo on 2011-01-24
> **SeijiSensei said:**
> [Google Docs]("http://docs.google.com/"), perhaps?

Thanks for the reply. However, the company is in its 8th year with most of its data on either MS Word, Excel, or Access. Moving to Google Docs is not really an option. 

I'm looking for a data hosting/access solution that I can do on company hardware.

---

### Post by HermanAB on 2011-01-24
Geez, there is no reason to pay anyone for a remote login service.  Windows has remote desktop protocol built in.  All you need to do is configure it such that each machine runs RDP on a different port, then forward those ports in your company router and get a static IP address for the router (get a server account from your ISP).  Then the users simply specify the address and port number when they log in. This is all really trivial to do.  There are 65000 ports on each IP address to choose from - that should be enough for anybody... ;)

---

### Post by wongo888 on 2011-01-24
If this were my gig I'd do a cost benefit analysis before doing any technical work. You def can pull this off, but why?

By the time you factor in the tech dev, your time and then the hardware and maintenance you're probably well into the thousands if not tens of thousands.

---

### Post by kgatan on 2011-01-24
If you and all your employees are working with documents and MS office id recommend a sharepoint portal which is included in the SBS.
Exchange is also included which is a really nice feature.

I dont think that kind of function is avalible in any open source together with MS office.

Its also quite easy to setup which saves you alot of development.

---

### Post by garfonzo on 2011-01-24
Thanks for all your responses thus far. 

What about if all computers had the necessary software (MS Office suite) installed locally and all they needed was to have a central server hosting the files? 

This is super simple with Ubuntu in a LAN situation, but what about when the user moves outside the realm of the LAN? How would the user take their laptop out into the field and still access the files?

This would be my preferred situation (Ubuntu server only serving files, no remote access). I have read articles on mapping network drives over the internet, but I do worry about possible security issues. 

Any thoughts?

---

### Post by Vegan on 2011-01-24
I can help with Windows Server but I will do that on my IT site. [http://www.windows-it.tk]("http://www.windows-it.tk")

Linux can much as well, SAMBA can be configured for remote access but security requirements make it non-trivial to setup.

---

### Post by kevinthecomputerguy on 2011-01-24
To backup what SeijiSensei said, i havent had any issues with google docs, you can set it up for your domain name here . [http://google.com/a](http://google.com/a) (paid) or here [http://www.google.com/apps/intl/en/group/index.html](http://www.google.com/apps/intl/en/group/index.html) (free)
 
I am able to use it side by side with MS Word and MS Excel, no file type issues yet.
 
I have also heard great things about acrobat.com, adobe air, and windows cloud, but i couldnt be happier with Google docs. Have you uploaded a .doc or .xls to your google docs account? It opens it no problem, but our needs are very very basic, maybe large scale excel would have problems, but our monthly budget sheet of $2,500, shared with (6) people works without a hitch, and one of the users is offline most of the time, and makes his changes locally, using excel, then uploads it.
 
*again, very basic plus \ minus stuff. No graphs, no pics
 
I have also heard great thing about MS Sharepoint.

---

### Post by garfonzo on 2011-01-24
> **kevinthecomputerguy said:**
> To backup what SeijiSensei said, i havent had any issues with google docs, you can set it up for your domain name here . [http://google.com/a](http://google.com/a) (paid) or here [http://www.google.com/apps/intl/en/group/index.html](http://www.google.com/apps/intl/en/group/index.html) (free)
 
I am able to use it side by side with MS Word and MS Excel, no file type issues yet.
 
I have also heard great things about acrobat.com, adobe air, and windows cloud, but i couldnt be happier with Google docs. Have you uploaded a .doc or .xls to your google docs account? It opens it no problem, but our needs are very very basic, maybe large scale excel would have problems, but our monthly budget sheet of $2,500, shared with (6) people works without a hitch, and one of the users is offline most of the time, and makes his changes locally, using excel, then uploads it.
 
*again, very basic plus \ minus stuff. No graphs, no pics
 
I have also heard great thing about MS Sharepoint.

Thanks for the reply. The problem with moving to Google docs is that the Excel files we use are quite complex. Plus, we have Access databases which aren't available in Google Docs.

---

### Post by garfonzo on 2011-01-24
I should also add the some of the MS Access databases are often opened and used by multiple employees at the same time so an FTP type solution is not possible.

---

### Post by Vegan on 2011-01-24
I hold a Microsoft MVP and I can help with all Office products.

---

### Post by kevinthecomputerguy on 2011-01-25
I see, darn, have you seen this?
[[COLOR=#000099][FONT=Arial]__[/FONT][/COLOR]]("http://ubuntuforums.org/-https://www.jungledisk.com/")[https://www.jungledisk.com](https://www.jungledisk.com)

---

### Post by garfonzo on 2011-01-25
> **kevinthecomputerguy said:**
> I see, darn, have you seen this?
[[COLOR=#000099][FONT=Arial]__[/FONT][/COLOR]]("http://ubuntuforums.org/-https://www.jungledisk.com/")[https://www.jungledisk.com](https://www.jungledisk.com)

That is very interesting and seems like a possible solution (and cheap!). I wonder, though, how it would handle a single file being used by multiple users at the same time (MS Access files can be opened and changed by multiple users at the same time). I think this might be a service where users pull a copy of the file they need to work with, edit it, and sync it back up in the cloud. I'm not sure that MS Access files would be handled properly as the database file needs to stay where it is so others can still use the file (access the database)

Anyone have experience with this service?

---

### Post by kevinthecomputerguy on 2011-01-25
I don't, just stumpled upon it while google'ing your situation. My guess is no, that will be a hard obsticle to overcome. My guess is you would have to go with something like MS Sharepoint, VPN to a file share, or the individual remote dekstop ports idea.
 
Maybe someone else knows how?

---

### Post by garfonzo on 2011-01-25
> **kevinthecomputerguy said:**
> I don't, just stumpled upon it while google'ing your situation. My guess is no, that will be a hard obsticle to overcome. My guess is you would have to go with something like MS Sharepoint, VPN to a file share, or the individual remote dekstop ports idea.
 
Maybe someone else knows how?

Thanks for your help/thoughts. Indeed the MS Access file situation (multiple users opening and editing the same file at the same time) is a tough hurdle. The only two ways I can see it working is either Remote Desktop sessions or mapped hard drives over the internet.

---

### Post by SeijiSensei on 2011-01-25
> **garfonzo said:**
> Thanks for your help/thoughts. Indeed the MS Access file situation (multiple users opening and editing the same file at the same time) is a tough hurdle. The only two ways I can see it working is either Remote Desktop sessions or mapped hard drives over the internet.

I take it you mean that you have a single Access database with multiple simultaneous users?  Are they actually editing the file itself, or simply running queries against it?  Access presumably handles things like file- and record-locking in this situation itself, no?

ODBC could be one solution to this issue for you.  I've only used it with Access as a client to data tables residing in PostgreSQL or MySQL, but I'm pretty sure you can set up Access as a server to which ODBC connections can be made.

I'm going to suggest one other file-sharing option that might work for things other than Access, and that's WebDAV.   Take a look at [mod_dav]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") for details. If you set it up with [SSL]("http://www.howtoforge.com/webdav_with_ssl_and_two_factor_authentication") encryption, you can easily and securely share files via the web.

I know you can mount a WebDAV share as a folder on the Windows desktop; I don't know whether you point a "network drive" at one as well.  Samba will, of course, allow you to map drives to SMB shares, but I can't find clear-cut discussions on whether the stream can be encrypted.  You could use OpenVPN tunnels to encrypt the entire connection as an alternative.

---

### Post by alienprdkt on 2011-01-25
> **garfonzo said:**
> 
What about if all computers had the necessary software (MS Office suite) installed locally and all they needed was to have a central server hosting the files? 
Any thoughts?

This is similar to how I have the systems set here at work. What you will need is a router / firewall / that supports ssl vpn. That will get you the security you need. We use the SonicWall tz-100 is not too high of price and gets the job done!

When you login VPN you get all your drives mapped to your pc/laptop

---

### Post by drdos2006 on 2011-01-25
Maybe it is time to try to migrate away from Access centric applications.....

[http://dabodev.com/](http://dabodev.com/)

regards

---

### Post by garfonzo on 2011-01-26
> **SeijiSensei said:**
> I take it you mean that you have a single Access database with multiple simultaneous users?  Are they actually editing the file itself, or simply running queries against it?  Access presumably handles things like file- and record-locking in this situation itself, no?


Yes, I mean that multiple users are using the database (running queries, editing records, etc.), not modified the design of the database. Access does handle all the record locking details behind the scenes. 

I am tempted to move the Access database to a web based, pure SQL database. It would take a bunch of work, but then all I would have to worry about is sharing single files and not have to deal with the multi-user file situation of the MS Access database.

---

### Post by kevinthecomputerguy on 2011-01-26
Garfonzo-
 
I really wanted to help you because you helped me a few years back with rsync, but really the best stuff i can find is vpn to an internal file share. I hope you find what you need, keep up the good work.

---

### Post by garfonzo on 2011-01-26
> **kevinthecomputerguy said:**
> Garfonzo-
 
I really wanted to help you because you helped me a few years back with rsync, but really the best stuff i can find is vpn to an internal file share. I hope you find what you need, keep up the good work.

Ha! I forgot about that rsync discussion. Well, I do appreciate your input into this thread. It has definitely helped me move forward with finding a good solution. I think your suggestion of a VPN to an internal file share may be the ticket. We'll see.

---

### Post by spynappels on 2011-01-26
Hi Garfonzo,

Would it be an option to migrate the AccessDB to a MySQL db on a linux server and use Apache/PHP to interact with it through a web frontend? Don't know what your business is, but PHP programming should be a cost effective solution.

Also for the VPN, look at OpenVPN in routed mode, which could also be run on the same server. This means you would not even need to have your Web interface for your DB system Internet facing, you could simply bind it to the OpenVPN IP. GUI clients for OpenVPN are available for all the major OSs so setting it up for end users is easy too.

---

### Post by SeijiSensei on 2011-01-26
> **garfonzo said:**
> I am tempted to move the Access database to a web based, pure SQL database. It would take a bunch of work, but then all I would have to worry about is sharing single files and not have to deal with the multi-user file situation of the MS Access database.

> **spynappels said:**
> Would it be an option to migrate the AccessDB to a MySQL db on a linux server and use Apache/PHP to interact with it through a web frontend? Don't know what your business is, but PHP programming should be a cost effective solution.

While I'd agree that, in the longer term, it might make sense to build a web application to replace the Access one, I'm concerned about the "business logic" contained in Access.  Presumably the staff is comfortable with the interface and know how to use it to generate queries, update data, etc.  Replicating all that in PHP would be a complex and perhaps costly task.

I'd suggest a middle-ground solution for the near term.  Strip the data tables out of Access and move them to PostgreSQL or MySQL.  Then replace the tables in Access with links via ODBC to the external data tables.  This preserves the look-and-feel of the existing application, but removes the need to share a single file across users.  Instead, each person can have his or her own copy of the stripped-down Access file while sharing a common database.

(I've used PostgreSQL for over a dozen years now.  I chose it back when the MySQL license didn't allow commercial redistribution.  I still prefer it to MySQL, today.  I'm also loathe to build future applications on a database owned by Oracle.)

---

### Post by drdos2006 on 2011-01-26
Maybe it is time to try to migrate away from Access centric applications.....

[http://dabodev.com/](http://dabodev.com/)

Based on python...

regards

---

### Post by koenn on 2011-01-26
I'd go for openvpn tunnels for secure remote access, and rdp sessions / windows terminal services for the actual work.

file sharing over an internet connection can be rather painful for larger files (loading and saving a word doc a couple of pages long will already have noticeable delays), and migrating from Access to real client-server databases is not trivial. 
Sharepoint can fix some issues, but you're still be dealing with relatively large files over relatively slow links, so ...

---

### Post by garfonzo on 2011-01-26
Great discussion folks, I really appreciate the conversation (thus solidifying my faith in the Ubuntu community). This is helping my focus my efforts on specific solutions to present to my boss. 

[QUOTE=spynappels]
Would it be an option to migrate the AccessDB to a MySQL db on a linux server and use Apache/PHP to interact with it through a web frontend? Don't know what your business is, but PHP programming should be a cost effective solution.
[/QUOTE]
I am leaning that way, yes. Although (as SeijiSensei points out) I think this may be a longer term solution.

[QUOTE=SeijiSensei]
While I'd agree that, in the longer term, it might make sense to build a web application to replace the Access one, I'm concerned about the "business logic" contained in Access. Presumably the staff is comfortable with the interface and know how to use it to generate queries, update data, etc. Replicating all that in PHP would be a complex and perhaps costly task.
[/QUOTE]
I completely agree. I think this is a long term goal for sure. This would remove the frustration of a) relying on MS Access files for work and b) having each user share the same file. Plus, once the employees get used to using a certain system, I doubt it would be a great idea to switch it up on them and force them to learn a new system (albeit with the same data). Longer term goal I think.  

[QUOTE=SeijiSensei]
I'd suggest a middle-ground solution for the near term. Strip the data tables out of Access and move them to PostgreSQL or MySQL. Then replace the tables in Access with links via ODBC to the external data tables. This preserves the look-and-feel of the existing application, but removes the need to share a single file across users. Instead, each person can have his or her own copy of the stripped-down Access file while sharing a common database.[/QUOTE]
So, are you saying that with this method, each user has a local copy of the Access file (but without any tables, just forms, queries, reports, etc.) and they connect to the actual tables via an ODBC? I haven't worked with ODBC much, is this a LAN only situation or can this span across the internet (server in one location with all the tables and the users in a completely different location using their local copy of the Access file to access the tables)?

---

### Post by garfonzo on 2011-01-26
> **koenn said:**
> I'd go for openvpn tunnels for secure remote access, and rdp sessions / windows terminal services for the actual work.

file sharing over an internet connection can be rather painful for larger files (loading and saving a word doc a couple of pages long will already have noticeable delays), and migrating from Access to real client-server databases is not trivial. 
Sharepoint can fix some issues, but you're still be dealing with relatively large files over relatively slow links, so ...

I agree. I think that either we setup a server within the LAN (not a great solution) or everyone remotes in to the server as you suggest.

---

### Post by garfonzo on 2011-01-26
Perhaps I should mention something at this juncture...

When I say that there are MS Access databases, really there is only one that has been in use for the past couple of years. It handles all the inventory processes for the company (ordering, tracking, etc.)

I am currently building a second Access database to handle virtually everything else about the company (billing, work orders, scheduling, client data, revenue, accounts receivable, etc.). It will be a rather substantial MS Access database once completed, but I am only about 1/3 done. 

I have had this thought nagging me that perhaps I should scrap Access and build this new database in MySQL and a web front end even though I have already started in Access. Then, once that one is up and running, I could rebuild the inventory database in MySQL and a web front end too. 

What do you guys think?  The employees have not used the new Access database yet so there is nothing to "unlearn". All this would mean is a delayed deployment date (I was shooting for April).

Again, thanks for all your thoughts and help thus far!

---

### Post by koenn on 2011-01-26
> **garfonzo said:**
> 
I have had this thought nagging me that perhaps I should scrap Access and build this new database in MySQL and a web front end even though I have already started in Access. Then, once that one is up and running, I could rebuild the inventory database in MySQL and a web front end too. 

long term, i think that's a good idea -- if you're confident you have the necessary skills or learn them well enough fast enough. (I've seen people click and drag together quite reasonable ms access apps, but who are lost at the sight of a simple select statement, not to mention a html form tag) 

known problems with ms access apps are
[LIST]
[*]the don't scale very well (size, number of users)
[*]they're not client-server; networking them requires workarounds, typically file sharing
[*]they tie you to ms office; you might end up in scenarios such such as "we could move away from MS Office if it wasn't for this ms access app everybody uses"
[*]you need the more expensive Office edition that includes Access, and so do all the users, unless you avoid that by using runtimes or those web data sheets - you probably didn't. 
[*]they are usually one of the trouble spots in ms office upgrades
[/LIST]

that's why you (should) only see them in SOHO and as prototypes.
(I guess you're in SOHO so you have an excuse :) )

---

### Post by SeijiSensei on 2011-01-27
> **garfonzo said:**
> So, are you saying that with this method, each user has a local copy of the Access file (but without any tables, just forms, queries, reports, etc.) and they connect to the actual tables via an ODBC?

Yes, that's exactly what I meant.  All the tables are ODBC links to the SQL server in the background.  Everything else like queries, reports, etc., are stored in each user's copy of the Access file.

> I haven't worked with ODBC much, is this a LAN only situation or can this span across the internet (server in one location with all the tables and the users in a completely different location using their local copy of the Access file to access the tables)?

If you can see the SQL server over the network, you can use ODBC.  I've got data in PostgreSQL on a hosted virtual server that I can manage with Access here at home.  Both PostgreSQL and MySQL provide free ODBC connectors for their databases.

While I'm not generally a Microsoft fan, I rather like Access as a database client.  I agree entirely that it's not well-suited to being a DB server, as it often is used in MS-centric organizations.  But it's really quite good for devising queries without having to slog through all the SQL syntax.  I've gotten pretty good at writing complex SQL queries from my years of web development, but I also find Access a nice solution for many data and DB management needs.

I just never store the data in Access.  A central SQL server is much more flexible.

> I have had this thought nagging me that perhaps I should scrap Access and build this new database in MySQL and a web front end even though I have already started in Access. Then, once that one is up and running, I could rebuild the inventory database in MySQL and a web front end too. 

What do you guys think?  The employees have not used the new Access database yet so there is nothing to "unlearn". All this would mean is a delayed deployment date (I was shooting for April).

I don't think any of us can answer this question.  How critical is this database for your business?  How important is it to meet the April deadline? How much experience do you have building database-driven web applications?  Perhaps you should try the Access front-end/SQL server back-end approach with this application.  Then you could later move to a web-based application using the already existing SQL database.

---

### Post by garfonzo on 2011-01-27
> **SeijiSensei said:**
> If you can see the SQL server over the network, you can use ODBC.
That's fantastic! This would kill two birds with one stone. I could move the tables over to a dedicated SQL server and the users wouldn't know the difference (no new learning), then in the mean time develop a web front end to be transitioned over to. I like it. 


> **SeijiSensei said:**
> How critical is this database for your business?  How important is it to meet the April deadline? How much experience do you have building database-driven web applications?  Perhaps you should try the Access front-end/SQL server back-end approach with this application.  Then you could later move to a web-based application using the already existing SQL database.

The April deadline was a wish of sorts. The database will be replacing daily workflow processes. If we don't hit the April deadline, it isn't as if the company would cease to operate. I do have a background in web development, CGI scripting, programming, and the like so learning SQL and the web front end language (Python or something) sounds like great fun!

I think you've provided a slick solution to my Access database dilemma. The other half of the equation is how to share all the other files (the Word, Excel, PDFs, etc.) over the network. I was thinking a CVS/Content management solution. In an attempt to not hijack my own thread, I started a thread  [over here]("http://ubuntuforums.org/showthread.php?t=1676696") where I describe what I'm looking for. There may be an easier way to do this, but this is just what comes to my mind.

---

### Post by garfonzo on 2011-01-27
> **koenn said:**
> long term, i think that's a good idea -- if you're confident you have the necessary skills or learn them well enough fast enough. (I've seen people click and drag together quite reasonable ms access apps, but who are lost at the sight of a simple select statement, not to mention a html form tag) 

known problems with ms access apps are
[LIST]
[*]the don't scale very well (size, number of users)
[*]they're not client-server; networking them requires workarounds, typically file sharing
[*]they tie you to ms office; you might end up in scenarios such such as "we could move away from MS Office if it wasn't for this ms access app everybody uses"
[*]you need the more expensive Office edition that includes Access, and so do all the users, unless you avoid that by using runtimes or those web data sheets - you probably didn't. 
[*]they are usually one of the trouble spots in ms office upgrades
[/LIST]

that's why you (should) only see them in SOHO and as prototypes.
(I guess you're in SOHO so you have an excuse :) )

I am in a SOHO situation and the business is a bit MS Office centric. I would agree that MS Access is a good piece of software, but long term it isn't the solution. I am very much leaning towards moving everything to an SQL server with a web front end. This would solve the majority of the problems you've outlined. 

I do have experience programming with an array of languages, but not SQL specifically. I think learning SQL and dusting off my web language texts for the front end (Python or PHP or something) would be a lot of fun. 

As I mentioned in my previous post in this thread, there is a second part to this problem. I'm trying to figure out a way to let everyone share all the other office files (MS Word, Excel, PDFs, etc.) over the internet with some sort of check in/check out solution. I started a thread [over here]("http://ubuntuforums.org/showthread.php?t=1676696") where I describe what I'm looking for. 

Thanks for the reply!

---

### Post by drdos2006 on 2011-01-27
Openoffice would be an alternative to Word and Excel but you may have to convert the internal macros into Openoffice basic.

I have previously written large multi-user databases with Access  with incremental changes to the databases from hand held Pocket PC's using abcDb programming. That was a couple of years ago. Previously I used dbxl under Digital Reseach DOS Version 6.0 to write PC databases.

I would recommend a look at dabodev.com as an alternative for the front end of an Access database. Written in python, apparently able to be ported from Windows to Linux so you could test the front end under Windows if you have a testing timeframe and later port across to Ubuntu with an SQL backend.

I have not needed to write a large database recently but if the request for me was to convert an Access database to SQL and include a front end, then I would be checking this out.

[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html)
[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html)


regards

---

