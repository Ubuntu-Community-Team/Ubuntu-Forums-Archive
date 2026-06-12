---
title: "Security"
date: 2014-12-01
forum: Security
---

### Post by Chris_Jenkins on 2014-12-01
Hi:

I would like to use the Bastille wizard to harden my system. How do you do this?  Is it installed after Ubuntu is installed or is there an install for the Bastille version?

What about maximizing the security for AppArmour? 

Also is there a way to opt-out of forwarding searches to Amazon?

How do you verify that the installs are genuine? Is there gpg? a https download site (this is http only).

How do you set up an unprivileged user account (non-Admin) for use? 

Thanks for responding.

---

### Post by sudodus on 2014-12-02
Welcome to the Ubuntu Forums :-)

Please start by reading the following wiki page

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

I think other people, who know the details better than I, will chip in and explain the details of your questions.

---

### Post by Chris_Jenkins on 2014-12-02
thank you. This is way too technical, too pedantic, and just too much information.

And it doesn't answer a lot of questions I had.

---

### Post by Chris_Jenkins on 2014-12-02
I looked at some other pages and, you guys just don't get it.

You are writing basic stuff for computer scientists. All I want to know is how to simply harden the system and I get documents filled with command line scripts.

Not user friendly at all.

Plus, 171 viewed this and only one responded?  Pretty poor.

---

### Post by Elfy on 2014-12-02
171 looked at the title. or 1 person viewed it 171 times, possibly people hovering over the less than helpful title to see what the thread was really about. 18 people bothered to read the thread. 

If you'd looked at bastille's availability for Ubuntu you'd see that bastille is available for versions 12.04 and older. 

So - you'll need to try and get the sourceforge download working for you.

---

### Post by deadflowr on 2014-12-02
> [COLOR=#000000]Also is there a way to opt-out of forwarding searches to Amazon?[/COLOR]

Turn off on-line search results in Privacy settings.

> [COLOR=#000000]How do you verify that the installs are genuine? Is there gpg? a https download site (this is http only).[/COLOR]

You can run an md5sum on the .iso of which ever version you downloaded.
You can usually find the hash buried on the download page, or here
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Lars Noodén on 2014-12-02
( Usually it is more effective to have one question per post.  Also, you will find that despite the many millions of $ spent by one company to disparage the shell, it is the fastest, most flexible and by far the most powerful interface for the intermediate and advanced user.  )

> **Chris_Jenkins said:**
> Hi:
What about maximizing the security for AppArmour? 
 

You will then need to customize the AppArmor profiles for each application that you want to limit.   It's not something that can be automated, nor can be hidden behind a clumsy GUI, and is a separate skill in and of itself.  If you are interested in limiting specific applications, you can ask here on this forum, but the starting point would be this document:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Which applications do you wish to restrict?  Unlike Systrace, AppArmor cannot (yet) limit network access, only directory and file access.  It is not something likely to be comfortable for starting with.  

> **Chris_Jenkins said:**
> Hi:
Also is there a way to opt-out of forwarding searches to Amazon?
 

Depending on which version of Ubuntu you are running, it will vary.  In 14.04 LTS it is System Settings -> Security&Privacy -> Search -> Off

> **Chris_Jenkins said:**
> Hi:
How do you verify that the installs are genuine? Is there gpg? a https download site (this is http only).
 

Yes, PGP-signed SHA checksums are available.  Digging around from the download page, they are here for 14.04 LTS:

[http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)

> **Chris_Jenkins said:**
> Hi:
How do you set up an unprivileged user account (non-Admin) for use? 

Any new user you add to the system will be a non-Admin user unless you go out of your way to ensure otherwise.

---

### Post by Chris_Jenkins on 2014-12-02
I did look for its availability and found nothing, but thanks for letting me know.

Let me give you a concrete example of why users might be frustrated, from 
[https://help.ubuntu.com/community/BastilleLinux](https://help.ubuntu.com/community/BastilleLinux)
Installing Bastille Linux

You must [enable the Universe repository]("https://help.ubuntu.com/community/Repositories") in order to install Bastille Linux.
IMPORTANT: There is a problem with the package in 9.10 Karmic. You must install any of these packages first: bsd-mailx, mailx or mailutils. See [Launchpad #434709]("http://bugs.launchpad.net/ubuntu/+source/psad/+bug/434709") for details. It is reported to be fixed for 10.10 Lucid.
The apt-get command, to be issued from a terminal prompt is as follows:
sudo apt-get install bastille
If you prefer Synaptic, perform a search for Bastille, mark the Bastille package for installation, and click the Apply button.


*****

How do you enable the repository-- doesn't say, the link doesn't say. Doesn't explain what it is, either.

What is an apt-get command, and where is this "Terminal"?

How do you perform a search from Bastille for Synaptic?

You might be rolling your eyes right now, but for new users this is ridiculous-- we have no idea what you are talking about.

---

### Post by deadflowr on 2014-12-02
> [COLOR=#333333][FONT=Ubuntu]How do you enable the repository-- doesn't say, the link doesn't say. Doesn't explain what it is, either.[/FONT][/COLOR]

The easiest way is to open software sources, but that changes depending upon which version of Ubuntu you have installed.
12.04, you can open the update manager and click on the button marked Settings.
14.04 and newer, open the program Software and Updates.
Universe is usually marked as Community-maintained.
Also you can run the terminal command
```
software-properties-gtk
```
it'll open the same page (software sources)

---

### Post by lisati on 2014-12-02
> **Chris_Jenkins said:**
> 
What is an apt-get command, and where is this "Terminal"?

In Ubuntu, Running "Terminal" is equivalent to using **cmd.exe** in Windows. There are different ways of accessing it - I generally use *dash* (found at the top of the pop-up menu on the left of the screen on "standard" Ubuntu) to start it. **apt-get** is *command* commonly used to install and uninstall software.

---

### Post by Elfy on 2014-12-02
> **Chris_Jenkins said:**
> I did look for its availability and found nothing, but thanks for letting me know.

Let me give you a concrete example of why users might be frustrated, from 
[https://help.ubuntu.com/community/BastilleLinux](https://help.ubuntu.com/community/BastilleLinux)
Installing Bastille Linux

You must [enable the Universe repository]("https://help.ubuntu.com/community/Repositories") in order to install Bastille Linux.
IMPORTANT: There is a problem with the package in 9.10 Karmic. You must install any of these packages first: bsd-mailx, mailx or mailutils. See [Launchpad #434709]("http://bugs.launchpad.net/ubuntu/+source/psad/+bug/434709") for details. It is reported to be fixed for 10.10 Lucid.
The apt-get command, to be issued from a terminal prompt is as follows:
sudo apt-get install bastille
If you prefer Synaptic, perform a search for Bastille, mark the Bastille package for installation, and click the Apply button.



This is the problem with bring a 'windows mindset' to somewhere else. 

It takes some getting used to - but it is possible, I managed ;)

As I said Bastille has not been available for almost 3 years in the repositories - except for the version available for 12.04.

If *someone, somewhere* is not updating their documentation for that long I would walk away - even more so if it's security based. Just a thought.


> **Chris_Jenkins said:**
> 
*****

How do you enable the repository-- doesn't say, the link doesn't say. Doesn't explain what it is, either.

What is an apt-get command, and where is this "Terminal"?

How do you perform a search from Bastille for Synaptic?

You might be rolling your eyes right now, but for new users this is ridiculous-- we have no idea what you are talking about.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Synaptic - the chances are high that to use Synaptic you would have to install it as it's not been installed by default in the majority of *buntu for some while. (Again - old information on the internet)

Nope - not rolling my eyes in the least, I don't for one minute believe anyone was born knowing how to use an OS, you had to learn to use Windows - you'll have to learn how to use linux too.

---

### Post by bfmetcalf on 2014-12-02
Bastille is not in the repositories for any version of Ubuntu over 12.04 (it also looks like debian removed it from their repositories as well), that wiki page is very out of date talking about stuff from 2009 and 2010 and should probably be updated.  To install bastille you will need to install it from the source code which will require some comand line stuff (this site may help a little... [http://bastille-linux.sourceforge.net/source.htm](http://bastille-linux.sourceforge.net/source.htm)) no guarantees that it will work without issues though.  

> [COLOR=#333333][FONT=Ubuntu]You might be rolling your eyes right now, but for new users this is ridiculous-- we have no idea what you are talking about.[/FONT][/COLOR]
With some of the security stuff you are trying to do, it is above what most new users are going to try to do, that is why it seems like so much information.  Most regular users don't get to in depth in stuff like you are trying to do.  Even a lot of people who have been using Linux for years don't get so deep into security.

> [COLOR=#333333][FONT=Ubuntu]What is an apt-get command, and where is this "Terminal"?[/FONT][/COLOR]
The terminal should be in the apps you have ( I'm not a Ubuntu user at the moment so I can't tell you exactly where it will be, but I think ctrl-t should bring it up) once you open the terminal you would type ```
# apt-get install package
``` to install a new program from the official repositories (the # means that you will need to use sudo or be logged in as the root user, sudo preferred).  With Linux most people are going to tell you how to do things using the terminal because it is the same no matter what desktop environment you have as it is much more standardized instead of trying to find things in the GUI.

---

### Post by Chris_Jenkins on 2014-12-02
Ok, thanks.  

I think you are presuming things when you assert that I have a Windows mindset.  I don't. Windows is too complicated to secure too, too much attack surface, not to mention (like Ubuntu) is monolithic too and not just the kernel.

Anyway, Bastille introduced the concept of a wizard to help users configure their systems to disable unused internet facing stuff to reduce attack surface.  Least privilege oriented questions, firewall set up could also be utilized in the wizard too. So, easy to implement, no command line stuff required, = more people who implement it. That's the key. 

Otherwise, you have confusion leading to frustration leading to inaction leading to insecure OS. The computer geeks and the autodidacts will be the only ones who can avail themselves, a kind of techno Darwinism, when it is the idiots of the world who need security the most.

Thanks.

I'm out, but thanks to those who took the time to reply.

---

### Post by ian-weisser on 2014-12-02
> **Chris_Jenkins said:**
> The computer geeks and the autodidacts will be the only ones who can avail themselves, a kind of techno Darwinism, when it is the idiots of the world who need security the most.

I might just make a poster from that quote.
I find it very funny.

---

### Post by bashiergui on 2014-12-02
> **Chris_Jenkins said:**
> Ok, thanks.  

I think you are presuming things when you assert that I have a Windows mindset.  I don't. Windows is too complicated to secure too, too much attack surface, not to mention (like Ubuntu) is monolithic too and not just the kernel.

Anyway, Bastille introduced the concept of a wizard to help users configure their systems to disable unused internet facing stuff to reduce attack surface.  Least privilege oriented questions, firewall set up could also be utilized in the wizard too. So, easy to implement, no command line stuff required, = more people who implement it. That's the key. 

Otherwise, you have confusion leading to frustration leading to inaction leading to insecure OS. The computer geeks and the autodidacts will be the only ones who can avail themselves, a kind of techno Darwinism, when it is the idiots of the world who need security the most.

Thanks.

I'm out, but thanks to those who took the time to reply. For a new user you sure seem to know an awful lot about security. It's remarkable, really.

I look forward to your fork of Bastille. Sounds like the perfect solution.

@ian-weisser I'd like to order 2 posters please. :)

---

### Post by bapoumba on 2014-12-03
Closing here.
@Chris_Jenkins, would you ever want to have this thread reopened, Please ask in the resolution Centre : [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

