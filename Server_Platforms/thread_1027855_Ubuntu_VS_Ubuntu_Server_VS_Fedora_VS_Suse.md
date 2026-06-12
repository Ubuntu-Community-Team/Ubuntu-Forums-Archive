---
title: "Ubuntu VS Ubuntu Server VS Fedora VS Suse"
date: 2009-01-01
forum: Server Platforms
---

### Post by Aram99 on 2009-01-01
Hello every one

I am setting up a webserver, I am paying a lot of money to host my website, it is only a personal website with some videos. I did some research but realized how sophisticated and hard setting up a server could be. 
I am torn between Ubuntu, Suse and Fedora. I heard many good things about Ubuntu but not sure what is the difference between Ubuntu and Ubuntu Server. 
I read online that Suse is not the best OS for running a server, and I am not familiar with Fedora.
For some reason I am with Ubuntu, but it is just my guts so I need a more accurate answer.

I am a bit confused, I really want to learn one of these OS but not sure were to start and not sure which one is better for my web server.

I appreciate any help
Thank in advance

---

### Post by SuperMike on 2009-01-01
My vote is for Ubuntu Server, and here's why, especially for serving up videos where you might need to do video translation:

1. Ubuntu comes with apt for doing easily installation of libraries with minimal pain. Suse and Fedora and Red Hat and CentOS all come with yum instead of apt, but my experience has been that the libraries have been smaller than the vast Debian apt source libraries.

2. Ubuntu is a bit more cutting edge, yet stable, than the competition. Therefore, you'll find more up to date video libraries there for doing video conversion on the fly.

3. I've tried using yum on the non-Debian and non-Ubuntu platforms to serve up a website like you speak of, and it was so hard I finally had to give up and tell the client I couldn't solve his problem.

---

### Post by Aram99 on 2009-01-02
Hello
Thanks SuperMike,

Thanks for mentioning the video capabilities of Ubuntu Server, that was really out of my scope, I wasn't aware of such deference. I guess I am gonna go with Ubuntu Server.

Thanks again

---

### Post by ibutho on 2009-01-02
Personally I wouldn't use any of the distros you mentioned for a server although they are all quite capable. I would go with Debian or CentOS because they are significantly more stable due to the long testing period before a release. If you are already familiar with Ubuntu, then Debian maybe the best option from the two that I mentioned.

---

### Post by Aram99 on 2009-01-02
Hello

Thank you ibutho,

I don't really know ubuntu or any other linux distros, I am a mac person but I always admired linux and wanted to learn it so my experience in all the distros is the same. I am just asking which one is better because I wanted to go directly into learning how to set up my server without going into the hassel of trying all the distros, I know they are all good and it is hard for a newbie to determine which one to foucus on.

appreciate it man

---

### Post by windependence on 2009-01-02
> **ibutho said:**
> Personally I wouldn't use any of the distros you mentioned for a server although they are all quite capable. I would go with Debian or CentOS because they are significantly more stable due to the long testing period before a release. If you are already familiar with Ubuntu, then Debian maybe the best option from the two that I mentioned.

I agree here and will go one step further and say FreeBSD would be the best performing, most secure option. Go to [www.netcraft.com](www.netcraft.com) and see what most of the web uses to serve their sites. You'll find a lot of *BSD in there.

As for the comments about OpenSuSE, my experience has not been close to that. SuSE uses their own proprietary software installer and management tool called YaST that IMHO beats the pants off Ubuntu's tools. You can even run an ncurses GUI from an ssh session - yeah - that's wjat I'm talkin' about man. It is very stable. I have customers running enterprise web sites on it for years. You will find SuSE installs much more in the default install than most distros. That can be good and bad, but for someone just starting out it's probably good as everything is there that you need.

-Tim

---

### Post by ibutho on 2009-01-04
> ...SuSE uses their own proprietary software installer and management tool called YaST that IMHO beats the pants off Ubuntu's tools...
Its actually been opensource for a few years now.

---

### Post by scorp123 on 2009-01-04
> **windependence said:**
> SuSE uses their own proprietary software installer and management tool called YaST  "yast" is opensource.

> **windependence said:**
>  that IMHO beats the pants off Ubuntu's tools. But "yast" does lots of stupid things too! Especially if you customize any settings or config files it can easily happen that "yast" decides to overwrite your settings again with its own defaults ](*,) ... This can be very frustrating too.

---

### Post by igknighted on 2009-01-04
> **SuperMike said:**
> My vote is for Ubuntu Server, and here's why, especially for serving up videos where you might need to do video translation:

1. Ubuntu comes with apt for doing easily installation of libraries with minimal pain. Suse and Fedora and Red Hat and CentOS all come with yum instead of apt, but my experience has been that the libraries have been smaller than the vast Debian apt source libraries.

Fedora/Red Hat/CentOS due use YUM.  Consider this to be just like Debian/Ubuntu's apt.  Debian/Ubuntu may have more applications in their repositories, but Fedora et. al. have better server management tools.  Also, YUM is much easier to deal with if you ever have to remotely access your server.  Overall, consider this a wash.

Not to mention, Suse does not use YUM.  It uses zypper, which is better at resolving dependencies than apt or yum.  Yast (mentioned above) is the gui interface for it.

> **SuperMike said:**
> 2. Ubuntu is a bit more cutting edge, yet stable, than the competition. Therefore, you'll find more up to date video libraries there for doing video conversion on the fly.

Fedora is the most up to date, or cutting edge if you will, of the major distros.  I would argue this may not be a good thing on a server, but it depends on your needs. 

> **SuperMike said:**
> 3. I've tried using yum on the non-Debian and non-Ubuntu platforms to serve up a website like you speak of, and it was so hard I finally had to give up and tell the client I couldn't solve his problem.

You were used to Ubuntu, so it was different.  I learned on CentOS servers and find Ubuntu's ways very foreign and backwards.  I don't think it is a fair statement for either of us to say the other way is "too hard", it just depends which you are more experienced with.

As you may have guessed, I would recommend one of the RPM distro's.  Either opensuse or CentOS (Fedora is too bleeding edge for a production server, and Red Hat is very expensive).  The kicker for me is that the RPM distro's tend to get more support for 3rd party apps.  Both CentOS and opensuse have commercially supported sister-distro's (RHEL and SLES, respectively), which makes more software available.

> **scorp123 said:**
> But "yast" does lots of stupid things too! Especially if you customize any settings or config files it can easily happen that "yast" decides to overwrite your settings again with its own defaults ](*,) ... This can be very frustrating too.

This is very true.  But lets not confuse Yast2 (the package manager front-end) with Yast (the system configuration control panel).  And on a GUI-less server, chances are you won't ever use either, you'll use zypper for command line package management.

---

### Post by scorp123 on 2009-01-04
> **igknighted said:**
> This is very true.  But lets not confuse Yast2 (the package manager front-end) with Yast (the system configuration control panel).  The two are the same program! Just different frontends!

> **igknighted said:**
>  And on a GUI-less server, chances are you won't ever use either, you'll use zypper for command line package management. Yast can be easily used in a text interface e.g. via SSH. And even if you use "zypper" most of the time for your package management needs, you will need "yast" sooner or later to configure some things for you. It's all there in yast: users, passwords, groups, permissions, package sources, shares, printers, and so on. That's the part where "yast" can become an annoyance, especially if you customised something and "yast" keeps overwriting your settings with some of its defaults. Rule of thumb here is: If you customise your SUSE, do it in yast! (chances are that "yast" gets it and wont change your customisations then).

---

### Post by cacycleworks on 2009-01-05
Personally, I'm running ubuntu for a handful of servers. One of my webhosts used ubuntu LTS until recently and they had over a year of uptime. :-)

We just needed another test server and I was wanting to emulate the platform that my current site is hosted on, CentOS. But it didn't want to install. After an hour or two, I said screw it and had ubuntu server 8.10 x86_64 running on it within a few minutes. And this was on a freshly put together franken-system... I bought an Asus mo-board and AMD quad-core cpu (for $200), while the rest of it was spare parts from the closet. 

A few suggestions I have based on my experience and observations:
[LIST=1]
[*]Pay for a professional port-scanning & vulnerability-checking service to hit your server's IP. This one was a real eye opener for me. It took about 20 or more hours of admin and programming to fix all the web-server vulnerabilities it found. The default install isn't crap, per se, but was great to get help finding more security.
[*]I do not use any options from the "TASKSEL" page on the installer. When I want to install packages, I use apt-get or aptitude. Aptitude is a great package installer, as it can help explain dependencies and also suggest alternatives.
[*]Set up your firewall.
[*]Have development boxes (or "servers") to test new things on, all the while leaving the production server alone.
[*]Along with "periodic" back ups, do them before any changes in case you screw it up. I sure have screwed things up without a .tgz to save my day.
[*]Never quit or give up. Keep at it.
[/LIST]

Anyhow, best of luck to you and I'm sure that your linux servers regardless of the distro will do their best to keep you happy.

:)
Chris

---

### Post by windependence on 2009-01-07
> **igknighted said:**
> Fedora/Red Hat/CentOS due use YUM.  Consider this to be just like Debian/Ubuntu's apt.  Debian/Ubuntu may have more applications in their repositories, but Fedora et. al. have better server management tools.  Also, YUM is much easier to deal with if you ever have to remotely access your server.  Overall, consider this a wash.

Not to mention, Suse does not use YUM.  It uses zypper, which is better at resolving dependencies than apt or yum.  Yast (mentioned above) is the gui interface for it.



Fedora is the most up to date, or cutting edge if you will, of the major distros.  I would argue this may not be a good thing on a server, but it depends on your needs. 



You were used to Ubuntu, so it was different.  I learned on CentOS servers and find Ubuntu's ways very foreign and backwards.  I don't think it is a fair statement for either of us to say the other way is "too hard", it just depends which you are more experienced with.

As you may have guessed, I would recommend one of the RPM distro's.  Either opensuse or CentOS (Fedora is too bleeding edge for a production server, and Red Hat is very expensive).  The kicker for me is that the RPM distro's tend to get more support for 3rd party apps.  Both CentOS and opensuse have commercially supported sister-distro's (RHEL and SLES, respectively), which makes more software available.



This is very true.  But lets not confuse Yast2 (the package manager front-end) with Yast (the system configuration control panel).  And on a GUI-less server, chances are you won't ever use either, you'll use zypper for command line package management.


You certainly can use YUM with OpenSUSE. You have been able to for a while

I have never had a problem with YaST overwriting things by itself. If it does that, you changed something in YaST.

At any rate, all my production stuff is on BSD and some of my clients use OpenSUSE or CentOS. I have one client running Ubuntu for Zimbra. All of them seem to perform pretty well, but BSD is far simpler than any of them and IMHO much more secure.

-Tim

---

### Post by halovivek on 2009-01-07
I tried from Redhat server, suse before ubuntu server in my office for the local project. 
Ubuntu gets first since easy installation and maintenance. if your hosting in internet make sure three things.
1. scan with vulnerabilities with third party software and fix it
2. Configure the firewall properly.
3. Make always root password very strong.

---

### Post by tubezninja on 2009-01-07
> **Aram99 said:**
> Hello

Thank you ibutho,

I don't really know ubuntu or any other linux distros, I am a mac person but I always admired linux and wanted to learn it so my experience in all the distros is the same. 


As someone who also started out in the *nix universe as a Mac person, I would highly recommend ubuntu for your server.  It's a nice balance between a great starter distro for someone just getting into linux server administration, while at the same time being advanced and flexible enough to grow with you as your skills grow.

As you get more comfortable with administering a server, you might want to move on to Debian.

I run several ubuntu servers as well as co-admin a number of OpenSuSE machine.  SuSE isn't bad as a server distro, and we've gotten some really good, 1 year+ uptimes with some of these machines.  The ubuntu machines less so, but only because I update them to the latest compiled kernels when they become available, and reboot them when that takes place.  If left alone, they'd run practically forever, too.

Even so, SuSE is not, IMO, a good distro if you're just cutting your teeth on linux server admin.  I did it, and it wasn't easy. :)

---

### Post by RobertBruce on 2009-01-07
Thanks cacycleworks for putting me onto Asus. What model m-board did you buy? 

I'm a complete newbie. Thought I could use a very old 60gb Advent 3112 Pentium 4 that was gathering dust in the attic for years. But the m/b decided this afternoon that its time had come and shuffled off to the soldering place in the sky! 

I had intended to have UBUNTU 8.10 installed by this evening but it will have to wait.

So I am looking to buy a new motherboard and will welcome any advice. I intend the server to be used by the villagers as well but ostensibly, I want to host my sites.

Thanks

RB

---

### Post by cacycleworks on 2009-01-07
> **RobertBruce said:**
> Thanks cacycleworks for putting me onto Asus. What model m-board did you buy? 

I'm a complete newbie. Thought I could use a very old 60gb Advent 3112 Pentium 4 that was gathering dust in the attic for years. But the m/b decided this afternoon that its time had come and shuffled off to the soldering place in the sky! 

I had intended to have UBUNTU 8.10 installed by this evening but it will have to wait.

So I am looking to buy a new motherboard and will welcome any advice. I intend the server to be used by the villagers as well but ostensibly, I want to host my sites.

Thanks

RB

I ended up with this one: [M3N78-VM]("http://www.asus.com/products.aspx?l1=3&l2=149&l3=643&l4=0&model=2268&modelmenu=1"). I walked into my local Fry's with the goal of getting an inexpensive great CPU, new mo-board, and new power supply. The box it went into was my AMD K6/2-3D Now! 266 MHz that I built in 1998. I ran win2k and quickbooks on it for like 7 years. :-)

When I got into Fry's the limiting issue was that the lower end mo-boards will only support dual core and not necessarily the quad core. Quad core CPUs are cheap enough that I decided to go for one of the low end intels or a comparably priced AMD. The next "problem" with the mo-boards was that all the low priced ones only had 2 memory slots, or really low maximum memory support. 

So I ended up with these criteria:
- no ATI video due to bad reputation in linux
- 4 memory slots and sane memory limit
- on board gigabit
- must be quad core capable
- preference for msi mo-board
- don't care about video at all. I don't game, it will start life as headless server, and worst case will run a desktop on 24" monitor. Is it possible to buy a mo-board that won't do 1920x1200?

There were 2 boards I wanted to buy but they were out. One was intel the other AMD. Neither had spiffy video, both had 4 memory slots, and one of them had dual onboard Gigabit. Of course, the two best server boards were sold out. :P 

The ASUS M3N78 was the best priced alternative that supported a quad core and had 4 memory slots. It just so happened to be for AMD, so I got the [9550]("http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=400") because it met the best price-to-performance ratio in my brain. I believe that if someone bought this board and wanted to run a desktop, there may be some need for small tweaks based on everything I read about "ASUS M3N78 linux problem" in google. We did boot the ubuntu 8.10 desktop live cd and it worked, so who knows, eh? (I clicked it instead of alternate server, so was a mistake)

Of course, I paid more for these than if I shopped on the net, but I wanted them in my mitts that day (which was 12/26), so I could put the server together. :-)

It is pretty amazing what $$ buys. This is a smokin system built for nothing. Also, watching tigerdirect, newegg, and dell for sales I have seen some amazing sub $500 systems... I'm getting the feeling that a "game changing" level of performance is about to happen with PCs. Kinda like PIII versus Pentium I.

:) Chris

---

### Post by windependence on 2009-01-07
Are you in Phoenix by any chance? If you are, I may have some server boards here if you need them in the future.

I have several AMD quad core systems running Linux and BSD no problems. Memory is cheap right now. I also have some brand new ECC memory, 2 gig sticks I bought for a server and did not use if you are interested. $50 each. I can deliver if you are in Phoenix.

-Tim

---

