---
title: "Windows server vs Linux server"
date: 2012-08-26
forum: The Cafe
---

### Post by yc2 on 2012-08-26
Hello,

"Microsoft has a majority market share" - we all know bug #1. But this isn't true for the server market. (I think even Ms CEO admitted Linux has 60% of the server market. - But this figure is just a detail.)

My question is: Why is Linux more successful on the server market?

or rather:

[B]What are the differences between a Windows server and a Linux server? Not so much the technical details, but more why server admins choose one over the other.
[/B]
I started another thread about command line differences:
[http://ubuntuforums.org/showthread.php?t=2048043](http://ubuntuforums.org/showthread.php?t=2048043)
But that is obviously just one aspect of it.

I run a Linux server so i know a little about that, but I do not know anything about Windows servers.

The only difference I know is that Linux is free of charge and also open software. But for a big company choosing a server platform, I am not sure these aspects are the most important?

Thanks for any input

ycc

---

### Post by Primefalcon on 2012-08-26
#1 Linux servers run on a command which means no gui's weighing down performance, also all that gui software omitted means extra stability....

#2 Since you can Alter the Linux code yourself, if you have the resources, you can fix ityou5rself rather than having to wait on anyone (especially useful for corps that have a large IT staff).

#3 Cost, Windows software costs a lot especially if you run a lot of servers, also since Linux softare and such is lighter an faster you will need less machines... so even hardware/utility costs will be less

#4 Also windows machines need to be rebooted more (linux can be configured on the run, even installing a kernal without a reboot if needed), have anti-virus software running.. and so on not to mention downtime for defragging

Of course thats just to start

---

### Post by codemaniac on 2012-08-26
it's a matter of arguing which server OS is the most appropriate in the context of the job that needs to be done, based on factors such as cost, performance, security and application usage.

---

### Post by forrestcupp on 2012-08-26
I use a Linux server, but from what I've seen, Linux servers usually don't support .Net stuff. So if you're wanting to create your solution using ASP.Net or something, you'd probably have to go with a Windows server.

---

### Post by lucazade on 2012-08-26
Windows Server... masochism???

:-&

Just an example: "Microsoft updates Skype to use secure Linux servers instead of P2P supernodes" .. The new boxes should support far more connections; 4,100 versus just 800. Neither Microsoft uses Win servers :)

---

### Post by SeijiSensei on 2012-08-26
Linux has a strong presence in the web and DNS space because it is free and has strong security when running exposed to the Internet.  For the first two decades of the Internet Microsoft products offered neither of these advantages.  It was a lot easier to harden a box running Linux and Apache than Windows and IIS.

What's true in the Internet world doesn't necessarily extend to enterprise or office networks though.  There you'll often find the full suite of Microsoft servers and server applications centrally managed via Active Directory.  For a company with large numbers of Windows desktops to manage, Microsoft's native server products make sense.

The one application besides web service where there was once competition between Linux and Microsoft servers was mail.  Exchange + Outlook now seems to be winning there as well, particularly on networks managed by AD.

---

### Post by buzzingrobot on 2012-08-26
"Server admins" may have their prefrences, often based on what they are used to. Plenty of Windows admins aren't about to trade it.  GUI vs CLI is a matter of preference and habit.  Both are interfaces. Using a CLI does not make you a better admin. It makes you an admin who uses a CLI. The notion that GUI's soak up server resources is not really relevant.  Command shells soak up resources, too. 

Most important, tho, admins typically do not make hardware purchasing decisions.  Businesses make those decisions for reasons that may or may not have anything to do with the software.  Then, they hire admins to nursemaid the stuff.

Admins often see software as an end in itself.  Businesses see software as a means to an end.  Admins represent an expense they would happily get rid of.

---

### Post by yc2 on 2012-08-26
> **forrestcupp said:**
> I use a Linux server, but from what I've seen, Linux servers usually don't support .Net stuff. So if you're wanting to create your solution using ASP.Net or something, you'd probably have to go with a Windows server.
I have no real knowledge about it. but isn't Mono some kind of implementation of .net??? But if it can do ASP, I have no idea.
Thanks for many replies.

---

### Post by arclance on 2012-08-26
> **yc2 said:**
> I have no real knowledge about it. but isn't Mono some kind of implementation of .net??? But if it can do ASP, I have no idea.
Thanks for many replies.
Yes but it is not up to date I believe only up to .NET 2.0 really works right.

---

### Post by oldfred on 2012-08-26
I am not sure Linux vs. Windows is even the right question. 

One of my early computer classes (before PCs :) ) , the question always was what software is best for what you want to do, then you choose the mainframe system and then hardware & operating system were tied together (and it was the 7 sisters or 7 large vendors).

So with Web servers the choice is usually LAMP and that runs on Linux.

---

### Post by Primefalcon on 2012-08-26
> **oldfred said:**
> So with Web servers the choice is usually LAMP and that runs on Linux.
you can run Apache, MySQL and PHP on Windows just fine, heck 2 all in one installers WAMP (I think only for windows) and XAMPP (is cross platform) do just that. And you can run .net apps under Mono very well actually...

---

### Post by directhex on 2012-08-26
> **arclance said:**
> Yes but it is not up to date I believe only up to .NET 2.0 really works right.

Mono implements .NET 2.0, 3.0, 3.5, 4.0, and 4.5 - although it implements only some of the libraries from each of those (e.g. WCF is partially supported, WPF is unsupported)

As far as ASP.NET goes, Microsoft have open-sourced their implementations of ASP.NET MVC, so Mono includes that. MVC1 and MVC2 are available in Ubuntu, and MVC3 will be available after the 2.12 release of Mono ships. MVC4 is open source, but does not run on Mono yet.

---

### Post by linuxyogi on 2012-08-26
I did my MCSA  5 years back on Window server 2003. What I have experienced is that Windows servers are quite easy to setup but they are very unstable.Things doesnt work the way they should be. I have never configured or used Linux servers but one thing that I hear is that they are very stable.

---

### Post by KiwiNZ on 2012-08-26
Horses for courses, It is a matter of what best suits your needs and best suits your budget, I would not make a decision regarding server purchase and config based on advice from a Forum.

Research
Research
Research
Plan
Plan
Plan
Scope
Config
Test
Reconfig
Test
Implement.

---

### Post by arclance on 2012-08-26
> **directhex said:**
> Mono implements .NET 2.0, 3.0, 3.5, 4.0, and 4.5 - although it implements only some of the libraries from each of those (e.g. WCF is partially supported, WPF is unsupported)

Yes but in my experience only 2.0 works "almost as well as windows", 3.5 "works pretty well but not for everything", and 4.0 is "not usable".
[The compatibility page does not even mention 4.5.]("http://mono-project.com/Compatibility")
They may have made some improvements since I last updated it so it might work better now.
You may also have been using programs that work better with mono than I did or were even written specifically to be compatible with it.
I am going to try the latest version an see if it works better, hopefully the .NET 4.0 buttons will have labels this time.
Edit:
Okay it works much better than last time, I don't have to go through the interface by memory anymore.

---

### Post by yc2 on 2012-08-27
Thanks for many views.

I think I read that Tomboy uses Mono. It was removed from the default installation in Precise. There are now no applications using Mono in the default installation. maybe Mono is on its way out, as I understand your comments?

ASP also comes into this question. I would really like to hear opinions about it. (I use PHP a lot. Even for non-web scripting. PHP is in my humble opinion the best,most intuitive and least error prone programming language I have ever seen. Even facebook seems to use it ;) )

What are the pros and cons of ASP. How does it differ from PHP?
I hope it is possible to reply without going into too much technical detail. i would like to know its pros/cons and how it is generally structured and how it differs from PHP.

Thanks a lot if someone feels like outlining a little about the differences of ASP and PHP. As I understand it is possible to run ASP on Linux server if Mono is installed?

---

### Post by mastablasta on 2012-08-27
Active domain (AD)  seems to be part of the package of windows servers.
 
and if you plan to use large number of windows desktops you might get good price on those servers.
 
i htink that is why windows servers are used quite a bit in companies.

---

### Post by SeijiSensei on 2012-08-27
> **yc2 said:**
> What are the pros and cons of ASP. How does it differ from PHP?
I hope it is possible to reply without going into too much technical detail. i would like to know its pros/cons and how it is generally structured and how it differs from PHP.

Thanks a lot if someone feels like outlining a little about the differences of ASP and PHP. As I understand it is possible to run ASP on Linux server if Mono is installed?

I've only ever programmed in PHP, but I cannot see any reasons to use ASP on a Linux server.  I also doubt that ASP would provide you functions to access the enormous range of open-source applications and libraries that PHP does.  I would guess that ASP is happy talking to MSSQL and maybe other SQL servers via ODBC.  But does it have native PostgreSQL drivers?  Links to the gd graphics libraries?  The ability to run complex shell scripts?  Access to the mcrypt encryption functions?  I would assume, being a Microsoft product, it wants developers to do things the "Microsoft way."  That's not a road I want to follow.

---

### Post by directhex on 2012-08-27
> **SeijiSensei said:**
> I've only ever programmed in PHP, but I cannot see any reasons to use ASP on a Linux server.  I also doubt that ASP would provide you functions to access the enormous range of open-source applications and libraries that PHP does.  I would guess that ASP is happy talking to MSSQL and maybe other SQL servers via ODBC.  But does it have native PostgreSQL drivers?  Links to the gd graphics libraries?  The ability to run complex shell scripts?  Access to the mcrypt encryption functions?  I would assume, being a Microsoft product, it wants developers to do things the "Microsoft way."  That's not a road I want to follow.

ASP and ASP.NET share only a name.

and [http://npgsql.projects.postgresql.org/](http://npgsql.projects.postgresql.org/) is a starting point.

---

### Post by directhex on 2012-08-27
> **arclance said:**
> Yes but in my experience only 2.0 works "almost as well as windows", 3.5 "works pretty well but not for everything", and 4.0 is "not usable".
[The compatibility page does not even mention 4.5.]("http://mono-project.com/Compatibility")

[http://go-mono.com/status/](http://go-mono.com/status/)

> I am going to try the latest version an see if it works better, hopefully the .NET 4.0 buttons will have labels this time.

Sounds like an Intel video driver bug from a few years ago to me.

---

### Post by forrestcupp on 2012-08-27
> **yc2 said:**
> I have no real knowledge about it. but isn't Mono some kind of implementation of .net??? But if it can do ASP, I have no idea.
Thanks for many replies.

Yeah, if you create your own server, you might be able to get it to work. I'm mainly talking about paying for a hosting service. When you're looking for hosting services, I've never seen any with Linux servers that support ASP.net. Believe it or not, I know people who can work with .net stuff, but not PHP.

---

### Post by arclance on 2012-08-27
> **directhex said:**
> [http://go-mono.com/status/](http://go-mono.com/status/)

Is that for the development version? 
The stable release page I linked to does not list 4.5 as being supported yet.
> **directhex said:**
> 
Sounds like an Intel video driver bug from a few years ago to me.
Nope this was on my laptop with a pre-optimus nvidia card and it was only about 1 year ago.

---

