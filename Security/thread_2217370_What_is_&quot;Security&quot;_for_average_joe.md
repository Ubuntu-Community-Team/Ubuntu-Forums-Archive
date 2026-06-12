---
title: "What is &quot;Security&quot; for average joe?"
date: 2014-04-17
forum: Security
---

### Post by husseinmoussa on 2014-04-17
Hi,
My question revolves around what is security like for an average user like me and other people around the world

Let me introduce myself (my background with the OSs generally) since we don't know one another just to save time

I've  been a windows user since 1995, I used to run most of my games from DOS  so I'm familiar with boring black and white screens with many lines!  Haha

I also used to play around with files of windows and stuff  like that; for example, I tracked down every single file of a program  called : system file checker on win me. Copied them all in one folder  and ran the program on a win98 and made it scan the system with results  on my friend’s computer. (btw I’m not saying that I’m genius or anything  I’m just saying that I was a young kid who didn’t settle with clicking  and right clicking!) anyways, he was an engineer, he liked what I did  and told me about this thing called linux. “something like windows” he  said. (of course he just wanted to simplify things for me then ) I said  ok, let me see. ran it with qemu emulator and so on...


I  liked it. So I searched, and found Ubuntu. But I didn’t stop there. I  had more free time in my hands; so I tried xubuntu, kubuntu, lubuntu  (much earlier before it becomes a relatively stable distro), And  recently I just ran mint. But I’m not an expert with the shell and the  terminal commands and such (yet!)

And finally I have downloaded,  like, almost literally a dozen of .ISOs and files of many distros of  linux and BSDs to check out and settle on a specific one to take for a  looong journey (haven’t install BSDs yet, but that’s another issue than  my questions)

I also understand the BSD is somehow different than Linux, with the tools of the repositories and such.

Quote from wiki:

“FreeBSD  is a complete operating system. The kernel, device drivers, and all of  the userland utilities, such as the shell, are held in the same source  code revision tracking tree. (This is in contrast to Linux  distributions, for which the kernel, userland utilities, and  applications are developed separately, and then packaged together in  various ways by others.) Third-party application software may be  installed using various software installation systems, the two most  common being source installation and package installation, both of which  use the FreeBSD Ports system.”

I understand the concept of the  same source, but have no actual/technical knowledge about it. All I’m  saying is (and please don’t be offended by direct approach English is  not my native tongue) I have a small idea about these “stuff”. I’m no  techie here. But I plan to be.

So, now for the discussion I’m hoping I have:


Even  after all this long introduction, I’m still an average joe. So I just  want to understand what will the famous OpenBSD (and Linux of course)  “security” will do to me as an average user (well, maybe if I  liked/understood it, I might be not only an average user but an average  user who’s willing to be a programmer someday)

You know, I read a  lot about privacy and security and programming languages, but, I still  can’t put my finger on what is this “security” everyone is talking  about.


Let’s talk practically here (giving practical examples that I need explanation/guidance for):

For example: (and sorry if I sounded so rookie to you guys, but people like me do exist! )

What about Firefox addons:



I actually use:

Noscript  – Disconnect – Disconnect facebook – Disconnect Twitter – Disconnect  google – DoNotTrack me – Adblock Plus – HTTPS Everywhere from the  eff.org guys – and even: Google Analytics Opt-out Browser Add-on 0.9.6  (after some "average joe" persistent search on the subject!)

I read things on prism-break.org

And I read somewhere on the internet that Addons reveal your ID or something other than that...(Maybe on a TOR-related article)


So,

[CENTER]1- Are these things what we’re talking about here? Just some Pre-set safety gadgets/features in OpenBSD/Linux?


Or


2-  Is this “security” thingy related to the coding/programming programmy  stuff that pros do on the system itself? (if it is, then it will be of  course a whole different thing now)
[/CENTER]


(Again and  again, I apologize if my imagination/understanding sounds childish or trivial to you  guys. Well, I have to reasons for that: the first is that I’m doing this  on purpose, because I really want to spread the message of the freedom  of software and the tools with-which people can use to better their  lives. I’m a total believer and want to learn, even if I sounded brashly  annoying (sorry!).
I could be the missing link between the pros and the amateurs here.
I  really wanna preach on with the whole thing with the open-source  software programming and the security/privacy thing. Think of me as that  annoying/curious student who really wants to learn; So encourage me,  don’t scold me. I’m well-intentioned and I like this programming world! I  hope I can be part of it someday.
And the second reason why I sound  childish and brash, is my vocabulary of English. It’s not much. So I  tend to use simpler words.

And I ask you (please) to use simpler  language (without cultural metaphors and stuff). Not baby language but  just a simple/clear one.

I mean the best answer for me would be:

“Yes, “security” is what you said in number 2” or “Yes, It’s closer to number 1”

Peace out, people!

(note:  Please ignore the BSD bit, This post was intended to be on a BSD forum,  The registration process takes longer time than usual. But I couldn't  wait to share my thoughts! so I registered here. and I hope to find  interaction/guidance)

---

### Post by HermanAB on 2014-04-17
You can just use Ubuntu with the default settings - out of the box - then relax and enjoy your computer.

---

### Post by OrangeCrate on 2014-04-17
This should help...

**Basic Security - Ubuntu**

> The most basic set of rules

If you're a simple desktop user who only uses his computer for the most ordinary things, then this is the basic rule set:

1. immediately install security updates when you're notified;
2. do not install antivirus, as you *really* don't need it in Linux;unless you share files with Windows
3. enable the firewall (sudo ufw enable) without further tweaks;
4. stick to the official repo's as much as possible, and only deviate from them when strictly necessary and with much caution;
5. keep Java (both openJDK and Oracle Java) disabled by default in your browser, and only enable it when needed;
6. use Wine with caution;
7. and most important of all: use your common sense. The biggest security threat is generally found between keyboard and chair.

If you have higher security needs, then read on...


[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by husseinmoussa on 2014-04-17
> **OrangeCrate said:**
> This should help...

**Basic Security - Ubuntu**



[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Thanks so much for the links, I feel so dumb that I didn't search the documentation first. But to be honest, I needed to have more of a discussion that just read.

Btw, May I ask, Do you know which programming languages should I learn to become a security programmer, well at least for the time being to be able to play around with scripts on my Xubuntu?

---

### Post by Xentime on 2014-04-18
> **HermanAB said:**
> You can just use Ubuntu with the default settings - out of the box - then relax and enjoy your computer.
I'd personally be a bit weary about advising that, especially with the default firewall settings being set to ACCEPT on all chains. This is more for those who plan on using public access points though.

@OP
You seem to have basic security down already.  As mentioned before by many others, security is a process. What kind of environment is this machine going to be used in? Will you be operating behind a hardware firewall (e.g router/NAT)? Will you be using this machine in a public place (e.g. coffee shop, library, etc.)?

One quick and simple way to lock down a machine is to create a second user account that does not have access to root (e.g. "sudo" command). By default the first user you create will have access. This is very similar to Windows approach but it is much more bullet proof because it won't allow exceptions to changes as it does on Windows.

---

### Post by husseinmoussa on 2014-04-18
> **Xentime said:**
> I'd personally be a bit weary about advising that, especially with the default firewall settings being set to ACCEPT on all chains. This is more for those who plan on using public access points though.

@OP
You seem to have basic security down already.  As mentioned before by many others, security is a process. What kind of environment is this machine going to be used in? Will you be operating behind a hardware firewall (e.g router/NAT)? Will you be using this machine in a public place (e.g. coffee shop, library, etc.)?

One quick and simple way to lock down a machine is to create a second user account that does not have access to root (e.g. "sudo" command). By default the first user you create will have access. This is very similar to Windows approach but it is much more bullet proof because it won't allow exceptions to changes as it does on Windows.

Thanks so much for your reply and questions. They're really interesting. Well, I'll be using my laptop on various regular environments; Home, Library, Cafe and so on. I have the regular router for the internet connection. But I didn't know about NAT. I read about it. and I don't think we have that in our network.

I actually posted the same topic on more than one Linux/BSD related forums. I reached this conclusion that I need to do more research while experimenting, practically, the use of the OSs to develop more knowledge :)

mentioning hardware firewalls, just out of curiosity, Can one buy devices to protect his network or internet connections from attacks? I've been attacked once by this "linkbucks"; it was very silly.

Are there actual devices for more protection????? :)

---

### Post by cariboo on 2014-04-19
> **husseinmoussa said:**
> Thanks so much for your reply and questions. They're really interesting. Well, I'll be using my laptop on various regular environments; Home, Library, Cafe and so on. I have the regular router for the internet connection. But I didn't know about NAT. I read about it. and I don't think we have that in our network.


Your router does the NAT (Network Address Translation) for you, so there is nothing to worry about there.

---

### Post by husseinmoussa on 2014-04-19
> **cariboo907 said:**
> Your router does the NAT (Network Address Translation) for you, so there is nothing to worry about there.

Great. Okay :)

What about actual devices for protection, is there something like that?

---

### Post by Xentime on 2014-04-23
I'm quite ignorant when it comes to dedicated security devices but with the right network set-up, you could add an intrusion detection system. Read [http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696) for more on that. You are really are stepping out of the realm of the "average joe" if you are moving to this point because all you really need for a home set-up is a router/NAT[**[COLOR=#990303][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=77104").

From what has been said so far, I'd recommend focusing on learning iptables from the CLI (command-line interface). iptables is the firewall of choice for the many *nix distributions. It is something with a beginner skill level, with capabilities that range from simple to advanced; be it rules that drop/accept connections (simple) to conditional responses that block brute force attempts (advanced), and much more (much much more). xD

This will give you a starting point for something security related to dive into, and it is a skill that is transferable from home to work.

---

### Post by SeijiSensei on 2014-04-23
> **husseinmoussa said:**
> What about actual devices for protection, is there something like that?

For most people not running servers and not running large managed networks, a simple consumer router is sufficient.  I manage an Internet gateway for a health-care provider with over 200 employees so we have more substantial security needs.  That box runs Linux with the Squid proxy to control outbound web requests.  It also scans every inbound object for viruses and malware using SquidClamAV.  The box also operates as an email gateway running MailScanner to check each inbound message for viruses and spam.  It also examines every outbound message to ensure that people in the agency aren't sending out emails with "patient health information" which violates the US Federal Government's regulations designed to protect the privacy and security of patients' health records.  It also runs an iptables firewall and hosts a website that enables patients to make appointments online.

There are commercial boxes that provide some or even most of these services, but they are thousands of dollars more expensive than a home-grown Linux solution and usually require annual support fees.  Often those boxes are themselves running Linux and standard open-source applications like SpamAssassin with a few bells and whistles added by the manufacturers.  Also these proprietary boxes offer none of the flexibility available if you have full control over the operating system and applications running on the device.

If you want to see what commercial devices look like, one of the most well-respected manufacturers is right across the border in Israel, [Check Point Software]("http://www.checkpoint.com/").

---

### Post by bashiergui on 2014-04-26
> **SeijiSensei said:**
> For most people not running servers and not running large managed networks, a simple consumer router is sufficient. I manage an Internet gateway for a health-care provider with over 200 employees so we have more substantial security needs. That box runs Linux with the Squid proxy to control outbound web requests. It also scans every inbound object for viruses and malware using SquidClamAV. The box also operates as an email gateway running MailScanner to check each inbound message for viruses and spam. It also examines every outbound message to ensure that people in the agency aren't sending out emails with "patient health information" which violates the US Federal Government's regulations designed to protect the privacy and security of patients' health records. It also runs an iptables firewall and hosts a website that enables patients to make appointments online
You have one box that runs the proxy, mail filter, network scanner, internet-facing firewall, and it also hosts the external website. I would have tried to separate those functions onto separate machines, or at least put the website behind the firewall on a separate box. I'm curious why you chose your approach. Did you only have budget for one box?


Are you using Bro for the network scanning piece?

---

### Post by LastDino on 2014-04-26
Usually for average user Linux OS itself is quite safe from Virus, malware and back-doors, for a simple reason that it has lot of well knowledgeable eyeballs checking each and everything, plus with Linux, even an average user like me or you generally has a good sense of maintaining security. So, 99.99% of the time you probably wont need anything other than enabled firewall with default rules. 
Real trouble is given to you by installation of 3rd party stuff, Java, Browser Plug-ins, windows files/programs you handle trough wine, relative security of sites you're inclined to visit or operate and sometimes browser you use itself. Make no mistakes, this are the things which go down first or at least this are the things which compromise your security most.

As far as your question of what security means to average user? It's entirely dependent on user itself and it's something only he/she can decide upon with respect to his computerized ecosystem. Though, it should be safe to say that the cleaner you're of the things above the more secure you're on Linux.

---

### Post by SeijiSensei on 2014-04-26
> **bashiergui said:**
> You have one box that runs the proxy, mail filter, network scanner, internet-facing firewall, and it also hosts the external website. I would have tried to separate those functions onto separate machines, or at least put the website behind the firewall on a separate box. I'm curious why you chose your approach. Did you only have budget for one box?

Are you using Bro for the network scanning piece?

There's no network scanner, though it does run ntop.  It's bound to the inside-facing interface for security.  

Putting the external website behind the machine was possible, but I don't see it as much of a security risk on the box itself.  All the "patient health information" is kept on another server behind the firewall and is encrypted with AES256.  The gateway box runs a PHP application I wrote that manages patient appointments.  I've been writing PHP applications for fifteen years now, and I'm pretty cognizant of security issues with web apps.

I've tried to get the client to offload the public-facing services to a server in the cloud (I use Linode), but I never seem to get very far with that.  There's always the concern about management and cost and just general organizational inertia.  I push on this every so often, but I'm just the consultant so there's only so little I can do.

And, yes, budget was a big part of the decision here.  The alternative was something like a Barracuda, but it wouldn't have nearly the flexibility of a Linux gateway and would cost a lot more to boot.  I built this on a Dell PowerEdge R410 with dual Xeons and 8 GB of memory; the machine rarely breaks a sweat.  We actually bought two of these with the intention of having one as a "hot" spare, or simply dividing the tasks between them.  As soon as they were ordered, the second box was commandeered for use as a Windows server.  A lot of these decisions had to do with the post-recession Federal stimulus money which would pay for new hardware for medical organizations but not cover any of the costs of consulting and support.  (Read:  Funnel the monies to companies like GE and leave the health providers with the costs of actually using the hardware they bought.)

The "firewall" is just a lengthy and complex set of iptables rules.  I wrote a custom script to generate them.  MailScanner runs two copies of sendmail and uses Perl scripts to scan the messages.  We use ClamAV via the clamd daemon.  That way the antivirus task can be shared by both the mail scanner and SquidClamAV.  Probably the most CPU-intensive activity is scanning mail with Perl-based SpamAssassin which is invoked by MailScanner.

The only open ports are 25, 80, 443, and a custom port that redirects back to the Exchange server to provide Outlook Web Access. There are no services on port 80; it just redirects traffic to 443 in case people type http:// rather than https:// when trying to connect to the appointments manager.

Unix servers have traditionally run multiple daemons.  I've built machines with some or all of these services for two decades now.  Back when I started in the 1990s, the hardware itself was so expensive that deploying multiple machines was cost-prohibitive.  Even a decent desktop i386/i486 machine was $2,500.  We spent about the same amount on this R410 and got a rocket ship.

---

