---
title: "Ubuntu needs more GUIs for System Administration ??"
date: 2011-08-10
forum: The Cafe
---

### Post by linuxyogi on 2011-08-10
Hi,

I have used openSUSE for some months & liked it a lot.

The only feature that makes openSUSE more user friendly than Ubuntu (IMO) is YAST.

I configured squid, DNS caching using YAST & it was really easy. It has a GUI for apparmor too.

So, don't you feel that Ubuntu should make something similar to YAST or try n create 

frontends for common administrative tasks like configuring a DNS/DHCP server, configuring 

apparmor & likewise ?

---

### Post by Bandit on 2011-08-10
I hate having to go through GUIs to do something when it comes to system admin. Thats a huge thing I hate about windows as its time consuming and is easy to get over complex with. I had rather go straight to a file and edit it and know the settings are good. Besides, if someone needs GUIs with Linux to be a system administrator then they are not qualified for the job nor the title.

---

### Post by linuxyogi on 2011-08-10
> **Bandit said:**
> I hate having to go through GUIs to do something when it comes to system admin. Thats a huge thing I hate about windows as its time consuming and is easy to get over complex with. I had rather go straight to a file and edit it and know the settings are good. Besides, if someone needs GUIs with Linux to be a system administrator then they are not qualified for the job nor the title.


Yes, but what if an amateur wants to do a little bit of system administration ? 

Like, what if someone wants to configure a DNS caching server for his/her home network ?

---

### Post by cariboo on 2011-08-10
The problem with using a gui to configure services, is that it you don't learn anything about the service that allows you to troubleshoot a problem when it happens. If you have to read a configuration file while you are setting up the service, at least you have an idea what is going on, whereas using a gui it is more or less just a fill in the blanks form.

---

### Post by cabbrick1243 on 2011-08-10
> **linuxyogi said:**
> Yes, but what if an amateur wants to do a little bit of system administration ? 

Like, what if someone wants to configure a DNS caching server for his/her home network ?

Then they can Google and learn.

---

### Post by linuxyogi on 2011-08-10
> **cariboo907 said:**
> The problem with using a gui to configure services, is that it you don't learn anything about the service that allows you to troubleshoot a problem when it happens. If you have to read a configuration file while you are setting up the service, at least you have an idea what is going on, whereas using a gui it is more or less just a fill in the blanks form.

But Windows got popular because of its blank forms :D 

Isn't Ubuntu trying to do the same thing ? I mean trying to be as popular as Windows ?

---

### Post by TheNosh on 2011-08-10
The responses in this thread are precisely why Linux will never have significant market share.

---

### Post by hakermania on 2011-08-10
> **TheNosh said:**
> The responses in this thread are precisely why Linux will never have significant market share.

It hurts, but it's truth

---

### Post by uRock on 2011-08-10
> **cariboo907 said:**
> The problem with using a gui to configure services, is that it you don't learn anything about the service that allows you to troubleshoot a problem when it happens. If you have to read a configuration file while you are setting up the service, at least you have an idea what is going on, whereas using a gui it is more or less just a fill in the blanks form.

+1 CLI is best. Especially when security policies are a requirement.

---

### Post by el_koraco on 2011-08-10
I don't think Ubuntu is going for the same market niche as openSUSE. Also, it would take them a gazillion years to duplicate the functionality of Yast.

---

### Post by LowSky on 2011-08-10
YAST or Ubuntu Software Center.... I wonder OpenSUSE's user base versus Ubuntu's user base... yup totally wonder...

---

### Post by linuxyogi on 2011-08-10
> **el_koraco said:**
>  it would take them a gazillion years to duplicate the functionality of Yast.

But it seems Ubuntu is more popular than openSUSE (I am not sure). This forum is undoubtedly more vibrant than any other distribution forum I have ever seen.  

So its mainly luck which made Ubuntu more popular in comparison to openSUSE ? I mean despite openSUSE's YAST ?

---

### Post by TheNosh on 2011-08-10
> **linuxyogi said:**
> But it seems Ubuntu is more popular than openSUSE (I am not sure). So its mainly luck which made Ubuntu more popular in comparison to opsnSUSE ? I mean despite openSUSE's YAST ?

Marketing and hype, mostly.

To Ubuntu's credit, Debian was the distro with the most expansive software availability. Ubuntu is largely Debian, but easier to install for people who are new to Linux, so that has something to do with it as well.

---

### Post by disabledaccount on 2011-08-10
> **TheNosh said:**
> The responses in this thread are precisely why Linux will never have significant market share.
The responses in this thread are precisely why Linux already has gratest market share on servers, supercomputers and many dedicated devices - Linux is what proffessionals exactly need.
Noobs howevwer will vote for having GUI, even though they don't understand most of the available options.

I belive it's possible to create good GUI for system administration, but I never have seen one, even on Windows.

---

### Post by capink on 2011-08-10
> **Bandit said:**
> I hate having to go through GUIs to do something when it comes to system admin. Thats a huge thing I hate about windows as its time consuming and is easy to get over complex with. I had rather go straight to a file and edit it and know the settings are good. Besides, if someone needs GUIs with Linux to be a system administrator then they are not qualified for the job nor the title.

Why not have both options and let users choose for themselves. This is what I keep hearing in Linux forums, Linux and open source are about freedom, choice ............

---

### Post by imortalninja161 on 2011-08-10
I have always Preferd CLI becuase if you know what you are doing it is much more effiecent having said that i think a GUI should be option because well some days plain old CBF lol

---

### Post by koenn on 2011-08-10
> **capink said:**
> Why not have both options and let users choose for themselves. This is what I keep hearing in Linux forums, Linux and open source are about freedom, choice ............

That thing you heer about freedom and choice, that's something that is often misunderstood.
The freedom comes from the licensing that allow you to use programs any way you like, including using the sources to build your own custom applicaztion, or recompile it with different options, and whatever. The choice coms from the availability of software that adheres to open, well documented standards, and designs that aim for interoperability, so it's easy (most of the time, and if not easy, then at least possible) to pick any program, and have it cooperate with another; your choice is not limited by what a vendor or software manufacturer prescribes.

That does not imply that linux/open source devs have any kind of obligation to provide unlimited choice for you. 



That said, it's probably not a bad idea to have some GUI sysadmin tools, like for quickstart setups or things you want to set and forget, or as a built-in checklist for tasks that require a lot of settings all over the place. In fact, the (debian text-based) installer already does that when you select tasks or programs during the OS installation, so why not expand that a bit.

Otoh, any decent sysadmin will always want to (also) have easily scriptable commands, and configs that can be easily read and modified with a limited set of standard tools (as opposed to an extensive set of dedicated tools and wizards

---

### Post by el_koraco on 2011-08-10
> **linuxyogi said:**
> 
So its mainly luck which made Ubuntu more popular in comparison to openSUSE ? I mean despite openSUSE's YAST ?

openSUSE is an extension of a distro designed for use in corporate environments. They (devs and community) are open to new users, but aren't actively seeking them out. Ubuntu is targeting new users, and concentrating a lot of their efforts towards that goal.

---

### Post by Thewhistlingwind on 2011-08-10
> **TheNosh said:**
> The responses in this thread are precisely why Linux will never have significant market share.

If you had to choose (And you don't.) would you rather:

1. Be able to do everything from the GUI 

or

2. Be able to do everything from the CLI. (First)

If you make a GUI version of something, theres a likelihood that there won't be a CLI tool in the future. Which is absolutely unacceptable. 

I don't think we need YAST right now, however, it's interesting to note that even YAST has an ncurses front end.

EDIT: if you make the GUI *first *that is.

---

### Post by christoph411 on 2011-08-10
> **thenosh said:**
> the responses in this thread are precisely why linux will never have significant market share.

+1!

---

### Post by Bandit on 2011-08-10
> **linuxyogi said:**
> But Windows got popular because of its blank forms :D 

Isn't Ubuntu trying to do the same thing ? I mean trying to be as popular as Windows ?

> **TheNosh said:**
> The responses in this thread are precisely why Linux will never have significant market share.


Your both incorrect. Its easy to look and at market share and "think" windows is running on more servers then linux. When in fact that percentage is based on SALES REVENUE.. Since most linux server software like Ubuntu Server is free of charge, the actual usage of linux on servers is more in the range of 60% while windows is less then 10%. The rest is a mix of other platforms from OSX Server, Cold Fusion, BSDs, etc.. etc..
Also as of November 2010 Linux is on over 91% of the top 500 Super Computers (459 to be exact). [LINK]("http://en.wikipedia.org/wiki/Linux#Servers.2C_mainframes_and_supercomputers")



> **cariboo907 said:**
> The problem with using a gui to configure services, is that it you don't learn anything about the service that allows you to troubleshoot a problem when it happens. If you have to read a configuration file while you are setting up the service, at least you have an idea what is going on, whereas using a gui it is more or less just a fill in the blanks form.

> **uRock said:**
> +1 CLI is best. Especially when security policies are a requirement.

++ Agreed ++

---

### Post by Paqman on 2011-08-10
A desktop system needs to have GUIs for admin tasks. CLI is fine for server work (inculding professional sysadmins) but it's entirely the wrong tool to present to a desktop user.

So yes, Ubuntu needs better admin GUIs. Setting up something like a permanent network share should be easily doable in a GUI. Other desktop OSes have jobs like this sorted, it's a genuine area of weakness for Linux IMO.

---

### Post by Thewhistlingwind on 2011-08-10
> **Paqman said:**
> A desktop system needs to have GUIs for admin tasks. CLI is fine for server work (inculding professional sysadmins) but it's entirely the wrong tool to present to a desktop user.

So yes, Ubuntu needs better admin GUIs. Setting up something like a permanent network share should be easily doable in a GUI. Other desktop OSes have jobs like this sorted, it's a genuine area of weakness for Linux IMO.

At the same time, I do think that more essential functions should have accompanying graphical interfaces that aren't bash prompts.

---

### Post by DangerOnTheRanger on 2011-08-10
> **uRock said:**
> +1 CLI is best. Especially when security policies are a requirement.

+float('inf').

> **linuxyogi said:**
> Yes, but what if an amateur wants to do a  little bit of system administration ? 

Like, what if someone wants to configure a DNS caching server for  his/her home network ?

"Amateurs" who aren't willing to break out some Google-fu and use the shell shouldn't try to perform system administration.

> **TheNosh said:**
> The responses in this thread are precisely why  Linux will never have significant market share.

It stuns me how often someone says this when J. Random Hacker says "X GUI tool is unnecessary". There is absolutely nothing wrong with the shell - in fact, it scares would-be self-destructing newbies away from vital parts of their system :)

---

### Post by cgroza on 2011-08-10
Based on the target audience of Ubuntu, there should be tools that allow the average user to configure his install. You don't want to get new users and force them to dig through config files and command line.
You can explain them, but they will say : No, this is not simple, it is stupid.

Is it possible to take some source code from YaST and modify it for Deabian based distros?

---

### Post by Bandit on 2011-08-10
> **Paqman said:**
> A desktop system needs to have GUIs for admin tasks. .............

Desktop wise for the average user I agree 110%. What I was implying was directed to Sever setups.

---

### Post by TheNosh on 2011-08-11
> **tomazzi said:**
> The responses in this thread are precisely why Linux already has gratest market share on servers, supercomputers and many dedicated devices - Linux is what proffessionals exactly need.
Noobs howevwer will vote for having GUI, even though they don't understand most of the available options.

I belive it's possible to create good GUI for system administration, but I never have seen one, even on Windows.

You can actually do plenty from a Windows command line. The reason Linux is so popular on super computers is that those administrating said super computers can tailor it as much as they want to fit precisely what they need. Windows just provides what's needed for the majority of desktop computers, since that's their target. I doubt anyone at Microsoft looses any sleep over their lack of presence on super computers.

As for servers, I'd mostly choose *nix on a server because it's free and I'm cheap. Also, I'll give it credit for being designed for servers. At that point I'd go with BSD, though.

> **Thewhistlingwind said:**
> If you had to choose (And you don't.) would you rather:

1. Be able to do everything from the GUI 

or

2. Be able to do everything from the CLI. (First)

If you make a GUI version of something, theres a likelihood that there won't be a CLI tool in the future. Which is absolutely unacceptable. 

I don't think we need YAST right now, however, it's interesting to note that even YAST has an ncurses front end.

EDIT: if you make the GUI *first *that is.

Everything should be doable from the CLI, obviously. I'd just also like it to be doable graphically, and more importantly, so would the majority of people.

Many programs are designed with both a CLI interface, and a graphical interface. I'd like that to be roughly standard, for administration software if nothing else.

---

### Post by uRock on 2011-08-11
> **TheNosh said:**
> You can actually do plenty from a Windows command line. The reason Linux is so popular on super computers is that those administrating said super computers can tailor it as much as they want to fit precisely what they need. Windows just provides what's needed for the majority of desktop computers, since that's their target. I doubt anyone at Microsoft looses any sleep over their lack of presence on super computers.

As for servers, I'd mostly choose *nix on a server because it's free and I'm cheap. Also, I'll give it credit for being designed for servers. At that point I'd go with BSD, though.



Everything should be doable from the CLI, obviously. I'd just also like it to be doable graphically, and more importantly, so would the majority of people.

Many programs are designed with both a CLI interface, and a graphical interface. I'd like that to be roughly standard, for administration software if nothing else.
What I like is a GUI, which shows what the software is doing via a cli window, kinda like what we see when running the ubuntu update manager. The app in the screenshot is something I would like to see, but for a desktop machine, instead of a router.

---

### Post by cariboo on 2011-08-11
If we are talking about a desktop system, you shouldn't need the CLI to administer the system, everything can be done with a GUI. The op's example was for a  server, which is totally different from a desktop system.

---

### Post by Thewhistlingwind on 2011-08-11
> **TheNosh said:**
> 

Many programs are designed with both a CLI interface, and a graphical interface. I'd like that to be roughly standard, for administration software if nothing else.

Thats the ideal situation.

---

### Post by TheNosh on 2011-08-11
> **uRock said:**
> What I like is a GUI, which shoes what the software is doing via a cli window, kinda like what we see when running the ubuntu update manager. The app in the screenshot is something I would like to see, but for a desktop machine, instead of a router.

That's an idea I could get behind, for sure.

---

### Post by TheNosh on 2011-08-11
> **Major_Bloodnok said:**
> Congratulations on volunteering to write a release of YaST for Ubuntu.

Now, there is n o t h i n g stopping you from downloading the source code for YaST.
[http://en.opensuse.org/openSUSE:YaST_development#YaST_Source_Code](http://en.opensuse.org/openSUSE:YaST_development#YaST_Source_Code)

Everyone with an opinion should be a software developer?

I suppose, no one who doesn't run for political office should have any political leanings?

---

