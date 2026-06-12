---
title: "[SOLVED] Leak test failed! firestarter"
date: 2008-09-02
forum: Security
---

### Post by cochingeek on 2008-09-02
[SIZE="2"]Hello,
          In Ubuntu 64 I am using firestarter. I have whitelisted only the bare necessary outgoing traffic. On test at the shieldup site my file test and port test came out pass with all ports in stealth. But , I ran their Leak test by running their
leaktest,exe in wine.There was leaking of the firewall and the programme connected to their test site,thus the leak test failed. How can we prevent this leaking? Please help.[/SIZE]

---

### Post by cariboo on 2008-09-03
Wine is not a full implementation of windows so some programs are bound not to work as expected, If you are really worried about any leakage, you can use the scan tool included in Network tools, but there is a bug that gives false positives. I suggest using **nmap** and its qui **zenmap**. Both are available in the repositories, and you can use Add/Remove Programs, Synaptic Package Manger and of course the command line to install them. 

Jim

---

### Post by hyper_ch on 2008-09-03
are you sure you even need to alter the default firewall configuration?
In most cases there's no need for that.

---

### Post by brian_p on 2008-09-03
> **cochingeek said:**
> [SIZE="2"]Hello,
          In Ubuntu 64 I am using firestarter. I have whitelisted only the bare necessary outgoing traffic. On test at the shieldup site my file test and port test came out pass with all ports in stealth. But , I ran their Leak test by running their
leaktest,exe in wine.There was leaking of the firewall and the programme connected to their test site,thus the leak test failed. How can we prevent this leaking? Please help.[/SIZE]

The focus of LeakTest is the Windows platform, not Linux. There  isn't a single program on your Ubuntu system which will generate outbound traffic without your knowledge or permission so you are unnecessarily concerned and there is nothing to prevent.

---

### Post by cdenley on 2008-09-03
> **brian_p said:**
> The focus of LeakTest is the Windows platform, not Linux. There  isn't a single program on your Ubuntu system which will generate outbound traffic without your knowledge or permission so you are unnecessarily concerned and there is nothing to prevent.

Unless you start downloading software from untrusted sources, especially windows software you run in wine.

---

### Post by Oldsoldier2003 on 2008-09-03
> **cochingeek said:**
> [SIZE="2"]Hello,
 On test at the shieldup site my file test and port test came out pass with all ports in stealth. [/SIZE]
turning icmp response off on your router/gateway ( hardly necessary since its the default setting for almost every homeuser class router shipped now ) "will stealth your ports".

To be absolutely honest the tests at grc.com are pretty worthless and serve to alarm more than they do to inform. Yes this is only my personal opinion and your mileage may vary, but consider what the tests tell you as opposed to what the results (and how they are obtained) really mean.

---

### Post by Vivaldi Gloria on 2008-09-03
Like everyone said grc and leaktest.exe are irrelevant for ubuntu. No need for a firewall in ubuntu desktop because there are no servers listening to any ports (possibly except for a few listening to localhost, like cups listening to 631).

So if a packet comes to your ubuntu box then it is just ignored because there's no server listening to the port that the packet arrives to.

---

### Post by thesurgeon on 2008-09-03
Seriously im not saying anyone else is wrong in what they are saying, but none of the people know what you have on your machine or how it was installed. Yes you should have a firewall on your machine and it should be pentested. NMAP and NESSUS can normally give you a good idea whats open and whats not. Doesn't matter what OS you use, always have antivirus and a firewall installed. Theres loads of networks I've stumbled upon and mates who are trying Linux and have installed crap on their machine. They have ports open left right and center. I don't know how your machines set up and I just stumbled upon this post so sorry I'm not here to help. Just always have antivirus and firewall and keep looking for the information you need don't settle for don't worry. Do worry.

---

### Post by lisati on 2008-09-03
I use a combination of the iptables defaults (some people might say aaaargh, but who cares?) and tweaking the settings in my network hardware (routers etc) to block unwanted access from the outside.

---

### Post by Vivaldi Gloria on 2008-09-03
> **thesurgeon said:**
> Doesn't matter what OS you use, always have antivirus and a firewall installed. 

I may understand that you may suggest a firewall if you don't understand how it works but suggesting an antivirus? Are you serious? I have never heard of a linux user who got infected by a virus. Never. Loose this windows mindset. Linux has no viruses. 

Now let's look at firewalls. What happens if I send a malicious packet to your computer? In order for it to damage there must be someone to accept it. But in the default ubuntu desktop install there are no apps listening to ports - no one accepts any packets. So it is as secure as it can be.

There is no difference whether it's no apps listening or you use a firewall to drop the packet. The packet reaches to no app in any case. Hence in the default ubuntu install you don't need to bother with a firewall as no packet reaches an app. 

If you install a server program then it listens to some port. In that case you might need a firewall.

> By default, Ubuntu includes a firewall, iptables, but by default nothing is engaged. This is reasonable as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant. However, installing "server software" will cause ports to open, so some people like to use a firewall as a catch-all layer to find mistakes in their configuration.

from bodhi.zazen's security guide: [[COLOR="Blue"]security[/COLOR]]("http://ubuntuforums.org/showthread.php?t=510812")

So antivirusses and firewalls are not necessary in the default ubuntu desktop install. But your browser can still be hijacked so I suggest you install the no script extension of firefox.

---

### Post by lisati on 2008-09-03
> **Vivaldi Gloria said:**
> I may understand that you may suggest a firewall if you don't understand how it works but suggesting an antivirus? Are you serious? I have never heard of a linux user who got infected by a virus. Never. Loose this windows mindset. Linux has no viruses. 

<aside>Linux might be heaps safer than Windows from viruses and other similar malware, but it is still possible to pass them on, which isn't a very nice thing to do, and doing so contravenes some email providers' conditions of use.</aside>

---

### Post by Vivaldi Gloria on 2008-09-03
> **lisati said:**
> <aside>Linux might be heaps safer than Windows from viruses and other similar malware, but it is still possible to pass them on, which isn't a very nice thing to do, and doing so contravenes some email providers' conditions of use.</aside>

Yeah. You're right. Any mail admin should run an antivirus.

---

### Post by SEMW on 2008-09-04
> **Vivaldi Gloria said:**
> suggesting an antivirus? Are you serious?  Never. Loose this windows mindset. Linux has no viruses. 
I'm no security expert, and certainly no Linux security expert; but I can't help thinking that exhorting people to not worry about their system being compromised, and steadfastly maintaining that "Linux has no viruses", isn't so much the Linux mindset as it is just a bad security mindset.  

Semantic quibbling about what exactly constitutes a virus aside, claiming that Linux boxes are perfectly secure is surely nonsense (wasn't it just last week that Red Hat/Fedora key signing servers were [compromised]("http://linux.slashdot.org/article.pl?sid=08/08/22/1341247")?).  And while, true, a home user who runs no server software, never downloads software except from distro repositories, never uses ssh, browses the web without scripting or flash in etc. etc. is probably pretty damn secure; I'd claim that such users are probably the exception rather than the rule, no?

And while it's also true that there's probably not much point running a *Windows*-centric antivirus checker unless you're running a mail server, that's surely not an argument for not running the relevent *Linux*-centric anti-malware tools ([rootkit]("http://www.chkrootkit.org/") [detectors]("http://rkhunter.sourceforge.net/"), [integrity]("http://freshmeat.net/projects/tripwire/") [checkers]("http://projinfo.sourceforge.net/") etc.)?

---

### Post by Oldsoldier2003 on 2008-09-04
> **SEMW said:**
> 
And while it's also true that there's probably not much point running a *Windows*-centric antivirus checker unless you're running a mail server, that's surely not an argument for not running the relevent *Linux*-centric anti-malware tools ([rootkit]("http://www.chkrootkit.org/") [detectors]("http://rkhunter.sourceforge.net/"), [integrity]("http://freshmeat.net/projects/tripwire/") [checkers]("http://projinfo.sourceforge.net/") etc.)?

Well said, this is exactly the type of dissenting opinion I like to see. As I have stated many, many times in threads here and in other subforums- It is possible to express your opinion while staying within the CoC.

---

### Post by Vivaldi Gloria on 2008-09-04
> **SEMW said:**
> ... their system being compromised, and steadfastly maintaining that "Linux has no viruses", 

Well, it has no viruses. Just give me a name of a linux virus which is available in the wild and a user effected by it. 

What has getting compromised got to do anything with viruses? 

There are tons of linux servers compromised but none by a virus. There are NO linux viruses in the wild. If you are looking for security in a server then there are lots of security monitors, rootkit detectors, and intrusion detectors. Install one of them. Not an antivirus, because, again, no point of an an antivirus in a desktop or a server because there are NO linux viruses. 

> ... claiming that Linux boxes are perfectly secure is surely nonsense

Who claimed that? That's a gross misrepresentation.

I only claimed that no linux box (server or desktop) needs an antivirus and no desktop linux box needs a firewall.

> And while, true, a home user who runs no server software, never downloads software except from distro repositories, never uses ssh,

Such a user doesn't need a firewall and as you can see from my above post I was talking about "the default ubuntu desktop install" which covers such users.

> browses the web without scripting or flash in etc. etc. is probably pretty damn secure; 

What did I say above: "But your browser can still be hijacked so I suggest you install the no script extension of firefox. "

> I'd claim that such users are probably the exception rather than the rule, no?

Exception or not, this thread was about a desktop user untill your post. If you have a server then like you said you can use "Linux-centric anti-malware tools" among other things. I suggest you look at

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)
[http://tldp.org/HOWTO/Security-HOWTO/index.html](http://tldp.org/HOWTO/Security-HOWTO/index.html)
[http://tldp.org/HOWTO/Security-Quickstart-HOWTO/index.html](http://tldp.org/HOWTO/Security-Quickstart-HOWTO/index.html)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://ubuntuforums.org/showthread.php?t=901195](http://ubuntuforums.org/showthread.php?t=901195)
[http://sectools.org/](http://sectools.org/)
[http://www.linuxsecure.de/index.php?action=46](http://www.linuxsecure.de/index.php?action=46)

---

### Post by cdenley on 2008-09-04
Can we all agree that...

-linux isn't invincible
-practicing good security practices provides adequate security
-checking for rootkits couldn't hurt
-many new ubuntu users aren't aware of good security practices, never heard of noscript, and don't realize browser plugins such as flash can compromise their system
-people who may have not had the good sense to always follow good security practices should check for rootkits and learn better habits
-linux viruses do exist, but there are no known viruses that can compromise recently released linux distributions, and linux viruses are much more rare than windows

Arguments such as what this thread is turning into aren't very productive and are a bit annoying.

---

### Post by hyper_ch on 2008-09-04
-linux isn't invincible
Yes

-practicing good security practices provides adequate security
Not really... good security practices also depend on what is behind that good practice... not too long ago it was good security practice to have a password of at least 6 characters in length. Do you know why? If not you should find out ;)

-checking for rootkits couldn't hurt
Yes

-many new ubuntu users aren't aware of good security practices, never heard of noscript, and don't realize browser plugins such as flash can compromise their system
Yes

-people who may have not had the good sense to always follow good security practices should check for rootkits and learn better habits
Yes

---

### Post by cdenley on 2008-09-04
> **hyper_ch said:**
> 
-practicing good security practices provides adequate security
Not really... good security practices also depend on what is behind that good practice... not too long ago it was good security practice to have a password of at least 6 characters in length. Do you know why? If not you should find out ;)

I was referring to the concepts listed here
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by SEMW on 2008-09-04
> **Vivaldi Gloria said:**
> Well, it has no viruses. Just give me a name of a linux virus which is available in the wild and a user effected by it.

If you do want to get into that, a little Googling shows Wikipedia has a [list]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Threats").  I don't know if any of them are active.  Very probably not, since whatever vulnerabilities they exploit are, thankfully, fixed reasonably quickly in the Linux world.

But that's a very different thing from asserting that Linux does not get viruses.  New security vulnerabilities are being discovered (and fixed) all the time; if a bad guy discovers an exploitable vulnerability before it's fixed, you have the possiblity of a virus.  True, one would hope that there will be *far* fewer such oppertunities than in the Windows world, but far fewer != none.

And also, I did say "Semantic quibbling about what exactly constitutes a virus aside": yes, attacks like browser hijacking, as you note, aren't viruses, but *are* the sort of thing that Windows antivirus software these days can help protect against; hence why I'm saying that it can be misleading to new users to dismiss all their questions about antimalware software with a flat "Linux has no viruses".

@cdenley: Absolutely agreed, with every one of your points (re the last one: Im afraid 'd already typed this out by the time I read your post :-) )

---

### Post by hyper_ch on 2008-09-04
and how would an antivirus program protect you against a virus it does not know about?

---

### Post by SEMW on 2008-09-04
> **hyper_ch said:**
> and how would an antivirus program protect you against a virus it does not know about?

It doesn't.  That's why it's important to keep antivirus programs and programs like chrootkit up to date.

Of course, there are other ways of detecting malware that don't require a database of known malware. For example, two of the Linux antimalware programs I linked to are integrity checkers: i.e. they checksum your system files to ensure that they haven't been replaced with malicious versions.  Of course, there are caveats to these: e.g. they should probably be run from a liveCD rather than installed, for obvious reasons; system updates would give false positives; etc.  So something like that is probably not worth running for desktop users.

---

### Post by hyper_ch on 2008-09-04
> **SEMW said:**
> It doesn't.
So why run it when it will probably quicker fixed than AV updated?

---

### Post by egalvan on 2008-09-04
I run anti-virus programs in my linux boxen for the same reason I am a member of my Neighborhood Watch Program...

To help make my neighborhood a safer place.

No-one is (easily) breaking into my house/computer.
But I will keep an eye on my neighbor's house/computer.

No document/file/usb-memorystick/hard-drive etc will leave my computer with a virus...


Isn't that what being a good neighbor is all about?

Isn't part of "Ubuntu" being a "good neighbor"?

ErnestG

---

### Post by SEMW on 2008-09-04
> **hyper_ch said:**
> So why run it when it will probably quicker fixed than AV updated?

The rootkit checkers and integrity checkers I linked to are a good example of the answer to your question.  If a rootkit has been planted on your computer, the attacker already has root access (you need it to plant a rootkit, by definition).  So if an update comes the next day that fixes whatever hole was used to get root access, that doesn't make any difference to you.  It's bolting the barn door after the horse has flown.  Or, indeed, there may not have been any security hole at all: an attacker may just have bruteforced your password through ssh!  Both of these situations are ones that a fully updated rootkit checker should catch.

(If you're talking more generally than Linux, your assumption that the hole will probably be fixed quicker than the AV updated may well not be true in general.  For example, in the Windows world, you usually only get updates once a month; AV programs on the other hand are usually updated daily or more often.)

**Edit:** If you missed the earlier part of the thread:  No, I'm not arguing that the majority of desktop Linux users need to regularly run AV, rootkit checkers, etc.; only that it is a bad idea to feed all new Ubuntu users asking about security and viruses a flat "Linux has no viruses", rather than a more cautious answer.

---

### Post by thesurgeon on 2008-09-04
People keep say Linux doesnt have viruses, well ill say your wrong. Yes every OS has viruses, aslong as theres people there will be viruses. To show some of the linux viruses etc there is a list of just some of them. So again always have virus protection and a firewall.

Some trojans, viruses, and worms are as follows:-

Trojans

Kaiten - Linux.Backdoor.Kaiten trojan horse
Rexob - Linux.Backdoor.Rexob trojan

Viruses

Alaeda - Virus.Linux.Alaeda
Bad Bunny - Perl.Badbunny 
Binom - Linux/Binom
Bliss 
Brundle
Bukowski
Diesel - Virus.Linux.Diesel.962
Kagob a - Virus.Linux.Kagob.a
Kagob b - Virus.Linux.Kagob.b
MetaPHOR (also known as Simile) 
Nuxbee - Virus.Linux.Nuxbee.1403
OSF.8759 
Podloso - Linux.Podloso (The iPod virus)
Rike - Virus.Linux.Rike.1627
RST - Virus.Linux.RST.a
Satyr - Virus.Linux.Satyr.a
Staog 
Vit - Virus.Linux.Vit.4096
Winter - Virus.Linux.Winter.341 
Winux (also known as Lindose and PEElf)
ZipWorm - Virus.Linux.ZipWorm 

Worms

Adm - Net-Worm.Linux.Adm
Adore
Cheese - Net-Worm.Linux.Cheese 
Devnull 
Kork
Linux/Lion (also known as Ramen) 
Mighty - Net-Worm.Linux.Mighty
Millen - Linux.Millen.Worm
Slapper
SSH Bruteforce

---

### Post by cdenley on 2008-09-04
> **thesurgeon said:**
> People keep say Linux doesnt have viruses, well ill say your wrong. Yes every OS has viruses, aslong as theres people there will be viruses. To show some of the linux viruses etc there is a list of just some of them. So again always have virus protection and a firewall.

Some trojans, viruses, and worms are as follows:-

Trojans

Kaiten - Linux.Backdoor.Kaiten trojan horse
Rexob - Linux.Backdoor.Rexob trojan

Viruses

Alaeda - Virus.Linux.Alaeda
Bad Bunny - Perl.Badbunny 
Binom - Linux/Binom
Bliss 
Brundle
Bukowski
Diesel - Virus.Linux.Diesel.962
Kagob a - Virus.Linux.Kagob.a
Kagob b - Virus.Linux.Kagob.b
MetaPHOR (also known as Simile) 
Nuxbee - Virus.Linux.Nuxbee.1403
OSF.8759 
Podloso - Linux.Podloso (The iPod virus)
Rike - Virus.Linux.Rike.1627
RST - Virus.Linux.RST.a
Satyr - Virus.Linux.Satyr.a
Staog 
Vit - Virus.Linux.Vit.4096
Winter - Virus.Linux.Winter.341 
Winux (also known as Lindose and PEElf)
ZipWorm - Virus.Linux.ZipWorm 

Worms

Adm - Net-Worm.Linux.Adm
Adore
Cheese - Net-Worm.Linux.Cheese 
Devnull 
Kork
Linux/Lion (also known as Ramen) 
Mighty - Net-Worm.Linux.Mighty
Millen - Linux.Millen.Worm
Slapper
SSH Bruteforce

Congratulations, you can copy and paste from wikipedia. Now which of those should be a concern to ubuntu users (if any)? If you were merely trying point out the fact that linux viruses do exist, the point has been made already and hasn't been disputed.

---

### Post by Vivaldi Gloria on 2008-09-04
> **cdenley said:**
> -practicing good security practices provides adequate security

Good security practices are not set on stone. That's why we are discussing what they are. 

> Arguments such as what this thread is turning into aren't very productive and are a bit annoying.

If you find it annoying then don't read it. ;)


> **SEMW said:**
> If you do want to get into that, a little Googling shows Wikipedia has a list.

I have never heard of an ubuntu desktop user who got infected. Really. 

> But that's a very different thing from asserting that Linux does not get viruses.  

If a day comes when there are linux viruses then it'll make sense to use an antivirus.

> New security vulnerabilities are being discovered (and fixed) all the time; 

Yes. It's important to keep your system updated. 

> if a bad guy discovers an exploitable vulnerability before it's fixed, you have the possiblity of a virus.  

If a day comes when it's a reality rather than a possibility then it'll make sense to use an antivirus. 

> True, one would hope that there will be *far* fewer such oppertunities than in the Windows world, but far fewer != none.

none=none. There are no linux viruses (in the wild).

> And also, I did say "Semantic quibbling about what exactly constitutes a virus aside": 

Now, now, you changed the meaning of virus to something like "all bad things that can happen to a computer". I never used it in that sense. 

> yes, attacks like browser hijacking, as you note, aren't viruses, but *are* the sort of thing that Windows antivirus software these days can help protect against; 

I'm all for an app like no script who prevents browser vulns.

>  hence why I'm saying that it can be misleading to new users to dismiss all their questions about antimalware software with a flat "Linux has no viruses".

Again, it's you who use "virus" as "all bad things that can happen to a computer". I always used it in a technical sense. 

Besides, I think it's enough for a new ubuntu desktop user to do the following things to be secure:

1) Install programs from repos (ask here if you cannot find an app in repos).
2) Don't run arbitrary scripts that you see or receive.
3) Keep your system updated.
4) Install the no script extension of firefox. 

These will protect 99.99 percent of all ubuntu desktop users against anything (provided that some bad guy doesn't get physical access to their computer!).

>  If a rootkit has been planted on your computer ...

I can't see how a rootkit can be planted on an ubuntu desktop computer if the user is careful about the four points above. Don't forget that there are no apps listening to any ports.

So your idea which sounds like "doomsday is coming, let's install every security program we can find" is unfounded. A desktop ubuntu user can be secure without using a single security program (barring no script). 

Thus it's good to tell all new Ubuntu desktop users the four points above and it's ok to add a flat "Linux has no viruses" even if we use virus in your sense. I'm (and always was) explicitly talking about desktop users here.

> **thesurgeon said:**
> People keep say Linux doesnt have viruses, well ill say your wrong. Yes every OS has viruses, aslong as theres people there will be viruses. To show some of the linux viruses etc there is a list of just some of them. So again always have virus protection and a firewall. ...

Sorry but never heard any virus effective in the wild. Also there is no added protection that a firewall can add to ubuntu desktop because of the technical reason I said above (no app listening). Also ssh bruteforce type of things don't count because I'm talking about ubuntu desktop.

I'm not trying to be an *** here. I really can't see why an ubuntu desktop user needs any security software if s/he's careful about the four items. 

But of course there is no harm in using additional security software.

---

### Post by hyper_ch on 2008-09-04
> **SEMW said:**
> The **rootkit checkers** and integrity checkers I linked to are a good example of the answer to your question.
Nevertheless they are not antivirus programs.

> **SEMW said:**
> only that it is a bad idea to feed all new Ubuntu users asking about security and viruses a flat "Linux has no viruses", rather than a more cautious answer.
Nevertheless viruses are no problem on linux and hence antivirus is (generally) not needed...


> **thesurgeon said:**
> People keep say Linux doesnt have viruses, well ill say your wrong.
No, people say viruses are not a problem on linux ;) that's something different ;)

> **thesurgeon said:**
> To show some of the linux viruses etc there is a list of just some of them.
[....]

(1) those are not "some" but very likely "all" viruses
(2) do any of those still pose a security risk? I don't think so as the source code has been fixed
(3) now compare that "long" list to about 60'000 known viruses on windows... and now ask yourself if windows has fixed all its security wholes - you get the idea?

> So again always have virus protection and a firewall.
(1) Ok, how does a firewall prevent viruses coming into your system?
(2) As said before, those viruses don't pose any risk on linux anymore... and new viruses will not be recgonized... so what do you want av for?
(3) The only real usage of av is when you run a mail- or fileserver so that you check the files and mails that other windows users won't get infected... if you are a business or something you are sort of mandated to do this, otherwise you could lose your clients. As a private person I think everybody should take care of their security on their own...

---

### Post by hyper_ch on 2008-09-04
btw, all those who think that you really, really, really, really, really must run antivirus in order to be safe, have a little read here: [http://www.schneier.com/blog/archives/2008/09/movie_plot_thre_2.html](http://www.schneier.com/blog/archives/2008/09/movie_plot_thre_2.html)

---

### Post by brian_p on 2008-09-04
> **SEMW said:**
> If you do want to get into that, a little Googling shows Wikipedia has a [list]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Threats").  I don't know if any of them are active.

I have researched that list extensively so can tell you none are active. Furthermore, none of the so-called viruses were ever active because they do not work.

> Very probably not, since whatever vulnerabilities they exploit are, thankfully, fixed reasonably quickly in the Linux world.

Viruses don't exploit vulnerabilities. Worms do. In the case of the so-called viruses there was nothing to fix.

> But that's a very different thing from asserting that Linux does not get viruses.  New security vulnerabilities are being discovered (and fixed) all the time; if a bad guy discovers an exploitable vulnerability before it's fixed, you have the possiblity of a virus.

No - you have the possibility of a worm. Semantics, I know, but the meanings words are important and help people to understand why Linux does not get viruses.

---

### Post by brian_p on 2008-09-04
> **SEMW said:**
> 

**Edit:** If you missed the earlier part of the thread:  No, I'm not arguing that the majority of desktop Linux users need to regularly run AV, rootkit checkers, etc.; only that it is a bad idea to feed all new Ubuntu users asking about security and viruses a flat "Linux has no viruses", rather than a more cautious answer.

New users often come to Linux with the notion that viruses are a fact of life on all OSs and are frequently resistant to the fact there are none and will be none. I agree a more detailed and cautious explanation of the differences between viruses, trojans and worms is better.

---

### Post by Oldsoldier2003 on 2008-09-05
> **egalvan said:**
> I run anti-virus programs in my linux boxen for the same reason I am a member of my Neighborhood Watch Program...

To help make my neighborhood a safer place.

No-one is (easily) breaking into my house/computer.
But I will keep an eye on my neighbor's house/computer.

No document/file/usb-memorystick/hard-drive etc will leave my computer with a virus...


Isn't that what being a good neighbor is all about?

**Isn't part of "Ubuntu" being a "good neighbor"?**

ErnestG

+1

Even though I am not a big fan of antivirus for Linux I must admit you make a compelling argument. Though people can argue this until the wee hours of the morning, and this thread really should be moved to recurring discussions I have to give you credit where credit is due.

---

### Post by thesurgeon on 2008-09-05
Well im not gonna waste time with you guys, Ill keep the way I do things and you guys can argue that you havent heard of Linux viruses...see what happens.

:popcorn:

---

### Post by hyper_ch on 2008-09-05
> **thesurgeon said:**
> see what happens.
The same as in the last 5 years ;)

---

### Post by jerome1232 on 2008-09-05
I think part of the argument stems from the semantics, some people think virus = every and all types of malware. Others think no firewall = Invite to hacker to hack system. People seem to hear "Linux has no security issues just relax and don't worry about it" when what was said was "A desktop computer doesn't really need anti-virus/firewall".

thesurgeon points to a list of viruses for linux, I'm not about to do exahustive research on that list but the ones I have looked into were proof-of-concept viruses, then patched, no real world usage came about before the patch came. 

The same is true of most exploits I hear about in the Linux world.

When talking about the average desktop environment I feel security boils down to the user and his(her) browser, the security of said browers plugins, good sane practices when downloading and running scripts, and/or downloading and installing software.

I do not feel that anti-virus/firewall assists in securing the individual Linux desktop computer.

Even in the server world security seems to deal with SELinux/Apparmour (kernel hardening), **properly configuring** the services you are going to be running, keeping backups, integrity checking, and staying updated and aware of current security events, not your firewall and anti-virus.

Now I'm no security expert but I think I've grasped the basics of security on Linux vs Windows.

---

### Post by egalvan on 2008-09-06
**I think part of the argument stems from the semantics,**

I agree with this statement, but from a different perspective...

I agreee with most everyone on this thread that **LINUX** does not need (at this time) an anti-virus program...

But as long as Windows is out there, and we Linux users interact with them,
 then Linux** COMPUTERS** should run anti-virus, if just to make sure we do not pass on any *bad things* to our Windows brothers.


At this point, I need to boot Windows to clean infected drives and USB sticks, until I get up to speed on ClamAV.
And this Win machine is erased and re-loaded at least once a week.

I for one will be glad when the anti-virus/trojan/root-kit tools are as good on Linux as on Windows... 
Not because Linux needs them, but because I repair Windows machines...
I feel MUCH safer doing this with Linux....

ErnestG

---

### Post by Vivaldi Gloria on 2008-09-20
I know this is an old thread but something bothered me.

> **egalvan said:**
> But as long as Windows is out there, and we Linux users interact with them,
 then Linux** COMPUTERS** should run anti-virus, if just to make sure we do not pass on any *bad things* to our Windows brothers.

Almost all contact I have with the windows world is through my gmail account. So I cannot help any windows users by installing an antivirus.

I understand why an email admin should install an antivirus but why should a regular desktop ubuntu user bother? It's email admin's responsibility to get rid of viruses, not a desktop user's. 

Also, I pay a lot of money to get a computer. Why on earth should I install an antivirus to slow down my system to save a couple of clueless windows users who don't use antivirus to begin with? I'm all for educating them but expecting me to wipe their asses is too much. 

A desktop ubuntu system cannot save the windows world and it's loss of time and resources to try it by installing an antivirus. It's server admin's job to use antivirus tools, not a desktop ubuntu user's job. So this brotherly love talk is nonsense.

> Not because Linux needs them, but because I repair Windows machines...
I feel MUCH safer doing this with Linux....

What does this got to do with installing an antivirus in a ubuntu desktop? Of course an antivirus is justified in a windows repair shop. 


I repeat: It's enough for a new ubuntu desktop user to do the following things to be secure:

1) Install programs from repos (ask here if you cannot find an app in repos).
2) Don't run arbitrary scripts that you see or receive.
3) Keep your system updated.
4) Install the noscript extension of firefox.

These will protect 99.999 percent of all ubuntu desktop users against anything (provided that some bad guy doesn't get physical access to the computer!).

You do NOT need to change firewall settings unless you install a server application which opens ports. You definetely do NOT need an antivirus.


The End.

---

### Post by hyper_ch on 2008-09-20
> **egalvan said:**
> But as long as Windows is out there, and we Linux users interact with them, then Linux** COMPUTERS** should run anti-virus, if just to make sure we do not pass on any *bad things* to our Windows brothers.
Why? If they don't have antivirus on their computer or don't protect them they will get infected. Chance that it will be you who infect them tends towards null if appropriate security is missing. If the security is in place, then it doesn't matter if you run antivirus also... because their computer is secure.

---

### Post by kevdog on 2008-09-20
I think antivirus programs are cool!

---

### Post by cpetercarter on 2008-09-20
Whatever else they are, AV programmes are not cool. When I had Windows XP on my machine, I had Zone Alarm AV and Firewall, and two anti-spyware programmes. I could make a cup of coffee, make a few phone calls and finish the sudoku in the time it took this merry band to complete their business and let me have a useable desktop.

---

### Post by Vivaldi Gloria on 2008-09-20
> **cpetercarter said:**
> Whatever else they are, AV programmes are not cool. 

+1. They kill resources.

> I had Zone Alarm 

This reminded me the 2005-6 news:

> It seems that ZoneAlarm Security Suite has been phoning home, even when told not to. Last fall, InfoWorld Senior Contributing Editor James Borck discovered ZA 6.0 was surreptitiously sending encrypted data back to four different servers, despite disabling all of the suite’s communications options. Zone Labs denied the flaw for nearly two months, then eventually chalked it up to a “bug” in the software -- even though instructions to contact the servers were set out in the program’s XML code. 

from [[COLOR="Sienna"]infoworld[/COLOR]]("http://www.infoworld.com/article/06/01/13/73792_03OPcringley_1.html").

---

