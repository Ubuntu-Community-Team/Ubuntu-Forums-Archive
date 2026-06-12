---
title: "The day of linux viruses."
date: 2007-07-09
forum: The Cafe
---

### Post by jonward0690 on 2007-07-09
Everybody says that there will never be big problems with linux viruses because they need root privlages,but think about this if you was to some how dowload one well it needs to run as root so all it would have to do is wait till you entered sudo.Once you enter sudo it has 15 minutes to do what it wants on a root level it could even ect your sudo folder to allow it to run as sudo when it wants or even change your root password by simply entering sudo passwd.So I think when the day of linux viruses come we will have to becacious.

---

### Post by dptxp on 2007-07-09
I switched to Linux to escape those damn viruses.
Now please do not scare me.
If I could survive in Windows for so many years with tons of them roaming around, I think I shall survive a few if and when they come.

---

### Post by Sweet Spot on 2007-07-09
I have my system set so that at ANY time I try and execute anything, I'm asked for my' password. There's no time limit, and I like it that way. Besides, I think you're making it  out to be easier than what the reality would be if that time were to indeed come.

---

### Post by AlexenderReez on 2007-07-09
lol...actually that is not call virus.....think again...hm,by the way,actually linux  is secure in virus protection but not everything....hacker/cracker can still play around if they target somebody that don't really know how to protect system...there is no such thing as completely secure in this world...because as protection grow by day , evil grow by second .....

---

### Post by stchman on 2007-07-09
> **jonward0690 said:**
> Everybody says that there will never be big problems with linux viruses because they need root privlages,but think about this if you was to some how dowload one well it needs to run as root so all it would have to do is wait till you entered sudo.Once you enter sudo it has 15 minutes to do what it wants on a root level it could even ect your sudo folder to allow it to run as sudo when it wants or even change your root password by simply entering sudo passwd.So I think when the day of linux viruses come we will have to becacious.

That may be, but first you would have to chmod 755 the virus to let it be executable.  You would then need to give the specific virus sudo permission to do what it wants.  The most a virus can do on a Linux system is mess up your ~/ folder.  I recommend backups on your ~/ folder frequently.

Typing sudo to do something else is not going to do any good to the virus.

Also the 100s of Linux distros all work a little differently so a virus written for a specific linux distro probably won't have any effect on a different distro.  Windows on the other hand is windows wherever you go.

So you see you have to do too many things to let viruses propagate on a Linux machine.

---

### Post by az on 2007-07-09
> **jonward0690 said:**
> .Once you enter sudo it has 15 minutes to do what it wants on a root level 

No, it doesn't work that way.  Once you enter your sudo password, you get a 15 minute timeout, but that doesn't mean that everything on your system has root priviledges.  It just means that the user sitting at that computer, using that terminal does not have to type the password in again.  If you use sudo in a terminal, for example and at the same time, try to install a package using synaptic from the menu, you will still be asked for your password, because you are not running the package manager from that terminal.

And the Sudo/Root/User permissions model is not the reaosn why GNU/linux is secure.  A vulnerability can take over a process or make another process do things on its' behalf - you don't have to be root to compromise a system.  GNU/linux is more secure for a lot of reasons, not the least of which is the development model which makes it possible to actually fix the vulnerability instead of having to scan and remove things that can exploit it.

---

### Post by jonward0690 on 2007-07-09
Oh know I am not saying that we are going to start finding trojan horses in are computer please don't think that,it would be realy hard for it to first get into your system.All I want you guys to do is just think about it don't worry about it though that day is still far away.

---

### Post by scragar on 2007-07-09
how would a virus download itself, then keep running continualy waiting to get root privilages without causing a noticable slowing of my system?

I must admit though thatyou raise an intresting point, what happens if it asks you to do it pretending to be a new update or something?(SPM and Update Manager both ask for your passwordin this way), it could trick some users into giving up all their passwords.

still since people on linux are smarter and less common I don't think viruses will spread that fast if at all.

---

### Post by jonward0690 on 2007-07-09
> **stchman said:**
> That may be, but first you would have to chmod 755 the virus to let it be executable.  You would then need to give the specific virus sudo permission to do what it wants.  The most a virus can do on a Linux system is mess up your ~/ folder.  I recommend backups on your ~/ folder frequently.

Typing sudo to do something else is not going to do any good to the virus.

Also the 100s of Linux distros all work a little differently so a virus written for a specific linux distro probably won't have any effect on a different distro.  Windows on the other hand is windows wherever you go.

So you see you have to do too many things to let viruses propagate on a Linux machine.

Yea I knind of figured that man all I am saying is that there could be a day we don't need to just be like my system is 1000% immune to anything and then wine when something happens.

---

### Post by Wiebelhaus on 2007-07-09
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

```
evilmalware 0.6 (beta)

Copyright 2000, 2001, 2003, 2005
E\/17 |-|4><0|2z Software Foundation, Inc.

This is free software; see the source for copying conditions.  There is
NO warranty; not even for MERCHANTABILITY, COMPLETE DESTRUCTION OF IMPORTANT 
DATA or FITNESS FOR A PARTICULAR PURPOSE (eg. sending thousands of Viagra 
spams to people accross the world).

Basic Installation
==================

Before attempting to compile this virus make sure you have the correct
version of glibc installed, and that your firewall rules are set to `allow 
everything'.

1. Put the attachment into the appropriate directory eg. /usr/src

2. Type `tar xvzf evilmalware.tar.gz' to extract the source files for 
   this virus.

3. `cd' to the directory containing the virus's source code and type
   `./configure' to configure the virus for your system.  If you're
   using `csh' on an old version of System V, you might need to type
   `sh ./configure' instead to prevent `csh' from trying to execute
   `configure' itself.

4. Type `make' to compile the package. You may need to be logged in as 
   root to do this.

5. Optionally, type `make check_payable' to run any self-tests that come 
   with the virus, and send a large donation to an unnumbered Swiss bank 
   account.

6. Type `make install' to install the virus and any spyware, trojans
   pornography, penis enlargement adverts and DDoS attacks that 
   come with it.
  
7. You may now configure your preferred malware behaviour in 
   /etc/evilmalware.conf .

SEE ALSO
   evilmalware(1), evilmalware.conf(5), please_delete_all_my_files(1) 
```

---

### Post by jonward0690 on 2007-07-09
> **scragar said:**
> how would a virus download itself, then keep running continualy waiting to get root privilages without causing a noticable slowing of my system?

I must admit though thatyou raise an intresting point, what happens if it asks you to do it pretending to be a new update or something?(SPM and Update Manager both ask for your passwordin this way), it could trick some users into giving up all their passwords.

still since people on linux are smarter and less common I don't think viruses will spread that fast if at all.

You are totaly write I am just making a point that is all.

---

### Post by stchman on 2007-07-09
> **scragar said:**
> how would a virus download itself, then keep running continualy waiting to get root privilages without causing a noticable slowing of my system?

I must admit though thatyou raise an intresting point, what happens if it asks you to do it pretending to be a new update or something?(SPM and Update Manager both ask for your passwordin this way), it could trick some users into giving up all their passwords.

still since people on linux are smarter and less common I don't think viruses will spread that fast if at all.

You would have to give the downloaded virus executable permissions.  Without that it might as well be a text file.

---

### Post by aysiu on 2007-07-09
> **stchman said:**
> You would have to give the downloaded virus executable permissions.  Without that it might as well be a text file.
Why not just make a malicious .deb for cool software?

Download the .deb
Double-click it.
Install it with gDebi (which prompts you for your sudo password).
Now the malicious program has full access to your system.

The system is only as secure as its user.

---

### Post by notwen on 2007-07-09
<--- not concerned.  If you're using stuff from the appropriate repos then you shouldn't have anything to worry about.  I try not to use files from untrusted sites.

---

### Post by jonward0690 on 2007-07-09
All I am saying it is a question to ask,people say it is imposible to do this and that.Years ago they said it was imposible to go the speed of sound but we did the human mind is a powerful thing we do the imposible yes I know it would be realy hard to make a efective virus on linux and that it is still a long time before we have to worry about this problem but if there is a will there is a way.

---

### Post by aysiu on 2007-07-09
This is a discussion thread, so I've moved it to the Cafe out of Absolute Beginner.

Some further reading for you:
[why Linux has no virus, adware, or spyware?](http://ubuntuforums.org/showthread.php?t=143119&highlight=virus)
[Help me make a virus for Linux!](http://ubuntuforums.org/showthread.php?t=472334&highlight=virus)
[A Virus Idea](http://ubuntuforums.org/showthread.php?t=476727&highlight=virus)
[ Security on Ubuntu](http://www.psychocats.net/ubuntu/security)

---

### Post by Vajra Vrtti on 2007-07-09
> **aysiu said:**
> Why not just make a malicious .deb for cool software?

Download the .deb
Double-click it.
Install it with gDebi (which prompts you for your sudo password).
Now the malicious program has full access to your system.

The system is only as secure as its user.

A real virus needs more than that to be successful and not just a proof o concept. Also, it _**must**_ have a high infection rate. Even if a virus can deceive some innocent Linux users it won't spread because the infection is so difficult. As a consequence, the probability of finding such a virus in the wild is extremely small. Windows Virus are successful because they replicate easily, without user intervention, and so can infect large numbers of machines.

---

### Post by stchman on 2007-07-09
> **aysiu said:**
> Why not just make a malicious .deb for cool software?

Download the .deb
Double-click it.
Install it with gDebi (which prompts you for your sudo password).
Now the malicious program has full access to your system.

The system is only as secure as its user.

You are correct, one could also make a root Gnome account, login and surf pr0n.  Really stupid stuff will get your system hosed.

---

### Post by Polygon on 2007-07-09
stick to the offical repos, or trusted sites, dont run random programs if you dont know where they came from, and you will be fine. (this applies for both windows and linux)

---

### Post by cobrn1 on 2007-07-09
Polycon is quite right - just take care and don't be stupid... it's that simple (at least on linux).

As I'm sure has already been pointed out, you would need to run the virus off your own bat for it to work. It won't be allowed to run, and therefor hide itself in anything else without the root access, so the only way left is for you to run it yourself. The need for permission just to run makes it much harder to crack...

PS: this is why whitelisting is an inherently better idea that blacklisting, but that's another topic...

---

### Post by DoctorMO on 2007-07-09
If it became a big issue we'd end up with SELinux or some other security features. I've seen people struggle to get apache working because they have to configure the computer to allow apache services or even the apache daemon to run. hopefully we can use deb tagging and process checking to keep tags on the origin and behaviour of processes.

Anyone want to write the worlds first anti-virus/anti-rootkit gui program? (no current linux anti virus checkers, check for windows viruses and are normally used to check email on servers)

---

### Post by Polygon on 2007-07-09
> **DoctorMO said:**
> If it became a big issue we'd end up with SELinux or some other security features. I've seen people struggle to get apache working because they have to configure the computer to allow apache services or even the apache daemon to run. hopefully we can use deb tagging and process checking to keep tags on the origin and behaviour of processes.

Anyone want to write the worlds first anti-virus/anti-rootkit gui program? (no current linux anti virus checkers, check for windows viruses and are normally used to check email on servers)

There are linux Anti virus programs.... like AVG. or is what your saying is that they just check for windows viruses, but not linux ones?

---

### Post by zero244 on 2007-07-09
I think the most likely way to pick up a virus in Linux is to download a infected file like a program and install it not thinking its infected.
For instance if someone compromised the repo's and exchanged a program with a infected one.
That is not likely to happen but it could especially from someone on the inside who wanted to make a big splash in the news.
This is how a lot of Windows viruses are spread, by installing a pirated program or a freeware program that someone infected.
Now if the Ubuntu repos did get hacked into it probably would be long before the infected file or program was nixed off the system.
Linux is pretty secure especially if you download from known sources like the Ubuntu Repos.

---

### Post by smartboyathome on 2007-07-09
Couldn't a virus "consievably" be made by embedding the fork bomb in different .debs for a program that everyone wants (perhaps from a hacking incident on the home site) and after it installs, makes itself start at the beginning of a linux session? Just wondering, as this may become one of the designs used.

---

### Post by aysiu on 2007-07-09
> **smartboyathome said:**
> Couldn't a virus "consievably" be made by embedding the fork bomb in different .debs for a program that everyone wants (perhaps from a hacking incident on the home site) and after it installs, makes itself start at the beginning of a linux session? Just wondering, as this may become one of the designs used.
If the server repositories get hacked, then a lot of Ubuntu users are in trouble, yes.

---

### Post by thisllub on 2007-07-09
There is a story about a bank that installed expensive security systems only to find that all the users had  their passwords and user names on a piece of paper on the noticeboard.

---

### Post by Iandefor on 2007-07-09
> **aysiu said:**
> Why not just make a malicious .deb for cool software?

Download the .deb
Double-click it.
Install it with gDebi (which prompts you for your sudo password).
Now the malicious program has full access to your system.

The system is only as secure as its user. What's frightening is the [new apt support]("http://www.cypherbios.org/blog/?p=41&language=en") the Ubuntu developers are building into firefox. Define an apt install queue and even make it possible to specify a repository (*not *in sources.list) to grab the packages from in a single URL. I can envision so many abuses caused by *that* functionality.

---

### Post by aysiu on 2007-07-09
Security v. convenience

---

### Post by wj32 on 2007-07-09
Programs from random places can invade your terminal session and start root-ing itself?

---

### Post by Scruffynerf on 2007-07-10
Some random thoughts on this thread..

Question: Could a rootkit not do this, as they exist under the abstraction layer? Once it's there, it'll be difficult to remove, and could possibly grab essentially root priviledges.

Thought: Download a media file / rar archive buried under a jpg. File contains a buried premade executable .sh script. User runs media/opens media. .sh file goes off and via wget from evilrepo.com downloads rootkit.

Or rootkit present in media. Rootkit acts as keylogger, could be set to look for typed commands before and after synaptic or update manager process is run.

Hum... I suppose initially the file could add ./evilfiles under the home directory. So it's on a system, but isn't activated.  Question, and I guess this is where *nix security steps up - how could the exploit activate itself? Hidden plugin under an app like firefox or azereus?

--

The other possible way is if a user added a custom repo to the sources.list, containing evilfiles masquerading as updates to system files. Update or synaptic runs, installing evilfiles.

--

However, even in the above unlikely examples, that's infecting a single machine, or possibly a few if you've got a few people adding in odd repos. I can't see how there could be a network-wide corruption... unless you manage to sneak in evil code into the official repos (unlikely), and then that'll potentially corrupt an install base, such as Ubuntu Feisty, however Edgy repos would be fine, as would most other distros.

I certainly cannot see anything systematic like botnets or significant worms trashing whole networks like what exists in windows-world. It's possible that a *nix install could control such a botnet, but not be affected by one.

Interesting thread / concept.

Of course, there is a proof of concept of a cross-platform virus. See [Here (Kapersky)]("http://computerworld.com/securitytopics/security/virus/story/0,10801,110330,00.html") or [Virus Analyst]("http://computerworld.com/securitytopics/security/virus/story/0,10801,110330,00.html")

---

### Post by macogw on 2007-07-10
> **Vajra Vrtti said:**
> A real virus needs more than that to be successful and not just a proof o concept. Also, it _**must**_ have a high infection rate. Even if a virus can deceive some innocent Linux users it won't spread because the infection is so difficult. As a consequence, the probability of finding such a virus in the wild is extremely small. Windows Virus are successful because they replicate easily, without user intervention, and so can infect large numbers of machines.

You have virus confused with worm.  Worms replicate.  Viruses just screw over one person at a time.

---

### Post by lisati on 2007-07-10
Viruses **can** replicate, it's the way that worms and viruses make a nuisance of themselves that differs.

---

### Post by macogw on 2007-07-10
> **Polygon said:**
> There are linux Anti virus programs.... like AVG. or is what your saying is that they just check for windows viruses, but not linux ones?
They check for Windows viruses so that you don't pass them on to other people.  Windows users find out when something's infected because it breaks, then they (if they're smart) don't pass it on.  We can't really tell without a virus scanner because it doesn't affect our systems.

@thisllub: [http://worsethanfailure.com/Articles/Electronic-Door-Lock-Security.aspx](http://worsethanfailure.com/Articles/Electronic-Door-Lock-Security.aspx)

lisati: oh, so is replicating required for a worm but optional for a virus then?

---

### Post by lisati on 2007-07-11
> **macogw said:**
> lisati: oh, so is replicating required for a worm but optional for a virus then?

As I understand it both viruses and worms replicate, but the replication is optional for a trojan. I suppose it depending on the definitions used, you might say a virus does its mischief on the machine its run on, a worm does its mischief by clogging up the delivery mechanism, and a trojan does its mischief by hiding behind something that looks harmless. And, of course, "malware" can easily fit into more than one of these categories.

---

