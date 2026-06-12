---
title: "mod_mono doesn't work on apache2 and feisty"
date: 2007-05-23
forum: Server Platforms
---

### Post by oldtappan on 2007-05-23
When I go to [http://localhost/gallery/default.aspx](http://localhost/gallery/default.aspx), I get the firefox dialog box to open or save default.aspx.  So default.aspx or any asp.net page is not getting processed.

I see this error in /var/log/apache2/error.log:
**[Wed May 23 23:36:19 2007] [error] Failed running '/usr/lib/pkgconfig/../../bin/mod-mono-server --filename /tmp/mod_mono_server_gallery --applications /gallery:/storage/Data/www/Gallery --nonstop (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory**

I see this process running:

**www-data 13037  0.2  1.4  22520 10988 ?        Ssl  23:36   0:00 /usr/bin/cli /usr/lib/mono/2.0/mod-mono-server2.exe --filename /tmp/.mod_mono_server2 --nonstop --appconfigdir /etc/mono-server2 --master**

My /etc/apache2/sites-available/default file has the following entry for my app:
[B]Alias /gallery "/storage/Data/www/Gallery"
  AddMonoApplications gallery "/gallery:/storage/Data/www/Gallery"
   <Location /gallery>
       #Options Indexes MultiViews FollowSymLinks
       SetHandler mono
   </Location>[/B]

So as far as I can tell, everything is set up correctly.  But ASP.NET pages are not being process by apache/mod_mono.  I'm new to Linux/Apache so I may have screwed something up.

Can anyone tell me how to get this working?

---

### Post by HAL98 SE on 2007-06-04
I've been having similar problems myself, which version of Ubuntu is it - 7.04? I managed to get it running on previous versions of Ubuntu, but I've just upgraded to 7.04, Perhaps we can work through it. 

I followed this howto:-[ https://help.ubuntu.com/community/ModMono]("https://help.ubuntu.com/community/ModMono") but to no avail so far

---

### Post by HAL98 SE on 2007-06-04
I'm getting this error message when I try to render an ASP page (.aspx etc):-
```

Service Temporarily Unavailable

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.
Apache/2.2.3 (Ubuntu) mod_mono/1.2.1 Server at 192.168.1.2 Port 80
```

This error message is contained in the /etc/mono-server2/mono-server2-hosts.conf file, but I have no idea what  causes it.

---

### Post by scdougl on 2007-06-06
try :

sudo aptitude reinstall mono-xsp2

---

### Post by creswick on 2007-06-11
> **oldtappan said:**
> When I go to [http://localhost/gallery/default.aspx](http://localhost/gallery/default.aspx), I get the firefox dialog box to open or save default.aspx.  So default.aspx or any asp.net page is not getting processed.

I see this error in /var/log/apache2/error.log:
**[Wed May 23 23:36:19 2007] [error] Failed running '/usr/lib/pkgconfig/../../bin/mod-mono-server --filename /tmp/mod_mono_server_gallery --applications /gallery:/storage/Data/www/Gallery --nonstop (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory**


I had the same problem, after dealing with the typical RTFM crap from #mono, I stumdled across the line: 

MonoServerPath default /usr/lib/mono/2.0/mod-mono-server2.exe 

on line, and the line:

MonoServerPath /usr/lib/mono/2.0/mod-mono-server2.exe

in /etc/mono-server2/mono-server2-hosts.conf.  Sticking the "default" back in there does the trick.  

Basically, the MonoServerPath entry is broken, so it doesn't reset the default (mod-mono-server.exe)

--Rogan

---

### Post by warcriminal on 2007-06-11
Use this guide, I did it with no trouble at all.

Just follow the screenshots.

[http://www.goitexpert.com/entry.cfm?entry=Run-ASP-and-NET-in-UBUNTU--and-Debian-LINUX](http://www.goitexpert.com/entry.cfm?entry=Run-ASP-and-NET-in-UBUNTU--and-Debian-LINUX)

---

### Post by dieter_kar on 2007-08-14
By default, the services apache und apache2 are activated in Ubuntu 7.04. As I turned off apache, apache2 and mod_mono worked perfectly to serve ASP.NET 2.0 written in C# (VB.NET is supported in Mono 1.2.4 which is not yet available for Ubuntu 7.04). It is even possible to use Windows Assemblies (e.g. dll). 
The documentation in ubuntu ([https://help.ubuntu.com/community/ModMono](https://help.ubuntu.com/community/ModMono)) is outdated because is does not refer to ASP.NET 2.0 or higher which is quite commonly used (MS Visual Studio 2005 or higher).

---

### Post by JC Denton on 2008-07-07
This is what my logs are telling me:

[Mon Jul 07 16:32:42 2008] [notice] Apache/2.2.8 (Ubuntu) mod_mono/1.2.5 configured -- resuming normal operations
[Mon Jul 07 16:32:42 2008] [error] Failed running '/usr/lib/mono/1.0/mod-mono-server.exe --filename /tmp/.mod_mono_server --applications /monodoc:/usr/lib/monodoc/web --nonstop --appconfigdir /etc/mono-server (null) (null) (null) (null) (null)'. Reason: Exec format error

Is this a known issue and, more importantly, is there a known fix?

---

### Post by rnz0 on 2008-07-13
This problem showed in my 8.04. Found a solution somewhere:

The /usr/sbin/mono-server-update script erroneously adds the following
line to /etc/mono-server/mono-server-hosts.conf:
```

MonoServerPath default /usr/lib/mono/1.0/mod-mono-server.exe

```
instead of the correct:
```

MonoServerPath default /usr/bin/mod-mono-server

```

In my case I needed to tweak it to work with mono-server2

```

MonoServerPath default /usr/bin/mod-mono-server2

```

---

