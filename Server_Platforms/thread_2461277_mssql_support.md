---
title: "mssql support"
date: 2021-04-27
forum: Server Platforms
---

### Post by jcaliff on 2021-04-27
My office is finally upgrading to MSSQL 2019. I'm struggling to understand if deploying this on Ubuntu is a good idea or not, and I have a few questions.

1. Has adutil been replaced by Ubuntu's flashy new AD support? If so, how do we enable mssql Windows Auth with new tools? If not, is there a way to use adutil on 20.04? If neither... I don't know!
2. Is there any kind of best practices documentation for taking advantage of the new and improved mssql support in 20.04/21.04 in an on-premises deployment?

RHEL has all sorts of documentation regarding mssql deployment and AD integration but I do not care for that flavor.

---

### Post by TheFu on 2021-04-30
When it comes to deploying DBMS, always deploy on the primary platform used by the development team.  For MS-SQL, that is Windows.
Just because a vendor claims support for other platforms, that doesn't make using it a good idea.  This has been true for many decades.  Please learn this lesson the easy way.
If you want to run a DBMS on Linux, use Postgres or MariaDB.

Nobody should be running production servers on a 21.04 system. It isn't LTS and by the time you get it to be stable, it will be time for a forced OS migration to 21.10. There is no choice. Support for 21.04 will end in 2021.

---

### Post by scorp123 on 2021-05-01
> **jcaliff said:**
>  RHEL has all sorts of documentation regarding mssql deployment and AD integration but I do not care for that flavor.

Why not? RHEL offers 10 years of patches, upgrades and support whereas Ubuntu LTS releases only offer 5. And if you don't want to pay for Red Hat's / IBM's support you could use one of the free clones such as e.g. Alma Linux:  [https://almalinux.org/]("https://almalinux.org/")

As much as I love to use Ubuntu as my personal desktop OS and as OS for my personal servers at home ... but for production installations at my workplace I find RHEL and its clones have advantages.

Just my opinion.

---

### Post by TheFu on 2021-05-01
> **scorp123 said:**
> Why not? RHEL offers 10 years of patches, upgrades and support whereas Ubuntu LTS releases only offer 5. 

Some Ubuntu LTS have 10 yrs of support, others 8 yrs. The first 5 are without hassles and the 2nd set are with some strings for a few systems or paid if you have many systems. I find this to be a great compromise, since after 5 yrs, a system that doesn't get upgraded becomes a fork-lift upgrade anyways and a liability for any company that delays upgrades.  

Basically, a server over 5 yrs old won't be able to be migrated to a newer release without much more effort.

Ran into someone who said they were having issues with their RHEL 5.2 <<<<---- YES, 5.2 >>>> server.  The fact that it hasn't been supported in a decade and was running a 2.6.x kernel didn't seem to bother the business decision makers.  That system will fail to boot and that will either kill the company or force them to a new release.
And a reference for my LTS support statements: [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)
```
Release 	ESM Duration 	End of Life
Ubuntu 14.04 (Trusty Tahr) 	3 years 	April 2022
Ubuntu 16.04 (Xenial Xerus) 	3 years 	April 2024
Ubuntu 18.04 (Bionic Beaver) 	5 years 	April 2028
Ubuntu 20.04 (Focal Fossa) 	5 years 	April 2030
```

---

### Post by scorp123 on 2021-05-01
> **TheFu said:**
>  Ran into someone who said they were having issues with their RHEL 5.2 <<<<---- YES, 5.2 >>>> server.  The fact that it hasn't been supported in a decade and was running a 2.6.x kernel didn't seem to bother the business decision makers ...

Where I work now (since 2019) we still have a few installations with **Red Hat Advanced Server 4**, **Debian 5.x "Lenny"** and **Ubuntu 8.04** up and running ... ](*,). And lots of other EOL stuff like RHEL 5, CentOS 6, Debian 7 ... ](*,)

I am now the one who introduced the concept of "Linux Patch Day" (... everything that can be patched gets patched at least once per week, no excuses, no exceptions! Emergency patches get applied immediately. No excuses!) and Ansible (... no more doing stuff manually and then forgetting how it was done! The code is the documentation, the documentation is in the code ...). I am also the one who introduced them to *"revolutionary new software"* like **fail2ban** ... those guys didn't even know about that one.

And I'm using every opportunity I can to get on their nerves about lifecycling those old systems. With success. I managed to kill off a few of those old systems in recent months, but it's a slow and tedious process. And I can't afford to let up, I have to constantly bug them about planning ahead, e.g. if they install something today then they should already make plans when to replace that thing again before EOL+EOS happens, not after the fact. "Being proactive" was an unknown concept here before my arrival ... ](*,)

So for me those 10 years of support + updates RHEL and its clones offer are just barely enough given how slow and so not "proactive" they are going about lifecycling here. 

Maybe I'll manage to change that by the time I get retired in about 19 years ... :lolflag:

---

### Post by jcaliff on 2021-06-24
Thanks everyone for the help! I don't think anyone directly addressed my question, but I hear that loud and clear! Maybe 22.04 will have better tooling, documentation and support for this.

---

### Post by TheFu on 2021-06-24
> **jcaliff said:**
> Thanks everyone for the help! I don't think anyone directly addressed my question, but I hear that loud and clear! Maybe 22.04 will have better tooling, documentation and support for this.

But MS-SQL will still be a port of the MS-Windows code.
I earned my living doing that from 1994-2001.  Cross platform development.  Our primary server development platform was Solaris. This was because we had the best development tools on that platform that helped find the most bugs.  Purify and Quantify are amazing!  While Unix is mostly Unix, very similar, there are little differences that just won't be found by the devs or QA teams.  We treated all Unix platforms equally internally. If my Solaris DB server was busy, I'd use AIX or HP-UX instead.  There might be 50 lines of code different between all the different Unix platforms we supported - which was over 10 platforms.  But we also had an MS-Windows port for all our code.  Over 95% of that code was the same, but that last 5% was wonky - extremely different from Unix. It was mostly in the multi-threaded parts, signals, and dynamic shared library loading where the differences happened.  The main reason we even had a Windows version at all was for the sales guys to provide demos on their laptop. Very few of our customers actually ran the servers on Windows.  It was a fine platform, stable, but maintaining an installation was a hassle compared to our other supported platforms. We would create better tools on the Unix platforms, because that was so much easier for our team.

I worked in very large enterprises both helping clients and eventually I moved into a role at one of the clients. They had Oracle DBMS as a standard on all platforms, including MS-Windows, but most vendors would privately say that on MS-Windows, we should use MS-SQL, not Oracle.  On my projects, I was an enterprise architect by that time, we'd listen and always use the native DBMS recommended by the vendor.  They cost about the same, except MS-SQL requires CALs too.

Just because something is possible, that doesn't make it a good idea.

---

### Post by MAFoElffen on 2021-06-24
LOL. I'm confused.

There "were" early versions of MySQL that were released for Windows 95 and Windows NT. Those were the first early stable versions. But then Sun bought MySQL and did the support. Sun's Flagship OS was Solaris, so the platform they drove was their own. But then Oracle bought Sun... So then they inheritted Solaris and MySQL in that aquisition.. Oracle's Flagship OS is Oracle Enterprize Linux, but their concentration on DBMS development and support is for their own Oracle Database... So you know where their prioroities are. LOL

Sidenote: Microsoft's past track record for offering things for free, or low cost (or not) on Linux, and other OS'es, has been to hook people for use of their applications on other platforms, then stop support of it on that platform, so those customers make a decision to migrate to their platform... It's a great marketing strategy. But that makes me wary of doing SQL  Server on Linux... And the Microsoft wriiten Linux "[COLOR=#ff0000]adutil[/COLOR]" package is written so that you can do Active Directory authentication with Microsoft SQL Server on Linux... Not for MySQL.

I think you could say the original MySQL DB engine was Microsoft code, but then it was Solaris, then Linux. (As business driven priorities, and ownership providing support shifted.)

As a past Database Administrator and Software Developer... The business sense kind of decisions go to the platform they use, then the toolsets that are available to them on that platform. On the Development side, the application makes API calls to the Database Service, no matter what platform it is on. My first DBA job concerning Oracle Database, was Windows in-house developed applications using an Oracle Database Server running on an IBM RISC server running AIX, in the early '90's. When it comes down to where things are from an application's point of view, it's a unique connect string with credentials. Past that, and a named service in DNS, it's transparent on where, or what it is running on.

An infrastructure is what it is. And it's not always left up to who knows the nuts and bolts. We recomend what should be the best solution. But some of the final decisions are political, financial and business driven. That's where the 3-Tier Application Architecture logical model came from: a presentation tier, application tier and data tier... So things can interchange (and be changed) over time.

So if you are worried about what the current MySQL DB engine "platform priority" is, Oracle is probably developing for Linux, then porting those changes and features to their other supported platforms. That is just a guess. But Oracle could probably answer that question themselves.

Your second question relates to SSSD and version MySQL 8.0:
    [SSSD AND IDENTITY PROVIDERS (DOMAINS)]("https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/configuring_domains") and [Ubuntu SSSD]("https://ubuntu.com/server/docs/service-sssd")
    [AUTHENTICATING MYSQL 8.0 (ENTERPRISE) AGAINST ACTIVE DIRECTORY]("https://blog.pythian.com/authenticating-mysql-8-0-enterprise-active-directory/")

Just from my experience.

---

### Post by scorp123 on 2021-06-25
> **MAFoElffen said:**
>   So if you are worried about what the current MySQL DB engine "platform priority" is, Oracle is probably developing for Linux 

But we're not talking about MySQL. We're talking about MS SQL.
[https://www.microsoft.com/en-us/sql-server/sql-server-2019]("https://www.microsoft.com/en-us/sql-server/sql-server-2019")

And as odd as it sounds ... Yes, an Ubuntu version exists:
[https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver15]("https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver15")

But I'm not convinced I'd want to use this combination. MS SQL is built for Windows, primarily. So if anything I'd use it on a Windows server. Just because a version of it can be installed on Ubuntu now does not automagically mean it's a "good idea", just as "The Fu" said above.

---

### Post by MAFoElffen on 2021-06-25
> **scorp123 said:**
> But we're not talking about MySQL. We're talking about MS SQL.

But I'm not convinced I'd want to use this combination. MS SQL is built for Windows, primarily. So if anything I'd use it on a Windows server. Just because a version of it can be installed on Ubuntu now does not automagically mean it's a "good idea", just as "The Fu" said above.
I see that now. LOL. I told you I was confused...
> **MAFoElffen said:**
> Sidenote: Microsoft's past track record for offering things for free, or low cost (or not) on Linux, and other OS'es, has been to hook people for use of their applications on other platforms, then stop support of it on that platform, so those customers make a decision to migrate to their platform... It's a great marketing strategy. But that makes me wary of doing SQL Server on Linux... And the Microsoft wriiten Linux "adutil" package is written so that you can do Active Directory authentication with Microsoft SQL Server on Linux... 
Then the above. I'm wary of that. I know MS and Canonical have had agreements since 2014, and more recent Linux support from them, but on MS SQL Server on Linux, I'm not sure how how dedicated they are in the long run. I've been doing MS SQL Server for 27 years, and can honestly say that I have never planned to use it on Linux. There are so many things in MS SQL Server that are tied into MS Windows, and how "Windows" does Active Directory, I'm wary of how they would apply that cross-platform. M$'es marketing says there is no diffrence. But there are.

Some of the major differences concern disaster recovery:

[LIST]
[*]Database mirroring, which was deprecated in SQL Server 2012, is not available on the Linux version of SQL Server nor will it be added. Customers still using database mirroring should start planning to migrate to availability groups, which is the replacement for database mirroring.
[*]Due to differences in the way the underlying cluster works on Linux and Windows Server, all failovers (manual or automatic) of availability groups are done via the cluster on Linux. On Windows Server-based availability group deployments, manual failovers must be done via SQL Server. Automatic failovers are handled by the underlying cluster on both Windows Server and Linux.
[*]The Failover Clustring is implemented completely different on the two platforms. MS is done internally. Linux is done and requires a separate, 3rd party package, Pacemaker or equivallent.
[*]In SQL Server 2017 and 2019, the recommended configuration for availability groups on Linux is be a minimum of three replicas. This is due to the way that the underlying clustering works.
[*]On Linux, the common name used by each listener is defined in DNS and not in the cluster like it is on Windows Server.
[/LIST]
And of course, MS has developed Enhanced Microsoft Distributor Transaction Coordinator (DTC) support for Windows Server-based configurations, which excludes that feature ever being on Linux.

---

### Post by MAFoElffen on 2021-06-25
One thing I'm not sure about, and maybe someone else here does(?) is the PAL layer. On Windows, that never existed. For MS SQL Server on Linux, they divided their code up into waht was the DB Engine application code, and the platform specific code....

In MS SQL Server 2019 is that on all platforms or just for Linux? Is there a resource footprint difference for each?

---

### Post by TheFu on 2021-06-25
*SQL Server* is a generic term. Let's be specific so not to add to any confusion.  DB2, MS-SQL, Oracle DBMS, MySQL, Postgresql are all "SQL Servers".

*MS-SQL* is Microsoft SQL.

Adding a year after the generic term is for the SQL language standard for that year.
Add the 2 leading characters, "MS".  Stop the confusion, please, especially in discussions for non-Microsoft environments where MS cannot be assumed.  Not everyone lives in Redmond.

---

### Post by LHammonds on 2021-06-28
> **jcaliff said:**
> My office is finally upgrading to MSSQL 2019. I'm struggling to understand if deploying this on Ubuntu is a good idea or not, and I have a few questions.

1. Has adutil been replaced by Ubuntu's flashy new AD support? If so, how do we enable mssql Windows Auth with new tools? If not, is there a way to use adutil on 20.04? If neither... I don't know!
2. Is there any kind of best practices documentation for taking advantage of the new and improved mssql support in 20.04/21.04 in an on-premises deployment?


To get answers to questions 1 and 2, you'll need to hear from someone using those.  I have a mixed environment but never tied my Linux servers to the Windows AD domain...which may or may not have been a good idea and usually depends on the situation.  The 1st reply you got from TheFu sums up exactly what I would say.  MS-SQL Server is primarily a Windows-platform system and I would recommend running it on a Windows server.  Very similar to my recommendation that if you have a Windows environment, you need to be running directory services on a Windows server rather than Linux...otherwise you are adding multiple layers of complexity that others coming in behind you may not be able to support.

Regarding use of Ubuntu servers, only use LTS versions for production systems (18.04, 20.04, 22.04, etc.) and avoid interim releases (20.10, 21.04, 21.10 etc.)

I understand wanting to use Ubuntu...trust me, I do.  But the above is just my opinion regarding this kind of situation.

LHammonds

---

### Post by TheFu on 2021-07-06
FYI, [https://www.theregister.com/2021/07/06/microsoft_cancels_sql_server_beta_windows_server_containers/](https://www.theregister.com/2021/07/06/microsoft_cancels_sql_server_beta_windows_server_containers/)
Non-Windows MS-SQL is different from MS-Windows MS-SQL.
[https://techcommunity.microsoft.com/t5/sql-server/update-beta-program-for-sql-server-on-windows-container-is/ba-p/2516639](https://techcommunity.microsoft.com/t5/sql-server/update-beta-program-for-sql-server-on-windows-container-is/ba-p/2516639)

---

