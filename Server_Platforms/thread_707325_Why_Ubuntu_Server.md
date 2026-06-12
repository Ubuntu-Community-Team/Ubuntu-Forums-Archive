---
title: "Why Ubuntu Server?"
date: 2008-02-25
forum: Server Platforms
---

### Post by AbtZ on 2008-02-25
So it's that time of day again -- I'm perusing the Ubuntu forums whilst enjoying a nice cup of (black) coffee.

I also ended up in a discussion with a friend who, admittedly, has a lot more experience than I when it comes to operating a server. The topic of Ubuntu Server came up and he said there are lots of better server options out there. ("C'mon, it doesn't even have a GUI!")

My question is this: Why Ubuntu server? 

Why should I choose it?

What's it's strong points? Weak ones?

I'm curious, as I'm planning on setting up a server of my own sometime soon. :)

---

### Post by Brazen on 2008-02-25
To the "it doesn't even have a GUI" I would reply: "Just look at Windows, you can't even remove the GUI!!"  Ubuntu server, of course, does have many gui options, it just does the sensible thing and does without a gui by default.

---

### Post by jonabyte on 2008-02-25
Servers really don't need a gui since you don't "sit" at it all day and use it like you would your desktop.
This alos helps to free up resources for you server to do other things.
But you can install a gui if you wish too.

Why Ubuntu? I have been using it now for two months and it is very stable and maybe most importantly is the support, these forums are very good compared to other distro's.

---

### Post by astrotech226 on 2008-02-25
I run 35 servers and there's not a gui on a single one of them.  If you want to squeeze out more free cpu cycles and free up ram, you don't want an X server running.

Ubuntu server is also geared towards running your computer as a server.  It will ask you in what capacity do you want to run the server as, such as supporting databases.  It will install those just those packages.

I've run many servers with many different distros and I've recently settled on Ubuntu.  Gentoo is nice if you want the ability to customize every aspect of the server, but it takes two or three days to get it up and running.  Ubuntu takes less than a half hour on my equipment.

I've been bit too many times with rpm based distros when enough time passes where upgrades become impossible.  And many of those distros need 5 cds or dvds to install.  Ubuntu is really compact.

I haven't really found any weak points to Ubuntu server.  It's Linux at the core so you just need to learn the Debian way of doing things as far as managing packages and how the init system works.

I absolutely love it and don't intend to go back to Gentoo or any other rpm based distribution.

---

### Post by faulkes on 2008-02-25
1. Committed community of developers and commercial support available.
2. Committed community based support (forums, irc, mailing lists).
3. Fixed release schedule.
4. Debian based with excellent working relationship with the Debian team.
5. Excellently maintained official and community documentation.

I won't enter into the GUI / No GUI discussion as I don't see it being relevant to
choosing a linux server - all of them are capable of being run with and or
without a GUI.  Ubuntu just defaults to not installing one (which is easy to do
if you choose).

Faulkes

---

### Post by FakeOutdoorsman on 2008-02-25
> **astrotech226 said:**
> ... And many of those distros need 5 cds or dvds to install.  Ubuntu is really compact...

This isn't always true.  For example, CentOS, one of the most popular free RPM based server distros, comes as 6 CDs, but you only really need the first disc.  It will ask for the other discs if you decide to install extra items besides the base install.  You may need more discs if you use the preselected packages in install, but I don't remember.  You can even do better than that by just getting the netinstall iso which is only 24 MB and selecting none of the boxes for package selection.  It will install just the minimum for you to build on.  However, in my experience a "minimum" install of CentOS is much bigger than a minimum Debian or a command-line only Ubuntu.

> **AbtZ said:**
> What's it's strong points? Weak ones?
These will look similar to other posts:
1. Excellent support, from Canonical, developers, and the community.
2. Faster release schedule and more up to date software (will be seen as a negative by some: less testing, etc).
3. Large number of packages in official repository.
4. The best Linux community (in my opinion).
5. The best package managers: apt/aptitude
6. Familiarity for those used to Ubuntu Desktop.

A few potential negatives compared to Debian:
1. Often considered less stable than something like Debian Etch because of the extensive testing Debian packages go through.  On the downside you can end up with some ancient packages.  Also, their release schedules aren't the same, so it's harder to compare.
2. The command-line install of Ubuntu has more packages installed than a minimum Debian.  This can also be viewed as a negative or a positive.
3. Ubuntu officially supports 3 processor architectures for its server; Debian supports 11.
4. I believe Debian has more packages in it's "main" repository compared to Ubuntu.
5. No netinstall iso!*****

***Update**: Ubuntu does have a [minimal cd image]("https://help.ubuntu.com/community/Installation/MinimalCD").  Why haven't I heard of this before?

---

### Post by koenn on 2008-02-25
> a friend who, admittedly, has a lot more experience than I when it comes to operating a server ...  he said there are lots of better server options out there. ("C'mon, it doesn't even have a GUI!")
I would not pay too much attention to the opinion of someone who thinks "having a GUI" is a requirement for a server. 
I also don't really trust sysadmins who play solitaire or mine sweeper or surf the web from a server, and have serious doubts about OS vendors that think a server needs to have those programs installed by default.

---

### Post by devnevyn on 2008-02-25
I don't want to be rude, but I happen to be OP's GUI-loving friend, and I can't help but feel like you're all very 80's in here. Either that, or you're deliberately misinterpreting his questions in order to make Ubuntu appear a better server OS.

Take what I say with a grain of salt. I'm a Mac guy, I've administered a few bsd boxes in my days but I'm no expert. All I know is, configuring a mail server on the command line was among the most painful experiences I've had. I never felt in control of my server, I just knew it lived -- for the moment. My 'production evironment' was a garbled mess of shell scripts and a few PHP guis.

I'm sure that I, even in shiny Mac-land, I'll surely have to dig up the terminal if I want to do something advanced, but for most tasks, I can breeze through my GUI in no-time, and being able to do that feels great. If you're curious as to what kind of tools I'm talking about, I threw up a few pictures at [URL="http://nevyn.nu/ServerGUIIsUseful/"]http://nevyn.nu/ServerGUIIsUseful/, e g this one:
[IMG]http://nevyn.nu/ServerGUIIsUseful/Picture%201.thumb.png[/IMG][/URL]

Is there anything like this for Ubuntu? Not "There's a php interface on top of cyrus which you can apt-get, and the SMB log can be piped through a cgi script", but a nice, consolidated GUI for getting a feel for the server's health and administering basic tasks. That would be awesome. Even though Abtz would learn much from doing it the hard way, learning all the common config file syntaxes, I'm sure he'd appreciate a simple tool for just getting things done when there's just not enough time to sit down and read a twenty-screen man page.

---

### Post by koenn on 2008-02-25
OK, that puts some perspective to the GUI thing. 
Grantend that a GUI can be helpful for complex tasks you don't do often. Still, in de end, GUI or no GUI, your still assigning values to parameters. Knowing what params you need to configure, and how & why, matters more than whether you do it in a text field on a colorful dialog box or as simple text in a plain text file. A Wizzard to help you through a procedure can be helpfull if it's something you don't do often, but it shouldn't be a requirement. Saying Ubuntu is "not a good choice for a server because it doesn' even have a GUI" is, in that respect, nonsense, i think. (There are some other reasons why Ubuntu wouldn't be my first choice for a server, but that wasn't my point)

Of course, a lot also depends what sort of server and what kind of context  you're talking about. If your talking about servers as in work horses that need to (eg for a file server) serve gigabytes of files to hundreds or thousands of users you just set it up to do just that, and you don't really need the GUI overhead.  And that's about efficiency rather than about being 80's  :-)
If your server is a glorified workstation -- be it at home or in some small business without trained IT personel -- that today needs to be configured to serve a website, tomorrow you want to add some file shares, the next day you want to let it stream media and over the weekend you'll add a mail service to it, then a point and click wizard to set up each of these tasks might be an advantage.

---

### Post by koenn on 2008-02-25
> **devnevyn said:**
> 
Is there anything like this for Ubuntu? Not "There's a php interface on top of cyrus which you can apt-get, and the SMB log can be piped through a cgi script", but a nice, consolidated GUI for getting a feel for the server's health and administering basic tasks. 
I think Canonical is working in something like that - or even 1 stap further : an integrated GUI environment to monitor and manage multiple servers : [http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)
although it doesn't seem to deal with the configuration of specific server roles / tasks as such.

---

### Post by devnevyn on 2008-02-25
I think you're missing the whole point of using a GUI, koenn. Administering a server might often consist of simple tasks, but it's my strict belief that a great GUI beats the commandline, unless you write your own scripts to hasten your specific common processes. (Also, being that there's no common format for config files, it's rarely as trivial as one would wish to just 'assign a value to a key' :P)

Also, visualizing data helps you get a perspective; a picture says more than a thousand words. That network throughput graph on my dashboard, for example, gives me a split-second sanity check if something is running amok or simply strangely.

Also, wizards are most often an abomination and a sign that your UI sucks.

By the way koenn, what /would/ you use for a server OS?

Edit: said I, seconds before you posted Canonical :P Looks nice on a first glance.

---

### Post by Brazen on 2008-02-25
> **devnevyn said:**
> I don't want to be rude, but I happen to be OP's GUI-loving friend, and I can't help but feel like you're all very 80's in here. Either that, or you're deliberately misinterpreting his questions in order to make Ubuntu appear a better server OS.

Take what I say with a grain of salt. I'm a Mac guy, I've administered a few bsd boxes in my days but I'm no expert. All I know is, configuring a mail server on the command line was among the most painful experiences I've had. I never felt in control of my server, I just knew it lived -- for the moment. My 'production evironment' was a garbled mess of shell scripts and a few PHP guis.

I'm sure that I, even in shiny Mac-land, I'll surely have to dig up the terminal if I want to do something advanced, but for most tasks, I can breeze through my GUI in no-time, and being able to do that feels great. If you're curious as to what kind of tools I'm talking about, I threw up a few pictures at [URL="http://nevyn.nu/ServerGUIIsUseful/"]http://nevyn.nu/ServerGUIIsUseful/, e g this one:
[IMG]http://nevyn.nu/ServerGUIIsUseful/Picture%201.thumb.png[/IMG][/URL]

Is there anything like this for Ubuntu? Not "There's a php interface on top of cyrus which you can apt-get, and the SMB log can be piped through a cgi script", but a nice, consolidated GUI for getting a feel for the server's health and administering basic tasks. That would be awesome. Even though Abtz would learn much from doing it the hard way, learning all the common config file syntaxes, I'm sure he'd appreciate a simple tool for just getting things done when there's just not enough time to sit down and read a twenty-screen man page.

There is Webmin for that.

---

### Post by koenn on 2008-02-25
As it happens, I like scripts for repetitive tasks. I run a few Windows servers at work, and if i need to add 1 user, I'd click through the "New User" procedure - If I had to add multiple (say, 20+) users with profile paths and home dir paths all following the same format, I'd use a script. Problem with Windows is that scripting is a pain, while on Linux it's easy so the threashold on Linux would drop to 10 or even 5 users. Or even just 1 : typing "adduser" and adding some stuff at a prompt is faster than clicking through a tabbed dialog with 12 tabs.

As for the config files - although there is no real common format, they all (or almost all) follow the keyword:value paradigm, and most of them list just about all configurable options with sensible defaults or commented out so that enabling them is as easy as removing the # or ; . Going through them to modify a few values or enable/uncomment them is not that hard, plus it shows you what else is configurable and makes you think about whether those default values in there are actually a good idea. A lot more transparant than dialogs with "the hard stuff" hidden behind 'Advanced' buttons, IMO.


What I would use for a server OS ? Depends what that server is supposed to do - and the context. I run a Debian + Samba + AD Integration as a file server at work, mainly as a workaround because the Windows file servers lacked disk space and I wanted a quick, cheap sollution + I'm familiar with how Debian works. (No GUI : it just needs to serve those files). We also have Redhat + Oracle rdbms - that choise was made by a vendor mainly but I'd probably would have opted for RH myself - for support. If I were to add a server, probably it would be Debian or RedHat again, Debian because it's stable and familiar ground to me, RH because its an industry standard with professional support so I'm not on my own and in the cold if something goes really wrong.
Or it could be yet another Windows server - depends on the apps it needs to run, and how those need to cooperate with other apps already present in the environment that server will be in - if I had to choose between a perfect fit on Windows and a "probably just as good but I'm not really sure'  linux alternative or something linux that needs extensive workarounds to play nice with an important Windows application we're already using, I'd probably go with Windows still. 

All of this in real life, of course. At home, I'm quite happy with some (GUI-less) Debian systems to play datacenter with, and, I admit that on some of them, I run e.g. a GUI file browser that I export to my desktop PC because sometimes visual aids help - but even then i'd use cp or mv rather than Copy or Move from the file browser - I've had a file browser crash on me in the middle of a large copy or move operation once too often  :-)

---

### Post by FakeOutdoorsman on 2008-02-25
I agree with Brazen that Webmin can replace most of the functionality of the GUI.  Or perhaps Webmin can be considered the middle-ground.

I suppose using a GUI isn't bad for a hobby or beginner server, but in a produciton environment where stability is required a GUI is just an extra, and memory heavy, aspect that can introduce more problems that it solves; especially on older hardware.

---

### Post by dmizer on 2008-02-25
specifically with web servers (or any server exposed to the internet), the question of gui is a question of security.

gui comes with an astronomical amount of little daemons and servers, tools, programs, and scripts all ripe for exploit.  if you want a web server, you want it to have as absolutely low a profile as possible.  anything beyond what is absolutely necessary for rendering a web page will provide a potential inroute for a hacker to compromise your system.

you may shrug your shoulders at that and call me paranoid, but a very small mistake in your php code, incorrect permission levels, or a security hole in apache, php, or mysql can be easily exploited.  if you have a gui running, your server can quickly become a hacker plaything.

this can be countered somewhat with a very carefully configured apache, as well as by running your server in a chroot jail.  however, chroot is difficult to setup, and not all web applications (cms and forums) will work correctly when apache is jailed.

i use ubuntu server becuase i'm familiar with ubuntu.  but now that i know more about serving a website, and after having been hacked a few times i would suggest reaching for something far more minimal in a web server.  something like debian or slackware.

edit:
i don't see any problem with using a gui on internal file and media servers.  in which case, there are lots of gui configuration tools.  in linux however, since the gui is not homogeneous, it's difficult to give support with gui directions.  gnome directions will alienate kde, xfce, and fluxbox users, but support given with command line commands is universal.  i believe that THIS is why most linux users reach for the command line (in other words, new users were given support by the command line, so they learned to use the system via the command line, and then continue to do so as their knowledge grows).

---

### Post by faulkes on 2008-02-25
> **devnevyn said:**
> I don't want to be rude, but I happen to be OP's GUI-loving friend, and I can't help but feel like you're all very 80's in here. Either that, or you're deliberately misinterpreting his questions in order to make Ubuntu appear a better server OS.

I don't think anyone is misinterpreting the OP's question, he asked why is 
Ubuntu better or worse than other distros.

If you are prepared to ask the question, be prepared to accept the 
answers.

As for being very 80's, I think you will find that many of us are just as 
comfortable working with a GUI as we are with a CLI.  It is just that many
of us have learned to use the CLI very effectively.  That isn't a pro, a con or
a dig at anyone.  Knowledge is power and when you're trying to accomplish
something with a server, the more you know, the better off you are whether
that be with the GUI or with the CLI.

> 
Take what I say with a grain of salt. I'm a Mac guy, I've administered a few bsd boxes in my days but I'm no expert. 


Noted.  Look at it from the other side of things, you have administered a 
couple of *bsd boxes, many of us have to manage 10's and 100's of 
servers.  There are GUI tools to do this as well, plugging for Canonical's
landscape (I am not a Canonical employee) and there are CLI tools.

> 
Is there anything like this for Ubuntu? 


Webmin is not supported by Ubuntu, or rather it is not in the repositories and
for a number of reasons.  That doesn't mean it can't be installed.

There is however eBox which is very rapidly progressing as an excellent
GUI tool to manage almost all aspects of a  server.

[https://help.ubuntu.com/community/eBox](https://help.ubuntu.com/community/eBox)
[http://forum.eboxplatform.com/index.php?topic=77.0](http://forum.eboxplatform.com/index.php?topic=77.0)
[http://ebox-platform.com/](http://ebox-platform.com/)

Faulkes

---

### Post by FakeOutdoorsman on 2008-02-25
Just an update about my previous post: Ubuntu **does** come with a [minimal cd image]("https://help.ubuntu.com/community/Installation/MinimalCD").  Huzzuh!

---

### Post by tubezninja on 2008-02-26
> **devnevyn said:**
> I don't want to be rude, but I happen to be OP's GUI-loving friend, and I can't help but feel like you're all very 80's in here.

You're welcome to that opinion.  But as someone who administers both Mac OS X and ubuntu servers, I will say that you grossly misunderstand the situation.

> 
 Either that, or you're deliberately misinterpreting his questions in order to make Ubuntu appear a better server OS.

And herein lies the fallacy, one that I've seen from many Mac users.  The shiny cocoa interface is nice, but it's not the superior choice for everyone, nor is it ideal in all situations.  Nor would I say that ubuntu is the supreme candidate in all situations, either.  OS X server has its applications and situations that it works wonderfully on, and ubuntu an other linux distros will shine on their own.

Let me also point something else out: it is **not** impossible to get a GUI on an ubuntu server.  In fact, it's quite easy to apt-get the gone, kde or x.org packages and get a nice graphical interface.  However, the reasons why it doesn't come like this by default have already been beaten to death in these forums.

> I never felt in control of my server, I just knew it lived -- for the moment. My 'production evironment' was a garbled mess of shell scripts and a few PHP guis.

With all due respect, there are two roads one can take in this situation.  They can either buckle down and learn the command line methods for administrations, or they can abandon the command line space and go GUI.  You chose the latter.  There's nothing inherently wrong in that, but I will point out that there are a number of situations where buying an Xserve and administering via point and click are not technically, physically or economically feasible.

Consider that most servers aren't doubling as desktops.  I very rarely sit physically at the keyboard of the production servers I'm responsible for.  They are all monitored remotely, from my Mac desktop in my office, or my computer at home, or my MacBook Pro when I'm on the road.  That's a necessity not just in my situation, but in plenty of other environments where servers are sitting in racks at a remote datacenter somewhere.

OS X has a very nice remote monitoring system, that a corporation spent lots of money putting together.  And, they charge $499 for the software.  Great!  But not every organization will be willing to pay that premium, and not every person can afford the hardware to get a Mac.  And still others simply might not want to use the software for personal, or philosophical reasons.

Does that mean we're stuck in the 80s?  Considering that the majority of production servers out there are NOT Macs, are often headless, and must be administered remotely, it's no wonder that few of them have GUIs installed - I guess that means that a majority of the web sites out there on the net, some of which you visit on a daily basis, are pretty old school.  The CLI, dated as it may seem to you, is still the most effective and efficient way to control a server at its basest levels.

For what it's worth, remote desktopping the Mac interface has its challenges, too.  Using the graphical interface from afar requires a LOT of bandwidth, and even with broadband the latency is pretty great.  Not to mention, to use the Apple-sanctioned remote desktop application, you need to have another Mac near you.  If something goes wrong when I'm out, and  all I've got nearby happens to be a Windows PC, I'm out of luck.

There are free cross-platform alternatives, like VNC, but then I could've just run GNOME an VNC'ed that for far less money.  Or I could use ssh to go into the Mac's command line... but then if I have to do that... why am I even using s Mac?

> I'm sure that I, even in shiny Mac-land, I'll surely have to dig up the terminal if I want to do something advanced, but for most tasks, I can breeze through my GUI in no-time, and being able to do that feels great. 

You must feel very liberated. :)  For what it's worth, I can take or leave running a server graphically.  It's all right on OS X, but I haven't found a situation any more difficult on the Xserves than I have on my Ubuntu or SuSE boxes.

> Is there anything like this for Ubuntu? Not "There's a php interface on top of cyrus which you can apt-get, and the SMB log can be piped through a cgi script", but a nice, consolidated GUI for getting a feel for the server's health and administering basic tasks.

KDE and GNOME are not php-based nor cgi-based.  They run platforms not too distinct from cocoa, actually.  You can even make [ubuntu look like OS X]("http://www.supriyadisw.net/2006/04/ubuntu-dapper-osx-style") if you like.  

Ubuntu server is not for everyone.  You've chosen your path, and that's perfectly fine.  I'm glad you're happy there.  Chiding the ubuntu users, however, doesn't change the truth of the situation: Mac isn't for everyone, either.

Again, don't get me wrong: I love Macs.  I'm typing this on one right now, in fact. :)  But being in a job where knowledge of multiple OSes (Windows, Solaris, SuSE, ubuntu, OS X) are a requirement, I can keenly see the strengths and weaknesses of each.

---

### Post by AbtZ on 2008-02-26
Ouch. 

In the words of my aforementioned friend: he got "owned". :)

---

### Post by tubezninja on 2008-02-27
> **AbtZ said:**
> Ouch. 

In the words of my aforementioned friend: he got "owned". :)

"Ownage" isn't part of the [ubuntu philosophy]("http://www.ubuntu.com/community/conduct"), but education is.  No one here was *trying* to own him, I don't think.  We (or at least I) just want to make sure he fully gets what this and other linux distros really can do.  

You should always truly know what you're bashing before you bash it. :)  I learned that the hard way myself.  I used to be Mr. Windows-fanboy, until I got the opportunity to know better.

---

### Post by cferthorney on 2008-04-03
Going back to the OP's question - where does Ubuntu Server have its advantages over say CentOS (The RPM enterprise distro I am most familiar with, mostly due to my RHCE)

I am a linux fan, I only have a windows box at home when I take my work's laptop home, but am finding myself more and more disillusioned with RPM based distros where RPM dependancy hell is frequent.  This is the reason I started using Ubuntu on my desktops and Gentoo on my home servers.

At work I don't have the luxury of being able to wait ages for source to compile, but I also like to be relatively up to date (For instance as a web house we want to use PHP 5.2 over PHP 5.1.6, which is what CentOS offers as an RPM...)

Is Ubuntu a worth while platform to consider as an alternative to CentOS, or am I better off with looking at Debian and compiling PHP from source?  What advantages does Ubuntu have over other server based distros such as Novell's SLES, or Red Hat's RHEL?  How up-to-date are the LTS versions of Dapper? Is it still using PHP 5.0? Or has it been updated to 5.2? etc etc

If i have posted this int he wrong section I appologise, but this looked like the most approapriate thread to post comments about this.  And if it helps I'm GUI neutral!  I'll use them if people want me to, I won't touch em if people don't. :)

Thanks in advance
Dave

---

### Post by jonabyte on 2008-04-03
> **cferthorney said:**
> Going back to the OP's question - where does Ubuntu Server have its advantages over say CentOS (The RPM enterprise distro I am most familiar with, mostly due to my RHCE)


Two reasons for me.

I am more familiar now with ubuntu, using the desktop version and i really like the fact that no gui is installed automatically when installing the server version (I have no use for one).

But I am not sure if there is much of a performance or other advantage over another "server" distro, I think its more personal.

I wasn't that interested in the ubuntu server until I just tried it on my test servers.

---

### Post by googlah on 2008-04-03
Good things in alot of ways. When I first started doing servers I looked into Linux or Windows. As the biggest companies and websites is using Linux, this was the choise I guess. Looking further, I began to look into Debian which had the great tool APT-GET, which get any package you want and installs it for you.

Had Debian for an year, and then looked into Ubuntu. The reason why I'm using Ubuntu instead of Debian is that it feels more up-to-date. I can't go away from the APT-GET system. I just love the way it serves me. Also, in the desktop envoirement, if you want let's say, Frets on Fire, you just call APT-GET. :)

Easy'.

---

