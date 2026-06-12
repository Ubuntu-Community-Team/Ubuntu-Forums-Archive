---
title: "*ubuntu server vs win2k3 server web?*"
date: 2005-11-15
forum: Server Platforms
---

### Post by kruz on 2005-11-15
hey guys im just wondering if you guys have and pros and cons on the win2k3 server web edition vs the ubuntu server

whats better and why?
dont mean to start a flame, but im really curious on what ubuntu has over win2k3

or even worse vice versea

let me know thanx guys

---

### Post by Glut on 2005-11-16
We're getting a lot of these lately. Perhaps there should be a sticky Ubuntu vs XYZ thread.

In terms of security, ease of use and features, you're not going to find much difference. 
The biggest difference is price. I think that you're best off choosing what you can use and what you can afford.

---

### Post by hostile on 2005-11-16
[QUOTE=Glut]The biggest difference is price. I think that you're best off choosing what you can use and what you can afford.[/QUOTE]


I concur.

Get what you can afford, and more importantly, what you can admin effectively.

---

### Post by kruz on 2005-11-16
sweet guys thanx for the advice
so you think a well setup ubuntu system
will match win2k3 in performance and stuff?

---

### Post by dtfinch on 2005-11-17
I think the web edition EULA prohibits installing any database server, even non-Microsoft ones. I can't see how it would be enforced though. Maybe SQL Server (besides the free MSDE/Express editions) might refuse to install, and the rest is honor system. The full SQL Server is very expensive anyways.

My Windows Server vs Linux benchmarking experience is very limited, as in none, but this is what I've gathered:

For database serving, MySQL seems faster than SQL Server for most queries, maybe not as fast for complex queries on poorly indexed tables. I have not actually laid eyes upon benchmarks where SQL Server beats MySQL, but I expect that it will in many cases. Postgres benchmarks tend to vary wildly. 8.x ought to be fast, if your tables are all properly indexed.

For web serving, I've seen more claims by individuals that IIS is faster than Apache, and they can often demonstrate it with simple benchmarks, but I feel like I've encountered more slow .asp and .aspx sites than slow .php sites. Despite .Net being compiled while .php is interpreted, I've been impressed by php's performance on several occasions, especially its string performance. There's a lot you can do to speed up Apache, and the same is true for IIS. Apache is not best known for its speed, but there are many alternatives. I've heard that lighttpd is one of the fastest free web servers, but I haven't tried it.

Unless you're hosting a very high traffic site, or hosting dozens of websites, performance may very well be a non-issue. Slashdot.org, which tends to knock out several websites a day just by posting links to them in their articles, is written in Perl, hosted on Apache (on Debian), accessing a MySQL database. The biggest part of the decision between IIS or not IIS is whether or not you're already accustomed to one or the other. IIS and Apache are very different beasts, and not interchangeable.

For file sharing, I strongly believe that Samba is faster than Windows, supported by benchmarks I've seen and my own personal experience. I maintain 5 Linux servers and 2 Windows servers at work, and just browsing the Linux servers in Windows Explorer feels an order of magnitude faster than the Windows servers. Samba is also easy to manage, and gives me a level of control I couldn't imagine under Windows. And Windows' NTFS filesystem does not perform nearly as well as they'd like people to believe.

I have a lot of Windows gripes, mostly architectural. Their implicit/mandatory file locking and filesystem layout are remnants of its DOS heritage, left in for backwards compatibility. Both make it hard to produce flexible and reliable system without sacrificing options or uptime. The file locking is why so many updates demand a reboot, and why some malware is very hard to remove. Then there's the issue that a low/idle priority process can bring the system to its knees with I/O calls, because process priority only gets applied to CPU scheduling. And on Linux I can run GUI apps remotely and have them appear locally. On Windows, you get remote desktop, and only one unless you pay per terminal. Then, I can configure Linux with a text editor. This can be a pain when documentation is poor, but most of the time it's a blessing. It's easy to make sweeping changes that would otherwise require the same steps to be repeated over and over in Windows. And I can upgrade Linux without rebooting, unless I want to upgrade the kernel. Server 2003 came with the claim that most upgrades wouldn't require rebooting, but still a lot of them do.

---

### Post by LordHunter317 on 2005-11-17
> **dtfinch]I think the web edition EULA prohibits installing any database server, even non-Microsoft ones.[/quote]No, it's not license for "enterprise" databases.  You're free to run MSDE.

> For database serving, MySQL seems faster than SQL Server for most queries,It *might* be faster for simple queries of the form:```
SELECT * from foo said:**
> I have not actually laid eyes upon benchmarks where SQL Server beats MySQL, but I expect that it will in many cases.SQL Server is used in all the various TPC tests, and even places very high in some of them.  MySQL isn't used at all.  Draw whatever inferences you wish from the empirical data.

> For web serving, I've seen more claims by individuals that IIS is faster than Apache, and they can often demonstrate it with simple benchmarks,For static content serving, *anything* is faster than Apache.  However, static content serving is generally meaningless.

> but I feel like I've encountered more slow .asp and .aspx sites than slow .php sites.The webserver has virtually no impact on this.  The part the webserver has any control over is absolutely insignificant.

> Slashdot.org, which tends to knock out several websites a day just by posting links to them in their articles, is written in Perl, hosted on Apache (on Debian), accessing a MySQL database.And uses a whole mess of servers to accomplish it's goal and wouldn't be functional at all without memcached.

> The biggest part of the decision between IIS or not IIS is whether or not you're already accustomed to one or the other. IIS and Apache are very different beasts, and not interchangeable.Funny, PHP runs on both just fine.

> For file sharing, I strongly believe that Samba is faster than Windows, supported by benchmarks I've seen and my own personal experience.No, it depends on the situation.  I've never seen any conclusive benches, since SMB is such a slow protocol anyway.

> Samba is also easy to manage, and gives me a level of control I couldn't imagine under Windows.What control does it give you that Windows filesharing really does not?  Most of the addons it gives you are quite minor.

 
> Both make it hard to produce flexible and reliable system without sacrificing options or uptime.Mandatory locking is a good thing for uptime, as it prevents data corruption, and I don't see how filesystem structure has anything to do with either.

> The file locking is why so many updates demand a reboot,You'd have to reboot anyway for the code to be reloaded.  This is no different on Linux: updating libc6 requires restarting every application for the currently running applications to use it.

> Then there's the issue that a low/idle priority process can bring the system to its knees with I/O calls, because process priority only gets applied to CPU scheduling.No, that's not true.  Windows does adaptive I/O priority scheduling, just like Linux 2.6. In fact, it's being doing it far longer than Linux.

What is far to say is because how I/O is performed, sometimes processes don't get the priority boost they should.  At the same time, the same can be leveled at Linux's elevator.

> And I can upgrade Linux without rebooting, unless I want to upgrade the kernel.You still have to restart your services, which means service interruption, and this is what's really important.  It follows from that, in order to have 100% uptime, that you must have a second box anyway.  If you have two boxes, it follows having to reboot one doesn't matter as long as the other doesn't crash during the reboot period.

I don't understand why people make such a big deal out of rebooting.  OpenVMS clusters have 100% uptime, and have to have the various members rebooted all the time.

---

### Post by grendelkhan on 2005-11-17
To me, and my clients, it's a cost issue.  By developing a site for them using free tools, it keeps my costs down and their bottom line better.

For my church, it's a moral issue: OSS best personfies the concept of give freely as you have been given.

---

### Post by dtfinch on 2005-11-17
> **LordHunter317]Funny, PHP runs on both just fine.[/QUOTE]

I was always under the impression that running PHP on IIS was slower. Most people use IIS for serving ASP or ASP.Net pages.

[QUOTE=LordHunter317]What control does it give you that Windows filesharing really does not?  Most of the addons it gives you are quite minor.[/QUOTE]

It gives me a lot of options that either don't exist or are hard to find on Windows.

For example, I have a couple shares set up for private drop boxes, for when email is inadequate. Files that people place in your box (under your name in the drop share) are visible only to you and them. Files that you place in your own box (the box share) are visible to everyone.
```
[drop]
        path = /store/boxes
        read only = No
        create mask = 0700
        force create mode = 0700
        directory mask = 0700
        force directory mode = 0700
        hide unreadable = Yes
        root preexec = mkdir /store/boxes/%U said:**
> 
        path = /store/boxes/%U
        force user = root
        read only = No
        create mask = 0755
        force create mode = 0755
        root preexec = mkdir /store/boxes/%U; chmod 777 /store/boxes/%U; chmod +s /store/boxes/%U
```

[QUOTE=LordHunter317]No, that's not true.  Windows does adaptive I/O priority scheduling, just like Linux 2.6. In fact, it's being doing it far longer than Linux.

If it does, I'm not feeling it. Some disk intensive processes bring my Windows system to a near halt, blocking other processes from accessing the disk but once every few seconds. If I set the intensive process to low priority, and the other processes I'm trying to use to high priority, the disk starvation isn't noticeably reduced. Maybe it's in 2003, but not 2000 or XP. Or maybe it's just broken, ineffective for solving the problem it's supposed to solve.

---

### Post by LordHunter317 on 2005-11-17
[QUOTE=dtfinch]I was always under the impression that running PHP on IIS was slower. Most people use IIS for serving ASP or ASP.Net pages.[/quote]It is, but that's not a fault of IIS.

> Files that you place in your own box (the box share) are visible to everyone.And is trivial to do on Windows.  Just set an Everyone or the correct group permissions on the directory.

In fact, that's how I do it on Linux do: either via ACLs or setgid and proper group ownership.

> If it does, I'm not feeling it. Some disk intensive processes bring my Windows system to a near halt, blocking other processes from accessing the disk but once every few seconds.What are you doing, specifically?

> Or maybe it's just broken, ineffective for solving the problem it's supposed to solve.Or maybe, and this is more likely IME, you're asking it to solve a problem it isn't meant to solve.

---

### Post by jstrubberg on 2005-11-17
I don't have the experience to jump into the discussion on web content, but this bugs me.


> You still have to restart your services, which means service interruption, and this is what's really important. It follows from that, in order to have 100% uptime, that you must have a second box anyway. If you have two boxes, it follows having to reboot one doesn't matter as long as the other doesn't crash during the reboot period.

It's the differnece between a fifteen second interruption and an eight minute one while the Win2K3 server reloads everything right down to the disk controller.

---

### Post by Glut on 2005-11-17
I believe that the inference is that if the 7:45 is going to cost you money, you would have spent money on a redundant server, or even not spent any money by hosting a virtual server on a less used server for this eventuality. 
*edit*
FWIW our w2k3 servers take about 3 minutes to reboot every fortnight (patch day - hoorah!) Our Linux (and other *nix) servers have their services down for around 1 minute in the same period. If this really affects you, then you have much larger problems. For instance if your server dies or is compromised, your services will be down until you can resurrect it - Our best time for a complete restore of a server onto an entirely new machine (not a transfer from a virtual server) is around slightly over an hour. This would also be solved by redundancy and if you're complaining about 7:45, over an hour will kill you.

---

### Post by LordHunter317 on 2005-11-18
[QUOTE=jstrubberg]It's the differnece between a fifteen second interruption and an eight minute one while the Win2K3 server reloads everything right down to the disk controller.[/QUOTE]But if you have *two* boxes, why does *how long* matter **at all** if *only one* is being rebooted?

It doesn't.  And anyone who's worked in HA situations before knows this.  Call it a "dirty little" secret.

I'm not saying it's justification for a multi-hour reboot process or anything of the sort: but the difference between 1 minute and say, 5 is pretty much irrelevant if you 100% uptime anyway.

And the difference these days between 2K3 Server and any Linux aren't long enough to matter.

[quote=Glut]I believe that the inference is that if the 7:45 is going to cost you money, you would have spent money on a redundant server, or even not spent any money by hosting a virtual server on a less used server for this eventuality.[/quote]Correct.  If you need 100% uptime you simply must have two boxes, end of story.  No way to build a single piece of hardware so it'll be up all the time (ignoring software issues).  Even if you could, it would never be cost effective.

---

### Post by jstrubberg on 2005-11-18
Two boxes is definitely the way to go.  Working in law enforcement, zero downtime is the only acceptable standard.

On my non-critical apps, I can often get away with half a minute of downtime without any user being the wiser.  Not so for a five minute reboot.

---

### Post by justhamade on 2005-11-19
Just wondering why the "security" issue never came up?  No software is 100% secure but I would trust apache over IIS, unless LordHunter317 (or anyone else) can prove me wrong.

If we are talking web server only then I dont see why you would pay for a 2k3/IIS box when linux/apache is free.  

If we are talking other things MS does like AD and Exchange then that is different.

---

### Post by dtfinch on 2005-11-20
I wouldn't really say that IIS is less secure than Apache. You're much more likely to be hacked through whatever server side scripts you put up, especially if it's some popular open source forum or CMS. I've seen more than one phpBB2 forum owned by kiddies simply googling for websites listing old phpBB2 versions numbers and running their little exploit scripts against them. Even home built websites can be easy to hack, if they use server side scripting and a database. SQL injection is an easy attack that works against way too many websites, allowing hackers to retrieve or alter sensitive data through lack of type casting (hacker puts SQL after a number) or lack of escaping special characters (hacker puts SQL after a single quote). PHP has a feature called "magic quotes" which protects against the single quote type, but not the other.

For making IIS as secure as apache, more or less, there's something called the IIS lockdown tool for closing off the extra services you might not know are running by default which you don't need and which have been exploited in the past. I remember discovering that I could connect to one of my favorite websites through webdav and have full control, anonymously with no login required. I was in Visual Studio .Net and clicked File->Open->Open Project from Web and typed the url, and it showed me the contents of the website's root directory as though it were a normal network share. I could view source files and such. My first thought was "Holy shit! That was too easy". I emailed the owners right away so they could secure it. The lockdown tool can ensure you won't accidentally open something up like that. More recent versions are probably a bit more secure by default, but you should run it anyway. If you're really worried about being hacked through your web server, moreso than through the scripts you put on it, you can always try a server other than apache or IIS.

---

### Post by LordHunter317 on 2005-11-20
[QUOTE=justhamade]Just wondering why the "security" issue never came up?  No software is 100% secure but I would trust apache over IIS, unless LordHunter317 (or anyone else) can prove me wrong.[/quote]IIS 6 has had two vulnerabilites reported since inception, neither of which are common.  One is DAV related and I forget the other.  Apache OTOH, has not had such a terrible track record.

IIS6 was rewritten from the ground up with security in mind, much like BIND 9 was.

[quote=dtfinch]. I was in Visual Studio .Net and clicked File->Open->Open Project from Web and typed the url, and it showed me the contents of the website's root directory as though it were a normal network share.[/quote]Thats' because by default, the webroot of an IIS server is shared over SMB/CIFS as wwwroot$.  I do believe VS.NET will connect using that automatically, as well (though I could be mistaken, and I'm too tired to verify).  However, I'm fairly certain it requires Administrator privileges to write to by default, so it's not a major security issue.  Again, too tired to verify... Perhaps I will tomorrow if I remember to do so.

---

### Post by dtfinch on 2005-11-20
[QUOTE=LordHunter317]Thats' because by default, the webroot of an IIS server is shared over SMB/CIFS as wwwroot$.  I do believe VS.NET will connect using that automatically, as well (though I could be mistaken, and I'm too tired to verify).  However, I'm fairly certain it requires Administrator privileges to write to by default, so it's not a major security issue.  Again, too tired to verify... Perhaps I will tomorrow if I remember to do so.[/QUOTE]

XP can actually mount a webdav share. Sometimes it even tries to connect to UNC paths using webdav first before falling back to SMB/CIFS. [http://support.microsoft.com/kb/832161/EN-US/](http://support.microsoft.com/kb/832161/EN-US/)

The URL I connected to was not one of mine. It was the site of a commercial online game I used to play. I don't know how they changed it from the defaults, but anonymous guests had at least read access to source code and such.

---

### Post by Chayak on 2005-11-20
How many widespread worms do you hear about that affect *nix systems?  I'm getting hits all the time on my firewall for IIS, makes me glad I'm not running it.

---

### Post by LordHunter317 on 2005-11-20
There are several.

---

### Post by MarcDM on 2005-11-21
Talking from experience here. 

I used to manage 2 Windows 2000 Boxes rented as dedicated servers from a hosting company. Which means I'm managing my Windows boxen in Texas, from my seat in Kingston (JM). 

One box was a web/database/email server, and the other was for streaming. 

The goin wasn't that hard. I had the setup pretty similar on both boxes, and all updates were applied to my local server setup to look like those two. That way, if I broke something, it was in my test environ, so I knew what to fix. 

Then came Win2k3, when one of my annual contracts expired with the hosting company, I upgraded to Win2k3. I could get the web edition for the same price as Win2k or a Linux box. 

This is 2003, and I know nothing about linux, so Gimme the Win2k3. Plus I had just installed the standard edition on a 2nd partition on my local server, and it seemed pretty stable. 

First problem, I can't install Enterprise Manager, or SQL Query Analyzer. Basically, you can't install ANY of the client apps for SQL Server on it. They will bitch, whine, complain then fail. 

Only problem is, I didn't know about this limitation until after I tried (and failed) at installing SQL Server 2000. In reading some more, I also found out that it does not support a lot of other things that one would do with a server alongside web-serving. 

Let's not even start to talk about viruses. or Windows update or the lack of a low-bandwidth method of communicating with the server. 

If you're on a budget, Linux is cheaper. It will cost u less time in updating a doing crap. Drag and drop takes a long time even if you have a 512k connection. (time is money)

Matter of fact, it was the problems I had with Win2k3/Imail (worms and such) that made me switch to Linux. I wanted spam-assassin on my server, but I wanted to learn this linux thing first. 

Fast fwd to 2005, finally comfortable with linux after spending some time with the Warty warthog, FC1 and Suse9. I decide it's time to switch the Win2k3 box to Debian Stable, which had just become 'Sarge'. Had the sites setup on the local server, and it seemed to be working. 

Using MySQL instead of MSSQL. The sites had been converted to ASP.NET after the move to Win2k3. This was in anticipation of Mono becoming more complete and able to host the sites on Linux. So no code changes, but now Mono and mod_mono instead of IIS and DotNET framework.

Day 1, it was slow. 
Day 2, it got slower. 
Day 3, the server crashed. 
Day 4 it crashed again. 

I was pulling my hair out trying to find the cause of these problems. I even said things like "Stupid Debian" :o

I had to go thru the code, and put in some explicit garbage collection code. And modify a few data access algorithms. Modified a table or two. There's redundancy in the data now, but less joins in the queries. On SQL Server (well MSDE on Win2k3 Web), lots of logic was enclosed in stored procedures.

So what follows is a list of things I noticed after my migration (upgrade ;)) to Debian Sarge from Win2k3. :

[list]
[*]Windows handle bad programming much better than linux. 
[*]SQL Server has some auto-connection-closing voodoo going on. Either that or MySQL doesn't like u not closing connections.
[*]SQL Server does a better job of creating indexes for you. I'm not sure if it actually creates indexes, but in my experience, it's faster on badly indexed data. MUCH faster.
[*]If you're renting a Dedicated server from a hosting company, cost is insignificant. Win2k3 (Web Edition) is usually abt the same price as 'Linux'. Especially if u pay annually.
[*]If you're programming in Java/C/C++/Python use linux. 
[*]If you're programming in C#/VB/ASP use Windows. 
[*]If you have to run a mail server, use Linux. All windows mail server packages are expensive and featureless
[*]IIS vs Apache. - Apache has MANY features that are just simply impossible in IIS (e.g. mod_auth*,mod_rewrite). Although i think most of these features are offered thru modules, the modules are as available as Apache itself. The same can't be said for "IIS Modules"
[/list]
Basically, unless you have some very Microsoft specific technology to implement, Win2k3 Web Edition will slow you down. 

Another issue you'll encounter is the limitations you'll have due to the nature of Windows based "Server" products. They tend to believe that they will be alone with Windows on the box. Also, due to the closed nature, not many libraries are shared between different products, and so the general process overhead will be higher. 

I hope I haven't babbled too much. And I hope this helps someone.

Thank you for reading.
Marc DM


PS. And Don't forget, you can't remove IE or msimn

---

### Post by LordHunter317 on 2005-11-21
[QUOTE=MarcDM]Let's not even start to talk about viruses. or Windows update or the lack of a low-bandwidth method of communicating with the server. [/quote]You can do low-bandwidth methods just fine.  RDP isn't actually all the bandwidth intensive, despite what one might think.  That's not to say it's as low bandwidth as an SSH session, but you can do SSH if one really must.

> It will cost u less time in updating a doing crap.Really?  I'm not sure who's downloads would be larger at this point: RHEL4 from scratch or Win2K3+SP1 from Dell.

> [*]Windows handle bad programming much better than linux. This isn't true at all.  Your issues are two-fold, and quite simple:[list][*]Mono's garbage collection and memory mangement are far less mature than that of MS' .NET runtime.[*]The MySQL .NET driver is rather immature.[/list]

> [*]SQL Server has some auto-connection-closing voodoo going on. Either that or MySQL doesn't like u not closing connections.No database tolerates you not closing connections, and ASP.NET especially doesn't like it.  I highly suspect there was another issue here.

> [*]SQL Server does a better job of creating indexes for you. I'm not sure if it actually creates indexes, but in my experience, it's faster on badly indexed data. MUCH faster.MySQL is known to be terrible at non-sequential access without index coverage.  SQL Server doesn't create any more indexes than MySQL to my knowledge, but it's just faster, period.

> [*]If you're programming in Java/C/C++/Python use linux. I don't see how this follows at least.  I've deployed solutions in all of those langauges on both platforms.  Neither is worse than the other, really.  Both have distinct advantages and disadvantages.  For two of those languages, the lines are really very blurred for a lot of things.

> [*]If you have to run a mail server, use Linux. All windows mail server packages are expensive and featurelessWhich is why Exchange is the most used mail system in the world?  Don't think so.  In fact, it's the groupware features it has that none of the Unix stuff doesn't (with cause) that make it so popular.

> [*]IIS vs Apache. - Apache has MANY features that are just simply impossible in IIS (e.g. mod_auth*,mod_rewrite).Utter rubbish, really.  I've yet to see anything I had to do in Apache I couldn't do in IIS.  And IIS has a flexible module system as well.

> They tend to believe that they will be alone with Windows on the box.I don't know what you're talking about here.

---

### Post by MarcDM on 2005-11-21
[QUOTE=LordHunter317]...  I'm not sure who's downloads would be larger at this point: RHEL4 from scratch or Win2K3+SP1 from Dell.
[/QUOTE]
Can't compare there. Apt is one of the things that convinced me to ditch Windows. RedCarpet is nice, but that's Novell I think. I haven't used RedHat since it's not free. 

I'm not talking about the size of the downloads really, but more my involvement. How much I have to actually do.

Generally, there are less steps involved in updating my debian/ubuntu boxes than updating Windows. So it can happen more quickly. Additionally, I have (and read about) less history with Debian security updates breaking (seemingly unrelated) functionality. It has happened to me with Windows. Many times.

> This isn't true at all.  Your issues are two-fold, and quite simple:[list][*]Mono's garbage collection and memory mangement are far less mature than that of MS' .NET runtime.[*]The MySQL .NET driver is rather immature.[/list]
 Yup, you're right on that one.

> No database tolerates you not closing connections, and ASP.NET especially doesn't like it.  I highly suspect there was another issue here. 

MySQL is known to be terrible at non-sequential access without index coverage.  SQL Server doesn't create any more indexes than MySQL to my knowledge, but it's just faster, period. :( Maybe I need to not talk out of my ass. I was using a lot of stored procedures on SQL Server. As a matter of fact, I didn't have a single query in the c# code. Only calls to stored procedures. Now, I have lots of non-sequential queries being passed to MySQL. Go figure. 

> I've deployed solutions in all of those langauges on both platforms.So have I
> Neither is worse than the other, really.  Both have distinct advantages and disadvantages.  For two of those languages, the lines are really very blurred for a lot of things. Agreed, and since that's the case, use the platform that gives you most freedom.

> Which is why Exchange is the most used mail system in the world? Does it run on Windows Server 2003 **Web Edition**?

> Utter rubbish, really.  I've yet to see anything I had to do in Apache I couldn't do in IIS.  And IIS has a flexible module system as well. Please point me to the IIS Modules that :
[list]
[*]Authenticate against LDAP using Basic Authentication
[*]match the power of mod_rewrite
[*]Serve a single directory from a user's home directory (ala server.com/~marcdm/ --> C:\Documents And Settings\marcdm\public_html\ )
[/list] Oh and since I'm asking, I've just made my point. They're not as available as IIS is. That is, not installed by default, don't cost the same and not mentioned on the IIS community website.

> I don't know what you're talking about here. Maybe I don't know what I'm talking about either :(, but ever notice how much stuff changes especially when you install a Microsoft Server Product (Commerce Server :confused: )? Let's just sum it up to me not fully understanding Windows "behind the scenes".

---

### Post by LordHunter317 on 2005-11-21
[QUOTE=MarcDM]I'm not talking about the size of the downloads really, but more my involvement. How much I have to actually do.[/quote]Windows is less, as it's automatic on .NET 2K3.  Well, you ought to reboot manually, but that's it.  It hardly gets more simplistic than that. 

> It has happened to me with Windows. Many times.It hasn't happened to me unless it was documented as such.

> Does it run on Windows Server 2003 **Web Edition**?How does that matter in the least?  The cost of Windows Server is small compared to the cost of Exchange for an enterpise setup.

And if you need low-cost Exchange, you buy SBS.

> Oh and since I'm asking, I've just made my point. They're not as available as IIS is.And my point is that doesn't really matter.  Many of the most commonly used Apache modules (e.g., mod_php4, mod_php5, mod_jk2) aren't part of the Apache source and shipped with an Apache install either.

> Maybe I don't know what I'm talking about either :(, but ever notice how much stuff changes especially when you install a Microsoft Server Product (Commerce Server :confused: )?No, I haven't, though I can't say I've run every server product Microsoft ships.

---

### Post by MarcDM on 2005-11-21
[QUOTE=LordHunter317]
How does that matter in the least?  The cost of Windows Server is small compared to the cost of Exchange for an enterpise setup.[/QUOTE]

Since the thread is about Win2k3 Server Web Edition vs Ubnuntu Server.

---

### Post by LordHunter317 on 2005-11-21
And you were talking about *mail*, not *web* serving, so that fact isn't very relevant anymore.  It's safe to assume that if he asked about a specific version of Windows, he's only interested in running web applications.

---

### Post by MarcDM on 2005-11-21
[QUOTE=LordHunter317]And you were talking about *mail*, not *web* serving, so that fact isn't very relevant anymore.  It's safe to assume that if he asked about a specific version of Windows, he's only interested in running web applications.[/QUOTE]
Is this why Win2k3 Web Edition comes with smtp and pop3 services?

---

### Post by LordHunter317 on 2005-11-21
IIS has had an FTP, SMTP, and POP3 service as part of it from way before there was a Web Edition of Windows server.

You can't infer from the fact they exist that MS really intends for someone to run a mail platform on .NET 2K3 Web Edition, given the above fact.

I mean, SQL Server can send mail so it must be an integral mail service, right?  No.

---

