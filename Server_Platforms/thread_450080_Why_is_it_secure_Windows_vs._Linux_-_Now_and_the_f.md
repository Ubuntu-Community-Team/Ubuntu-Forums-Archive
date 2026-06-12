---
title: "Why is it secure? Windows vs. Linux - Now and the future"
date: 2007-05-20
forum: Server Platforms
---

### Post by nightfire117 on 2007-05-20
Sorry, I didn't know where to post this. I was just thinking that...:

The number of Windows users greatly outnumbers those using Linux. Although we see Linux in general as being more secure, isn't Windows only more vulnerable because more hackers and malicious code writers attempt to find its flaws and penetrate those systems running Windows? If Linux ever gets to be anywhere near competition with Windows (not that I am putting Linux down, it's just that so many aren't prepared to make the switch - once the transition is flawless then we may see some pretty good competition) I'm sure that many are considering this. When there are more Linux users, there will be more viruses for Linux. They even exist for Mac OS, which is said to be so secure and stable (which, personally, using it only twice I have found not to be the case - but then again, I have only used it twice). (Actually, Mac OS's Boot Camp is pretty nice, and appealing.)

I'm no security expert or anything, this is just something I thought. I'm sure when Dell rolls out its Ubuntu PCs and notebooks some script kiddies will come out with some kind of malicious software for (Ubuntu/Linux). Just felt the need to mention this.

~Nightfire

[EDIT]: I don't even think this is the right forum.... So I wouldn't mind, and would in fact prefer, if it were moved to a more appropriate forum.

~Nightfire

---

### Post by Stephen Howard on 2007-05-20
<i>isn't Windows only more vulnerable because more hackers and malicious code writers attempt to find its flaws and penetrate those systems running Windows?</i>

That's not really true.  If you think about the number of servers out there, most will be linux or bsd.  It happened that way for a reason - unix is secure by design, while windows is only secure by ad hoc patches.

Unix variants such as linux and bsd were designed from birth with the idea that they would be used in a networked and multi-user environment - in other words, they were designed in the knowledge that strangers might have network access to other users.  Because of that, unix based systems developed with stranger-danger being the number one security threat.  Contrast that with windows.  It started life as just an overlay on top of dos, and dos was never designed for multiuser/network environments.

---

### Post by hartz on 2007-05-21
> **Stephen Howard said:**
> Unix variants such as linux and bsd were designed from birth with the idea that they would be used in a networked and multi-user environment - in other words, they were designed in the knowledge that strangers might have network access to other users.  Because of that, unix based systems developed with stranger-danger being the number one security threat.

This is not actually true.  Security was added as an afterthought, some time after the first Unix systems were designed.  Today we are still stuck with the paradigms of that ancient design.

Which goes to show just how brilliant this design was.  We're doing everything from video editing to running databases with our Unix and Unix-clone boxen.

> **Stephen Howard said:**
>  Contrast that with windows.  It started life as just an overlay on top of dos, and dos was never designed for multiuser/network environments.

Microsoft made a design decision to allow normal users to be able to control hardware, peripherals, install software, etc.  It is a usability vs security trade off decision.  It made Windows "friendly", and gained Microsoft the upper hand in the market place.  Business-wise, the correct choice.  But it left the users open to threats of data loss, compromise, and loss of service (eg DoS).  Thus it is not the Dos legacy, but rather Microsoft's design decisions which is responsible for the pop-up adverts, viruses and VB/doc script trojans.

The OP's concern that Unix/Linux is only secure because not more malware writers are focusing on it as a viable target is not entirely without merit.  This question is not by any means new, it is in fact exactly the point that Microsoft is laboring so heavily.

However here are some reasons why I think Linux/Unix is less prone to malware.
1. For a virus to infect a system, it needs to have access to system files/directories.  Under Linux, you normally run your user-software, eg IRC, Web, IM, VoIP, and P2P client programs as non-root.  The principle in Unix is that any software which is executed, inherits the permissions of the program that executes it.  Usually this is your login session which gives permission/owner to the desktop, which gives permissions/owner to applications executed form the Menu.  Should one of these programs, lets say Firefox, download and execute a piece of malware, that piece of software will only have access to parts of the system where your user have access.  Basically, damage potential is therefore normally limited to your home directory.

2. Linus would have us believe that because the source code of Linux is open, we have that many more reviewers and therefore potential to catch flaws.  This remains an unproven and often disputed theory to this day, but it is a good principle.  Note: Closed source vendors claim that because the flaws [of open-source software] are published, there is more potential for exploit.  This counter-claim has not been proven or disproven either.

3. It is easier for an administrator to see what is going on in a Linux system than in a Windows system.  Who knows what Windows installer programs are doing to your Windows system.  Who knows what programs executed by normal users on a windows system are really doing.  Are they making connections to the web, changing system files, downloading adverts to pop up, etc?  On Linux you can monitor and/or limit what is happening.  Unfortunately, we all to often just trust the programs we download and install (as root).  For this reason I prefer to stick to the officially sanctioned Ubuntu repositories because then at least a few other people have checked the programs I put onto my computer.  Looking at it the other way round - it is harder for a virus/piece of malware to hide on a Linux system than it is on a Windows system.

However, your data, accessible to your primary logon ID, eg your documents and files, are very much at risk of trojan programs and scripts in documents.

There are a few other more fuzzy things.
1. Linux users often are more diligent in checking what they download/install/run/open.
2. Virus writers don't find Linux a challenge - Once you have root, the challenge is over.

The one thing I have not really talked about is exploiting program faults, eg buffer-overflows.  On Solaris I can turn on a kernel flag which completely disabled stack execution.  This (reportedly) breaks a few badly written programs, but nothing I've ever encountered.  I seem to recall having read about something similar on Linux, but can't find it now.

Nr 3 on the list above is that Linux developers are often more mature, and follow good coding principles which blocks buffer-overflow type attacks.

Like I said, much of this is fuzzy and subjective stuff.  It is always well advised to practice safe computing - don't open un-trusted programs, don't use root except when you have to, don't leave unused ports on your computer/firewall open, don't trust anything on the internet, etc etc etc.

There was one other point I wanted to make but now I forgot what is was.

---

### Post by nightfire117 on 2007-05-22
> **hartz said:**
> This is not actually true.  Security was added as an afterthought, some time after the first Unix systems were designed.  Today we are still stuck with the paradigms of that ancient design.

Which goes to show just how brilliant this design was.  We're doing everything from video editing to running databases with our Unix and Unix-clone boxen.

Microsoft made a design decision to allow normal users to be able to control hardware, peripherals, install software, etc.  It is a usability vs security trade off decision.  It made Windows "friendly", and gained Microsoft the upper hand in the market place.  Business-wise, the correct choice.  But it left the users open to threats of data loss, compromise, and loss of service (eg DoS).  Thus it is not the Dos legacy, but rather Microsoft's design decisions which is responsible for the pop-up adverts, viruses and VB/doc script trojans.

The OP's concern that Unix/Linux is only secure because not more malware writers are focusing on it as a viable target is not entirely without merit.  This question is not by any means new, it is in fact exactly the point that Microsoft is laboring so heavily.

However here are some reasons why I think Linux/Unix is less prone to malware.
1. For a virus to infect a system, it needs to have access to system files/directories.  Under Linux, you normally run your user-software, eg IRC, Web, IM, VoIP, and P2P client programs as non-root.  The principle in Unix is that any software which is executed, inherits the permissions of the program that executes it.  Usually this is your login session which gives permission/owner to the desktop, which gives permissions/owner to applications executed form the Menu.  Should one of these programs, lets say Firefox, download and execute a piece of malware, that piece of software will only have access to parts of the system where your user have access.  Basically, damage potential is therefore normally limited to your home directory.

2. Linus would have us believe that because the source code of Linux is open, we have that many more reviewers and therefore potential to catch flaws.  This remains an unproven and often disputed theory to this day, but it is a good principle.  Note: Closed source vendors claim that because the flaws [of open-source software] are published, there is more potential for exploit.  This counter-claim has not been proven or disproven either.

3. It is easier for an administrator to see what is going on in a Linux system than in a Windows system.  Who knows what Windows installer programs are doing to your Windows system.  Who knows what programs executed by normal users on a windows system are really doing.  Are they making connections to the web, changing system files, downloading adverts to pop up, etc?  On Linux you can monitor and/or limit what is happening.  Unfortunately, we all to often just trust the programs we download and install (as root).  For this reason I prefer to stick to the officially sanctioned Ubuntu repositories because then at least a few other people have checked the programs I put onto my computer.  Looking at it the other way round - it is harder for a virus/piece of malware to hide on a Linux system than it is on a Windows system.

However, your data, accessible to your primary logon ID, eg your documents and files, are very much at risk of trojan programs and scripts in documents.

There are a few other more fuzzy things.
1. Linux users often are more diligent in checking what they download/install/run/open.
2. Virus writers don't find Linux a challenge - Once you have root, the challenge is over.

The one thing I have not really talked about is exploiting program faults, eg buffer-overflows.  On Solaris I can turn on a kernel flag which completely disabled stack execution.  This (reportedly) breaks a few badly written programs, but nothing I've ever encountered.  I seem to recall having read about something similar on Linux, but can't find it now.

Nr 3 on the list above is that Linux developers are often more mature, and follow good coding principles which blocks buffer-overflow type attacks.

Like I said, much of this is fuzzy and subjective stuff.  It is always well advised to practice safe computing - don't open un-trusted programs, don't use root except when you have to, don't leave unused ports on your computer/firewall open, don't trust anything on the internet, etc etc etc.

There was one other point I wanted to make but now I forgot what is was.

That was an excellent response, and I thank you very much for it! It clarified quite a bit for me. I'm almost sold to running Ubuntu 7.04 full time, personally. From what you said it looks to be a safer decision - that is, of course, if you don't do anything potentially harmful - *i.e.* stupid. I don't know much about the subject, but thank you for responding since you evidently do.

Oh, and yes: I haven't heard of the term "boxen" before, but it's obviously a pluralized form of "box." Looking it up in the dictionary online evidently it's used to describe Unix "boxen." Hehe, interesting.

Anyways, thank you for the response. Anyone interested in this topic is more than welcome to expand and post their ideas here as well.

~Nightfire

---

### Post by Frosty Cold Drink on 2007-05-22
I had some huge cool thing typed out, but damned if I didn't hit the wrong button. I need sleep.

To be breif.

Your average Linux user tends to be a bit more skilled and knowlegeable than your average windows user. A seasoned windows admin's machine will be just as difficult a target as a unix admin's. When people do these silly comparative studies, they tend to be skewed or deeply flawed in some ways. The realy good ones put Linux ahead, but not by the huge margin many claim.

The eairly UNIX philosophy has had a huge impact on the way things are done today. One highly specialized piece of code for one task. Everything is segmented to some degree. This is contrary to Windows, where Internet Explorer shares some code with Windows explorer, and other bits of the shell in userspace. Of course, Gnome and KDE are headed this way. I'd think they are doing a better job, but we will see how this pans out. (I'm looking at you Konqurer and KIO slaves.)

Yes, Windows is a bigger target. The "server's are the biggest target" thing doesn't really work out as well as one would think. Back in the day when everyone n the internet had crappy dial-up service, that would have been true. Now, with so many beefy machines connected to high-ish speed links, desktop farms are as good a target as a few choice servers. These days, servers tend to be targeted as a stepping stone to get desktop machines. Servers tend to be better secured and watched. Its often easier to grab and keep hold of a desktop accessing the server than the server itself. If you are malicious, you'll probably find the easiest way to done. If Linux/Windows market share was split 50/50, with similar skills throughout the respective userbases,  I'm sure Linux attacks and exploitation would rise, but for now I don't think they would be comparable to Windows' issues. This is just speculation, of course.

---

### Post by dfreer on 2007-05-22
> **hartz said:**
> This is not actually true.  Security was added as an afterthought, some time after the first Unix systems were designed.  Today we are still stuck with the paradigms of that ancient design.

Which goes to show just how brilliant this design was.  We're doing everything from video editing to running databases with our Unix and Unix-clone boxen.



Microsoft made a design decision to allow normal users to be able to control hardware, peripherals, install software, etc.  It is a usability vs security trade off decision.  It made Windows "friendly", and gained Microsoft the upper hand in the market place.  Business-wise, the correct choice.  But it left the users open to threats of data loss, compromise, and loss of service (eg DoS).  Thus it is not the Dos legacy, but rather Microsoft's design decisions which is responsible for the pop-up adverts, viruses and VB/doc script trojans.

The OP's concern that Unix/Linux is only secure because not more malware writers are focusing on it as a viable target is not entirely without merit.  This question is not by any means new, it is in fact exactly the point that Microsoft is laboring so heavily.

However here are some reasons why I think Linux/Unix is less prone to malware.
1. For a virus to infect a system, it needs to have access to system files/directories.  Under Linux, you normally run your user-software, eg IRC, Web, IM, VoIP, and P2P client programs as non-root.  The principle in Unix is that any software which is executed, inherits the permissions of the program that executes it.  Usually this is your login session which gives permission/owner to the desktop, which gives permissions/owner to applications executed form the Menu.  Should one of these programs, lets say Firefox, download and execute a piece of malware, that piece of software will only have access to parts of the system where your user have access.  Basically, damage potential is therefore normally limited to your home directory.

2. Linus would have us believe that because the source code of Linux is open, we have that many more reviewers and therefore potential to catch flaws.  This remains an unproven and often disputed theory to this day, but it is a good principle.  Note: Closed source vendors claim that because the flaws [of open-source software] are published, there is more potential for exploit.  This counter-claim has not been proven or disproven either.

3. It is easier for an administrator to see what is going on in a Linux system than in a Windows system.  Who knows what Windows installer programs are doing to your Windows system.  Who knows what programs executed by normal users on a windows system are really doing.  Are they making connections to the web, changing system files, downloading adverts to pop up, etc?  On Linux you can monitor and/or limit what is happening.  Unfortunately, we all to often just trust the programs we download and install (as root).  For this reason I prefer to stick to the officially sanctioned Ubuntu repositories because then at least a few other people have checked the programs I put onto my computer.  Looking at it the other way round - it is harder for a virus/piece of malware to hide on a Linux system than it is on a Windows system.

However, your data, accessible to your primary logon ID, eg your documents and files, are very much at risk of trojan programs and scripts in documents.

There are a few other more fuzzy things.
1. Linux users often are more diligent in checking what they download/install/run/open.
2. Virus writers don't find Linux a challenge - Once you have root, the challenge is over.

The one thing I have not really talked about is exploiting program faults, eg buffer-overflows.  On Solaris I can turn on a kernel flag which completely disabled stack execution.  This (reportedly) breaks a few badly written programs, but nothing I've ever encountered.  I seem to recall having read about something similar on Linux, but can't find it now.

Nr 3 on the list above is that Linux developers are often more mature, and follow good coding principles which blocks buffer-overflow type attacks.

Like I said, much of this is fuzzy and subjective stuff. **[B] It is always well advised to practice safe computing - don't open un-trusted programs, don't use root except when you have to, don't leave unused ports on your computer/firewall open, don't trust anything on the internet, etc etc etc.**[/B]

There was one other point I wanted to make but now I forgot what is was.

Huzzah, best post of the week!
This of course doesn't just apply to virii (damn can't remember how that is spelled and my spell-checker is failing me :( ), but worms, trojans, and of course hackers.
Overall, in windows or linux, 'don't be stupid' is the best advice I've seen.

---

### Post by hartz on 2007-05-23
> **nightfire117 said:**
> 
Oh, and yes: I haven't heard of the term "boxen" before, but it's obviously a pluralized form of "box." Looking it up in the dictionary online evidently it's used to describe Unix "boxen." Hehe, interesting.


Google is brilliant at finding definitions of words or phrases.

In the google search box, enter something like this:
define:hacker
define:LAN
define:boxen

There must be no space between define and the colon, or between the colon and the first term of the phrase.

---

### Post by eentonig on 2007-05-23
My 2cents. 

Even in the unlikely effect that user numbers between Linux and Windows would swap, linux will remain the safer option by design (but it doesn't have to be).

My reasons for thinking so.

- sudo allows regular users to be granted the required admin rights to alter whatever setting they need. But it will not allow any malware to be installed unattended. The user will always have to type his password to be enabled to do such. This makes him more aware then just clicking <ok> without reading and prevents hidden installs.
- Open-source and more importantly repositories (in case of debian based distro's at least.): Becasue (almost) all software is made available through a centrally, comunity maintained, system, you get a few extra safeguards. 1. Software is kept up to date without you having to follow up. The systems warns you system wide for updates on all installed software. 2. source-code is reviewed by independant coders and compiled to work for your distribution. There will in the future be occasions where a virus or other will slip through the mazes and make it to the repo's. But they will be rare and dealt with swiftly.


The only thread I see to linux, is the more Windows users come over just for the 'free (beer)' aspect, the more you will have people following guides to enable the root account and default to logging in as root (they were used so in Windows). Thus bypassing a lot of the systems that make linux secure. 

That's why I always will disencourage users to enable the root account.

---

### Post by tturrisi on 2007-05-23
While I use both linux and windows for specific things, and each is better at certain things, security is over-hyped for both.  On any system, a virus cannot get installed until it is executed by the user.  This includes windows web viruses via malicious web pages, e.g. the user must do something, even if that something is "open a www document".  Knowledge of how things work is of senior importance to security patches and security software.  (I've not used an av pgm on my windows boxes in 6 yrs, although I have av installed, it's never running in the bg, always do manual scans as needed)

A point not mentioned is the quantity of windows vs linux servers.  There are far more windows servers being used today than unix based servers.  This stat is oft skewed to make us think that unix has the lead because most often this stat is obtained by domain queries, and if a unix server is hosting 100 sites using virtual hosting then it "appears" that there are more unix servers being used.

Windows gets attacked more than unix because: (in no particular order)
1. it's easier
2. it's the market share leader
3. there's financial gain to be had (spyware, adware, etc)
4. there's a long standing grudge due to MS practices
5. reasons mentioned earlier in this thread

I assure you that if there was profit available in exploiting nix based desktops, then we'd see that many more exploits for the nix desktop.  But the quantity of unix desktops running today is hardly worth the effort by spyware-virus coders since www profit is monitored by quantity, not quality.

---

### Post by Frosty Cold Drink on 2007-05-23
> **eentonig said:**
> - sudo allows regular users to be granted the required admin rights to alter whatever setting they need. But it will not allow any malware to be installed unattended. The user will always have to type his password to be enabled to do such. This makes him more aware then just clicking <ok> without reading and prevents hidden installs.
Not really. This is configurable. Yes, that is the way things tend to be set up in distros by default, though.

[quote=tturrisi] On any system, a virus cannot get installed until it is executed by the user. This includes windows web viruses via malicious web pages, e.g. the user must do something, even if that something is "open a www document".[/quote]

First, we have to ignore proper definitions for a minute. Its a waste of time to try and argue the difference between various types of malicious code.

Worms often don't need user interaction to do thier thing.

---

### Post by tturrisi on 2007-05-24
> First, we have to ignore proper definitions for a minute. Its a waste of time to try and argue the difference between various types of malicious code.

Worms often don't need user interaction to do thier thing.
Agreed, and let's not get into semantics either. ( various types of malicious code)
However, a worm has to get onto a system to begin with somehow, which does require user interaction, usually by the user having installed some sort of other malicious downloader or via p2p.  Yes, there are network style works such as code red, but these are usualy filtered by the isp as they are known about and use definite ports.

---

### Post by hartz on 2007-05-24
If the software you trust behaves badly, you may not need to do anything special.  Just viewing an email message or web page could leave you exposed if you mail or web client software does not protect you.

Also you forget about exploits of vulnerabilities in running services.

Lastly, there is denial-of-service, which you can do little or nothing about.
Example:  If I get hundreds of clients trying to make connections to your computer, I could simply deny you access to your bandwidth (A flood of SYN, FIN or ACK packets for example).  If you have a listening service such as an FTP, web or ssh daemon, I could connect to it thousands of times (without even having to complete the login process) and leave the TCP connections established, thus denying you of TCP/IP ports.  Sending specially crafted (sometimes referred to as malformed) packets could cause your operating system and/or running services to fail/crash/hang/execute arbitrary code.

So "doing nothing wrong" is not a guarantee of safe computing.

---

### Post by Frosty Cold Drink on 2007-05-24
> **tturrisi said:**
> Agreed, and let's not get into semantics either. ( various types of malicious code)
However, a worm has to get onto a system to begin with somehow, which does require user interaction, usually by the user having installed some sort of other malicious downloader or via p2p.  Yes, there are network style works such as code red, but these are usualy filtered by the isp as they are known about and use definite ports.

To expound on what hartz said, consider the [Blaster worm]("http://en.wikipedia.org/wiki/Blaster_(computer_worm)"). It attacked via the RPC service and required 0 user interaction, as the RPC service on Windows is enabled by default.

---

### Post by nomb on 2007-05-24
Sorry if this was already posted.  The threads were so long I didnt read them fully... ><

From a security standpoint there is more angles that should be looked at.  For example:

If a virus was released which affected both windows and linux which would be quicker in getting a fix out?

a) microsoft with its few hundred programmers / then put it up for review/ then add it to the update list 
or
b) unix with its millions of programmers / then reviewed / then added to repos

I say b

People will argue that linux is less secure because it is open source, but also it being open source allows the full linux community to get fixes out for security flaws, usually a lot quick the m$.

just my 2 cents.

nomb

---

### Post by stanjam on 2007-05-24
I will add one other reason that Linux is inherently more secure than Windows.

Windows loads a lot of services by default.  In order to secure it you must disable many of those services, and some can not be turned off at all!

With Linux you generally have the option to load only those services that you need.  Every service you are running is a potential vulnerability.

Take GUI for instance.  In server 2003 GUI is pretty much necessary in order to set up any type of server.  In Linux this is not the case.  I can set up a web server with zero GUI interface on the machine.  This is one less major service that can be exploited.

Linux allows you to run "lean and mean."  Run only those services that are necessary for your server.

Additionally the cost savings of not having to buy product licenses allows you to invest more in security :)

---

