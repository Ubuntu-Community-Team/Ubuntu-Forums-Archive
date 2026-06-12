---
title: "Debate on Linux vs Windows, help needed..."
date: 2007-05-05
forum: The Cafe
---

### Post by M$LOL on 2007-05-05
I'm having a debate on Linux vs Windows, and I need some rock-solid evidence to show that it's more secure. I know a reasonable amount about it, but I need something to show that Linux is way better security-wise, other than more people using Windows.

Thanks.

---

### Post by Mazza558 on 2007-05-05
Sudo?

---

### Post by M$LOL on 2007-05-05
Yeah, I was actually thinking of that, but how do I say that in such a way that shows it as a strength for Linux and a weakness for Windows?

---

### Post by meng on 2007-05-05
[http://www.theregister.co.uk/security/security_report_windows_vs_linux/](http://www.theregister.co.uk/security/security_report_windows_vs_linux/)

---

### Post by mech7 on 2007-05-05
> **Mazza558 said:**
> Sudo?

Isn't that the exact same thing as UAC in windows :confused:

---

### Post by unnes on 2007-05-05
FWIW, Vista's security (in the form of UAC) is vastly improved over XP. Unlike previous incarnations of Windows, you don't run everything as administrator by default (and consequently expose yourself to mal/spyware and accidental deletion/changing of system files), even if UAC prompts are annoying out-of-the-box (they can be fine-tuned to your specs -- for example I only get a UAC prompt if I want to change something in my Windows or Program Files directories).

I'm not saying Windows is necessarily more secure than Ubuntu, but if you're going to use that as a debate point, it's wise to know the other side of things.

---

### Post by ali4949 on 2007-05-05
Speaking of sudo check this out....
[http://www.linuxtoday.com/infrastructure/2007050402126OPLL](http://www.linuxtoday.com/infrastructure/2007050402126OPLL)

This just goes to show things MS have borrowed from unix/linux. Your biggest argument that will work in your favor as far as security goes Explorer is part of the OS. This allows zones to be able to have access to other parts of the file system. When i say  Explorer I dont mean Internet Explorer alone, the file browser is also Explorer and no matter how many times MS re -writes this application as long as its part of the OS it will always be security feature. Forget about Open source vs closed source for a minute and argue this point. The OS should be responsible for only managing resources and processes on a system. When you start to integrate applications into the OS, it starts to open security holes. 

WIndows was designed to be single user OS with no outside world connection. Well the internet changed that. The very reason why Unix was built was to work in a network environment. The Internet just brought the idea full circle. Now companies like google are working on providing applications over the net, thats the same idea as  thin client systems from a long long time ago. We started with distributed computing, went to individual desktops and are now going back to distributed computing.

---

### Post by thedaemon on 2007-05-05
More viruses are written for microsoft windows than linux. That's all that needs to be said.

---

### Post by mech7 on 2007-05-05
> **ali4949 said:**
> 
This just goes to show things MS have borrowed from unix/linux. Your biggest argument that will work in your favor as far as security goes Explorer is part of the OS. This allows zones to be able to have access to other parts of the file system. When i say  Explorer I dont mean Internet Explorer alone, the file browser is also Explorer and no matter how many times MS re -writes this application as long as its part of the OS it will always be security feature. Forget about Open source vs closed source for a minute and argue this point. The OS should be responsible for only managing resources and processes on a system. When you start to integrate applications into the OS, it starts to open security holes. 

Wrong the browser now runs in sandbox

---

### Post by Sef on 2007-05-05
> Wrong the browser now runs in sandbox

That is true only if the UAC is turned on.

---

### Post by mech7 on 2007-05-05
> **Sef said:**
> That is true only if the UAC is turned on.

Same counts for linux when user logs in as root.. that kind of arguing does not get you anywhere ;) Although if you ask me Sudo / UAC does improve security by much most users will enter their password everywhere does not matter what asks for it especially when they need to do it 10 times a day, or they will turn it off if they can find it :)

---

### Post by %hMa@?b&lt;C on 2007-05-05
almost no linux users log in as root.  almost every windows user logs in as root.

---

### Post by pingvin on 2007-05-05
Perhaps turn the argument to a more hardware-based point - have you ever watched how hard your DVD drive works in Windows trying to play a disc, then played that same disc in Ubuntu? I lost a hard disk to FAT32 recently - I just can't afford to run Windows any more.
Mike

---

### Post by lancest on 2007-05-05
Open source servers (Linux,BSD) dominate the internet. Why is Microsoft's IIE server record so poor? Bad security model, poor OS design. [SIZE="5"]Has nothing to do with the number of viruses written.[/SIZE] Linux is modular (safe) and was designed for  secure networking from the get go.

---

### Post by dbbolton on 2007-05-05
> **M$LOL said:**
> I'm having a debate on Linux vs Windows, and I need some rock-solid evidence to show that it's more secure. I know a reasonable amount about it, but I need something to show that Linux is way better security-wise, other than more people using Windows.

Thanks.
you have to keep in mind that debates are pointless, especially when the person on the other side is too obstinate, ignorant, or indolent to listen to another person's perspective.

just look at the number of unresolved debates on abortion, religion, etc.

---

### Post by macogw on 2007-05-05
> **ali4949 said:**
> Speaking of sudo check this out....
[http://www.linuxtoday.com/infrastructure/2007050402126OPLL](http://www.linuxtoday.com/infrastructure/2007050402126OPLL)

This just goes to show things MS have borrowed from unix/linux. Your biggest argument that will work in your favor as far as security goes Explorer is part of the OS. This allows zones to be able to have access to other parts of the file system. When i say  Explorer I dont mean Internet Explorer alone, the file browser is also Explorer and no matter how many times MS re -writes this application as long as its part of the OS it will always be security feature. Forget about Open source vs closed source for a minute and argue this point. The OS should be responsible for only managing resources and processes on a system. When you start to integrate applications into the OS, it starts to open security holes. 

WIndows was designed to be single user OS with no outside world connection. Well the internet changed that. The very reason why Unix was built was to work in a network environment. The Internet just brought the idea full circle. Now companies like google are working on providing applications over the net, thats the same idea as  thin client systems from a long long time ago. We started with distributed computing, went to individual desktops and are now going back to distributed computing.
That would be a link to my blog.

---

### Post by mech7 on 2007-05-06
> **pingvin said:**
> Perhaps turn the argument to a more hardware-based point - have you ever watched how hard your DVD drive works in Windows trying to play a disc, then played that same disc in Ubuntu? I lost a hard disk to FAT32 recently - I just can't afford to run Windows any more.
Mike

Nobody uses FAT32 anymore, atleast nobody with a recent version of windows ;)

---

### Post by phenest on 2007-05-06
> **pingvin said:**
> I lost a hard disk to FAT32 recently - I just can't afford to run Windows any more.
Mike

FAT32 is very good at fragmenting files and placing them in no particular order on the disc. This means the drive has to do more work to retrieve the pieces, which results in earlier failure than it needs to be. NTFS is more intelligent.

I think the main difference in security between Linux and Windows is, simply Windows users don't use it. They login as administrators without using a password, and what's more shocking is this is how the Windows installer sets up your computer by default. UAC in Vista can be switched off. And asking "how to switch UAC off?" was one of the first questions Vista users were asking because they didn't like the idea. It is possible to login as permanent root in Linux, which I have read posts here asking how to do it, which I think shows that security is not necessarily a Linux selling point.

I think the best difference between Linux (Ubuntu in this case) and Windows is the EULA. I can install Ubuntu on as many computers as I want, and even give a copy to my friends and family. Try doing that with XP or Vista. I have installed my OEM copy of XP Home that came with my Dell Dimension as a virtual guest OS (VirtualBox) and it wants me to activate it. M$ like to treat you like a criminal. Also, it is rumored that Vista will soon be 'calling home' once a month just to check you haven't installed it on a 2nd machine. Now this is where Linux shows it strength. FREEDOM!

---

### Post by mech7 on 2007-05-06
> **phenest said:**
> 
I think the best difference between Linux (Ubuntu in this case) and Windows is the EULA. I can install Ubuntu on as many computers as I want, and even give a copy to my friends and family. Try doing that with XP or Vista. I have installed my OEM copy of XP Home that came with my Dell Dimension as a virtual guest OS (VirtualBox) and it wants me to activate it. M$ like to treat you like a criminal. Also, it is rumored that Vista will soon be 'calling home' once a month just to check you haven't installed it on a 2nd machine. Now this is where Linux shows it strength. FREEDOM!

Yeah i think you are right though most users will not really care about this too much i think though, they will just use what is installed for them. Most of them don't even know how to install a OS. So let alone install one on a different computer they rather go out and buy one with something installed allready.

---

### Post by rai4shu2 on 2007-05-06
Sometimes a picture can say more than a thousand words:

[http://www.google.com/trends?q=linux+security%2C+windows+security](http://www.google.com/trends?q=linux+security%2C+windows+security)

---

### Post by BuffaloX on 2007-05-06
I was thinking this...

Windows Vista security is based on user acceptance of actions.
AFAIK it's just a matter of "accept" or "deny"
If malware gets into your system, it could easily be made to accept all security popups in Windows Vista, and Vista would be totally open for further attacks.
This is not possible in Linux, because a password is needed, to grant root access.

I haven't tried Vista, but from what I read, this is how I understand it to work.

---

### Post by jiminycricket on 2007-05-06
Talk about Linux + Apache high marketshare in the server market (high risk target) which has fewer critical bugs than Windows? [http://www.redhatmagazine.com/2007/04/18/risk-report-two-years-of-red-hat-enterprise-linux-4/](http://www.redhatmagazine.com/2007/04/18/risk-report-two-years-of-red-hat-enterprise-linux-4/)
> 
by Mark Cox

Red Hat® Enterprise Linux® 4 was released on February 15th, 2005. This report takes a look at the state of security for the first two years from release. We look at key metrics, specific vulnerabilities, and the most common ways users were affected by security issues. We will show some best practices that could have been used to minimise the impact of the issues, and also take a look at how the included security innovations helped.
...
A default installation of Enterprise Linux 4 AS was vulnerable to only 3 critical security issues in the whole two years

Distributions use trusted signed repositories so spyware and viruses can't be installed.  Shared libraries, so all applications are updated automatically rather than separately.  See the WMF problems with Office and Windows using separate libraries.

---

### Post by mech7 on 2007-05-06
> **jiminycricket said:**
> Talk about Linux + Apache high marketshare in the server market (high risk target) which has fewer critical bugs than Windows? [http://www.redhatmagazine.com/2007/04/18/risk-report-two-years-of-red-hat-enterprise-linux-4/](http://www.redhatmagazine.com/2007/04/18/risk-report-two-years-of-red-hat-enterprise-linux-4/)


Distributions use trusted signed repositories so spyware and viruses can't be installed.  Shared libraries, so all applications are updated automatically rather than separately.  See the WMF problems with Office and Windows using separate libraries.

Your quote is from a research done in 2005.. not too mention from a source called red hat magazine ;) Not really independent i would say.

---

### Post by jiminycricket on 2007-05-06
> **mech7 said:**
> Your quote is from a research done in 2005.. not too mention from a source called red hat magazine ;) Not really independent i would say.

RHEL 4 was *released* in 2005, but this report is from February 2007. It is still supported.  Red Hat supports their enterprise releases for quite a few years.

> All the data used to generate this report applies to Red Hat Enterprise Linux 4 AS from release day, February 15, 2005 **through February 14, 2007** unless otherwise stated.

As for independance, well take it or leave it, but all the information about security vulnerabilities is publically available on security websites.  RHEL 4+ also uses SELinux for system-wide MAC which is much better than just a browser sandbox for Internet Explorer.  There's a ton of other comparisons here which sometimes go both ways: [http://www.osnews.com/topic.php?icon=33](http://www.osnews.com/topic.php?icon=33)

---

### Post by phenest on 2007-05-07
I don't think you can really compare Linux to Windows, because, as everyone keeps saying, Linux is not Windows.The debates are mostly pointless if your trying to convince someone to use Linux. Here is one reason to continue using Windows:

Support -

If I go to a computer store to buy a pc, it will be running Windows. If something goes wrong, I can call the shop where I bought it, the OEM manufacturer, MS, a pc technician in the Yellow Pages, and so on. But none of those places are going to help me if I'm running Linux. Why? Because they know nothing about Linux (or Linux isn't popular enough for them to bother). This means, unless I have a friend or family member who knows about Linux, I'm on my own.

Another reason is -

It's something people WANT to try. You can't talk them into it, unless they have already been thinking about it. They won't try Linux if they don't NEED to. If Windows does everything they want, then why change.

It's not about Linux being free, or being more secure, or more efficient, or more useful.

I tried Linux, for many reasons: it isn't MS, it's free, it doesn't have a restrictive EULA, and because I was curious. And I was pleasantly surprised, too. I have no-one to call on to help me with Linux. I've had to learn myself. But then I've been playing with computers for over 25 years, have a determined nature, and an understanding mind. Not that should be the criteria for a Linux user, but it helps.

Until something drastic happens to MS (bankruptcy, or general dropping of OS software development) that affects users to the point where there is no more support for Windows, or OEM manufacturers start installing Linux as an alternative OS (well done Dell), then Windows users will keep using Windows.

Linux IS popular, but we are thin on the ground.

---

### Post by Sweet Spot on 2007-05-07
> 
If I go to a computer store to buy a pc, it will be running Windows. If something goes wrong, I can call the shop where I bought it, the OEM manufacturer, MS, a pc technician in the Yellow Pages, and so on. But none of those places are going to help me if I'm running Linux. Why? Because they know nothing about Linux (or Linux isn't popular enough for them to bother). This means, unless I have a friend or family member who knows about Linux, I'm on my own.

Kind of a moot point there though, wouldn't you say ?  (This isn't an argument, just anobservation) Chances are that if someone chose to install *insert distro of choice here*, and was successful at doing so, it's also more than likely that they've done enough reading or research to know how to either fix it themselves, or they'd know that they could easily get help (take this community as an example) from that distribution's technical/help forum. 

And usually with Linux, problems from distro to distro are documented a hell of a lot better and are more organized than with Windows stuff, not to mention are mostly centralized and more often than not, have very precise solutions lain out for any level of user. 

Just sayin' is all. :)

---

### Post by KIAaze on 2007-05-07
> **M$LOL said:**
> I'm having a debate on Linux vs Windows, and I need some rock-solid evidence to show that it's more secure. I know a reasonable amount about it, but I need something to show that Linux is way better security-wise, other than more people using Windows.

Thanks.

Here's a little joke that explains it all:

> ***_Why Linux Viruses are fairly uncommon_***

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

[http://www.gnu.org/fun/jokes/evilmalware.html]("http://www.gnu.org/fun/jokes/evilmalware.html")

---

### Post by Nikron on 2007-05-07
<snip>
**Sadly, in Ubuntu many of these steps are already done for you**

Before attempting to compile this virus make sure you have the correct
version of glibc installed, and that your firewall rules are set to `allow
everything'.**glibc is usually installed, and iptables does have allow all outgoing**

steps 1 - 6 done with an easy one click .deb package

7. You may now configure your preferred malware behaviour in
/etc/evilmalware.conf .

SEE ALSO
evilmalware(1), evilmalware.conf(5), please_delete_all_my_files(1)

---

### Post by Wiebelhaus on 2007-05-07
Correct me if I'm wrong but I was under the impression that the main security difference is that the core OS components & registry are segregated from the user unlike windows , so in essence only the root or "as root" can make changes which automatically deters any type of malware from
infecting,writing to or damaging the OS unless explicitly allowed to do so?

---

### Post by KIAaze on 2007-05-08
Yes, but the problem is that sudo gives all root permissions as fas I know.
Basically "sudo" is the equivalent of "su", the only difference being that instead of doing something explicitely as root, you do it as a user with root permissions.

The difference compared to windows is that you have to enter a password, meaning that only the "real user" can do things as root.
In windows, you just click "allow" or "ok". So any person having access to your normal account can do whatever he wants.

The weak point is always the user.
If a system is correctly set up, the root password or sudo password should never be required.

I have never tried editing the sudoers file, but I think it's a good thing to do.

Nikron is right. Ubuntu is still vulnerable...

---

### Post by saulgoode on 2007-05-08
> **KIAaze said:**
> Yes, but the problem is that sudo gives all root permissions as fas I know.
 <snip>

It was my understanding that Ubuntu only provides 'sudoers' authorization to the *first* account created during installation (any accounts created subsequently would have to explicitly be granted that authority). Most Linux distributions do not provide any accounts with 'sudoers' authority (since they implement 'root').

---

### Post by jiminycricket on 2007-05-08
You can revoke sudo access by removing a user from the wheel group

Anyways biggest security is trusted, signed repositories for all software IMO, no need for random downloading.  Microsoft can't do that for technical and legal reasons.

Ubuntu also ships with all ports closed by default.

---

### Post by rai4shu2 on 2007-05-08
The main thing Windows runs into is its dependency on pirated marketshare. They can't really punish users for pirating their products, but they can't afford to be seen tolerating it. They have been forced into a situation where they cannot place implicit trust in the end user, and those mechanisms create their must significant security threats.

---

### Post by KIAaze on 2007-05-08
> **saulgoode said:**
> It was my understanding that Ubuntu only provides 'sudoers' authorization to the *first* account created during installation (any accounts created subsequently would have to explicitly be granted that authority). Most Linux distributions do not provide any accounts with 'sudoers' authority (since they implement 'root').

Yes, but how many users create an extra account to use everyday?
Most people do it just like in windows: use the default account.

---

### Post by ky4623 on 2007-05-08
going from windows to linux is a lot like having brain surgery. it take a long while to get uses to, but if you are willing to learn then i say go a head. it took me 3 years, a semester of unix in college, and that crappy vista to finally make me want to use linux. if you are not willing to learn, then security is useless if you don't know how to use it. on another note, vista looks like it has a lot good security policies, but it is not for pirates, lolz.

---

### Post by saulgoode on 2007-05-08
> **KIAaze said:**
> Yes, but how many users create an extra account to use everyday?
Most people do it just like in windows: use the default account.

Not to stray too far off-topic, but those people should read the Ubuntu Wiki's [RootSudo article]("https://help.ubuntu.com/community/RootSudo") because they are severely compromising their security (unless they are the only user with physical access to the machine).

[QUOTE="The Ubuntu Wiki"]*The basic security model is the same, and therefore these two systems share their primary weaknesses. Any user who uses su or sudo must be considered to be a privileged user. If that user's account is compromised by an attacker, the attacker can also gain root privileges the next time the user does so. The user account is the weak link in this chain, and **so must be protected with the same care as root***.[/QUOTE]

---

