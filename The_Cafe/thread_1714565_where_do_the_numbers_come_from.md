---
title: "where do the numbers come from?"
date: 2011-03-25
forum: The Cafe
---

### Post by jennybrew on 2011-03-25
Interesting that many people on Linux forums are happy to repeat the claim that there are far more servers running on Linux than on Windows.
I have never encountered a commercial organisation using Linux servers ... albeit I have only ever worked for two employers. More interestingly; none of our network team have ever seen a Linux server either.
Most companies seem to be using ISA servers and Win Server 2008.
So where do the figures come from? How do we know how many servers run Linux or how many run Windows?
The majority arent reachable from the outside so how do the numbers get compiled ??

---

### Post by mips on 2011-03-25
I don't think it's possible to get accurate numbers for linux use on internal networks as you can only really gauge that from sales figures and not everybody buys red hat, novell etc.

Suppose a lot of the info is based on surveys and results extrapolated from those surveys. There are however many companies out there using linux.

Web servers on the internet are easy to get info for.

---

### Post by koenn on 2011-03-25
linux is big on web servers, it powered most of the dotcom explosion in the 90's

webservers aside, "serious" computing is usually done with Linux, eg on IBM mainframes and others. 
re. surveys s.a. [http://www.top500.org/stats/list/36/osfam](http://www.top500.org/stats/list/36/osfam)

if you and your network team have never seen a linux server probably means that you're working for a small business with one Windows Small Business Server, or a medium sized business that replaced its Small Business Server with 2 regular Windows servers.

---

### Post by jennybrew on 2011-03-25
> **koenn said:**
> linux is big on web servers, it powered most of the dotcom explosion in the 90's

webservers aside, "serious" computing is usually done with Linux, eg on IBM mainframes and others. 
re. surveys s.a. [http://www.top500.org/stats/list/36/osfam](http://www.top500.org/stats/list/36/osfam)

if you and your network team have never seen a linux server probably means that you're working for a small business with one Windows Small Business Server, or a medium sized business that replaced its Small Business Server with 2 regular Windows servers.

We currently run a suite of file servers on WinServer 2008 using active directory, about 50 sqlserver databases on 10 servers WinServer 2008 again and we have a windows proxy server + two mirrored ISA servers for the net.
We also have space in a data centre provided by telecom company.
I have only worked for two employers but some of my colleagues have extensive experience and unfortunately have never encountered a server running linux.

EDIT: Ive just checked out your super link. It is giving statistics on super computers ..not normal business computers.
I think those statistics should be easy to collect ..however ..where does this widely held belief that Linux servers outnumber Windows servers come from ?
This wiki tells a different story stating the Linux market share wrt servers is about 13%
[http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)



**Market share and uptake**

 Main article: [Linux adoption]("http://en.wikipedia.org/wiki/Linux_adoption")[URL="http://en.wikipedia.org/wiki/File:Operating_system_usage_share.svg"]
[/URL] 

 
 
 See also: [Usage share of operating systems]("http://en.wikipedia.org/wiki/Usage_share_of_operating_systems") and [List of Linux computers]("http://en.wikipedia.org/wiki/List_of_Linux_computers")
 Many quantitative studies of [free]("http://en.wikipedia.org/wiki/Free_software")  / open source software focus on topics including market share and  reliability, with numerous studies specifically examining Linux.[[75]]("http://en.wikipedia.org/wiki/Linux#cite_note-74")  The Linux market is growing rapidly, and the revenue of servers,  desktops, and packaged software running Linux was expected to exceed  $35.7 billion by 2008.[[76]]("http://en.wikipedia.org/wiki/Linux#cite_note-75")
 [IDC]("http://en.wikipedia.org/wiki/International_Data_Corporation")'s Q1 2007 report indicated that Linux held 12.7% of the overall server market at that time.[[77]]("http://en.wikipedia.org/wiki/Linux#cite_note-Linux-watch.com_IDC.27s_Q1_2007_report-76")  This estimate was based on the number of Linux servers sold by various  companies, and did not include server hardware purchased separately  which had Linux installed on it later.

---

### Post by CraigPaleo on 2011-03-25
[W3Techs]("http://w3techs.com/technologies/overview/operating_system/all") surveys the top 1,000,000 websites. Linux is included as a subset of UNIX.

---

### Post by jennybrew on 2011-03-25
> **CraigPaleo said:**
> [W3Techs]("http://w3techs.com/technologies/overview/operating_system/all") surveys the top 1,000,000 websites. Linux is included as a subset of UNIX.

I think thats web servers?

I just wonder where the numbers come from for actual servers inside businesses ?

---

### Post by CraigPaleo on 2011-03-25
> **jennybrew said:**
> I think thats web servers?

I just wonder where the numbers come from for actual servers inside businesses ?

Oh, yes, those would be web servers.

---

### Post by jennybrew on 2011-03-25
> **CraigPaleo said:**
> Oh, yes, those would be web servers.

The other thread on here has fantastic results for Red Hat so someone is obviously running linux business servers :)

---

### Post by jennybrew on 2011-03-25
This article seems to throw a little light on things .............

[http://blogs.computerworld.com/15676/linux_is_doing_just_fine_on_servers](http://blogs.computerworld.com/15676/linux_is_doing_just_fine_on_servers)

---

### Post by aguafina on 2011-03-25
> **CraigPaleo said:**
> [W3Techs]("http://w3techs.com/technologies/overview/operating_system/all") surveys the top 1,000,000 websites. Linux is included as a subset of UNIX.


Yeah but Linux has nothing to do with UNIX right, it's only become like it over the years?

---

### Post by koenn on 2011-03-25
> **aguafina said:**
> Yeah but Linux has nothing to do with UNIX right, **it's only become like it over the years?**
you need a history lesson.

---

### Post by el_koraco on 2011-03-25
> **jennybrew said:**
> where does this widely held belief that Linux servers outnumber Windows servers come from ?

as far as i know, people who know what they're talking about usually mention either the web server market, the data for which is easilly collectible, or the mainframe market, in which linux is starting to become a mayor player. it's impossible to colllect data about servers in companies, and gauge the real figures, so if people are talking about how linux "servers" are outnumbering the windows ones, they're just misrepeating some of the things they've read.

---

### Post by aguafina on 2011-03-25
> **koenn said:**
> you need a history lesson.


LoL   I study 9 hours a day so it might be tricky fitting that in. :)

---

### Post by el_koraco on 2011-03-25
> **aguafina said:**
> LoL   I study 9 hours a day so it might be tricky fitting that in. :)

when do you get a chance to run 20 servers a day then?

---

### Post by fela on 2011-03-25
> **aguafina said:**
> Yeah but Linux has nothing to do with UNIX right, it's only become like it over the years?

No, Linux was developed by many different people but started out by Linus Torvalds, who designed it as an alternative hobby OS based on MINIX (I think) (a flavour of UNIX). Originally he didn't intend it to become widespread and included many features designed around his specific computer architecture. So I guess you could call it a 'clone' of UNIX, however many official UNIXes share features with most Linux distributions. For example, Mac OS X (which is an official UNIX apparently), includes many GNU utilities such as bash, screen, etc...).

On a visual representation of OS history it might appear the way you say it, but in reality it's quite the opposite :D

---

### Post by koenn on 2011-03-25
> **jennybrew said:**
> never encountered a server running linux.
I'm not going to argue whether it's actually 90%, 60%, or any other number.
I don't really care. I just want to note that the only places I've ever seen that run Windows servers exclusively, are SMBs. Just anecdotal evidence, like your "never seen a linux server"

As for the numbers? Steve Balmer has Linux at 60% for servers. I asuuming that's business servers - the market he's interested in. I'm also assuming large, multinational businesses and banks still use IBM mainframes - nowadays these are compartimentalized and run multiple linux systems in parallel. 

The 12-13% number you quote are sales figures for servers with Linux pre-installed. Most sysadmins I know buy bare servers without operating system, and install RedHat. Redhat seems to be doing fine, and they're only present in the server market, they don't do desktop systems anymore. 

Oracle prefers its databases to run on their Unbreakable Linux. There must be database servers out their running linux, then, right ? 

Also, looking through the wikipedia articles you mention, there seem to be quite a lot of institutions, organizations and busineses that run 'Linux'. are you assuming they just run *linux desktops *?  


So if you and your colleagues have never seen a Linux server, you've been looking in the wrong places, or your definition of "server" is too limited  - eg web servers don't count;  It's like someone would survey server systems market share "but servers doing Active Directory or Windows File and Printer sharing don't count". It's a "No true Scotsman" fallacy.

---

### Post by fela on 2011-03-25
Sorry to sort-of hijack the thread, but talking of Linux servers, what's so great about the commercial distros such as Red Hat/SuSE, as opposed to free (as in beer) ones like umm, Debian, Slackware, Ubuntu even? I use Debian on my server, never used the commercial ones, and I was wondering why you would pay for it, aside from reasons such as commercial support?

Also, to answer the original question. Many of the biggest internet companies (facebook, google (inc. youtube), ...) run Linux on their servers as it provides the performance and flexibility and blah blah that they really need. And speaking as a web developer, I can tell that I couldn't imagine running a server with Windows on it. For example, I couldn't imagine hooking up a screen/keyboard to a server, let alone running a GUI :O

As for the MS server propaganda ad (2004 I think), most of that was either lies, or misleading statements not telling the whole truth (such as their 'experiment' trying to prove Linux was more expensive, not actually mentioning that the hardware they used for the Linux servers was 10x more expensive).

---

### Post by aguafina on 2011-03-25
> **fela said:**
> No, Linux was developed by many different people but started out by Linus Torvalds, who designed it as an alternative hobby OS based on MINIX (I think) (a flavour of UNIX). Originally he didn't intend it to become widespread and included many features designed around his specific computer architecture. So I guess you could call it a 'clone' of UNIX, however many official UNIXes share features with most Linux distributions. For example, Mac OS X (which is an official UNIX apparently), includes many GNU utilities such as bash, screen, etc...).

On a visual representation of OS history it might appear the way you say it, but in reality it's quite the opposite :D


Yeah I was basing my reply on a visual diagram of UNIX history 
[http://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg](http://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg)

It shows no connection between Linux and the others but obviously a diagram is no real solution to show the exact history.

and sorry for highjacking this thread, was'nt intentional.

---

### Post by Bölvaður on 2011-03-25
Just want to add some anecdotal evidence to this thread :lolflag:
no Im not going to be that annoying.. but my story would be the opposite to your's and add an insult about the skills of the IT department at those places ^^

I hold high regards for the main people I talk to that handle our servers, we run solaris mainly and bit linux.

---

### Post by CharlesA on 2011-03-25
> **fela said:**
> Sorry to sort-of hijack the thread, but talking of Linux servers, what's so great about the commercial distros such as Red Hat/SuSE, as opposed to free (as in beer) ones like umm, Debian, Slackware, Ubuntu even? I use Debian on my server, never used the commercial ones, and I was wondering why you would pay for it, aside from reasons such as commercial support?

Mostly support and the reputation of them being rock solid stable.

---

### Post by 3Miro on 2011-03-25
Unix is an operating system developed in the late 60's. The most notable feature was the uniqe design (everything is a file), which to this date is the best design we have (in terms of speed, stability and security). Some systems still use original Unix code, Linux only borrows the design (without any code). Linux is a Unix-like system and it was designed that way from day 1.

All servers that run Windows that I have seen a smaller businesses that do finance/something else. All IT companies or larger businesses that I have seen use Linux/Unix of some sort. This of course is more anedotal evidence. I don't deal with businesses that much. I live in the supercomputer world, which is almost exclusively Linux.

There is an argument that in fact everybody in the world is using Linux, since Google runs on Linux and everyone does Google searches (or almost everyone).

---

### Post by JRV on 2011-03-25
I know my Internet service provider uses Linux.

Sound Internet 
[http://scc.net](http://scc.net)

---

### Post by Sporkman on 2011-03-25
Sporkforge.com runs linux - that should put this issue to rest!

---

### Post by lucazade on 2011-03-25
I have seen very few windows server at work, I would say fortunately! 
Especially when I was in IBM and in other IT companies...
and sincerly I hope to not see and use any another Win server or desktop in a near future! :D

---

### Post by fela on 2011-03-28
As for the OP, well, speaking from my own experience as well as objective evidence; many services / large companies, such as Google, Facebook, Youtube, Yahoo (I think), Wikipedia, right down to small things like Greennet (admittedly the only web hosting provider I've had experience with), all run Linux.

Also, any sysadmin will tell you that they would take the responsibility of 10 Linux servers over 1 Windows server any day ;)

EDIT: Well, I guess there's more stuff aswell. If you look at the top 500 supercomputers list ([http://www.top500.org/](http://www.top500.org/)), that's almost exclusively Linux (and then after that almost exclusively *nix, hardly any Windows whatsoever). So Linux definitely seems to have an advantage in high performance computing (you can't argue with that based on the evidence I've shown here).

If Linux has an advantage in high performance computing, that would suggest that it should be the system of choice for any server, unless there's a specific need for Windows-only server software. This is very rare, as most of the 'de facto' web server software (such as Apache, MySQL, Perl, Python, PHP, JSP, etc...) all run on Linux.

EDIT 2: I realize you were talking about any servers, not just web servers. However, this also applies in the field of any server: most of the de facto software runs well on Linux, and there are many advantages to using it (performance, price, flexibility, scalability, you name it, Windows was just never developed with the intention of running on servers. Bill Gates said himself in 1994, that he didn't think the internet was anything special).

---

### Post by MasterNetra on 2011-03-28
> **jennybrew said:**
> Interesting that many people on Linux forums are happy to repeat the claim that there are far more servers running on Linux than on Windows.
I have never encountered a commercial organisation using Linux servers ... albeit I have only ever worked for two employers. More interestingly; none of our network team have ever seen a Linux server either.
Most companies seem to be using ISA servers and Win Server 2008.
So where do the figures come from? How do we know how many servers run Linux or how many run Windows?
The majority arent reachable from the outside so how do the numbers get compiled ??

Yes you have encounter a commercial entity running linux servers. Google.

---

### Post by Rachel_Eliason on 2011-03-28
> **jennybrew said:**
> We currently run a suite of file servers on WinServer 2008 using active directory, about 50 sqlserver databases on 10 servers WinServer 2008 again and we have a windows proxy server + two mirrored ISA servers for the net.
We also have space in a data centre provided by telecom company.
I have only worked for two employers but some of my colleagues have extensive experience and unfortunately have never encountered a server running linux.

EDIT: Ive just checked out your super link. It is giving statistics on super computers ..not normal business computers.
I think those statistics should be easy to collect ..however ..where does this widely held belief that Linux servers outnumber Windows servers come from ?
This wiki tells a different story stating the Linux market share wrt servers is about 13%
[http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)



**Market share and uptake**

 Main article: [Linux adoption]("http://en.wikipedia.org/wiki/Linux_adoption")[URL="http://en.wikipedia.org/wiki/File:Operating_system_usage_share.svg"]
[/URL] 

 
 
 See also: [Usage share of operating systems]("http://en.wikipedia.org/wiki/Usage_share_of_operating_systems") and [List of Linux computers]("http://en.wikipedia.org/wiki/List_of_Linux_computers")
 Many quantitative studies of [free]("http://en.wikipedia.org/wiki/Free_software")  / open source software focus on topics including market share and  reliability, with numerous studies specifically examining Linux.[[75]]("http://en.wikipedia.org/wiki/Linux#cite_note-74")  The Linux market is growing rapidly, and the revenue of servers,  desktops, and packaged software running Linux was expected to exceed  $35.7 billion by 2008.[[76]]("http://en.wikipedia.org/wiki/Linux#cite_note-75")
 [IDC]("http://en.wikipedia.org/wiki/International_Data_Corporation")'s Q1 2007 report indicated that Linux held 12.7% of the overall server market at that time.[[77]]("http://en.wikipedia.org/wiki/Linux#cite_note-Linux-watch.com_IDC.27s_Q1_2007_report-76")  This estimate was based on the number of Linux servers sold by various  companies, and did not include server hardware purchased separately  which had Linux installed on it later.

Did you notice that wiki article later says that Steve Ballmer admits the real number is closer to 60% Linux?

---

### Post by jwcalla on 2011-03-28
> **koenn said:**
> linux is big on web servers, it powered most of the dotcom explosion in the 90's


I thought that was Solaris?

---

### Post by koenn on 2011-03-28
> **jwcalla said:**
> I thought that was Solaris?

who told you that ?

---

### Post by jwcalla on 2011-03-28
> **koenn said:**
> who told you that ?

Sun did.  ;)

---

### Post by koenn on 2011-03-28
> **jwcalla said:**
> Sun did.  ;)

you have a point (or Sun has); Sun/Solaris did really well during the dotcom bubble. 
At the same time, **L**AMP *also* practically became a household name then.

---

### Post by CraigPaleo on 2011-03-28
I love LAMP.

---

### Post by fela on 2011-03-29
> **CraigPaleo said:**
> I love LAMP.

I love it, except I can't for the life of me figure out how to get an SSL site running with it, Grrr >.<

---

### Post by Paqman on 2011-03-29
> **jennybrew said:**
> 
I have never encountered a commercial organisation using Linux servers ... albeit I have only ever worked for two employers. More interestingly; none of our network team have ever seen a Linux server either.


This is probably because Windows people get hired into places using Windows, and Linux people get hired into places using Linux.

---

