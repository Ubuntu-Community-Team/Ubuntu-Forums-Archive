---
title: "Mono &amp; Vb.net on Ubuntu Server 7.10"
date: 2009-04-08
forum: Server Platforms
---

### Post by jay0316 on 2009-04-08
I have a website running on an in-house ubuntu server running 7.10.  One of our vb programmers said he may be able to do some things with VB.net to solve a couple problems I'm dealing with on the mysql/php end of things.

I did some searching on the forums and saw some people recommending the mono project.  I checked out their website and it sounds like it runs visual basic applications.  The download was in a area titled "[unsupported downloads]("http://www.mono-project.com/Other_Downloads")", which worried me a bit.

Is Mono something that may be a good solution or are their better ways to run vb.net apps on ubuntu?  Is it something that would allow the programmer to develop applications in Visual Studio on his windows machine, and then run them off the ubuntu server?

Any comments you want to add that I'm not considering?

---

### Post by linux_lover69 on 2009-04-08
Mono is the best way.

---

### Post by directhex on 2009-04-08
Unsupported by Novell, i.e. they only produce packages themselves for SUSE. Doesn't mean it doesn't work

And unsupported by Ubuntu too in a few weeks - 7.10 is EOL

VB.NET packages aren't included in Ubuntu until 9.04

---

### Post by jay0316 on 2009-04-08
Thanks for your replies.

directhex, is there a place to download these?
> VB.NET packages aren't included in Ubuntu until 9.04 

We'll be upgrading our Ubuntu server when it is no longer supported.

Is mono buggy at all?

Will the programmer be able to use visual studio on his computer and then run the application on ubuntu?

---

### Post by directhex on 2009-04-08
> **jay0316 said:**
> Thanks for your replies.

directhex, is there a place to download these?

Mono is included by default in all Ubuntu desktop installs. It's part of the main Ubuntu repository. You probably want the mono-vbnc and libapache2-mod-mono packages.

> Is mono buggy at all?

All software is buggy. Mono is less buggy than it was in 2006 when I first started paying attention to it

> Will the programmer be able to use visual studio on his computer and then run the application on ubuntu?

If the programmer doesn't do anything Windows-specific (e.g. use Windows-only namespaces, P/Invoke any Windows-only libraries, do retarded things like hard-coding paths instead of using System.IO.Path.Combine), then YES. If you want to be certain, "MoMA" (google for it) will analyse a set of assemblies & produce a portability report.

---

