---
title: "How mature is the Ubuntu Server distribution?"
date: 2008-06-19
forum: Server Platforms
---

### Post by CompiledMonkey on 2008-06-19
I'm looking to evaluate a few server distributions for usage in a production environment.  Someone mentioned Ubuntu, which I didn't really think of for server usage.  My first thought was RHEL or CentOS, depending on our budget for this.

I'm downloading the server ISO now and wanted to know how mature this distribution is.  How would you rate it when compared with others like RHEL, CentOS, Debian, and other popular server distributions?

---

### Post by HermanAB on 2008-06-19
Linux is Linux is Linux...

Some parts are 38 years old.  Most parts are younger than that.  All Linux distributions are built off the same OSS projects.

---

### Post by CompiledMonkey on 2008-06-19
Very true.  However, there must be something different between the two.  Better support?  Better documentation?

---

### Post by NateMan on 2008-06-19
There isn't really anything better, meaning works more efficiently. The differences are normally in things such as drivers supported by default, package managers, and default software. I like ubuntu/debian's apt-get as opposed to yast or yum. I don't know much about centos, but it seems to have fallen out of favor in recent years. Another thing to examine would be what hardware you actual server has, as I have found some hardware that works best in debian based distros and some that works better in rpm based distros. The rpm ones are normally closed source anyway. Debian and ubuntu are very similar, as they have the same base. I am sure ubuntu server can be used in a production environment as easily as any of the others, esp if you compile most software from source. What sort of work would you be doing on it?

---

### Post by CompiledMonkey on 2008-06-19
Our initial usage would be very simple.  We'd just be running Tomcat on the machines.  Currently we run about 10 application servers, all of which run Windows Server 2003 and only run Tomcat.  It's a pretty big waste of money in my opinion to buy Windows Server licenses for each of those when we're only running a single piece of software, and it is open source.

The big gain our operations staff sees with Windows Server is the ease of keeping that machine up to date.  It's easy to understand using Windows Update and really not something that requires any effort.  Fact is, these machines "just run" and are kept up to date with nearly no interaction by our staff.  Obviously keeping it that way is important, so the updating and maint process for any Linux distro is important.

In the future, if these tests are successful, we'd explore the option of running our database software on a Linux environment as well.  There's more involved there as that environment uses a Sun disk array, fibre channel connections, and such.  The educational curve there would most likely be more difficult so we're hoping to start simple, at the application layer.

---

### Post by NateMan on 2008-06-19
Ubuntu server should do a good job of running tomcat, there are numerous guides out there on how to set it up. I also know that linux is more than capable of running your database server as well, since we do that as well, although personally for that purpose I highly recommend solaris over any flavor of linux. Solaris is now free to download and even somewhat older sun machines would be able to run it just fine. Solaris is a rock solid stable unix blend. As for updating, linux is very capable of automatically updating, even better than microsoft. You can setup cron jobs to automatically update, even setup a script to do so and then use a cron job to execute it at a convenient time, such as early in the morning. You shouldn't have any trouble setting that up. I'm sure that the performance gains from switching to linux will be nice as well, since linux servers use much less resources.

---

### Post by hyper_ch on 2008-06-19
for server based on linux I just love debian :)

---

### Post by artesvida on 2008-06-19
I really enjoy Ubuntu server, and despite some postings I have seen that insist Debian is better/more stable/etc, I have had zero problems with Ubuntu, even the non-LTS releases.  My $0.02.

> **NateMan said:**
> ...I also know that linux is more than capable of running your database server as well, since we do that as well, although personally for that purpose I highly recommend solaris over any flavor of linux. Solaris is now free to download and even somewhat older sun machines would be able to run it just fine. Solaris is a rock solid stable unix blend. ...

What makes Solaris a superior choice?  Faster?  More stable?  I have had minimal experience with Solaris, so I don't know its strengths/weaknesses.

---

### Post by spike_strip on 2008-06-19
I have a good bit of exposer with CentOS. I have recently migrated from CentOS 5 [final] to Ubuntu. One of the main differences is this forum...I have attempted to inquire about issues with CentOS—on their forum and get no replies. This forum is very active w/ many members. The forum is a great resource. 

I do not find the other differences; like apt-get over yum, to have any significance—they both work great.

I have an inside connection at Google [witch has a huge server farm] and they implement Ubuntu, and use every opportunity to faze out CentOS.   

One consideration might be that CentOS use SELinux ... I hear there can be a huge learning curve!  

I am very pleased with my Ubuntu LAMP server and will be with Ubuntu for a long time!

---

### Post by NateMan on 2008-06-19
Solaris is sun microsystems unix flavor. It is very reliable and stable, more so than any linux flavor I've dealt with. It also has many enterprise type hardware support built in (such as your SAN). Solaris is all we use at work to operate our fiberchannel san.

---

### Post by molotov00 on 2008-06-19
> **CompiledMonkey said:**
> I'm looking to evaluate a few server distributions for usage in a production environment.  Someone mentioned Ubuntu, which I didn't really think of for server usage.  My first thought was RHEL or CentOS, depending on our budget for this.

I'm downloading the server ISO now and wanted to know how mature this distribution is.  How would you rate it when compared with others like RHEL, CentOS, Debian, and other popular server distributions?

I think it's hilarious that you are asking for opinions on UBUNTUforums.org. The responses you're going to get are predictable.

---

### Post by squirrel_chaser on 2008-06-19
I am also testing Ubuntu server at work.  No problems so far.  Most of our servers run CentOS and I can not tell a difference in functionality.

The Debian and Ubuntu OpenSSL flaw bothered me a little for production server work, but I'll continue to test Ubuntu server.

---

### Post by theonegod on 2008-06-19
What is this OpenSSL flaw you mentioned?

---

### Post by hyper_ch on 2008-06-20
Something that has been fixed meanwhile.

---

### Post by ibutho on 2008-06-20
I personally would go with RHEL (or CentOS) and Debian Stable for production servers. Ubuntu has a good server product, butit doesn't seem to be tested as rigourously as RHEL or Debian.

---

### Post by gtdaqua on 2008-06-20
> **molotov00 said:**
> I think it's hilarious that you are asking for opinions on UBUNTUforums.org. The responses you're going to get are predictable.

Not so. Go through the posts here again :)

Ubuntu has been very stable on our production servers. Ubuntu is a spin-off from Debian. So basically, any debian-based distro out there (both desktop and server) are pretty stable. 

The reason why many consider Debian as more stable is because it requires lesser updates than Ubuntu. However, restarts in both the cases are very rare. Admins like an OS that needs very little 'patching'. 

You have to shell out $$$ if you want to get RHEL. Its not even the in the concept of OSS. The edge you will get over Debian in Ubuntu is this community support. These forums are very active indeed!

---

