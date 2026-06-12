---
title: "Virus, what?"
date: 2006-07-20
forum: The Cafe
---

### Post by jordilin on 2006-07-20
Many Windows pro activists say that it's a question of time that Linux will have viruses like Windows. Their arguments are that hackers program viruses that target the most used OS, so if Linux is used by a high number of people then it will get viruses. I don't agree at all. It does not matter the popularity of Linux nor its number of users, Linux will never have viruses. First of all, everything in Linux is a file. So, viruses if ever they get into your computer, they are just files without permissions. If they enter into your computer they will go into your home directory and without the +x permission (remember we don't have .exe files, ;-)). If this file (virus) is run (having the +x permission), it will affect only your  /home directory and will not touch system files, since to touch system files you must be root. We have double protection:
1- a file must have +x permission
2- it must be root to destroy our machine
Only for these two reasons, it is impossible that we, Linux users, we will ever get a virus. Obviously,  if the computer is run by an inexpert it can cause damage, but if that person is an inexpert, most obviouly he/she will not know how to change the permission of a file by doing chmod +x, will he/she? 
I need more arguments to fight against those who say that Linux will fall into the world of spyware, viruses, and all kind of crap.
What do you think, Ubuntu fellows, do you agree with me?

---

### Post by Derek Djons on 2006-07-20
Well, I wouldn't say it's impossible. Everything made by a human can also be destroyed by a human. The fact that security measures, user accounts and permissions are set different (and better) does not mean it's necessarily bulletproof.

Some time ago Debian's server got compromised. So I don't see why Linux is bulletproof. I agree that for black hat hackers it will be difficult to infect a system directly. But exploits discovered in other applications can maybe do enough damage.

Also I agree that the number of viruses, hacks and what not will be very very very low. But I don't think it's impossible (based on my blabbing above here).

---

### Post by jordilin on 2006-07-20
> **Derek Djons said:**
> Well, I wouldn't say it's impossible. Everything made by a human can also be destroyed by a human. The fact that security measures, user accounts and permissions are set different (and better) does not mean it's necessarily bulletproof.

Some time ago Debian's server got compromised. So I don't see why Linux is bulletproof. I agree that for black hat hackers it will be difficult to infect a system directly. But exploits discovered in other applications can maybe do enough damage.

Also I agree that the number of viruses, hacks and what not will be very very very low. But I don't think it's impossible (based on my blabbing above here).

So, will we need an antivirus in a near future?

---

### Post by awakatanka on 2006-07-20
> Subject:      Debian Server restored after Compromise
From:         Martin Schulze <joey@infodrom.org>
Newsgroups:   linux.debian.news
Date:         Thu, 13 Jul 2006 20:10:19 +0200

------------------------------------------------------------------------
The Debian Project                                [http://www.debian.org/](http://www.debian.org/)
Debian Server restored after Compromise          [email]debian-admin@debian.org[/email]
July 13th, 2006                 [http://www.debian.org/News/2005/20060713](http://www.debian.org/News/2005/20060713)
------------------------------------------------------------------------

Debian Server restored after Compromise

One core Debian server has been reinstalled after a compromise and
services have been restored.  On July 12th the host gluck.debian.org
has been compromised using a local root vulnerability in the Linux
kernel.  The intruder had access to the server using a compromised
developer account.

The services affected and temporarily taken down are: cvs, ddtp,
lintian, people, popcon, planet, ports, release.

Details
-------

At least one developer account has been compromised a while ago and
has been used by an attacker to gain access to the Debian server.  A
recently discovered local root vulnerability in the Linux kernel has
then been used to gain root access to the machine.

At 02:43 UTC on July 12th suspicious mails were received and alarmed
the Debian admins.   The following investigation turned out that a
developer account was compromised and that a local kernel
vulnerability has been exploited to gain root access.

At 04:30 UTC on July 12th gluck has been taken offline and booted off
trusted media.  Other Debian servers have been locked down for further
investigation whether they were compromised as well.  They will be
upgraded to a corrected kernel before they will be unlocked.

Due to the short window between exploiting the kernel and Debian
admins noticing, the attacker hadn't had time/inclination to cause
much damage.  The only obviously compromised binary was /bin/ping.

The compromised account did not have access to any of the restricted
Debian hosts.  Hence, neither the regular nor the security archive had
a chance to be compromised.

An investigation of developer passwords revealed a number of weak
passwords whose accounts have been locked in response.

The machine status is here: <http://db.debian.org/machines.cgi>


Kernel vulnerability
--------------------

The kernel vulnerability that has been used for this compromise is
referenced as CVE-2006-2451.  It only exists in the Linux kernel
2.6.13 up to versions before 2.6.17.4, and 2.6.16 before 2.6.16.24.
The bug allows a local user to gain root privileges via the
PR_SET_DUMPABLE argument of the prctl function and a program that
causes a core dump file to be created in a directory for which the
user does not have permissions.

The current stable release, Debian GNU/Linux 3.1 alias 'sarge',
contains Linux 2.6.8 and is thus not affected by this problem.  The
compromised server ran Linux 2.6.16.18.

If you run Linux 2.6.13 up to versions before 2.6.17.4, or Linux
2.6.16 up to versions before 2.6.16.24, please update your kernel
immediately.


About Debian
------------

Debian GNU/Linux is a free operating system, developed by more than
thousand volunteers from all over the world who collaborate via the
Internet.  Debian's dedication to Free Software, its non-profit nature,
and its open development model make it unique among GNU/Linux
distributions.

The Debian project's key strengths are its volunteer base, its dedication
to the Debian Social Contract, and its commitment to provide the best
operating system possible.


-- 
To UNSUBSCRIBE, email to [email]debian-news-REQUEST@lists.debian.org[/email]
with a subject of "unsubscribe". Trouble? Contact [email]listmaster@lists.debian.org[/email]

If this is possible then it possible to make a virus that can use that kind of things.

---

### Post by GeneralZod on 2006-07-20
Many viruses/ malware are commonly contracted by exploits in applications (most notably, web browsers) that allow arbitrary code to be run.  Once an attacker has the ability to run arbitrary code, he can do anything to your machine that the person using the web browser (i.e. - you ;)) can do, so I don't find the "chmod +x" defense terribly convincing.  Also, priviledge escalation vulnerabilities *do* happen, so it's not at all inconceivable that a person running as a limited user could get his machine rooted simply by visiting a dodgy website. 

However, technologies such as SELinux and AppArmour can offer some defence against this, by stipulating that your web-browser is not allowed to go writing to directories outside of its designated sandbox without the user's permission.  Other proactive technologies (I don't know the exact names, I'm afraid, but there is some kind of randomisation technology around that means that the same buffer overflow attack won't necessarily work on all installs) will make it your OS  an even tougher nut to crack.

Truthfully, I see all three major OS's (Windows, OS X and Linux) converging on roughly the same level of security - one where "drive-by" infections from just visiting websites are very hard to accomplish, and social-engineering becomes the dominant vector of infection.

---

### Post by jordilin on 2006-07-20
in the note it says:
> The intruder had access to the server using a compromised
developer account.
Obviously, if anyone has root access, it can do anything, but I'm talking about getting viruses while working in your Desktop as a normal user.

---

### Post by Lord Illidan on 2006-07-20
> If this file (virus) is run (having the +x permission), it will affect only your /home directory and will not touch system files, since to touch system files you must be root.

And do you think that system files are the most important parts of an OS? Try telling that to someone who has just lost his/her thesis because of a virus, or all of his mp3 collection or all of his pictures.

System files are important for the system to run, definitely. However, should they be infected, all I have to do is re-install. If I lose my /home files, I have to do much more than re-install, assuming I don't have backups, that is.

Nothing is impossible.

---

### Post by aysiu on 2006-07-20
Marketshare has a big role to play in malware, but not for the reason most anti-Linux/pro-Microsoft people say it does.

Basically, if Ubuntu were the dominant operating system, that would mean the bulk of Ubuntu users would be stupid (just as the bulk of Windows users are currently stupid)--I'm speaking of the computer equivalent of "street smarts" here, not scholastic achievement.

Once you have stupid people with *sudo* rights, all security goes out the window. Just as they do now in Windows, these future potential Ubuntu users would click on anything that moves. They would give their passwords away for any "cool" new program they download from god-knows-where (not the repositories).

It would not be difficult at all for malware writers to create a double-click installation script for Ubuntu where you double-clicked the .deb file, gDebi asked for your password, and then all sorts of spyware, viruses, etc. would infest your Ubuntu installation.

The old expression is that a chain is only as strong as its weakest link. A lot of times, the weakest link in the chain is the user.

That said, even as Ubuntu stands now--am I the only one who considers the contents of my /home directory more important than the other files? If I didn't back them up regularly, I'd be pissed to find all those files gone. The /usr or /etc files I can get back with a reinstall. My music, pictures, etc. can't be replaced if I haven't backed them up.

---

### Post by jordilin on 2006-07-20
> **Lord Illidan said:**
> And do you think that system files are the most important parts of an OS? .

What happens if this system file or directory is /boot?
Then, you will not be able to boot your OS and you will lose, not only your thesis, or mp3 collection, you'll lose all your home and all your system.

---

### Post by aysiu on 2006-07-20
> **jordilin said:**
> What happens if this system file or directory is /boot?
Then, you will not be able to boot your OS and you will lose, not only your thesis, or mp3 collection, you'll lose all your home and all your system.
That's what they made live CDs for, my friend.

Boot up Ubuntu and mount the partition and save your files.

---

### Post by jordilin on 2006-07-20
> **aysiu said:**
> That's what they made live CDs for, my friend.

Boot up Ubuntu and mount the partition and save your files.

Yes, you are right ;-)

---

### Post by aysiu on 2006-07-20
Really, though, the best solution is to back up often.

My external hard drive was one of the best investments I ever made.

---

### Post by jordilin on 2006-07-20
> It would not be difficult at all for malware writers to create a double-click installation script for Ubuntu where you double-clicked the .deb file, gDebi asked for your password, and then all sorts of spyware, viruses, etc. would infest your Ubuntu installation.
That's a good point and it would be really painful for the Linux community, since it would get into the news and many people would think what an horrible OS Linux is. As always, a computer must be run with a little care and a bit of knowledge.

---

### Post by Adamant1988 on 2006-07-20
> **jordilin said:**
> Many Windows pro activists say that it's a question of time that Linux will have viruses like Windows. Their arguments are that hackers program viruses that target the most used OS, so if Linux is used by a high number of people then it will get viruses. I don't agree at all. It does not matter the popularity of Linux nor its number of users, Linux will never have viruses. First of all, everything in Linux is a file. So, viruses if ever they get into your computer, they are just files without permissions. If they enter into your computer they will go into your home directory and without the +x permission (remember we don't have .exe files, ;-)). If this file (virus) is run (having the +x permission), it will affect only your  /home directory and will not touch system files, since to touch system files you must be root. We have double protection:
1- a file must have +x permission
2- it must be root to destroy our machine
Only for these two reasons, it is impossible that we, Linux users, we will ever get a virus. Obviously,  if the computer is run by an inexpert it can cause damage, but if that person is an inexpert, most obviouly he/she will not know how to change the permission of a file by doing chmod +x, will he/she? 
I need more arguments to fight against those who say that Linux will fall into the world of spyware, viruses, and all kind of crap.
What do you think, Ubuntu fellows, do you agree with me?
I know I'm going to get flamed for this but I've read in multiple places that not only does linux have = to or > than number of security problems as Windows, they are slower to be patched.

And YES linux viruses ARE a possibillity, someone has already written a 'proof of concept' virus that was able to infect both windows and linux pc's.  Linus wrote the fix for that himself, as I understand it. 

(please not that the sources comparing the numbers of security risks did not rate the severity of each risk etc.  The linux risks might have been MUCH less potentially damaging, but there were still security flaws none the less.)

I think the future of Linux security comes in the form of AppArmor and SElinux (they both do about the same thing yes?) they basically protect the system by keeping a profile of what each program is allowed to do and not allowing it to go outside of what's allowed.

If my statements are incorrect please correct them for me... I didn't double check anything before I posted.

---

### Post by blitzd on 2006-07-20
> **Adamant1988 said:**
> I know I'm going to get flamed for this but I've read in multiple places that not only does linux have = to or > than number of security problems as Windows, they are slower to be patched.

Consider this... A "Windows security flaw" is considered to be a flaw in only the software which is distributed with windows, i.e. a fresh install of Windows with no additional software other than a whack of patches from MS. Sometimes maybe an additional piece of software from MS as well.

A "Linux security flaw" on the other hand is any of the multitude of packages that may or may not be included in the default install of the tons of different distributions out there. The "Windows security flaw" count certainly isn't taking into consideration *every* piece of software which may run on Windows though.

I think it's easy to see why there may be more "flaws" in Linux when you take that into account.

As for how long one of those flaws remains unpatched - they're typically counting from the time the flaw is publicly disclosed to the time a patch is released. With the open nature of Linux the flaws are much more likely to be reported straight to the public, whereas flaws in MS products can be known to the company for months before they are made public.

Anyways, malware and other malicious software targetted towards Linux users just doesn't seem very feasible (though it is certainly still a possibility) in my mind. There is so much diversity between different distributions and the distributions themselves are so customizable that to infect Linux users on a wide scale would take one whopper of a security flaw. That seems even less likely when you take into account the scores of people who have access to review all of open source code involved.

---

### Post by aysiu on 2006-07-20
I think there's something to be said for not only what in theory could attack you but also what actually will attack you.

After all, in my parents' neighborhood, a lot of people leave their garage doors open, their doors unlocked, and bikes lying around outside. There are very few thefts because it's a "nice" neighborhood.

On the other hand, where I went to college and where I'm living now (both urban areas), your car will be broken into, your bike stolen, possibly even your apartment burglarized, despite whatever lock you may put on.

It's nice to know you are secure "just in case," but the downright truth of the matter is that right now and in the near future, viruses and malware are not a threat to Linux operating systems (cracking may be... for Linux servers). When the first really threatening virus appears, people will quickly find ways to deal with it, as most Linux users are at least a little tech-savvy.

Once the dumb users become the majority of Linux users... well, that'll be a different story.

---

### Post by xtacocorex on 2006-07-20
> **aysiu said:**
> Once the dumb users become the majority of Linux users... well, that'll be a different story.

This is probably a reason why older Linux users don't like new Linux users because they think they're dumbing the OS down.

I, in fact, see this in a different light. I think that, although Linux is getting easier for new users to learn, it still isn't easy to use unless you are proactive in learning it. Being pro-active in learning Linux means that you will progress from being a 'dumb' user to a smarter one. 

I've witnessed both Windows and Linux machines getting exploited by attackers. It's not easy to do (10 hrs for the Win2K3 machine and 5 for the FC4 machine which ended up having a chrooted filesystem), but once one gets in as root/admin, things are over unless you're watching the computer and can turn it off. The nice thing about Ubuntu is the lack of an activated root account. Most attackers try this route first by brute force cracking the root password. With Ubuntu, one would need to know the username for the first person who created a user on the system as that's the only user who is able to use sudo unless that person modified it.

I'd say that we're fairly safe in Linux for a while. If new users don't attempt to run ssh servers or web servers on their system right after they install, then they won't have any open ports for attacking attempts and will be very secure. Until the advent of malware .deb packages or random scripts to destroy a users home folder, we won't have to worry. 

It's amazing the amount of trust the people in the F/OSS community have. I trust the developers to make sure that the code is good and I know that a developer can't catch all bugs or exploitable code right away, but that's why the code is out there and there are placs for bug reports. If it wasn't this way, we'd all have compromsed computers and no one would be into Linux.

---

### Post by BugenhagenXIII on 2006-07-20
> **Adamant1988 said:**
> And YES linux viruses ARE a possibillity, someone has already written a 'proof of concept' virus that was able to infect both windows and linux pc's.  Linus wrote the fix for that himself, as I understand it.


As I understand it, there was a bug in the kernel that prevented the proof of concept virus from working.  The kernel specs said it was supposed to do one thing and the virus depended on it doing that thing.  It either didn't do anything, or did the wrong thing (I don't know, as I don't know what the particular bug was), which prevented the proof of concept virus from working.  Linus then went and fixed the bug.  It was discussed on an episode of the [LUGradio]("http://lugradio.org") podcast (Season 3 Episode 15: Pigeon! Like your English!).

---

### Post by blitzd on 2006-07-20
> **xtacocorex said:**
> This is probably a reason why older Linux users don't like new Linux users because they think they're dumbing the OS down.
There is no dumbing down the OS, it's open source - you can do what you wish really (regardless of how anything is built by default). Snazzy GUIs may give the impression of a dumbed down product, but it's still just as configurable under the hood. 

I can also see how you may have formed the opinion that older linux users 'don't like' newer users (the old standby RTFM response to a 'newbie' question often leads to this impression) - but I assure you it's a misconception in the majority of cases. The term 'teach a man to fish' comes to mind. ;)
> **xtacocorex said:**
> I've witnessed both Windows and Linux machines getting exploited by attackers. It's not easy to do (10 hrs for the Win2K3 machine and 5 for the FC4 machine which ended up having a chrooted filesystem), but once one gets in as root/admin, things are over unless you're watching the computer and can turn it off. 
Doing tech support for close to 8 years now I have yet to see a Linux install that got hacked, I have seen numerous Windows environments that got 'Pwned' though. Maybe I'm just supporting the wrong clients though.. :o
> **xtacocorex said:**
> It's amazing the amount of trust the people in the F/OSS community have. I trust the developers to make sure that the code is good and I know that a developer can't catch all bugs or exploitable code right away, but that's why the code is out there and there are placs for bug reports. If it wasn't this way, we'd all have compromsed computers and no one would be into Linux.
If you think that's amazing you should take a look at how many people trust software to which very few people have access to the source code... A certain company who has a majority share in the OS market is known to run their own (insecure) products in their own corporate environment... Who's to say that someone hasn't hacked into their network and inserted some malicious code undetected along the way?

---

### Post by az on 2006-07-20
> **jordilin said:**
> in the note it says:

Obviously, if anyone has root access, it can do anything, but I'm talking about getting viruses while working in your Desktop as a normal user.
Case in point, the compromised account did not have root privileges, but used an exploint inthe kernel to become root (or escalate priviledges)

So will linux become infested with viruse, no.  The way it is developed will not allow that to happen.  The development of much more flexible than to allow a security rist to go unclosed on purpose.

Will linux suffer from security vulnerabilities like all other software, yes.

Do you need a virus scanner?  No.  Do you need to keep up-to-date with your security updates?  Yes.

---

### Post by Skia_42 on 2006-07-20
The main reason why Linux will never have as much trouble with viruses as windows is the speed in which security holes are fixed. Microsoft can't release a new version a few days after an incident like Linux. We heal, they bleed.

---

### Post by jordilin on 2006-07-21
> **aysiu said:**
> When the first really threatening virus appears, people will quickly find ways to deal with it, as most Linux users are at least a little tech-savvy.

Once the dumb users become the majority of Linux users... well, that'll be a different story.

Perhaps in the near future, as Linux becomes more widespread, there will be viruses, but these will only affect as aysiu says inexpert     Linux users who don't know anything about computers. These kind of viruses more probably will be the like of hoaxes. As I said in my first post, doing a virus targeting Linux is quite difficult, at least more difficult than its windows counterpart. And I don't think we are going to end up installing some antivirus like soft. If we end up with antiviruses, Linux will not be really the same.

---

