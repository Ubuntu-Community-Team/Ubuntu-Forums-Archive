---
title: "Is Windows REALLY that virusy?"
date: 2008-10-03
forum: Windows
---

### Post by NintendoTogepi on 2008-10-03
I've been using Windows XP for about 7 years now, I think. Over the course of that time, I've only gotten two viruses, the latter of which was in 2004. 

I don't use an anti-virus except for the very limited free one that came with my computer, but no viruses.

I don't understand how people get the viruses?

---

### Post by daniel_I on 2008-10-03
install a good, trustworthy antivirus and u will be surprised at how many u will find

---

### Post by amauk on 2008-10-03
> **NintendoTogepi said:**
> I've only gotten two viruses
2 that you know about

seriously, most malware tries **very** hard to be invisible

---

### Post by daniel_I on 2008-10-03
that's true, **VERY** hard

---

### Post by Silent Ninja on 2008-10-03
> **daniel_I said:**
> install a good, trustworthy antivirus and u will be surprised at how many u will find

One Firewall, one active antispyware and a good (or even free, but reliable) antivirus, and.. tadá, you're done.

It's all about what you do, because if you work only with official software and don't execute any exe, scr, pif.. from the internet..  and just visit sites like Google or Clarin, Ubuntu site, which are known not to be infected... it's really hard to get infected.

The fact is that people who uses windows, are mostly guys that don't know anything about security and would run a file called "this is a virus yeah, run me.exe" if some friend seems to have sent it to him, and once he ran it.. it's infected.

On linux by the other way, unless you're too dumbass to use the root account to navigate on internet, download and install things you don't know, you're like 80% securer than on windows.

Linux also have some "viruses", called rootkits, but they're hard to find, and if you have the latest kernel, you're almost 100% secure against them.

Windows is not a fully insecure system, it's just unsecurer than others.

---

### Post by daniel_I on 2008-10-03
that's true, but u don't have to run a file to get infected, some web sites will actually install viruses into your computer, and u need a good firewall and antivirus to detect and stop it, mine isn't good enough. but that's why i love ubuntu because, well, windows apps dont really work, and if u try to install one, wine will give u a message and so it is on the internet. windows is not at all secure to brouse the internet, and if im not mistaken, rootkits will invade your boot sector, making sence that ubuntu would have them too, but like u said, they arnt that common.

---

### Post by daniel_I on 2008-10-03
what do u mean by tada

---

### Post by NintendoTogepi on 2008-10-03
If I haven't even noticed them, why are they a problem? :confused:

---

### Post by cardinals_fan on 2008-10-03
Anti-* provides a false sense of security and is worthless without user competence.

I used one XP install for 6 years, and got no viruses or malware.  How do I know?  I scanned with five major anti-* apps at the end of the 6 years and found nada.  That doesn't mean that I didn't have anything, but even if I did, those apps would have done no good.

---

### Post by Jose Catre-Vandis on 2008-10-03
I have to agree with the OP to some point. Both my kids run XP, fully updated,with no anti-virus/antispyware and the default firewall. Two bits of malware in the last three years. I regularly do a sweep on their machines just to check, but find nothing of note to worry about. They are behind a NAT on the router, and of course do not venture to "those" web-sites where the nasties live :)

---

### Post by amauk on 2008-10-03
> **NintendoTogepi said:**
> If I haven't even noticed them, why are they a problem? :confused:
why is it a problem?
seriously....

there was a virus (broad sense of the word, it was actually a combination of a trojan and a rootkit) that sat on a persons machine and stole login credentials
specifically email accounts, but variations cropped up that targeted FTP, SSH & other services

the rootkit took the form of a modified keyboard driver, as well as piping the keyboard character sequences to user programs, it parsed them looking for anything that looked like a username/password combo, and logged them to the end of driver system file

the trojan attached itself to the users email client and masked it's activities by hiding among legitimate email activity

It waited until the user sent an email, and 
when an email is sent, an additional recipient (just a disposable address used to harvest the login info) is added to the Bcc header

in addition to this, the info collected so far is appended to the email (malformed, so it doesn't show up as an actual attachment in email clients)
and copies of the trojan/rootkit combo are inserted

the real recipient of the email gets infected
the secret email recipient gets the login details
neither the original user nor the real recipient are any the wiser
the only outward evidence of anything suspicious is that certain emails are a few dozen kb's larger than they normally would be

purpose: your compromised email account is now used as routing account for spam

so, why are they a problem?

---

### Post by L815 on 2008-10-03
No it's not. 

Getting a virus on Windows is the same as telling someone to run rm -rf in Linux and they do it without knowing what it does.

Majority of junk installed on Windows is from carelessness in general.

---

### Post by Giant Speck on 2008-10-03
> **L815 said:**
> No it's not. 

Getting a virus on Windows is the same as telling someone to run rm -rf in Linux and they do it without knowing what it does.

Majority of junk installed on Windows is from carelessness in general.

+1

It's not the operating system.  It's the user.

---

### Post by cammin on 2008-10-03
> **daniel_I said:**
> install a good, trustworthy antivirus and u will be surprised at how many u will find

Especially when you pay for one and the subscription is just about to expire. If only those viruses had waited a week. They wouldn't have given you a reason to re-subscribe.

---

### Post by steveneddy on 2008-10-03
We use XP at work and only go to industry websites and we still all get about four different little buggers a week.

We scan with an updated Mcafee nightly.

Of course if we weren't all running as administrator I think we would do a little better.

:)

---

### Post by Frak on 2008-10-03
> **Giant Speck said:**
> +1

It's not the operating system.  It's the user.
i.e. PEBCAK

Ubuntu is just as susceptible to harm as Windows if the users are ignorant and/or careless.

---

### Post by Canis familiaris on 2008-10-04
> **cardinals_fan said:**
> Anti-* provides a false sense of security and is worthless without user competence.


+1. 

If you want secure Windows use SuRun or SuDown.

---

### Post by Sorivenul on 2008-10-04
Short answer: Yes.
Extended answer: IMO, it is the user's responsibility to keep his/her machine secure, clean and operational.  What measures need to be taken vary from individual to individual.

For computer virus information is suggest the [WildList]("http://www.wildlist.org/").
Also, while dated, [this article]("http://www.linuxtoday.com/security/2006050502026OPSW") gives an interesting spin on Linux vs Windows on the virus front.
And one final, yet slightly dated, [word on OS security]("http://www.esecurityplanet.com/views/article.php/11163_3665801_1") that is related.

---

### Post by davidryder on 2008-10-04
Viruses start with a fallible user. I don't remember the last time I ran AV software and I've been on the same install since Vista came out. 

My router pretty much stops any attacks plus I don't run any servers on my Vista machine and I don't download anything or click yes to anything I'm not 100% on. If I can't validate the source I can live without it. 

While I'm on constant guard with Vista it's much more relaxed in Linux. I'm still wary about what I install (read: do I *really* need this?) but as long as I'm not prompted for my sudo or root password I have little to worry about. I do a weekly backup of my /home folder automatically (new & modified files only) so recovery isn't that far if my $HOME folder is ever wrecked. 

I heart Linux. srsly

---

### Post by K.Mandla on 2008-10-04
I remember seeing a BBC short once about two years ago where they connected a pure XP installation directly to the Internet, expecting it to go a few days before someone found it and hacked into it, or implanted a virus on it.

It only took a few hours. And it wasn't a live broadcast either, so it wasn't someone watching the show and breaking into the system at the same time. The broadcasters were visibly amazed.

---

### Post by davidryder on 2008-10-04
> **K.Mandla said:**
> I remember seeing a BBC short once about two years ago where they connected a pure XP installation directly to the Internet, expecting it to go a few days before someone found it and hacked into it, or implanted a virus on it.

It only took a few hours. And it wasn't a live broadcast either, so it wasn't someone watching the show and breaking into the system at the same time. The broadcasters were visibly amazed.

That's pretty insane. Is that one of those times that a vulnerability is found before a patch is release or something that is just a downfall of Windows?

When I enabled my SSH server I was getting brute-force attacks hours later. I don't understand how they find IP's so quickly... unless they are just scanning IPs on a continual basis.

---

### Post by Kinetic_lord on 2008-10-04
The most insecure you mean...

---

### Post by Kinetic_lord on 2008-10-04
There were only 2 viruses you knew about... Windows doesn't crash only because of viruses so that's why you don't know if you had viruses. btw what anti virus did you had?

P.S. I can't understand how people can actually BUY an antivirus and find viruses on their computer...

---

### Post by ronnielsen1 on 2008-10-04
Well, you people that had no problems with xp are very lucky. Not the scenario I had. I had 2 kids at the house and I switched to linux because I was tired of getting nasties even after having windows protected to the point of being ridiculous. I popped a Mandrake cd (I think it was) figured out how to install it (no live cd's then) and after a lot of  ](*,)
 finally got it figured out.
My kids weren't too excited about the change initially. They got over it[ATTACH]87237[/ATTACH]

---

### Post by davidryder on 2008-10-04
> **ronnielsen1 said:**
> Well, you people that had no problems with xp are very lucky. Not the scenario I had. I had 2 kids at the house and I switched to linux because I was tired of getting nasties even after having windows protected to the point of being ridiculous. I popped a Mandrake cd (I think it was) figured out how to install it (no live cd's then) and after a lot of  ](*,)
 finally got it figured out.
My kids weren't too excited about the change initially. They got over it[ATTACH]87237[/ATTACH]

Luckily my GF doesn't use the computer enough to reall know the difference between Windows and Linux.

---

### Post by aysiu on 2008-10-04
It's easy for power users on these forums to say "I've never gotten a virus in Windows," but most computer users are not that savvy about good security practices, and viruses *are* a real problem on Windows, particularly XP, which defaults to running as administrator.

---

### Post by lisati on 2008-10-04
> **NintendoTogepi said:**
> If I haven't even noticed them, why are they a problem? :confused:

I recently had a virus on my XP system without realising a few days after a clean install of XP. I had noticed that the wireless did seem to be behaving a bit oddly (dropping its connection after a short time) but initially put it down to having a lot going on in the machine - video editing can be resource hungry. Another clean install of XP after I noticed that one of the system restore point files mentioned in the logs seems to cure the wireless woes. (I subsequently had partition problems when replacing the existing install of Ubuntu with Xubuntu. The system was subsequently restored to functionality, but that's another story. Unless of course there was mischief done to the relevant partition tables that I hadn't noticed.)

---

### Post by Torgas Prim on 2008-10-04
What the OP obviously forgot to mention, he probably has dialup access with no software like AOL  :lolflag:

---

### Post by Koori23 on 2008-10-04
"Client for Microsoft Networks", the concept there is mind boggling. The last time I had XP running as my primary OS, port 445 and a few others would broadcast themselves even with the default firewall enabled. Why you'd broadcast system service ports by default is beyond me.

ActiveX Controls.. Even if you're running as an LUA, you can still have a messed up system if you're using IE as your browser.

The thing that bugs me the most is.. You have to have like 4 programs dedicated to keeping your system in shape. Firewall, AV, AdAware and Defrag.. That sounds like a lot of time wasted just keeping your system up to date.

---

### Post by 3rdalbum on 2008-10-04
> **Silent Ninja said:**
> It's all about what you do, because if you work only with official software and don't execute any exe, scr, pif.. from the internet..  and just visit sites like Google or Clarin, Ubuntu site, which are known not to be infected... it's really hard to get infected.

But not impossible. My father had two firewalls (one in router, one on his computer), never opened any unsolicited e-mail or executable attachments, and the only software he installed was stuff that was personally recommended to him by people he knew. I ended off having to remove "zlob.downloader" - an infection that downloads more malware. To this day, neither of us know how on earth he got it, or if maybe I contracted it while I owned the computer. It doesn't matter now - the incident convinced him to switch to Linux Mint.

---

### Post by cardinals_fan on 2008-10-04
> **ronnielsen1 said:**
> Well, you people that had no problems with xp are very lucky. Not the scenario I had. I had 2 kids at the house and I switched to linux because I was tired of getting nasties even after having windows protected to the point of being ridiculous. I popped a Mandrake cd (I think it was) figured out how to install it (no live cd's then) and after a lot of  ](*,)
 finally got it figured out.
My kids weren't too excited about the change initially. They got over it[ATTACH]87237[/ATTACH]
I hope you weren't letting your kids run with admin accounts...
> **aysiu said:**
> It's easy for power users on these forums to say "I've never gotten a virus in Windows," but most computer users are not that savvy about good security practices, and viruses *are* a real problem on Windows, particularly XP, which defaults to running as administrator.
That's why I set up my mom's XP system with an LUA and Opera :)
> **Koori23 said:**
> 
ActiveX Controls.. Even if you're running as an LUA, you can still have a messed up system if you're using IE as your browser.

...which is why you should never, ever run IE.

---

### Post by jrusso2 on 2008-10-04
I have been using Windows of some form since about 93, so thats about 15 years.  Never got a single virus, trojan or other malware and for years I never used a background anti virus.

But its more about knowing what to do and exercising caution.  But I have seen enough infected machines to know yes Windows really is that virusy if you don't know what your doing or just don't care.

---

### Post by Kinetic_lord on 2008-10-04
> **L815 said:**
> No it's not. 

Getting a virus on Windows is the same as telling someone to run rm -rf in Linux and they do it without knowing what it does.

Majority of junk installed on Windows is from carelessness in general.

Thwe first 42 seconds on the internet in a unprotected windows means you have an infected computer. "Careless???" Would you buy an antivirus even if you know it doesn't protect you from ALL viruses?

---

### Post by Battie on 2008-10-04
Why do people keep saying "that you knew about"?  If you know what you're doing (and I assume most of the advice-givers here do), it's fairly obvious when you have an active infection of some kind.  You might not see right away, but then you'll notice strange processes, services or startup entries, at the very least.  The only thing that a savvy tech has any excuse to miss, IMO, is a really good rootkit.

---

### Post by cardinals_fan on 2008-10-04
> **Kinetic_lord said:**
> Thwe first 42 seconds on the internet in a unprotected windows means you have an infected computer. "Careless???" Would you buy an antivirus even if you know it doesn't protect you from ALL viruses?
Antivirus is a scam, and I've never seen any decent evidence proving otherwise.  That 42-second number is doubtful (to me).  As I have already said, I ran XP for 6 years with no anti-*, and when I finally ran scans with a number of noted anti-* products, none of them found anything.

---

### Post by rsambuca on 2008-10-04
> **cardinals_fan said:**
> Antivirus is a scam, and I've never seen any decent evidence proving otherwise.  That 42-second number is doubtful (to me).  As I have already said, I ran XP for 6 years with no anti-*, and when I finally ran scans with a number of noted anti-* products, none of them found anything.

Antivirus is definitely not a scam, but it should be taken for what it is - the last line of defence.  If you know what you are doing and are careful, you really don't need one.  Like you, I only run scans occassionally and don't have it running  all the time, and have never had a virus.  I would not recommend this to everyone though.

---

### Post by Kernel Sanders on 2008-10-04
The answer to the thread title is no, for vista especially so. The problem is between the keyboard and the chair.

---

### Post by NintendoTogepi on 2008-10-04
> **Kinetic_lord said:**
> There were only 2 viruses you knew about... Windows doesn't crash only because of viruses so that's why you don't know if you had viruses. btw what anti virus did you had?

P.S. I can't understand how people can actually BUY an antivirus and find viruses on their computer...

Well, no viruses, no spyware, nothing that would impede my computer efforts in the slightest.

My anti-virus is a crappy mcaffee that came as bloatware 3 years ago. It does nothing.

> **K.Mandla said:**
> I remember seeing a BBC short once about two years ago where they connected a pure XP installation directly to the Internet, expecting it to go a few days before someone found it and hacked into it, or implanted a virus on it.

It only took a few hours. And it wasn't a live broadcast either, so it wasn't someone watching the show and breaking into the system at the same time. The broadcasters were visibly amazed.

What? :confused: That's baffling. I've never had anything like that.

> **Torgas Prim said:**
> What the OP obviously forgot to mention, he probably has dialup access with no software like AOL  :lolflag:

:|

No, I've got DSL although it could definitely use to be a bit faster.

> **3rdalbum said:**
> But not impossible. My father had two firewalls (one in router, one on his computer), never opened any unsolicited e-mail or executable attachments, and the only software he installed was stuff that was personally recommended to him by people he knew. I ended off having to remove "zlob.downloader" - an infection that downloads more malware. To this day, neither of us know how on earth he got it, or if maybe I contracted it while I owned the computer. It doesn't matter now - the incident convinced him to switch to Linux Mint.

Indeed, my one virus from 2004 I'm still baffled how I got it. I never went on anything that could be even slightly questionable, and I got this awful virus that changed my desktop background, my homepage, installed programs....I still get nightmares about getting a virus on my computer!

---

### Post by Jaxco on 2008-10-04
> **L815 said:**
> No it's not. 

Getting a virus on Windows is the same as telling someone to run rm -rf in Linux and they do it without knowing what it does.

Majority of junk installed on Windows is from carelessness in general.

Exactly

---

### Post by NintendoTogepi on 2008-10-10
I would just like to bring this back. I seen someone on another site exaggerating about Windows viruses.

There's no need to exaggerate Windows viruses, there's plenty other reasons to switch to Linux! :)

---

