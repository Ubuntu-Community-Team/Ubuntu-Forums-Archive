---
title: "Getting Antivirus for Email"
date: 2007-06-08
forum: Server Platforms
---

### Post by gobbles414 on 2007-06-08
Hi all,

**I am trying to find a functioning antivirus program that will integrate with the Thunderbird email client on Feisty Fawn.** Ideally, the antivirus will have a GUI. But at this point I am willing to sacrifice such a convenience. I'm so close to going crazy with this issue that I am considering PURCHASING antivirus software for my Feisty installation. :o

As of now, I have tried: installing ClamAV via Synaptic (like a lot of people I have had problems getting Clam to recognize its definitions database), installing F-Prot via Synaptic (I follow the instructions but the installation will not complete), Avast from official website (the scanner continually reports that it cannot access files for scanning due to permission errors -- despite being run under gksudo).

**What I need is a step-by-step walkthrough on how to get an antivirus solution working, preferably using apt-get or Synaptic.** This includes any extra packages that I will need to add for email integration. *Thanks in advance!* :D

---

### Post by MJN on 2007-06-08
Whilst this doesn't answer your question (sorry) do you have particular reasons for wanting an AV client? I could understand having one on a mail server who's accessing clients may be Windows machines which require protecting but given you're using what could be considered a 'safe' client on a 'safe' platform what do you need (want) AV for? Presumably you're not in the habit of forwarding executables, for example, onto others who might not themselves have any protection in place?
 
Mathew

---

### Post by gobbles414 on 2007-06-08
Mathew et al,

I know that many Ubuntu users tend to brush aside virus concerns because Linux is inherently immune to infections. But, as you say, Windows computers are not as secure. I do a lot of emailing back and forth with clients -- most of whom are using Windows. Yes, it is the responsibility of Windows users to protect their own systems. Unfortunately for me, people often like to shift the blame for their mistakes onto others.

Let's say that a trusted colleague emails an infected how-to document to me. Maybe my source uses an unprotected Windows machine; maybe he/she is a Linux user who unknowingly sent the infected file. Anyway, I find the document to be informative and I want to forward it to all of my clients. I assume that you see my problem at this point... sending the infected file to my clients could really hurt my business. My "excuses" may find sympathy with some of the clients. Nevertheless, even one client lost to such an easily prevented chain of events is unacceptable to me.

Sorry for rambling... But you did ask after all!;)

---

### Post by MJN on 2007-06-08
It's not rambling - it explained it well!
 
I can understand your need for it now - I only asked to make sure you were firm on your requirement as many often dive straight into the solution for a problem that sometimes doesn't exist.
 
Mathew

---

### Post by gobbles414 on 2007-06-08
Mathew et al,

Thank you for your understanding. Do you have any ideas that might help me? If not a list of procedures, maybe you have found a URL in your web-travels that I have yet to visit...

---

### Post by sunstar on 2007-06-08
I heartily recommend Avast! antivirus.  There's a Home Edition for free, and a Professional Edition for business use.  It can be downloaded at [www.avast.com](www.avast.com).  It is highly rated by reviewers and automatically updates almost daily.  Registration is free (there'll be a link), with a registration key emailed to the email address you give them.  (Sometimes it takes as long as a day to get the registration key email.  That seems to happen when you request it at night or on the weekend.) After that, you just re-register every so often (maybe every six months or one year--they'll let you know.)  

I have used Avast! on all my home computers for several years, and have had no problems with it.  It's on my Windows boxes, and now on my Ubuntu.  Zero viruses (virii ? ;) ) missed, rare false positives with one friend's email.

Sunstar   (Fairly recent Ubuntu user) 

Dual-booting WinXP Professional and Ubuntu Feisty Fawn on an HP desktop with AMD 3200+ (2.2GHz) / 1 gig RAM.

---

### Post by Mr. C. on 2007-06-08
Is email your primary (or only) concern for passing/receiving malware ?

MrC

---

### Post by gobbles414 on 2007-06-08
Mr C., sunstar, et al:

Thanks for your replies. No, email is not my only reason for wanting a good antivirus. I often find myself working with removable volumes that have been and/or will be connected to Windows machines. I'd also like to be ready for the possibility of file sharing within my home network.

Regarding the free (and registered) version of Avast --> using the *gksudo avastgui* command, a manual scan of my entire hard drive in thorough mode with test archives enabled results in several scanning errors, such as "no such device" or "permission denied". Also, I have not been able to confirm email scanning between Avast and Thunderbird is taking place. If these problems can be solved, I would love to use Avast. It is the easiest to use of all the AV solutions I have tried so far.

---

### Post by Mr. C. on 2007-06-08
Ok, in that case, clamav would not be as much value, is its primary focus is as an email attachment scanner.

One of the scanners I use for my mail server is McAfee's uvscan.  it is command line, but has the same engine / malware defs as its window's counterpart.

Sorry, I don't know much about free GUI-based scanners for *nix systems.  Let us know what you decide to use.

MrC

---

### Post by gobbles414 on 2007-06-09
Mr. C.,

Do you happen to know the difference between McAfee's uvscan and McAfee's LinuxShield? I have actually not been able to locate a link for uvscan on the McAfee website -- will you please provide a link for uvscan?

---

### Post by djmaxmalta on 2007-06-09
> **gobbles414 said:**
> Mr C., sunstar, et al:

Thanks for your replies. No, email is not my only reason for wanting a good antivirus. I often find myself working with removable volumes that have been and/or will be connected to Windows machines. I'd also like to be ready for the possibility of file sharing within my home network.

Regarding the free (and registered) version of Avast --> using the *gksudo avastgui* command, a manual scan of my entire hard drive in thorough mode with test archives enabled results in several scanning errors, such as "no such device" or "permission denied". Also, I have not been able to confirm email scanning between Avast and Thunderbird is taking place. If these problems can be solved, I would love to use Avast. It is the easiest to use of all the AV solutions I have tried so far.
you guys are arguing on a anti-viruse mc affe i never new offerd a linux scanner but after a long search on google with mc affee site adviser i went to free.grisoft.com and found AVG Free anti -viruse, i use the same program on my windows dual boot and found it good

but for ntfs scaning it will say wich file it had error's reading and wich need some permisions (aka the pasword protected ones)

---

### Post by gobbles414 on 2007-06-09
djmaxmalta et al,

Do you know if AVG for Linux provides email scanning? If it does, could you provide me with step-by-step help to get it working with Thunderbird?

---

### Post by djmaxmalta on 2007-06-09
> **gobbles414 said:**
> djmaxmalta et al,

Do you know if AVG for Linux provides email scanning? If it does, could you provide me with step-by-step help to get it working with Thunderbird?
actually u just download

install...

update...

scan...

avg automaticly scans e-mails, residential shield, viruse voult and the rest of the baisics but on the gui is just the "TEST CENTER" its not the main center like its windows countepart but if u have a better one i would like to know and is there a anti-spyware thing or anti adware???

---

### Post by Mr. C. on 2007-06-09
McAfee's uvscan is a simple command line scanner; no GUI, no auto-updates.  It is geared towards server in/oubound file and email scanning.  LinuxShield is similar to Norton A/V, Kaspersky A/V, etc.  It has a GUI, auto-updates, real-time protection, etc.  This type of product is bloat-ware, and unnecessary for today's Linux desktop in general.

MrC

---

### Post by gobbles414 on 2007-06-09
djmaxmalta,

You report that, "AVG automatically scans e-mails..." That's great. But you also mention that the GUI does not allow for the management of this service. If I can confirm via the command line that my emails are being scanned, AVG may be the scanner for me. **Do you know what command I can issue in terminal to verify that AVG is scanning my Thunderbird emails**? My email provider does not allow the sending of industry standard virus test files. Otherwise, I'd just send those files to myself a few times per month as a confirmation method.

Mr. C.,

You say that, "McAfee's uvscan is a simple command line scanner..." And you add that LinuxShield is bloat-ware. I actually investigated further and discovered that LinuxShield is only sold in groups of five or more at 20 USD per license. So much for that idea! **Can you please provide a link for uvscan?** The only command line scanner from McAfee that I can find is for enterprise-level security. I'm afraid that I'm a few thousand employees -- and dollars -- short of being an enterprise. :D

---

### Post by Mr. C. on 2007-06-09
Uvscan free trial (requires registration)
[https://secure.nai.com/apps/downloads/free_evaluations/default.asp?region=us&segment=smb](https://secure.nai.com/apps/downloads/free_evaluations/default.asp?region=us&segment=smb)

Uvscan Beta 2:
[http://www.mcafee.com/us/enterprise/downloads/beta/beta_mcafee/avengine/enginemainpage.html](http://www.mcafee.com/us/enterprise/downloads/beta/beta_mcafee/avengine/enginemainpage.html)

McAfee, like many large, corporate-targetting companies make their products very difficult to purchase without a lot of hassle.  Their minimum purchase is a 10 license copy, which costs about $100 US.  I use uvscan as a backup A/V scanner, with ClamAV as the primary scanner.  I evaluated AntiVir as well to use as a second backup scanner, but found it to be even slower than uvscan.

If you feel you want a more comprehensive solution for a single-client situation, consider Kaspersky's A/V or any of the VB 100 rated A/V scanners at: [http://www.virusbtn.com](http://www.virusbtn.com) (register to read some articles, others require subscription).

MrC

---

### Post by djmaxmalta on 2007-06-10
> **Mr. C. said:**
> Uvscan free trial (requires registration)
[https://secure.nai.com/apps/downloads/free_evaluations/default.asp?region=us&segment=smb](https://secure.nai.com/apps/downloads/free_evaluations/default.asp?region=us&segment=smb)

Uvscan Beta 2:
[http://www.mcafee.com/us/enterprise/downloads/beta/beta_mcafee/avengine/enginemainpage.html](http://www.mcafee.com/us/enterprise/downloads/beta/beta_mcafee/avengine/enginemainpage.html)

McAfee, like many large, corporate-targetting companies make their products very difficult to purchase without a lot of hassle.  Their minimum purchase is a 10 license copy, which costs about $100 US.  I use uvscan as a backup A/V scanner, with ClamAV as the primary scanner.  I evaluated AntiVir as well to use as a second backup scanner, but found it to be even slower than uvscan.

If you feel you want a more comprehensive solution for a single-client situation, consider Kaspersky's A/V or any of the VB 100 rated A/V scanners at: [http://www.virusbtn.com](http://www.virusbtn.com) (register to read some articles, others require subscription).

MrC



Well avg is ont he vb 100 its ont here site too, and for the command line i doent know but when i sent an e-mail it came "scanned by avg- no viruse found - definitions base"

thats all on the windows counter part but on the linux i heard it does all just has the gui for the computer scans, on the e-mail i aint't sure as this is the free version if u want all the other crap that could come with it, like anti spam and others, u have to pay but what can i say i have it on windows and i found it good and then i found it on linux and is a bit good but the non gui thing i hate and i am a linux newbie  or rookie and most of the community tells me

and in the ubuntu repos... there is clam av, and antivir are they any good for me? u know to cover the basics and that it can detect windows viruses to? since i dual boot


--------- edit-------


and on thunder bird the avg will recgonise all ur pop 3 connections and stuff and it should do like its windows counter part that any new mail comes, a small banner comes from the low right conner saying scanning pop3 mail or imap etc...

---

### Post by MJN on 2007-06-10
I don't know about anti-virus djmaxmalta, but I think you'd be better off with a spell checker! ;) You've clearly got a lot of good stuff to share to why make it so hard to digest? I had to read it a couple of times to work out the message!

(this isn't meant to cause offence so I hope it doesn't)

Mathew

---

### Post by djmaxmalta on 2007-06-10
i understand to you  but i type fast some times and that on the quick reply the firefox spell checker and the yahoo and goole toobat ones don't really work, and is there a avast edition for linux and the Kaspersky's A/V where do i go to get it? and do you guys know of a good anti-spam? and how do i get rid of evolution i have thunderbird installed but the evo has some stuff with i like and thunderbird dosn't really work with ubuntus clock

and os there an anti-spyware or anti malware for ubuntu?

---

### Post by MJN on 2007-06-10
> **djmaxmalta said:**
> i understand to you  but i type fast some times and that on the quick reply the firefox spell checker and the yahoo and goole toobat ones don't really work, and is there a avast edition for linux and the Kaspersky's A/V where do i go to get it? and do you guys know of a good anti-spam? and how do i get rid of evolution i have thunderbird installed but the evo has some stuff with i like and thunderbird dosn't really work with ubuntus clock

and os there an anti-spyware or anti malware for ubuntu?

Tell me you're winding me up! :eek:

---

### Post by djmaxmalta on 2007-06-10
> **MJN said:**
> Tell me you're winding me up! :eek:

er...... nope, sorry man i am Maltese and English but lately i have been talking in Arabic and on the reply to thread section the spell checker works, its that when i am in some type of hurry i spill the beans in my work lol

---

### Post by gobbles414 on 2007-06-10
Hi everybody,

Allow me to thank you all once again for your help!

Anyway, some of you mention that you have been able to successfully install ClamAV on Ubuntu. Since it is supported by Ubuntu, **ClamAV is my first choice for an antivirus.** If there are no objections, I would like to focus on getting ClamAV working on my system. Since ClamAV has never installed successfully for me, **I will need a step-by-step guide.** That is, what packages do I need to install, in what order should I install them, etc. Remember, my focus at this point is to get **antivirus integration with the Thunderbird email program.**

Let's forget about AVG and McAfee for the moment because:

According to the article at [http://www.pcw.co.uk/personal-computer-world/software/2151042/avg-free-linux](http://www.pcw.co.uk/personal-computer-world/software/2151042/avg-free-linux) "...unlike AVG, ClamAV also scans emails. A fix can be found here, but this is a workaround." So apparently, the free version of AVG for Linux does not scan emails -- at least in an officially supported manner. I am not clear about what McAfee's definition of trial software is. Will I get the full functionality of the command line scanner, is it crippled in some way, will it only work for a limited time without a paid registration?

---

### Post by Mr. C. on 2007-06-10
Let's clear up a possible misconception or terminology issue.  "Scans mails" has two flavors: 

1) automatically scanning email via inbound download via POP as done by mail clients (MUA) such as Evolution, and outbound via SMTP.  This method acts as a proxy service, getting inbetween the MUA and the service.  The client is configured to send/recieve email to/from the virus scanner essentially.

2) scan in/outbound email at the email server level.  This requires that you run your own mail server.

ClamAV is designed for (2), not for (1).  Nor is ClamAV designed to be a comprehensive virus scanner for general real-time file access; it has far few signatures and abilities than more comprehensive Windows A/V scanners, simply because it is designed to protect from emailed malware.

I can help you setup ClamAV; let's first make sure the distinction above is understood.

MrC

---

### Post by gobbles414 on 2007-06-10
> **Mr. C. said:**
> Let's clear up a possible misconception or terminology issue.  "Scans mails" has two flavors: 

1) automatically scanning email via inbound download via POP as done by mail clients (MUA) such as Evolution, and outbound via SMTP.  This method acts as a proxy service, getting inbetween the MUA and the service.  The client is configured to send/recieve email to/from the virus scanner essentially.

2) scan in/outbound email at the email server level.  This requires that you run your own mail server.

ClamAV is designed for (2), not for (1).  Nor is ClamAV designed to be a comprehensive virus scanner for general real-time file access; it has far few signatures and abilities than more comprehensive Windows A/V scanners, simply because it is designed to protect from emailed malware.

I can help you setup ClamAV; let's first make sure the distinction above is understood.

MrC

You see... That is the magic of these forums. It is almost always possible to learn something new and interesting. **I am indeed interested in POP/SMTP scanning, option #1**. While it is possible that I might need additional antivirus functionality in the future, all I am interested in at the moment is an antivirus that can scan my hard drive and protect my POP/SMTP email account in Thunderbird. **Everyone, please use the following checklist and, reading from top to bottom, stop at the first option that you are sure will work in Feisty Fawn. Then provide step-by-step directions for installing that option. In order of my preference:**

(A) permanently free antivirus from Ubuntu repositories (add/remove, apt-get, or Synaptic)
(B) permanently free antivirus from the web in a Ubuntu-comapatable installer package
(C) commercial antivirus from Ubuntu repositories (add/remove, apt-get, or Synaptic)
(D) commercial antivirus that can be installed from a package and has a GUI
(E) commercial antivirus that can be installed from a package but does not have a GUI.
(F) permanently free antivirus from the web that requires a MAKE from the command line to install
(G) commercial antivirus that requires a MAKE from the command line to install
(H) any other options that have slipped my mind...

---

### Post by Mr. C. on 2007-06-10
I think part of the problem in providing assistance has been with your concept that there is a single classification of antivirus software.  There are many forms A/V software may take, and which form depends upon needs.  There is A/V for web servers, mail servers, gateway or perimeter protection, desktop protection, real-time scanning, and then each of those may have variants as well.  And do you require disinfection, or just detection?

It sounds like you want a free package that is the equivalent of Norton Antivirus, which is a desktop product that does real-time scanning, pop/smtp mail scanning and auto-updates.

There is a GUIish interface for ClamAV:
[http://www.linuxquestions.org/linux/answers/Security/Antivirus_Desktop_protection_for_Linux](http://www.linuxquestions.org/linux/answers/Security/Antivirus_Desktop_protection_for_Linux)

but it does not provide real-time, always on, system-wide scanning.  Such protection requires additional kernel modules to intercept various system calls such as open/read/write/creat.  It also requires running the A/V product as a server, so that it can create the network proxy that intercepts POP/SMTP network connections.  It would be useful to take yourself out of the "Windows" desktop PC mindset, where constant, real-time scanning of every file access, or even nightly scans of the entire system is unnecessary and essentially useless.

Your goal should be : allow me to scan any new file received from an untrusted source.

Two other free products are: AVG and Avira.

MrC

---

### Post by gobbles414 on 2007-06-10
> **Mr. C. said:**
> It sounds like you want a free package that is the equivalent of Norton Antivirus, which is a desktop product that does real-time scanning, pop/smtp mail scanning and auto-updates... It would be useful to take yourself out of the "Windows" desktop PC mindset, where constant, real-time scanning of every file access, or even nightly scans of the entire system is unnecessary and essentially useless.

I may have allowed this issue to get confusing early on. :( That's totally my fault! ;) Let me try to fix that now. **Think of me as a typical home computer user.**

*I have one computer with Feisty Fawn on it.
*I have one Gmail email account for my personal/business use.
*I use Thunderbird to send/receive the emails for that one Gmail account via POP/SMTP.
*I need an antivirus program that can interface with the Thunderbird installation described above.
*POP intigration with Thunderbird is required since viruses can be inbedded within the bodies of emails
*SMTP intigration is prefered but optional since I can scan any of my files manually before attaching them to an email.  
*I also need my antivirus to be able to manually scan selected directories and drives for viruses (main hard drive, USB flash drive, CD-ROMs, etc.)
*I prefer to update my AV definitions manually.
*GUI is preferable, but not required
*Free is preferable, but not required
*Easy installation is preferable, but not required

---

### Post by Mr. C. on 2007-06-10
I got that; I think we're on the same page.

Other than what has been suggested, I have no other alternatives to suggest.

Sorry,
MrC

---

### Post by gobbles414 on 2007-06-10
> **Mr. C. said:**
> I got that; I think we're on the same page.

Other than what has been suggested, I have no other alternatives to suggest.

Sorry,
MrC

Okay, I'm going to make a list of what I've learned so far from this thread. Please correct any mistakes you find and I will edit this post accordingly. This is both for my future reference as well as for others who may be in the same situation that I am:

* ClamAV is not for POP/SMTP scanning.
* The free home version of Avast for Linux does not support POP/SMTP scanning (no mention of it on product page)
* McAfee's uvscan is the same as McAfee VirusScan Command Line Scanner for Linux. It is available as a trial download. The meaning of trial is unclear.
* McAfee's LinuxShield requires a minimum of 5 licenses @ 20 USD per license.
* Kaspersky A/V does not appear to be a solution for desktop users wanting to scan POP/SMTP.
* The free version of Avira does not support POP scanning, but the paid version does. SMTP protection is unclear.
* The free AVG for Linux does not support POP/SMTP scanning.
* F-Prot's home scanner for Linux does not support POP/SMTP scanning.

***Panda's commercial Linux scanner, Panda DesktopSecure for Linux, appears to support POP/SMTP scanning. Panda's free scanner for Linux does not support this.**

---

### Post by PizzaHog on 2007-06-10
New chum to Ubuntu here, so take this FWIW:  From my attempts to install the AVG server versions, it seems that it needs the DAZUKO kernel installed, which means that the Ubuntu kernel needs to be re-compiled.

I'm too new for that, so the next attempt will be the desktop version...*sniff*

PH

---

### Post by gobbles414 on 2007-06-10
> **PizzaHog said:**
> New chum to Ubuntu here, so take this FWIW:  From my attempts to install the AVG server versions, it seems that it needs the DAZUKO kernel installed, which means that the Ubuntu kernel needs to be re-compiled.

I'm too new for that, so the next attempt will be the desktop version...*sniff*

PH

PizzaHog,

It's good to know that I'm not the only person who is afraid to recompile a Linux kernel! :D Anyway, thanks for replying to this thread. Why is it this difficult to find a good antivirus solution for Linux? :roll: Despite some of the accusations that have been made against it in the past, I'm thinking of giving Panda a try (see [http://en.wikipedia.org/wiki/Panda_Software](http://en.wikipedia.org/wiki/Panda_Software))

---

### Post by Mr. C. on 2007-06-10
It is difficult to find what you are looking for because a) it is overkill and unnecessary, b) has a very small market, and c) open source folks may not provide a market (eg. they want free), and d) there is no standard Linux kernel (many flavors, distros, variations, compile-time options).

You have the power to create your own antivirus / antispam email server at your fingertips.  This will give you complete control over content scanning.  You can use ClamAV to do your occasional file or directory scans, either command line or with the GUI I mentioned previously.

MrC

---

### Post by gobbles414 on 2007-06-11
> **Mr. C. said:**
> It is difficult to find what you are looking for because a) it is overkill and unnecessary, b) has a very small market, and c) open source folks may not provide a market (eg. they want free), and d) there is no standard Linux kernel (many flavors, distros, variations, compile-time options).

You have the power to create your own antivirus / antispam email server at your fingertips.  This will give you complete control over content scanning.  You can use ClamAV to do your occasional file or directory scans, either command line or with the GUI I mentioned previously.

MrC

Mr. C.,

Again, thank you for your help. But it seems like you and I have major philosophical difference of opinion. Covering each of your comments in turn:

(A) I'm not asking for always-on hard drive scan, nor automatic updates. All I want is the ability to manually scan my hard drive once or twice per month, and automatically queued POP/SMTP email protection for Thunderbird (a major open source email client with an antivirus tab in its preferences for goodness sakes). Having a good antivirus is critical for me because it protects my friends and business contacts who are using Windows. In other words, not overkill...

(B) Agreed, it is a very small market. But it would be interesting to learn just how many Windows viruses have been unintentionally propagated by Linux users. Don't assume that something is unimportant just because of its small size.

(C) I totally respect the right of programmers to ask payment for their software. They do things that I cannot even dream of accomplishing. However, for home users, the ideas of free and open source are somewhat interchangeable. That's why I have written in this thread that I am willing to pay for an antivirus if a free version fails to meet my needs.

(D) My skills are not high enough to agree/refute what you are saying here.

(*) You say that I, "have the power to create [my] own antivirus / antispam email server..." The tools may be there in Linux. But the knowledge is not there in my brain. Not everyone who uses Linux is a computer programming genius. Some of us have to muddle our way through installs, oftentimes having to reformat several times before getting the system running correctly. That's why I use Ubuntu instead of Red Hat, SuSe, Mandrake, or Freespire (tried all of these at multiple versions). Ubuntu does the best job of using standard Linux commands in the terminal, and of documenting each step for the user in community docs.

---

### Post by gobbles414 on 2007-06-11
Hi anyone,

I know that Mr. C. has already stated that ClamAV does not scan POP/SMTP emails. But can somebody take a look at the following URL, and explain to me why it won't work for that purpose? Pay close attention to the explanation of the clamav-daemon package. Thanks as always:

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by vitalstatistix on 2007-06-11
I have a feeling that installing the AVG free AV on Ubuntu may help, as it most likely has pop3/smtp scanning enabled by default. Anyway if you use Gmail, its unlikely you will ever send/receive a virus due to Google's strong scanning which disallows even ordinary executables.

---

### Post by gobbles414 on 2007-06-11
> **vitalstatistix said:**
> I have a feeling that installing the AVG free AV on Ubuntu may help, as it most likely has pop3/smtp scanning enabled by default. Anyway if you use Gmail, its unlikely you will ever send/receive a virus due to Google's strong scanning which disallows even ordinary executables.

vitalstatistix,

Thanks for posting to this thread. Regarding AVG, my research shows that the home Linux version does not support POP/SMTP email scanning. You make a good point about Gmail's reputation for excellent antivirus protection. I just enjoy the reassurance and hard drive scanning abilities that come from having a local antivirus installation. No antivirus is perfect 100% of the time; and that includes Gmail's.

I'd love to read any other ideas you may have.

---

### Post by Mr. C. on 2007-06-11
> **gobbles414 said:**
> Hi anyone,

I know that Mr. C. has already stated that ClamAV does not scan POP/SMTP emails. But can somebody take a look at the following URL, and explain to me why it won't work for that purpose? Pay close attention to the explanation of the clamav-daemon package. Thanks as always:

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

ClamAV in daemon mode is designed to avoid the repeated startup time associated with the command line clamscan.  Instead, the program is daemonized, and *sits idle* waiting to be called upon by, for example, a **mail server**'s content filter (via amavisd-new, or other).  It does not act as a POP or SMTP proxy, intercepting MUA calls to download/send email.

The damonized version of ClamAV is used via the **clamdscan **command line utility.  Standalone, **clamscan **is used.

MrC

---

### Post by Mr. C. on 2007-06-11
> **gobbles414 said:**
> Again, thank you for your help. But it seems like you and I have major philosophical difference of opinion. Covering each of your comments in turn:



No difference in opinion as much as different goals in our responses.  You asked *why* it was hard to find; my responses were targeted at the *why* question.  I gave the rationale as to why such a product doesn't exist or is limited in meeting your goals.

---

### Post by gobbles414 on 2007-06-14
Hi all,

I've decided to try AVG Anti-Virus Professional Edition for Linux/FreeBSD. The product page is at ([http://www3.grisoft.com/doc/2216/us/crp/2](http://www3.grisoft.com/doc/2216/us/crp/2)). I have downloaded the program and will report back to this thread once I've had a chance to test it.

---

### Post by gobbles414 on 2007-07-26
Hi once again,

I know that it has been a long time since anyone has posted on this thread. But, I am keeping my promise to report back on AVG Anti-Virus Professional Edition. First, allow me to compliment the company responsible for AVG for its free tech support of the trial version of its software. That is above what I would have expected -- even for Windows-based software. Unfortunately, **this software will not work for me** due to the following:

*Despite help provide by AVG support, I was never actually able to complete a scan of (/). Indeed, it would stop scanning after less than 200 files.

*POP/SMTP scanning would have required the use of the Dazuko kernel module. I'm still learning Linux, and I'm not quite ready to mess with the kernel at this time.

I have started a new thread with a smaller "wish list" of features. Please look at ([http://ubuntuforums.org/showthread.php?p=3083008](http://ubuntuforums.org/showthread.php?p=3083008)).

---

### Post by reckless2k2 on 2007-09-04
day and late and dollar short on my solution as i just stumbled on this thread looking to implement something myself. i basically used this combo to get something running:

thunderbird + clamav + klamav + dazuko

the dazuko module load was the problematic area. Just follow this thread through and it worked fine. No need to compile source or anything because it's already there:

[http://ubuntuforums.org/showthread.php?t=78794&page=2&highlight=dazuko](http://ubuntuforums.org/showthread.php?t=78794&page=2&highlight=dazuko)

then in klamav just turn on autoscan and point it to .mozilla-thunderbird down to the "mail" that you want it to scan. it seems to be working fine for me.

---

### Post by gobbles414 on 2007-09-18
reckless2k2,

Thanks for your post. For several weeks now, I've been scanning my Evolution emails manually with Avast. I am starting to enjoy using Evolution and Avast is better at cleaning infected files than AVG. I was never able to get Clam working on my system -- kept losing the virus definitions. I'm satisfied with my current solution.

---

