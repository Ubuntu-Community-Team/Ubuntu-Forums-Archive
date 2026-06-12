---
title: "Ubuntu Server - A meta-package to provide a complete ISP setup?"
date: 2005-12-23
forum: Server Platforms
---

### Post by Entity on 2005-12-23
Hello all,

After using a how-to we can find at [http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10) in order to setup my personal hosting server, I was wondering if it wouldn't be possible to simply include a meta-package that would easily install and create a complete "ISP setup" on Ubuntu server.

Maybe this has been discussed already, but a LAMP setup including a DNS, FTP,mail server and a free web-hosting control panel would be really nice as companies and users could simply install this package and answer a few debconf questions (or use a configuration file?) to have their servers up and running.

Another problem is that a lot of people are asking all the time what they should use for their servers. For example, *BSD vs. Linux? and if Linux, which distribution? Then it comes to which mail or ftp server to use, etc. But I guess, most of them would simply use what has been chosen ?for them? by the Ubuntu team, as long as it's easy to install and integrates well "out of the box".

This possibility could make Ubuntu their server platform of choice for the same reasons Ubuntu has now been the desktop of choice for a lot of people.

I also sent this to the mailing list [http://lists.ubuntu.com/archives/ubuntu-users/2005-December/061674.html](http://lists.ubuntu.com/archives/ubuntu-users/2005-December/061674.html)

---

### Post by nocturn on 2005-12-23
This poses several problems...  What DNS server to provide, enable FTP or not (which actually is a very insecure protocol and should not be used).

In short, an ISP setup is complex, there are an endless number of variations which make such a metapackage difficult to construct, and potentially dangerous (imagine someone not realising that ftp is installed and started by the metapackage).

The best solution is to pick and choose the components that fit your setup the best (I use Apache2+PHP with no FTP and Postfix, MailScanner and Cyrus, but your needs may differ).

---

### Post by Entity on 2005-12-23
I really understand these concerns, but it would be relatively "easy" to make sure that every component defaults to its "most secure" scheme.

As for the choices to make for each component, I think the ubuntu team can make the best choices possible according to their opinion but it's not really the point of what I'm saying since the only thing that really matters is the simple fact that Ubuntu would offer THAT possibility where the others don't.

And a lot of people will simply like it and most important, use it and if neccessary customize it. The same problem occurs with most meta-packages. For example, I think the ubuntu-desktop meta-package is great even though I don't like gnome-games to be installed.

I'm free to remove it whenever I want to.

---

### Post by nocturn on 2005-12-23
[QUOTE=Entity]
And a lot of people will simply like it and most important, use it and if neccessary customize it. The same problem occurs with most meta-packages. For example, I think the ubuntu-desktop meta-package is great even though I don't like gnome-games to be installed.

I'm free to remove it whenever I want to.[/QUOTE]

I understand.  But desktop packages are a lot different form server ones.  Having an extra notepad app on your system may take up some space, but on a server, every redundant app may pose a security risk, more so if it is activated on bootup.

Then, there may be a difference in what you understand to be a server, as to what I understand it to be (my server runs Apache, PHP but also mailscanner, postfix, cyrus, svn, kerberos, nagios, bacula...).

---

### Post by LordHunter317 on 2005-12-23
[QUOTE=Entity]I really understand these concerns, but it would be relatively "easy" to make sure that every component defaults to its "most secure" scheme.[/quote]No, it isn't.  Apache isn't a very secure webserver yet it would inarguably be the one chosen because of popularity.

"Secure" and "'Functional" are frequently at odds, even on the server.

Moreover, many of us use our servers for dedicated tasks and a metapackage would be worse than useless.

A new debian style task with tasksel coulde be useful, however.

---

### Post by Entity on 2005-12-23
[QUOTE=LordHunter317]Apache isn't a very secure webserver yet it would inarguably be the one chosen because of popularity.[/QUOTE]Like I said I understand... but installing a meta-package wouldn't make apache security worst. People must understand what they're doing at some point, when installing a web server. The goal is of this meta-package would be to simplify the installation and give focus to Ubuntu as a web server platform.

What do users do now? they apt-get all needed packages? but what packages is needed exactly to do that? meta-packages would answer that question. An Ubuntu "out of the box" ISP server would be great. Millions of appliances were sold just because of the "out of box" scheme.

---

### Post by LordHunter317 on 2005-12-23
[QUOTE=Entity]Like I said I understand... but installing a meta-package wouldn't make apache security worst.[/quote]No, but it would make security worse if it installs a ton of apache modules that no one needs, unless they're not enabled by default.  And if they're not enabled by default, they just as well may not be installed.

> People must understand what they're doing at some point, when installing a web server.Which would include knowing what packages to install.  And I don't think that's an unreasonable position to take.

> The goal is of this meta-package would be to simplify the installation and give focus to Ubuntu as a web server platform.It wouldn't do either.  Installing the right packages is by far the eaisest part.  I can do that in a few minutes.  IT's securing and configuring everything that takes up easily 90% of my time on any new installation.

> An Ubuntu "out of the box" ISP server would be great.No, it wouldn't.  It would be a configuration and security nightmare--you're trying to solve the wrong problem.

> Millions of appliances were sold just because of the "out of box" scheme.Web servers aren't such an appliance.  Trying to make one such an appliance is rather foolhardy.

---

### Post by dalani on 2005-12-23
> --you're trying to solve the wrong problem.

No he's trying to solve HIS problem: setting up and running a server easily without having memorize syntax from dozens of man pages.  Turn key solutions make a lot of sense for Linux in general. Its lacking somewhat. A few front ends to easily set up and configure basic server functions makes good sense. Why blow him off?

---

### Post by LordHunter317 on 2005-12-23
[QUOTE=dalani]No he's trying to solve HIS problem: setting up and running a server easily without having memorize syntax from dozens of man pages.[/quote] Unless he's lucky enough for the default configuration of *all* the packages in question to be correct for his installations, I'll claim (and be right more often than not) that he'll still end up hunting through documentation and man pages to finish the system configuration.

That's the hard part: the questions asked of any server package currently are insufficent for *every server system* I setup, and I daresay that trying to get even 50% coverage is rather difficult.

>  Turn key solutions make a lot of sense for Linux in general. Its lacking somewhat.Because this isn't anything resembling turnkey or even really timesaving.  I'm still going to have to configure the box; I'm still going to have to know all those arcane details.

---

### Post by Entity on 2005-12-24
Some of your points are understandable, but there is a need outhere for it:

[https://wiki.ubuntu.com/UbuntuInstantServer](https://wiki.ubuntu.com/UbuntuInstantServer)

And helping users to install their servers easilly won't change anything to the security issues you're discussing because to apt-get all packages is NOT more secure than using a metapackage to do it for you!

The suggestion is to SIMPLY help them by making a choice for them and trying to make this installation simplier. It wouldn't be perfect, but helpfull.

[http://lists.ubuntu.com/archives/ubuntu-users/2005-December/061697.html](http://lists.ubuntu.com/archives/ubuntu-users/2005-December/061697.html)

---

### Post by LordHunter317 on 2005-12-24
> **Entity]And helping users to install their servers easilly won't change anything to the security issues you're discussing because to apt-get all packages is NOT more secure than using a metapackage to do it for you![/quote]It will if it installs more than they exactly needs.  Server surfaces should always be as small as possible.

Hell, I'm of the general mind that no server daemon should run on package installation said:**
> The suggestion is to SIMPLY help them by making a choice for them and trying to make this installation simplier.**And you cannot** make that choice correctly, which is the whole point.  If you can't make the choice in an informed manner, *then you do not make it*.

For example, if your ubuntu-lamp package installed mysql, that's a problem for me because I run mysql nowhere.  I do LAPP instead.  Are you going to have both packages now?  How does the user pick?  It doesn't take much logic to see we haven't really reduced the problem any, so we're right back where we started.

LAMP is too much of a choice to safely make.  A simple 'Web Server' task that just installs apache2 (like Debian has) is fine.  But going much beyond that isnt' worth it, and I personally don't see the value of the doing that in the first place.

---

### Post by dalani on 2005-12-24
somebody has made those choices for us  for server packages : [http://flurdy.com/docs/postfix/#conf_imap](http://flurdy.com/docs/postfix/#conf_imap)

This comes close to being a 'meta' ware by establishing in verbose all the standard steps to configure a variety of server apps. Of course if for each package config there are 26 steps, with only a 1% chance of a glitch or install error then in all cumulative probabilty there will be config problems. If we thoughto of these steps as a software app wouldn'y testing all these steps on many hardware combinations result in a fool proof yet secure meta-app????

---

### Post by dalani on 2005-12-24
[QUOTE=Entity]Some of your points are understandable, but there is a need outhere for it:

[https://wiki.ubuntu.com/UbuntuInstantServer](https://wiki.ubuntu.com/UbuntuInstantServer)

And helping users to install their servers easilly won't change anything to the security issues you're discussing because to apt-get all packages is NOT more secure than using a metapackage to do it for you!

The suggestion is to SIMPLY help them by making a choice for them and trying to make this installation simplier. It wouldn't be perfect, but helpfull.

[http://lists.ubuntu.com/archives/ubuntu-users/2005-December/061697.html](http://lists.ubuntu.com/archives/ubuntu-users/2005-December/061697.html)[/QUOTE]

that's very much close to a viable alternative. It would be interseting to see : Instant coffee! plug and play server in thirteen flavors... good concept!

---

### Post by LordHunter317 on 2005-12-24
[QUOTE=dalani]somebody has made those choices for us  for server packages : [http://flurdy.com/docs/postfix/#conf_imap](http://flurdy.com/docs/postfix/#conf_imap)[/quote]Linking to an external documentation describing how to do the setup isn't "someone making those choices for us."  My installations don't look anyhting like that.  I use mailscanner instead of amavis, for example.  I don't run SMTP/TLS anywhere as I have no present need.  I don't have virtual hosted users setup for the same reason.

I don't use MySQL because it's crap.  And I'm hardly alone in my choices.

> This comes close to being a 'meta' ware by establishing in verbose all the standard steps to configure a variety of server apps.**But *not everyone,* or *even a large majority* use that guide**.

Do you see the problem now?  What if I don't want amavais?  Your meta package is no good to me.  So are you going to ask now?  You can't do that with a metapackage, you must have some "server-configure" program that asks you these questions and then installs it.

And yes, what to install is a question that needs to be asked.  Which is the whole point I've been trying to make: ***you cannot even correctly assume which packages to install, so you can't have a metapackage.***

Now, a tool that runs a series of questions and then figures out what to install might be useful, but that's quite a jump from a simple "smart" metapackage.

---

### Post by Entity on 2005-12-25
[QUOTE=LordHunter317]***you cannot even correctly assume which packages to install, so you can't have a metapackage.***
[/QUOTE]Yes you can, or else, "distributions" wouldn't exist because they are all about choices made by few for their users! (What desktop, what default sound server, etc.)

And remember, YOU would be free not to use it, damn it... Some people would love to though. Why not give them that possibility? Because YOU use LAPP instead of LAMP? I mean come on.

---

### Post by LordHunter317 on 2005-12-25
[QUOTE=Entity]Yes you can,[/quote]No, you cannot.  Quick, what's the right webserver in all situations?  Mailserver?  A/V?  Spam scanning?  DB Server?  SCM?  Shell server?  You can't answer any of those, which is my whole point.  

> or else, "distributions" wouldn't exist because they are all about choices made by few for their users!False dilemma.  There's no onus on the distribution to make all the decisions, and most leave most server decisions like this up to the user, quite extensively, in fact.  And that's a good thing, because it's not possible to anticpate the choices to be made sanely.

I don't install apache2 anywhere and get mod_php, mod_perl, mod_python, etc all installed for me as well.

> And remember, YOU would be free not to use it, damn it...If it's a meta package like the desktop ones (which I assumed you were implying, sorry if I was incorrect) then no, becaues it would be installed at startup for me.  At any rate, even if this was a task, my point that it's still too large of a task holds.

> Some people would love to though. Why not give them that possibility?Because you can't adequately do it with a package alone, that's why.  You're doing them a disservice.

>  Because YOU use LAPP instead of LAMP? I mean come on.:rolleyes: If you think that's my only reason, you either need to reread what I've said very closely and think about it, or realize you're painfully out-of-league when considering the issues.

---

### Post by Entity on 2005-12-25
[QUOTE=LordHunter317]No, you cannot.[/QUOTE]Well I think you and I won't change our mind about this anyway. But hopefully you're not in charge for that type of decision. Yes you could say the same thing about me, I know ;)

But if [https://wiki.ubuntu.com/UbuntuInstantServer](https://wiki.ubuntu.com/UbuntuInstantServer) exists I have faith.

MERRY CHRISTMAS :D

---

### Post by LordHunter317 on 2005-12-25
Yes, but the listed Instant servers are at much smaller, saner, and reasonable scopes.  Well, I think the SCM one is probably bunk (there are more issues to consider then, on the level of an ISP one) but a simple WWW task that essentially installs Apache isn't a trick, or an FTP that installs VSFTP.  Taking that one step further is pushing it, however.

---

### Post by dalani on 2005-12-25
[QUOTE=LordHunter317]Yes, but the listed Instant servers are at much smaller, saner, and reasonable scopes.  Well, I think the SCM one is probably bunk (there are more issues to consider then, on the level of an ISP one) but a simple WWW task that essentially installs Apache isn't a trick, or an FTP that installs VSFTP.  Taking that one step further is pushing it, however.[/QUOTE]

I sense a double standard here: its ok to have applications and other OS that offer pre-configured wizards and featuers which may or may not please everyone but when the same is proposed for Linux it's not ok. Which one is it?

By your stance word processors wouldn't exists because ONE set of features does'nt suit every single user and use. Help us here don't impede progress. Since you know so much on the subject i'm sure you see some solutions

---

### Post by LordHunter317 on 2005-12-25
[QUOTE=dalani]I sense a double standard here: its ok to have applications and other OS that offer pre-configured wizards and featuers which may or may not please everyone but when the same is proposed for Linux it's not ok. Which one is it?[/quote]There is no double standard, I even said a specific kind of solution would be a good idea in my own posts.  If you cannot read and comprehend what I wrote, kindly stop posting.

> By your stance word processors wouldn't exists because ONE set of features does'nt suit every single user and use.No, and this is a non-sequitur anyway.  *It's not a question of **features**, it's question of **defaults***.

My whole point is, you cannot have a ubuntu-isp-sever metapackage because you *cannot know* what software is correct to install without asking the user first.  If you decided, "We're going to make these the defaults, regardless of the consequences" and made a package anyway, the fallout would likely be:[list][*]No one would use it, as it wouldn't install the stuff they wanted.[*]You'd end up creating a thousand ubuntu-isp-server packages to deal with all the possible combinations.  This is no better than the present situation.  It's arguably worse.[/list]

*Moreover,* I'm suggesting from a pure usability standpoint, *this is the **wrong thing** to focus on if you want to improve server usability.*  Why?  Because the time spent running 'apt-get install <packages>' is so small on any real server setup that it can be ignored.  

The real time is spent on configuring the services to actually run properly and securely and safely. It takes me maybe 5 minutes to do that, ignoring the time spent downloading and unpacking the things (which you can't do anything about really).  It takes me several hours to change all the configuration files, doing any auditing necessary, performance tune integrate it into the network, etc.

If we assume it takes a normal business day to configure one server from scratch (8 hours) and 15 minutes to decide all the packages that need to be installed, then you're trying to make a task I spend 3% of the time on eaiser.  That's not a very good optimization technique. 

As such, if you want to improve usability and make life eaiser, working on things like better default configurations for services, better debconf questionaires for configuration, and smart wizard-eqsue packages that can handle dealing with complex configuration of multiple services, like would be required of a real mailserver.   A tool that automatically rigged up MailScanner for postfix integration, handled setting up the postfix hold queues, setup SQL Bayes, SQL AWL, SQL SA configuration and vhosts would be far, far more useful to me than a single package to install the stuff I need.

All of those would go much, much further then a simple metapackage of any sort.

> Since you know so much on the subject i'm sure you see some solutionsI do, and I already mentioned them before and I mentioned them again.

---

### Post by Entity on 2005-12-25
It seems that you can not simply understand that apt-getting one metapackage that would install mysql apache and php with the needed modified config files (to make things simply work "out of the box") IS NOT LESS SECURE than apt-getting each individual packages that don't work together "out of the box"!

Do you get my point? :rolleyes: 

The problems you're talking about can be applied to any level... the linux distribution itself, the choices made for your default desktop applications, your default iptables config, etc.

Linux distributions ARE ALL ABOUT CHOICES MADE BY A FEW FOR THEIR USERS like I said... Don't tell me it's not. Users are free to use it or not.

The same way we chose your default music player, web browser, we can choose your default database server... Oh yeah security is a problem, but config files can be tweaked to represant a "minimal" risk for users.

There is a marker for that. SWsoft are making millions a year because their "out of the box" ISP products (i.e. PLESK)! If the market exists, the need exist! And you won't stop it because you have habbits.

---

### Post by dalani on 2005-12-25
I must say I agree with what Entity is saying here because we re essentially agreeing on the same thing: that it is a complex issue that has been solved countless times in the form of distros and/or the desicions of IT professionals daily for installing or configuring servers.
> As such, if you want to improve usability and make life eaiser, working on things like better default configurations for services, better debconf questionaires for configuration, and smart wizard-eqsue packages that can handle dealing with complex configuration of multiple services, like would be required of a real mailserver. A tool that automatically rigged up MailScanner for postfix integration, handled setting up the postfix hold queues, setup SQL Bayes, SQL AWL, SQL SA configuration and vhosts would be far, far more useful to me than a single package to install the stuff I need.

Now imagine I am a computer literate (not expert) customer who walks into YOUR store and asks for a solution to my central email needs at my office. I could have gone for a turn-key solution costing several thousand dollars from REdhat or MS.  But my budget is a fraction of any corporate enterprise solution. So here I am asking like countless others for a 'standard' server. Wheter this can be accomplished with something called a metapackage, a tool or two hours of an ITpros time is moot to me. But because of limited budget, it's not worth the IT pros time to install. So obviously this is an area were a metapackage or scripted expert system can exist. The individual apps and deamons choices are moot to me. Unless it was a server for a bank or something totally mission critical, good usabilty and good security would be good enough. If TEN ITPROS did ballots on wheter they prefer MySQL or other choice, I'm sure a consensus could be reached especialy when there's a demand and the result would be excellent usabilty and secure. Exactly what Entity was saying about Linux distros (equally complex if not more so).

> There is no double standard, I even said a specific kind of solution would be a good idea in my own posts.

I never disagreed with that or propose any different. I said Linux can offer  integrated solutions just like other platforms can, if not better. LIke Entity, I think the Ubuntu Instant server solution is a good approach to make servers accessible to anyone with a desktop.

---

### Post by LordHunter317 on 2005-12-26
[QUOTE=Entity]It seems that you can not simply understand that apt-getting one metapackage that would install mysql apache and php with the needed modified config files (to make things simply work "out of the box") IS NOT LESS SECURE than apt-getting each individual packages that don't work together "out of the box"!

Do you get my point? :rolleyes: [/quote]Sure, but it's apparent **you do not get mine**.

So we start with Apache 2, MySQL, PHP5.  Innocent enough.  But lots of people need mod_perl too, and they need to run web applications packaged in Ubuntu.  So why not include it?  

And here's the problem **if you do include:** now you've installed a DSO that someone doesn't need, and that's a security risk.  The PERL people don't need PHP and the PHP people don't need PERL.  So your metapackage is now a security issue unless it disables both and makes the user pick, **which isn't a usability advantage.**

And here's the problem **if you don't include:**[list][*]Either your package doesn't cover enough people to be useful, or[*]You end up with many packages for all the combinations, which is no better.  It's arguably worse.[/list]

Moreover, an **ISP** package like you suggested goes way beyond just Apache, MySQL, and PHP.  It includes an MTA, which is a big personal preference for a lot of people (many still use *ick* qmail, meaning they wouldn't want one at all).  It includes AV, which very well maybe commercial and means they don't want one installed by default.  It includes spam scanning, which falls in the same case.

So in the original case you suggested, **no, it's a bad idea for a host of reasons, *including security related ones*.**

That's also ignoring you cannot actually performance tune MySQL or Apache until you know what webapplications will be running above.  What I have to tune for Drupal is way different from bugzilla, etc.  So you don't even have enough information to make the decisions you need to be able to make, as defaults.  And the default performance values for both, as shipped by everyone, are just useless.

> The problems you're talking about can be applied to any level...Perhaps, but it's not like they're being applied here incorrectly.  You're narrowing the scope of the problem incorrectly, and ignoring issues.  The moment you install one thing someone doesn't need and configure it to run, you have a potential security issue.  If you don't have it running, you really haven't gained much over what we have.  This is the crux of the issue:  *mearly installing* the software isn't a usability gain, but installing something unnecessary is a risk.

You seem to be ignoring the fact that's even an issue at all, when it's a very real issue.

> Linux distributions ARE ALL ABOUT CHOICES MADE BY A FEW FOR THEIR USERS like I said... Don't tell me it's not.No, they're really not.  If that were true, then why can install any software at all.  Nevermind it's a)  false dilemma b) a non-sequitur by irrelevance, and c) plain silly.

It's perfectly acceptable to not make a choice at all, and in the case where a choice cannot be safely made (such as this one) it's the most prudent action.

You've failed to show why that's not true.

> The same way we chose your default music player, web browser,Neither of which are started for me when I startup, nor can be compromised by an attacker without some sort of user input.

A insecure Apache setup however, is an instant compromise.

> we can choose your default database server...And if I don't like your choice?  *You just made things **harder** for a portion of your userspace.*  In this case, it would be a substantial portion.

> Oh yeah security is a problem, but config files can be tweaked to represant a "minimal" risk for users.Not always for servers, and it still leads back to my original point: you must know how to configure the beast, which is much harder than installing the software at all.

> There is a marker for that. SWsoft are making millions a year because their "out of the box" ISP products (i.e. PLESK)! And Plesk isn't used by everyone because it sacrifices too much control, and people don't like the software it uses.  Which is my whole point.  You're trivalizing the problem way too much.

> If the market exists, the need exist! And you won't stop it because you hav habbits.My habbits[sic] have nothing to do with it and I resent the personal attack.  If all you can cite is my preferences against me, that should show you how weak your position is from a logical POV.

[quote=dalani]that it is a complex issue that has been solved countless times in the form of distros and/or the desicions of IT professionals daily for installing or configuring servers.[/quote]No, it hasn't.  Show me the Linux distribution that automaticall installs postfix, Mailscanner, SA, Postgres and then walks me through the whole configuration to get it working, from the start.   And that's what's needed.  Not just installing all the packages.

There are a few *very-specific, very **VERY** limited cases* where it's been done.  None of which are general or worth talking about at extreme length.

> I could have gone for a turn-key solution costing several thousand dollars from REdhat or MS. But my budget is a fraction of any corporate enterprise solution. So here I am asking like countless others for a 'standard' server.The "standard" is sadly, MS Exchange.  Have a ball.  There is no Linux or UNIX standard, it doesn't exist.  **That's my *whole point***.  

> So obviously this is an area were a metapackage or scripted expert system can exist.The latter, not the former.  The former can't make the decisions necessary.

>  The individual apps and deamons choices are moot to me.They're not to whoever has to support the thing.  Someone is supporting this, right? Talking about one-shot servers that are ignored forever isn't interesting, you could give them insecure open-relay sendmail and they wouldn't care or know.  Talking about the PHB who says, 'Yea go forth and produce a mailserver' isn't intersting either, as he's not making the technical calls.  It's not like I'm denying the need exists, what I'm saying is the solution presented is the wrong one to solve it.

Mail is a *huge* deal by itself, nevermind all the other crap.  Even SMBs pay lots of money to make sure it's properly planned for and dealt with.  They have to, it's their lifebood.  

> Unless it was a server for a bank or something totally mission critical, good usabilty and good security would be good enough.But what is "good"?  Good is a subjective measurment, and I don't measure it the same way someone else does.  If "Good" is your only standard, then go run Exchange.  It's clearly "good enough".  Obviously, that's not a reasonable standard to apply yet.

> If TEN ITPROS did ballots on wheter they prefer MySQL or other choice,You're absolutely crazy.  First, that's a sample size so small as to be worse than meaningless.  It's laughable you'd even suggest it.  Second off, you'll never get a consensus.  If there was a clear consensus on what is best, the DB market would have soldified to a monopoly ages ago.  

Yet we have MySQL, MS SQL Server, Sybase, PostgreSQL, DB II, Oracle, Informix, SAP DB (now MySQL MAX DB), Firebird, ...

Even if we limited ourselves to the choices that are actually suitable for the other software (likely just MySQL and PostgreSQL), you still won't see a hard consensus.  

And there are other factors to consider: I've had UNIX systems working on MSSQL databases simply because *everything* was stored there.  Consistency was more important than anything else.  

Pretending you can actual come up with a reasonable default for these things, to extent to have a working metapackage at a broad of scope as an "ISP server", that won't do anything more than save me a few seconds of package selection, is delusional.

---

### Post by Entity on 2005-12-26
First, I did not mean any personal attack or offense.

[QUOTE=LordHunter317]And Plesk isn't used by everyone because it sacrifices too much control, and people don't like the software it uses. Which is my whole point.[/QUOTE]

They still sale their products alot! So objectively, the market and the need exist. My conclusion is that it can be done with free software on Ubuntu. Simple as that. The issues you discussed are not to be ignored, don't get me wrong.

Don't forget we're talking about an "ISP setup", so let's keep in mind the following:

Most of the time, the ISPs have chosen the web server, the database server, mail server, etc. for their present and potential clients! And a lot of these components (i.e. apache modules) are installed (often more then needed, it's true) simply in order to give their clients the options they need (PERL, PHP, CGI, etc.). There are more than ONE client, and each is different. So to give your clients the multiple possibilities that will make you attractive as an ISP, you unfortunately need to install "most" of the usual components outhere. (i.e. I don't see an ISP today providing web hosting without installing php AND pearl AND cgi AND etc. It's an ISP, not a home user we are talking about.)

And IMHO to provide multiple metapackages for multiple setup is not a bad thing. We see this with other free software in repos these days.

---

### Post by LordHunter317 on 2005-12-26
[QUOTE=Entity]They still sale their products alot! So objectively, the market and the need exist.[/quote]Despite what microeconomics likes to profess, lots of sales can't be used to conclude need for a product.

And I've never denied the need exists.  What I've said is your trying to solve *the wrong* problem if you want something far closer to an instant server.  Just pretend the installation issues don't exist, and worry about the configuration ones.

> My conclusion is that it can be done with free software on Ubuntu. It can, but not solely with the software that is currently provided.

> Simple as that. The issues you discussed are not to be ignored, don't get me wrong.You seem pretty ignorant of the issues then.  You wouldn't suggest a simple metapackage and keep narrowing the problem if you were.

>  And a lot of these components (i.e. apache modules) are installed (often more then needed, it's true) simply in order to give their clients the options they need (PERL, PHP, CGI, etc.).Correct, and that requires the proper tranining and understanding to secure it.  You cannot infer from the fact that people do this that it's a safe configuration to use *in all cases*.  It's an inductive fallacy.

If someone wants to run just PHP, then the system should only install PHP for them.  Simple as that.  If it doesn't, it's broken in my mind.

> It's an ISP, not a home user we are talking about.)I understand that, but all the ISPs in the world have existing setups, so you need to cover a larger use-case than that.  You're still making the problem much, much smaller than it is.

> And IMHO to provide multiple metapackages for multiple setup is not a bad thing.Yes it is when you're talking about literally hundreds of them, which you'd have to do to cover all the combinations.

---

### Post by dalani on 2005-12-26
317 ...We're getting bogged down in specifics and your responses smell of napalm. I did read your posts and returning to my wordprocessor analogy, it's obvious that thousands of combinations exist for every word process use of all menu items. Just as you describe for all the configuration choices of an email server. But that does not exclude the existence of successful word processors. If we discussed the subject the way you are discussing an IMAP server, we'd break open the word processor app into its disparate and complex interrelated parts like menu fuctions, grep and formating.-But it's just another app handling a complex task for the user. I think we agree on that. But if you think of it, Linux is also a collection of seperate parts working together (with chosen components. That what I said when I posted *solved countless times in the form of distros and/or the desicions of IT professionals * Before you misinterpreted that statement. A distros installs software AND DOES CONFIGURE AS WELL. How else could Ubuntu recognize my modem, monitor and security level (even ask me what settings I want etc..). Doing with setting up a desktop exactly as you mentioned here for a mail server.

> Show me the Linux distribution that automaticall installs postfix, Mailscanner, SA, Postgres and then walks me through the whole configuration to get it working, from the start. And that's what's needed

No it doesn't exist yet but the Wiki shows Ubuntu has begun to do so and shows it as a sort of distribution like package.

I think you see a metapackage as too simple for the task rather than a mini-distribution to solve  'standard common needs' (read my lips: I mentioned 'standard' as in common needs eg.LAN mail server. I never once implied a Unix 'standard' . And yes, a  dozen ITpros could produce some good metapackage/Tool/application/iso-meta-distro to implement something functional and SAFE (as in nearly too time consuming for a hacker to hack into for too little return on their time investment). 
> Even if we limited ourselves to the choices that are actually suitable for the other software (likely just MySQL and PostgreSQL), you still won't see a hard consensus. 
I would as a client accept either of these choices and/or care less as long as it gets the job done. 

In your store, you are sending me next door to the 'simpler' expensive Exchange while making a simple need more complicated than it needs to be. If security is the only issue, you seem to imply a shut-down armored computer box as the only solution (no features, installed software or usabilty). Perhaps ISP implementation is too broad a coverage. But what about all those other server uses??? 

Personaly I dont see the fuss. I made the decision a while back to park my website on a webhosting service that cost me less than running my own webserver 24/7 365 days a year. No down time, no DOS attacks and security breaches non-existant. Yet all these CGI,PHP, and ecoomerce apps are accessible to me. So the risks you are talking about seem theoritical to me. Set up a hardened webhosting service if you will. I'm sure there's a need somewhere..

---

### Post by LordHunter317 on 2005-12-26
[QUOTE=dalani]I did read your posts and returning to my wordprocessor analogy, it's obvious that thousands of combinations exist for every word process use of all menu items. Just as you describe for all the configuration choices of an email server. But that does not exclude the existence of successful word processors.[/quote]**And once again, *your word processor analogy is invalid.***


> If we discussed the subject the way you are discussing an IMAP server, we'd break open the word processor app into its disparate and complex interrelated parts like menu fuctions, grep and formating.But we wouldn't, it's not relevant.

***It's not a question of features, but defaults.***  Stop looking at it from a features POV:  that's not the issue at hand.  The problem to solve is providing: ***sane and correct defaults in a metapackage.***  One a solution hasn't been provided for, because it cannot be.

> Linux is also a collection of seperate parts working together (with chosen components. That what I said when I posted *solved countless times in the form of distros and/or the desicions of IT professionals ***No, it doesn't not.  *What distribution does what I ask?***

>  Before you misinterpreted that statement. A distros installs software AND DOES CONFIGURE AS WELL.***No, it does not to the level NECESSARY.  If that were true, then why do I have to touch apache2.conf at all?***

That's the part you're missing: ***The configuration done already IS NOT GOOD ENOUGH, AND THAT IS WHAT NEEDS TO BE SOLVED.***.  I don't need easier installation.  I need something to hold my hand through the mailscanner configuration, through the SA configuration, to setup the DB tables, roles, and passwords, to setup a default backup cronjob to dump the DB anywhere, etc.  ***No one does all of these things already, and they're an integral part of setting up a functional, performing mailserver.***

And doing that would be helpful to me.  Not making the installation easier.

> How else could Ubuntu recognize my modem, monitor and security level (even ask me what settings I want etc..). Doing with setting up a desktop exactly as you mentioned here for a mail server.Yes, but Ubuntu doesn't do that for a server.  It doesn't do enough.  It's rather clear at this point you really have no clue whatsoever what's involved with setting up a proper mail server, or perhaps any sort of server.

> No it doesn't exist yet but the Wiki shows Ubuntu has begun to do so and shows it as a sort of distribution like package.Not at the level or scope he was describing.  At anyrate, even if that's how it's described on the page, the solution won't end up being like that, which was my other point.  You can't solve this with mere packaging.  An actual tool will have to be written.

> I think you see a metapackage as too simple for the taskIt is.

>  rather than a mini-distribution to solve  'standard common needs'That's not what a package is.  So decide which one we're talking about.  It can't be both. 

> (read my lips: I mentioned 'standard' as in common needs eg.LAN mail server.That's not what the word standard means, so don't use it that way.  

> And yes, a  dozen ITpros could produce some good metapackage/Tool/application/iso-meta-distro to implement something functional and SAFE (as in nearly too time consuming for a hacker to hack into for too little return on their time investment). For *their needs*.  ***What about the dozen with different ones?***

> In your store, you are sending me next door to the 'simpler' expensive Exchange while making a simple need more complicated than it needs to be.You said you didn't care about the solution, so I gave you the 'standard' one, which is MS Exchange.  Like I said, "saying I don't care about the tools," isn't a relevant answer here.  Stop with the PHB-think.

>  If security is the only issue,It's not.

>  you seem to imply a shut-down armored computer box as the only solution (no features, installed software or usabilty).I never said that at any point.  Only a slippery slope could reach that conclusion.

>  Perhaps ISP implementation is too broad a coverage. But what about all those other server uses???I noted some could be covered.  But they're at very small scope and I personally question the value. 

> Yet all these CGI,PHP, and ecoomerce apps are accessible to me. So the risks you are talking about seem theoritical to me.**Because *someone else* took the time and work to do it.**

> Set up a hardened webhosting service if you will. I'm sure there's a need somewhere..I have, many times. 

However, doing that OOB is much, much harder for a distribution, *as they must account for all cases*.  You can't say, "mod_perl will always be installed" as some people will not tolerate that.  You can't exclude any potential combination when searching for a solution here.  And you're failing to do that.

---

### Post by Entity on 2005-12-26
OK on my side I had enough, let time proove you wrong :-)

---

### Post by dalani on 2005-12-26
In case you didn't get the concept the first time : a word processor is more complex or is as complex as implementing a server if you had to do it from scratch. Each have have their concerns and tasks. DEfaults is one thing sure. But look at what my webhosting service is providing me: CGI, MySQL, PHP support and so on. What are those? defaults to you but they are features to me the END USER. They figured it out and that's fine by me and all their clients and users. If a dozen or one ITpro did the trick, so what? To you that's a problem because you have a different way to skin a cat. Their choices are quite sane to me: it works. Some decisions were made by developers and I'm sure no one is complaining (otherwise they can find another setup somewhere else). But since you mention defaults, the choices made by my webhosting service could have easily been the choices of a Linux distribution that installs and CONFIGURES over a server base install. To go further than just an install which is what that wiki is aimed. Those programmers or whom ever setup my webhost service choices could just be the Ubuntu developers' blueprint to offer something similar to someone who wants to offer same. The rest is detail.

You seem intent on critiquing every sentence put down while agreeing in principle to what we've been saying and this thread's intent. My point is that an Ubuntu server distro could step through server CONFIGURATION A to Z to satisfy some common needs. That's what meta-package is here. Not just installing a choice of deamons and apps. Heck my Ubuntu 5.04 install disk already has apache! ANd setting up user passwords, defaults for screen resolution was part of MY installation. A distro that does a little bit more or less is still a distro. If you disagree with the term call it what it is: a front end or wizard.

Standards? I think we both misused that term. **Exchange is not a standard**-never was- (which you obviously intended to mean as a popular widely used solution). A standard is an accepted level of quality. In my case, when I said standard server need, I talking about widely accepted need eg. A LAN email server, a simple webserver(with or without spam filters, PHP, CGI etc...), or a network file server . Do you think there a thousand implementations for a thousand users? I'm sure they share similar concerns and needs. If someone can afford the services of an IT pro for a customized setup fine. But sooner or later (if not already) there will be something for those who wont (or can't) shell out for Exchange or pay more.

> You can't say, "mod_perl will always be installed" as some people will not tolerate that. You can't exclude any potential combination when searching for a solution here. And you're failing to do that.

Not tolerate what? An end-user wants something that works. If those who would not tolerate that is another IT guy who thinks he can do better, so what? You keep showing me 1250 piece tool box and saying there are endless combinations. Yet there is need for a handful of basic implementations used in counless ways.

---

### Post by LordHunter317 on 2005-12-26
> **dalani]In case you didn't get the concept the first time : a word processor is more complex or is as complex as implementing a server if you had to do it from scratch.[/quote]**I get it.** ***You don't get that it's an INVALID EXAMPLE.***  Period.  It's not an issue of features.  It never was, it never has been.  The minute you use the word "features", you're instantly wrong.  You already strayed from the issue.  I really don't know how many times I can repeat that.


> Each have have their concerns and tasks. DEfaults is one thing sure.It's also the relevant issue here.  Your handwaving no longer amuses me.

 > But look at what my webhosting service is providing me: CGI, MySQL, PHP support and so on.And you, as the end using of the webhosting service, *are irrelevant*.  This is a non-sequitur.  The relevant party is the  person providing the hosting service.  They care very much about the OS packages provide, and what configurations they ship.

>  What are those? defaults to you but they are features to me the END USER.No that's not true and it's irrelevant anyway so it matters not in the least.


> They figured it out and that's fine by me and all their clients and users.**Right, but *that doesn't help them make THEIR JOB EAISER, and THAT's WHAT AN ISP METAPACKAGE WOULD ACCOMPLISH.***

:rolleyes:  Seriously, at this point I don't know if yo're being obtuse, parading in your ignorance, or just silly.  How does the end user of a webhosting service matter in the least to this?

> Their choices are quite sane to me: it works.And on one cares what you think, because you don't care what they do.  I don't know how many times I can say that's irrelevant.

> Some decisions were made by developers and I'm sure no one is complaining (otherwise they can find another setup somewhere else).Wonderful.  Irrelevant.  The *issue here is what the Ubuntu devlopers are going to do*.

> But since you mention defaults, the choices made by my webhosting service could have easily been the choices of a Linux distribution that installs and CONFIGURES over a server base install.**But they cannot, *becuase they are not suitable to all cases*.  And a general purpose distribution *(i.e., Ubuntu) must handle all cases*.** 

> To go further than just an install which is what that wiki is aimed.Nonsense.  That doesn't help me any.  That doesn't make my job eaiser, as one of these "IT pros" you speak of.  :rolleyes:  What I've repeatedly clamored for would make my job eaiser.

> The rest is detail.Important detail you're ignoring.  You can't gloss these issue over, they're fundamental to desinging the solution.

> You seem intent on critiquing every sentence put down while agreeing in principle to what we've been saying and this thread's intent.And you're unwilling to accept the fact the original solution purposed is totally inadequate, which was my original point in the thread.  There are better ways to achieve the goal posited in the OP, which is what I've been repeatedly saying.

> My point is that an Ubuntu server distro could step through server CONFIGURATION A to Z to satisfy some common needs. That's what meta-package is here.But *that's not what a metapackage is*.  You're clearly confused on what a simple package can do.  You need an actual program, called 'server-setup-wizard' or something.  The issues I raised ***were technical*** ones.  If you don't understand the technical terminology, then stop posting.  You're not qualified to raise any objections.

If that was the whole issue, I apologize for drawing it out.  But the simple matter is a mere virtual/meta/whatever package cannot do what needs to be accomplished.  If you cannot understand or accept that, just stop posting.  If you want to understand why, then read the Ubuntu and Debian policy on development and packaging.  It should be apparent from those documents and the other concerns I raised why an actual tool has to be written.

Which is fine.  A tool to do that would be a great thing.  But calling it the right thing is important, and understanding what it needs to be capable of is important.

> If you disagree with the term call it what it is: a front end or wizard.Yes, I do disagree and your misuse of the terms doesn't help the issues any.

> **Exchange is not a standard**-never was- (which you obviously intended to mean as a popular widely used solution).Yes, it is said:**
> A standard is an accepted level of quality.No, it's not.  It has many more definitions.

>  In my case, when I said standard server need, I talking about widely accepted need eg. A LAN email server, a simple webserver(with or without spam filters, PHP, CGI etc...), or a network file server .Which while valid, was an ambiguous and vauge use of the term.  Saying, "common need" would have avoided the ambiguity.  Diction is important, especially online.

> Do you think there a thousand implementations for a thousand users?Yes.  I've probably implemented or worked with 950 of them. 

> But sooner or later (if not already) there will be something for those who wont (or can't) shell out for Exchange or pay more.That doesn't make a canned, fixed, limited package an acceptable solution for Ubuntu.

> Not tolerate what? An end-user wants something that works.Which in a host of situations, includes not having any extra software installed.

> If those who would not tolerate that is another IT guy who thinks he can do better, so what?***Because Ubuntu must cater to them as well.***

> You keep showing me 1250 piece tool box and saying there are endless combinations. Yet there is need for a handful of basic implementations used in counless ways.***And you HAVEN'T shown your basic implementations are actual that, or that they satisfy a sufficent number.  Seeing as you're claiming this solution as adequate, the onus is on you to do so, and you have not.***

---

### Post by dalani on 2005-12-27
"70% of all connections to the Internet are primarily to check eMail. Web or POP3/IMAP Email is an important aspect for ISP's, businesses"

That's from [@Mail own documentation]("http://support.atmail.com/faq.html#14"). I'm sure you've heard of @Mail which basicly rolls out an Email server built with a MySQL backend (which you don't agree with). It is A SOLUTION which addresses A COMMON NEED. It is comprised of a few of the various Open source software available and as such are CHOICES made by the @Mail developers.

You seem to find that troubling that someone would solve a common problem with choices you might not agree with. I'm sure Ubuntu would have their SOLUTION for configuring an EMAIL server for a ISP that might differ from @Mail. I'm sure it would be as good if not better. I'm sure you have yours. Instead of using napalm, present your solutions or don't. That's your choice.

---

### Post by LordHunter317 on 2005-12-27
[QUOTE=dalani]It is A SOLUTION which addresses A COMMON NEED.[/quote]Wonderful, and it's relevant how?  It's only relevant if you're going to suggest *Ubuntu use @Mail's software **for everyone, INCLUDE PEOPLE WHO ARE NOT NOT NOT ISPs,*** 

> It is comprised of a few of the various Open source software available and as such are CHOICES made by the @Mail developers.Wonderful.  Configuration still has to be done.  You're not  further your points any (because you don't have any to further) you're just rehashing things you've already said.

I'm well aware distributions make choices.  My point is ***choices they don't have the information to make, they shouldn't make***.  You still don't seem to be grasping that.

> You seem to find that troubling that someone would solve a common problem with choices you might not agree with.No, I don't.  What I have a problem with is people forcing those choices on me, or making it more difficult to use my choices.  This is one of the reasons I stopped using Red Hat, because using sensible KDE was far too difficult.

> Instead of using napalm, present your solutions or don't. That's your choice.I have.  You're the one who's ignoring them and continually bringing up tagential, irrelevant, agreed upon issues.

---

### Post by dalani on 2005-12-30
ALL YOUR OBJECTIONS ARISE FROM THE INABILITY OF SUCH A DISK TO ACCOMODATE VARYING NETWORK TOPOLOGIES AND CONDITIONS. 
Show me where in Ubuntu&#8217;s agreement  their disks (or future ones) must accommodate every possible condition. Where I work we run W2000 on a LAN. Now such a disk, where it to exist, could turn a spare computer into an email server. And BTW, the services worked out by my webhosts could be applianced on any computer that ubuntu can install on (perhaps with limits on performance). Same for a email server.  I can't justify wasting a day configuring an Ubuntu server but pop in a disk answer a few questions (Clam? spammassassin? no to both questions my ISP provides that, how many users?) and let the thing run. Issues like importing messages from OE6's Inbox should not prevent such a solution and are minor even if they are particular to a single installation. 

You say Exchange is a &#8216;defacto standard&#8217; (wrong term check your dictionary) yet object that MySQL is the choice of most of the linux email server HOW-TOS .  Contradictory! which one is it? BTW it would be easier to trouble shoot a MySQL,Postfix, etc.. setup than some obscure off the wall choices of some 'purist'.

---

### Post by LordHunter317 on 2005-12-31
> **dalani]ALL YOUR OBJECTIONS ARISE FROM THE INABILITY OF SUCH A DISK TO ACCOMODATE VARYING NETWORK TOPOLOGIES AND CONDITIONS.[/quote]Right, ***because mail and web are really, really, REALLY complicated things.*** As such, any solution will be complicated  to some degree.  You cannot simplify the problem such that a single package will do away with the issues.


> Show me where in Ubuntu’s agreement  their disks (or future ones) must accommodate every possible condition.It doesn't, it's not an issue of what Ubuntu agrees to.  **It's an issue of what's *useful*, and the originally suggested solution *was not useful.***  Pure and simple.

Let's assume we'll only support one fixed set of software: Postfix, MailScanner, MySQL, ClamAV, Spamassassin.  The configuration tool still must accomidate all these situations:[list][*]Maildirs and mboxes[*]Many ISPs use a commerically purchased email solution, meaning at the very least it must have the capability to not configure any AV solution, and leave it to the sysadmin to do later.  From that, it follows it's reasonable that it shouldn't even install ClamAV in the case it won't be used.[*]It has to handle all the update configuration for the virus scanner.[*]It has to handle all the spam preference and network configuration. This includes configuration of things like SQL Bayes, SQL AWL, SQL SA configuration/customization.[*]It must support the situtation where a commercial spam agent is used and kill spam scanning entirely.  Ideally in this case, it would shut mailscanner off and feed viruses to the virus scanner in another fashion, as MailScanner becomes wasted resources at this point.[*]It must support sites that don't use virtual hosts at all.  This means two very important things: a) making local mail not be a vhost (as many guides do, and are wrong for doing so: it breaks the "expected" semantics), and b) Not installing the database if virtual hosts aren't used.[*]It must support LDAP vhosts/configuration, as that's important for many ISPs these days.  (From this, we can see it ought to support any database postfix supports as well, as it's rather silly not to at this point).[*]If any of these packages are already installed, it cannot break an existing configuration without asking the user.  Ideally, it doesn't make any changes at all and instead says, "I would do this, but you've already changed something, so I didn't."[/list]That's a bare minimum to be functional in all cases.  Anything below this isn't functional enough to be worthwhile.  It's not better than what I already get with Debian and/or Ubuntu.  It doesn't save me time.
And hey look, it doesn't cover:[list][*]Webmail[*]Any other "ISP" tasks.[*]Graylisting[*]SMTP TLS[*]Mail retrevial (i.e., POP3/IMAPv4).[/list]And we can conclude from the above requirements:[list][*]A "metapackage" will not suffice, as the packages to install cannot be known until the user is queried.[*]Such a tool will be difficult to write to cover even a majority of user's needs.[/list]Which is why it hasn't been done: Mail is a complicated things and has a ton of solutions because there are a ton of problems and use cases.    Even if you limit your target audience to "ISPs", you can't narrow the issues enough to come close to a one-size-fits all solution without a ton of difficult, complicated work.


> Where I work we run W2000 on a LAN. Now such a disk, where it to exist, could turn a spare computer into an email server.Bully for you.  ***What about My needs***?  And my customers' needs?  And the Fortune 50's needs?  And other people with far more complicated cases than are quite common and you haven't even considered?

> And BTW, the services worked out by my webhosts could be applianced on any computer that ubuntu can install on (perhaps with limits on performance).No, they cannot.  You cannot tell what's running, so you cannot make any sane performance tuning of Apache or a DB server.  You have no clue what you're talking about.

> I can't justify wasting a day configuring an Ubuntu server but pop in a disk answer a few questions (Clam? spammassassin? no to both questions my ISP provides that, how many users?) and let the thing run.But it's not a few questions, ***and that's been the entire issue***.  You're making the problem too simple: You've only solved it for the admin wannabes who are setting up these complicated servers for themselves, their friends, and maybe one customer.  You haven't considered enterprise needs or solutions.  The fact you keep looking at such a small, limited case tells me that.  It's apparent you have no clue how much literature, time, and effort has been devoted to these issues.  The material on Exchange alone (one product) published by Microsoft (one publisher) could fill a small library.  It's massive, because Exchange tries to handle as many cases as possible.

> Issues like importing messages from OE6's Inbox should not prevent such a solution and are minor even if they are particular to a single installation.How is this relevant in the least?  Total non-sequitur.  We've never been talking about end-user issues. 

> You say Exchange is a ‘defacto standard’ (wrong term check your dictionary)Yes, it is the *de facto* standard.  I've yet to work at a corporation in my lifetime that hasn't used exchange at least in part.  There'se only a select few major corporations that don't.

> yet object that MySQL is the choice of most of the linux email server HOW-TOS.I never objected anything of the sort.

> Contradictory!They're not in the least.   At this point, a course in reading comprehension and logic would do you good.  MS Exchange can be the de facto mailer, and MySQL can be the de facto standard DB used for vhost configuration on Linux without any contradiction.  It would only be contradictory if the latter implied the former wasn't the de facto ***mailer***, which isn't the case said:**
> setup than some obscure off the wall choices of some 'purist'.My choices are hardly obscure.

---

### Post by dalani on 2005-12-31
> Right, because mail and web are really, really, REALLY complicated things. As such, any solution will be complicated to some degree. You cannot simplify the problem such that a single package will do away with the issues.

I never said it was simple. Read my posts again. If anything I repeateldy stated it was a complexity that could be managed. 

> You've only solved it for the admin wannabes who are setting up these complicated servers for themselves, their friends, and maybe one customer.

Which is are end-users who CHOOSE to do it for themselves. And BTW  **SO given time, the issues you raise can be delt with. Which is the point I've been making.**

> What about My needs? And my customers' needs? And the Fortune 50's needs? And other people with far more complicated cases than are quite common and you haven't even considered?

I have to repeat myself again?? I wasn't refering to large sensitive installations but rolling a server on a new install.

 BTW, dismissing end-user concerns and needs is downright stupid and not condusive to anything,trust or helping *your* needs. Because it from end-user (eg. ISPs or a LAN mail server admin) needs that SOLUTIONS are originated.  In small installations, the IT hat is commonly worn by end-users. 

> 
[QUOTE]
Issues like importing messages from OE6's Inbox should not prevent such a solution and are minor even if they are particular to a single installation.
How is this relevant in the least? Total non-sequitur. We've never been talking about end-user issues. [/QUOTE]

There are instances where a orgs or companies email messages are not trivial but are LEGALLY required to be archived and kept accessible for over five years
If their legacy apps are replaced and file formats change what then??

Exchange is widely used  so are all the packages in that  Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail + Postgrey how-to. Yet you DID dismiss that these choices be made BEFOREHAND. Yet Exchange is a choice as well that you accept. Yes.. that contradiction!

---

### Post by LordHunter317 on 2005-12-31
[QUOTE=dalani]I never said it was simple.[/quote]No, you never explictly said that.  But that's not what I said, either.  **What I said was, *you're oversimplfiying the problem to be solved.***

> If anything I repeateldy stated it was a complexity that could be managed.But you've said this without considering all the facets of the problem. 

> Which is are end-users who CHOOSE to do it for themselves.***But that's NOT ENOUGH USERS TO MATTER.*** And no, those weren't the end users I was referring to prior, so don't even go there.

Frankly, I only care about an enterprise-level setup.  Give me that and the casual peopel fall in to place as well, assuming the tool is good.  You're looking at it from the other direction, and that's not very useful here.  This isn't the sort of thing where it's trivial to bolt on new stuff later unless you planned for it from the beginning.

> And BTW  **SO given time,It shouldn't take time.  The 1.0 release must do everything I suggested above.  That's all [b]*basic, core*** functionality.

> the issues you raise can be delt with. Which is the point I've been making.No, you haven't.  You haven't even made it clear you're aware of all the issues that must be dealt with.  And in several cases, you've made it clear you not only don't grasp all the issues, you don't understand why certain solutions don't work (e.g., pretuning apache).

> I have to repeat myself again?? I wasn't refering to large sensitive installations but rolling a server on a new install.[b][i]AND FOR THE LAST TIME, YOU'RE NOT CONSIDERING ENOUGH USE CASES.

YOU MUST CONSIDER THE "large sensitive installations" AS WELL.
YOU MUST CONSIDER THE "large sensitive installations" AS WELL.
YOU MUST CONSIDER THE "large sensitive installations" AS WELL.[/i][/b]

This is my whole problem with everything you've said this whole time: you're ignoring cases that cannot be ignored.  If anything, you're ignoring the far more important cases.  More people need setups without virtual hosting than with, for example.  Enterprise setups must have LDAP support or you haven't gained them a thing, for example.  

It's fruitless to talk about cases that exclude them.  It's just not good design for a tool of this sort, as it's hard to write the tool in such a manner that supporting the enterprise later will be easy.

>  BTW, dismissing end-user concerns and needs is downright stupid and not condusive to anything,trust or helping *your* needs.But it is ok to ignore them, ***Because the server-side software has zero impact on the concerns you raised.***

How does say, courier vs. davecot have any bearing on your ability to import messages to/from OE6?  It doesn't.  And those are the types of issues I'm saying can be ignored.

And this is my other problem with you: in a technical discussion, it's clear you don't have the faintest clue how the components even connect together, much less how they actually work.

> Because it from end-user (eg. ISPs or a LAN mail server admin) needs that SOLUTIONS are originated.Not all of them, hence non-sequitur by irrelevance.   That's ignoring the fact that the *origin* of the need is irrelevant, mearly it's existance is (Non-sequitur again).

> In small installations, the IT hat is commonly worn by end-users.Non-sequitur by irrelevance.  They're seperate roles, and what else the person responsible for the box doesn't matter in the least. 

> There are instances where a orgs or companies email messages are not trivial but are LEGALLY required to be archived and kept accessible for over five yearsWonderful.  I've worked in such situations before, you know.  I've worked in situations with document retention policies far more complicated than you can probably imagine.

> If their legacy apps are replaced and file formats change what then??Well beyond the scope of a server configuration tool, unless it covered backups.  Even then, I'd still say it's beyond the scope of a mail server configuration tool.  Archiving of data is it's own seperate problem domain.

And the file format for mail on Linux won't change any time soon, as it's just text (ignoring Cyrus, which stuffs it in a DB).  This is why you use IMAP and force the mail to stay on the server: retention is easy this way.  

> Exchange is widely used  so are all the packages in that  Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail + Postgrey how-to.Wonderful.  They're *not as widely used as Exchange*, despite whatever you may wish is true.

> Yet you DID dismiss that these choices be made BEFOREHAND.No, I dismissed the notion that ***Ubuntu should be making them for their userbase***, which is what an automatically installed metapackage would do (the solution proposed originally).  That's unacceptable to me, at the level originally selected.

> Yet Exchange is a choice as well that you accept. Yes.. that contradiction!There is no contradiction when you take my full statement and take the context it was made in.  There's only a contradiction because you refuse to take anything I say in full.

---

### Post by hostile on 2005-12-31
If you need a meta-package to "Set up an ISP ootb", you shouldn't be "running an ISP" in the first place.

Period.

;)

---

### Post by Jammy_Stuff on 2005-12-31
Bit of a noobish question, but if I'm following the instructions that you posted about on the first page. Where they would put "server1.example.com" what would I put if I just wanted it to run on my local network? Would it just be server1.localhost?

---

### Post by lorenco on 2006-01-03
A couple of Brief comments:

1. I tried to get ISP setup numerous times without success. (A meta package to setup a basic system will be helpful)

2. Posting an essay on every reply makes people  go to sleep and skip the post... (Sorry LordHunter317, but I got tired reading all your long winded posts ...) 

3.  I agree that a server sould not be "defaulted" to anything.  

4. I think you lost the original plot :

Having a metapackage will greatly increase the ability to "Demo run" a server. Yes if you run a production system you should accept the disclaimer... not to use the defaults.  (Surely it should be possible able to have a couple of options in the meta package as well, like MySQL vs Basic Auth, Virtual Domains vs Single... etc ?) 

Do not install the Metapackage by default and leave it there for people (like myself) that would run this on my Personal web site and for my Personal mail to install...  If you don't like it and want to run other funny stuff you can even write and compile your own (see my sarcasm here ;)  )

The bottom line :
**So give people freedom to choose, is this not what we are aiming for in running this beautifull thing called Ubuntu ?  (Ouch)**

---

### Post by LordHunter317 on 2006-01-03
[QUOTE=lorenco]2. Posting an essay on every reply makes people  go to sleep and skip the post... (Sorry LordHunter317, but I got tired reading all your long winded posts ...) [/quote]If you're not willing to read the material, then kindly stay the hell out of the thread.  Seriously.  Few things anger me more.

> Having a metapackage will greatly increase the ability to "Demo run" a server.Wonderful.  I think the number of people needing to "demo" a mail server is zero.  If it's not, it's close enough to consider it as such.

> (Surely it should be possible able to have a couple of options in the meta package as well, like MySQL vs Basic Auth, Virtual Domains vs Single... etc ?) Not without leaving excessive software installed, which a potential security risk and a major auditing problem for those of us with such hassles.

Which is why an actual metapackage will not work, which was my original point.  A tool that does all this configuration will work, but it must be a plain tool in a single package that in it's course-of-duties, may install software on the system.  Which is a perfectly acceptable and reasonable solution.  In fact, it's really the only acceptable one to this problem.

> The bottom line :
**So give people freedom to choose, is this not what we are aiming for in running this beautifull thing called Ubuntu ?  (Ouch)**This was the other half of the issue: the solution originally purposed was a risk at making it harder to make choices.  Server software isn't like desktop software, and it's really easy to corner oneself where choices can no longer be made.

---

### Post by davidcollantes on 2006-03-31
I think this would a be a nice thing to have, that is, a meta-package to provide a complete ISP setup. Has anything like it been done?

---

### Post by etcpool on 2007-03-12
why bother arguing this?

we are not talking about perfection.

we are talking about making use of something to someone, of course! it's not exactly suitable for everyone or even the most.


:confused:

---

