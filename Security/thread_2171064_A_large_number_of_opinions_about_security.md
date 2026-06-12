---
title: "A large number of opinions about security"
date: 2013-08-27
forum: Security
---

### Post by 1clue on 2013-08-27
***Prelude:** This thread was split off of another discussion by a moderator, and without any sort of explanation.  I'm responding to a query about anti-malware software for Linux.  So this didn't just pop up out of the blue like it seems to.*


ALL anti-malware software for Linux I've used has false positives.  You need to investigate them and mark them as such.

I've heard of LMD but never used it.

Before anyone gives you a false sense of security, if Linux or Ubuntu were "secure enough" with a basic installation and no extra anti-malware or security software on it, I'm betting the forum would never have been hacked.  I've been preaching active anti-malware security for years, and yes I'm capitalizing on Ubuntu Forum's unfortunate incident to illustrate my point.

I'm NOT an expert at this, but I do it to the best of my ability.

I've been owned a few times, including when I thought I was bullet proof.  Had I not been running software to detect malware AND watched the logs obsessively, AND periodically looked things over myself, I would never have known I had been owned.  Most of the serious malware is designed to be available to the black hat hacker for a long time without ever being detected.  Trashing your box dramatically does nothing for them.  Having your computer as a tool does much for them.

Start here:  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

I get seriously bent when people claim that Linux is not susceptible.  Yes, linux as Ubuntu sets it up is probably better than most desktops you get, but that in no way means you need not worry about it.

How much effort you put into this is up to you.  You can't possibly KNOW you haven't been owned.  You CAN, however, KNOW that you HAVE been.  The problem is the vast number of possibilities in the middle where you have been owned and don't know about it.

---

### Post by SeijiSensei on 2013-08-27
> **1clue said:**
> Before anyone gives you a false sense of security, if Linux or Ubuntu were "secure enough" with a basic installation and no extra anti-malware or security software on it, I'm betting the forum would never have been hacked.

You'd lose your bet.  Have you read the [descriptions]("http://ubuntuforums.org/showthread.php?t=2164064") of how the forum was hacked?  It had nothing to do with the security of Linux.

---

### Post by 1clue on 2013-08-27
Yes, I read it.

Which just illustrates my point.

If you listen to a whole lot of forum posters, if you're running Linux you have absolutely nothing to worry about.

Security is ONLY about the weakest link.  In this case, that was either a weak password (It's a forum, so probably almost all of the passwords are the user's last name or maybe the name of their cat) and the forum COULD have made a more stringent password policy -- or a shared password or a password stored in plain text somewhere.  But that doesn't really matter.  My point is, it's always either something that was overlooked or something that was deliberately compromised in order to facilitate ease of use.

What's the password policy like on Ubuntu?  Does that password policy extend to forum software?  Does it extend to EVERY piece of software in the repository that might need security?

Now, the forum was vulnerable to a cross-site scripting attack, because that's what it was.  So again, a vulnerability on Linux.

Before you claim that forum software is not Linux, I'm going to remind you that technically the only thing that IS Linux is the Linux Kernel.  The system loggers, the window managers, the boot scripts, the network configuration -- all that is just some open source software that runs on Linux and probably a few other operating systems.  So where do you draw the line?

You might draw it at the point where the install CD stops.  So a bare installation.  But who stops there?  By asserting that Linux is secure, you're implying that anything in the software provided by Canonical in the Ubuntu Repository is secure.  It's almost certainly not, even if there are no known vulnerabilities.

You can waffle about it all you want.  By any reasonable standard, Linux can be vulnerable, and it has ALWAYS been vulnerable.  Any security expert you ask will say exactly that.

You CAN make Linux secure enough to handle credit cards and auction sites and bank transfers ***Edit:** for a commercial site, not just for handling your personal banking*, but it does not come that way, and there are LOTS of things a user can do to breach that security.  If you ever have to set up a server for compliance to a standard fit for credit card transfers, and have to be audited for that, you're going to have your eyes opened.  Especially if you hire an expert to test for vulnerabilities.

How many times have you heard "As long as you update regularly and pay attention to vulnerability announcements you don't have to worry about it." or something similar?  I'll bet you that the Ubuntu Forums staff was doing more than that.  There are so many pieces of software on any real-world system that it's extremely difficult to keep up with it, and to test from every angle you can imagine.

---

### Post by SeijiSensei on 2013-08-27
> **1clue said:**
> Before you claim that forum software is not Linux, I'm going to remind you that technically the only thing that IS Linux is the Linux Kernel.  The system loggers, the window managers, the boot scripts, the network configuration -- all that is just some open source software that runs on Linux and probably a few other operating systems.  So where do you draw the line?

You can run vBulletin on Windows servers, too. To say that a vulnerability in a web application written in PHP is somehow equivalent to a buffer-overflow exploit in a server daemon or, worse, a security problem in the kernel itself runs into the usual "apples-and-oranges" problem.  These are all different issues and have different consequences.  Except in the last case they also are not intrinsic to Linux itself in either the narrow kernel definition, or the broader "GNU/Linux" definition that includes the usual array of system tools.

If you read what informed people say about vulnerabilities here, you'll see most commentators are quite circumspect about Linux security.  Most of us recognize that any operating system will have vulnerabilities, Linux included.  If I can get you to run a script as an ordinary user that installs a keylogger, you're in trouble.  Is that the fault of Linux or the fault of the person sitting in the chair?

---

### Post by 1clue on 2013-08-28
> **SeijiSensei said:**
> You can run vBulletin on Windows servers, too. To say that a vulnerability in a web application written in PHP is somehow equivalent to a buffer-overflow exploit in a server daemon or, worse, a security problem in the kernel itself runs into the usual "apples-and-oranges" problem.  These are all different issues and have different consequences.  Except in the last case they also are not intrinsic to Linux itself in either the narrow kernel definition, or the broader "GNU/Linux" definition that includes the usual array of system tools.

If you read what informed people say about vulnerabilities here, you'll see most commentators are quite circumspect about Linux security.  Most of us recognize that any operating system will have vulnerabilities, Linux included.  If I can get you to run a script as an ordinary user that installs a keylogger, you're in trouble.  Is that the fault of Linux or the fault of the person sitting in the chair?

You are exactly correct.  The short answer to all of my ranting is that you have to be careful, you have to be educated and you have to be vigilant.

My angst is aimed at the people who insist that once you install Linux, nothing more need be done for security.

A Windows users who doesn't really know what an operating system is, or that there's any difference between that and a web browser, typically comes in and asks a question similar to the OP here.

For the record, THIS thread's OP is more informed than that.

Anyway back to the point.  It happens over and over, there's always several somebodies on the forum who cannot be convinced that any sort of malware would ever land on their system.  They might acknowledge that there's a theoretical possibility, but insist it's so unlikely as to not worry about it.

Back in the 90's when I got started on Linux, I heard the same guys and believed them.  Then I got owned, and then I learned something, and got owned again.  Then learned some more.  The cycle continues.

For years I sat back and quietly disagreed with the misinformed and loudly ignorant.  I know the difference between bad PHP and a buffer overflow exploit.  The problem is, the new guy who's asking legitimate questions rarely knows about this.  I've decided to dummy up my language a bit to try and drive the point home.  I figure more people on this site might relate to the business aspects of it than the programming aspects.  I can talk to that too.  I can pretend the other guy is my sister, and speak to the concept of the entire machine as a single piece.  Whatever gets the job done.

On any level, the "system" is vulnerable if any piece of it is vulnerable, and therefore you have to be careful.  If you buy a million dollar safe that can't be cracked, it doesn't keep your money safe if you left the door open.

The absolute truth about Linux security and any other security for that matter is education and vigilance.  There is no shortcut.  Start reading, start learning and start practicing.

Sorry about the rant.  This isn't so much about you guys as my angst at the @$$#0735 who told me I was secure years ago, and the perpetual tsunami of ignorance it started.  People (me) rant about how secure it is, then we get owned, and then we rant at the new guys who insist how secure it is.

---

### Post by cariboo on 2013-08-28
The Forum hack really had nothing to do with Linux, one of the Loco mods that had more privileges than he should have, which is a forum operator problem, had his account compromised by social engineering, which is a user problem. Once the bad guy gained access to the Forum backend he exploited some php hooks in the vBulletin php scripts, created by former Forum operators, to gain access to mysql. He did't have enough access privileges to change anything in the database, but we admins did have the ability to do a database dump.

Notice I haven't mentioned the underlying operating system, as vBulletin runs on Windows as well as on a Linux distribution. As we well know apache, php and mysql are all cross platform applications, and the exploit could have just as well happend no matter what operating system we were running, be it Linux, BSD, OSX or Windows.

---

### Post by 1clue on 2013-08-28
> **cariboo907 said:**
> The Forum hack really had nothing to do with Linux, one of the Loco mods that had more privileges than he should have, which is a forum operator problem, had his account compromised by social engineering, which is a user problem. Once the bad guy gained access to the Forum backend he exploited some php hooks in the vBulletin php scripts, created by former Forum operators, to gain access to mysql. He did't have enough access privileges to change anything in the database, but we admins did have the ability to do a database dump.

Notice I haven't mentioned the underlying operating system, as vBulletin runs on Windows as well as on a Linux distribution. As we well know apache, php and mysql are all cross platform applications, and the exploit could have just as well happend no matter what operating system we were running, be it Linux, BSD, OSX or Windows.

Yes.  That's been repeatedly stated, and I understood that when I originally got my account back when the forum came back up.

Rewind, Joe User is a freshly converted Windows guy who didn't really understand Windows either.  He wants to know if somebody can hack into his system.  Can they, or can't they?  To Joe, it's black and white.  He doesn't care if it's Linux itself, he wants to know if his pictures are still going to be there, if his music collection is going to be there.  He doesn't want his credit card information stolen.

A Linux system can be cracked by cracking anything on the system that can give you something you want.  Did the forum get hacked?  Yes.  Did somebody get data they shouldn't have had access to?  Yes.

I don't remember the figures anymore, but most security breaches are to some extent an inside job.  Some of them are social engineering based on somebody who knows somebody and guesses correctly.

As well, if you're going to insist that anything that can be run on Windows can't count as a Linux hack, glibc compiles and works on Windows too.  So that's not a valid line.  How much of what most people call Linux would be compromised if somebody injected malicious code into glibc?

---

### Post by samiux on 2013-08-28
About a year ago, I replied one of the threads here about anti-malware/virus for Linux/Ubuntu.  Later, I began a debate with other users (including admins of Ubuntu Forums) as I suggested to use anti-malware like software to protect Linux/Ubuntu.  In addition, I also pointed out that Linux is not secure at all.  We then debated about the definition of malware/virus as well as worm.  I also provided the PoC (Proof-of-Concept) video to proof my words.  Admins of the Ubuntu Forums got angry as they disagreed with me as well as other users.  Finally, Admins closed the thread.

Today, when I am browsing Security Discussion sub-forum, I seldom answer the thread.  When I want to answer, I will say "yes, Linux/Ubuntu is very secure and she do not need any protection as security is by born".  "Don't worry, it is a false positive." and so on.  Then, you will have less change to be attacked by other users and admins.  If yes, there are only one or two who suggest/agree to use anti-malware/virus.  That is, he is on my side.

So, why I answer this thread?  It is because I agree with 1clue.  I want to support him.

Almost all users and admins in this sub-forum are minded blocked.  They will not accept truth and new things that do not match their mind or desire.  In my opinion, Windows is as secure as Linux; Linux is as vulnerable as Windows.

Most of them say that the vulnerable is to the application software but not Linux, so, Linux is not counted as vulnerable.  But I want to say, Linux distributions are consisting of a lot of application software, including desktop and server version.  If not the kernel vulnerability, it is not counted as Linux vulnerability?  If yes, RPC vulnerability of Windows XP is not kernel vulnerability.  So, Windows is not vulnerability to this attack.  So as web application.  Right?

Most of them say Social Engineering exploit is not counted as vulnerabilities.  It is users fault only.  However, BlackHats count these kind of exploit as vulnerabilities.  So, there is a different mindset between you all and the BlackHats.  

Some professionals or experts here say that they never been attacked or infected.  For real?  I think most of them do not know that they are intruded or infected as there are no sign of the intrusion or infection at all.  For most malware/virus, they are not detected by any anti-malware/virus.

Some professionals or experts here also say that the malware/virus need root rights to run and they also cannot run themselves automatically.  Really?  You all think about it in more deeply.  You will know that it is not impossible to do so.

Some professionals or experts here may say that there are no open port for Ubuntu Desktop version.  Or, you behind NAT/router.  So, you are safe.  For real?  Any BlackHat can pivot any system very easily.

Okay, I should not talk anymore or this thread may be closed.

Samiux

**Edit :** The latest news.  In 2011, developer of vsftpd find that vsftpd legit source code is injected backdoor.  Almost all Linux distributions (including Ubuntu 11.04) collect it as repos.  So, rkhunter or chkrootkit will not detected that as it is official repos and you will whitelist it after update.  Any idea?

---

### Post by cariboo on 2013-08-28
@samiux , all you have been doing, is to try to spread FUD, show us some case studies, prove what you are saying.

I'm by no means a security exert, and I know one of my accounts was exploited, wouldn't it be better to help us recognize things like this when they happen, instead of just posting veiled warnings?

---

### Post by samiux on 2013-08-28
> **cariboo907 said:**
> @samiux , all you have been doing, is to try to spread FUD, show us some case studies, prove what you are saying.

I'm by no means a security exert, and I know one of my accounts was exploited, wouldn't it be better to help us recognize things like this when they happen, instead of just posting veiled warnings?

So, you agreed that I had provided the proof that it is not impossible and it is also FUD (Fully Un-Detected).  So, why the thread was closed.

Samiux

---

### Post by samiux on 2013-08-28
> **cariboo907 said:**
> @samiux , all you have been doing, is to try to spread FUD, show us some case studies, prove what you are saying.

I'm by no means a security exert, and I know one of my accounts was exploited, wouldn't it be better to help us recognize things like this when they happen, instead of just posting veiled warnings?

I have given my advice to you all after the Forum has been exploited.  However, you transfer my thread (originally posted at Security Discussion sub-forum) to Other OS sub-forum.

Okay, if you cannot find it yourself.  I tell you once more.

That is, employ at least one professional Penetration Testing team to pentest the Forum web application software as well as the Forum server (if the whole network is better) at least once a year.

Period.

Samiux

**Edit :** One hacker cannot do it, it does not mean that another hacker cannot to it.

---

### Post by aysiu on 2013-08-28
Some users here seem to putting forth a false dichotomy of "Linux is invincible" v. "Linux needs antivirus."

Antivirus does **not** in any significant way make your Linux installation more secure. It's like putting tissue paper over chainmail. If something can break the chainmail, the tissue paper on top doesn't really help.

---

### Post by lisati on 2013-08-28
Another thought that sometimes comes up in discussions such as these: no matter how careful the user is, no matter how secure the OS, an antivirus product is only as good as what it knows about.

---

### Post by 1clue on 2013-08-28
I don't support the idea of a dichotomy.  Linux has never been invincible because a system which is exposed to and communicates with the outside world can't be invincible, and UN*X is all about networking.  The "linux needs antivirus" idea is not really accurate because the types of exploits typical on Linux are too widely varied to be easily dealt with by a piece of software, IMO.  Linux needs informed, careful admins.

Linux can be extremely secure, and it can be extremely vulnerable.  Windows can be extremely secure, and it can be extremely vulnerable.  The vulnerabilities typical of each are different.

I have had the task of putting a couple servers through PCI compliance surveys and testing (so you can process credit cards), and all I'm saying is that there are a lot of extras to go through if you really want to have a secure system.

PCI compliance surveys make absolutely no distinction between an operating system hole or an application hole or a stupid user hole.  Each hole is a vulnerability and can risk your data.  In the case of a system which processes credit cards, that means credit card data is compromised.

All I'm saying is that when somebody says, "Is my system secure?" or "What sort of protection do I need?" you don't just give a blanket "don't worry about it."  Give a link to the basic security page, or tell them it depends on what you're doing, and how careful you are.  We need users to be smarter and safer, not happier and easier to hack.

When I started using Linux back when the 1200 baud modem reigned supreme, I believed all the "don't worry about it" people and did some outrageously stupid things, developed habits that lasted too long and got me hacked way too easily.

It doesn't matter how secure Linux itself is.  If somebody convinces you to run something that installs a key logger even in your user's $HOME directory someplace, all they gotta do is wait for you to type "sudo" and send off whatever comes next off to some remote place.  You're done, they have root access.

In terms of your data and your account security, the only thing that matters is that you were compromised, not whether it was Linux or something else that did it.

Maybe we need a super short security manual for unbelievers?

---

### Post by cariboo on 2013-08-29
I've moved a number of threads from [this]("http://ubuntuforums.org/showthread.php?t=2170849") thread to here, as they weren't really helping the op.

---

### Post by coldraven on 2013-08-29
If you let a child use a computer they will eventually see "Install our toolbar and you get a free candy bar" and of course they will do it.
I recently nearly installed a deb package from a Chinese site in order to watch streaming movies. I stopped myself when the installer asked me "Do you trust this software?". (D'oh!)
So we need to grow up and use our knowledge to avoid being owned. We need to educate (if that is possible) Joe Public not to blindly trust everyone on the Internet.
Sadly, this is unlikely. Most peoples tablets, smartphones and PCs are full of malware of some form or another, regardless of OS.

---

### Post by samiux on 2013-08-29
I don't want to misleading anyone here.

I suggest to use anti-malware/virus to all kind of systems, including Linux, Mac OSX, *BSD, *nix and Windows.  My home network is implemented UTM (Unified Threat Management System), and IDS/IPS (Intrusion Detection/Prevention System).

However, it does not mean that my home network is safe and no need to keep my eyes on it.  I always monitor the incoming and outgoing traffic of my home network.

Anti-malware/virus, UTM and IDS/IPS as well as WAF (Web Application Firewall) are based on signature.  If the malware/virus/exploits are in the wild, experts/professionals will include such signature of those malware/virus/exploits in their products/programs.  If not, no signature at all.  By the way, those signature can be bypass very easily in most cases.

I also use Firefox add-on, NoScript and etc, but it does not proof that I am safe when surfing internet.  If a legit website, which I trusted, is infected or intruded, I may have chance to be infected too.

So, there is no bullet-proof or silver bullet.  The missing part is education even you implemented all of the above.  Education includes how to monitor the traffic as well.  Does education is a silver bullet?  It is still not, sorry.

So?  How to get the silver bullet?  I can show you how - not to use computer, not to surf internet, not to use smartphone and etc.

Samiux

---

### Post by 1clue on 2013-08-29
The entire thrust of my part in this discussion is that to separate any part of security as not relevant to Linux security is passing the buck and a disservice to any new user who's trying to find out about security.

"Don't worry about it, Linux is secure."  Does not help.  "The forum hack was a human error, it does not affect Linux security."  Does not help.

Again, let's go back to the forum hack.  The black hat convinced someone with access to give him the keys to the forum.  That's every bit as pertinent to a security discussion as a buffer overflow problem.  The problem lies with a different system (the human one) but it's still a major issue with security.

Do some forum searches on antivirus/malware detection.  How many of those threads have, "Don't worry about it, Linux can't get viruses?"  All of them have it, so fervently that they drown out all the people saying what the problems really can be.

This forum and most other Linux forums I've been on incorrectly educate users to believe that once they install Linux they need not worry about security.  It's just not true.

There are all sorts of issues with where beginning users go after they finish with the installer CD.  They do it because of convenience and because they don't know any better.

There's another thing:  Linux provides all sorts of logs about what's happening in the system, but if you never look at them then almost no security breach or attempted security breach can be detected, during or after the breach.  I suspect all sorts of forum members have had malware on their systems for months or years, and they would never know because they never look.

I've had an intrusion that I detected from pure log file diligence, the only way I knew about it is the log entry that said that my user logged out from a remote location.  Reverse DNS pointed at a company based in China.  There was no matching login entry.  I never logged in remotely, so I knew right away that was an intrusion.  How did it happen?  Brute force ssh exploit.  He guessed my password.  He had cleaned up the current log for all the attempts, but I'd seen the attempts before, done nothing about it (yes, my fault and my laziness) thinking that my password was unguessable.  Suddenly all those entries are gone, and only this one place where I logged out.

---

### Post by coldraven on 2013-08-30
> but I'd seen the attempts before,
A genuine question: Does fail2ban work with ssh logins? 

I've seen tutorials on blocking logins from outside of an IP range and general hardening of systems but it would be nice to find them all in one place.
e.g. here :)

---

### Post by 1clue on 2013-08-30
There are a lot of Linux security write-ups.  Here's my favorite Ubuntu-specific one:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

The issue with yet another one is you need to add significant value or you just litter googlespace with more noise.

---

### Post by 1clue on 2013-08-30
In this post I'm referring to white hats and black hats.  It's a pretty widespread set of terms, but for those of you who don't know:

White hats are the good guys.  In this case it's people who work toward system security.  They include Ubuntu staff, upstream developers and testers, general security organizations like CERT, and well intentioned users who might report a problem.

Black hats are the guys who want to break into systems they don't own or have legal access to for one or more nefarious purposes.

Take a look here:

[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

This is the list of vulnerabilities in Ubuntu, published on the official Ubuntu web site. Yes, they exist, EVERY operating system has them.

Usually, this list has at least temporary solutions for every item. Which means if you keep your system up to date you're probably pretty safe.  But people put way too much faith on this.

What nobody seems to think about is that for every one of these items, there is a period of time between the discovery of the vulnerability BY A WHITE-HAT and the release of a fix. That period of time is sufficient for somebody to validate the problem, think of a solution (at least a temporary one) test it and then release the fix. Could be minutes or weeks. For minor issues or issues they don't believe to be publicly known they might wait to make the announcement until they have a fix.

There's also the period of time BEFORE the white hats learned of the vulnerability, in which time a black-hat hacker could have known about it. They might have an exploit active already, and just because Ubuntu knows about the vulnerability doesn't mean they know about an exploit out "in the wild". Sometimes the way Ubuntu knows about the problem is because somebody is actively exploiting it in a malicious way. In that case it's the time it takes the victim to realize they have a problem, realize they can't do anything about it, decide whether to report it and then have some expert come in and see what happened.  The potential time period here is from the time the software was written (could have been a black-hat added an exploit that nobody noticed!) until right now, whenever you read this.

As far as I've ever seen, Ubuntu fixes vulnerabilities, but if you're one of the unlucky ones who have already been exploited, then chances are even if you keep up with your updates you'll still have the malware even after the fix was applied.

---

### Post by aysiu on 2013-08-30
I love this post, 1clue, because you talk about real security issues without mentioning the placebo a lot of people like to call *antivirus software*. > **1clue said:**
> In this post I'm referring to white hats and black hats.  It's a pretty widespread set of terms, but for those of you who don't know:

White hats are the good guys.  In this case it's people who work toward system security.  They include Ubuntu staff, upstream developers and testers, general security organizations like CERT, and well intentioned users who might report a problem.

Black hats are the guys who want to break into systems they don't own or have legal access to for one or more nefarious purposes.

Take a look here:

[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

This is the list of vulnerabilities in Ubuntu, published on the official Ubuntu web site. Yes, they exist, EVERY operating system has them.

Usually, this list has at least temporary solutions for every item. Which means if you keep your system up to date you're probably pretty safe.  But people put way too much faith on this.

What nobody seems to think about is that for every one of these items, there is a period of time between the discovery of the vulnerability BY A WHITE-HAT and the release of a fix. That period of time is sufficient for somebody to validate the problem, think of a solution (at least a temporary one) test it and then release the fix. Could be minutes or weeks. For minor issues or issues they don't believe to be publicly known they might wait to make the announcement until they have a fix.

There's also the period of time BEFORE the white hats learned of the vulnerability, in which time a black-hat hacker could have known about it. They might have an exploit active already, and just because Ubuntu knows about the vulnerability doesn't mean they know about an exploit out "in the wild". Sometimes the way Ubuntu knows about the problem is because somebody is actively exploiting it in a malicious way. In that case it's the time it takes the victim to realize they have a problem, realize they can't do anything about it, decide whether to report it and then have some expert come in and see what happened.  The potential time period here is from the time the software was written (could have been a black-hat added an exploit that nobody noticed!) until right now, whenever you read this.

As far as I've ever seen, Ubuntu fixes vulnerabilities, but if you're one of the unlucky ones who have already been exploited, then chances are even if you keep up with your updates you'll still have the malware even after the fix was applied.

---

### Post by 1clue on 2013-08-30
Thank you.

I work for a small company.  I'm a software designer, a developer and customer support.  I work with people who have, when I asked for a screen shot, taken a photo of their computer screen, copied it to their computer, printed it and then faxed it to me.  And then they call me in a few minutes, and I've got to be done snickering by then.

Some of the Ubuntu users are here because they know they don't like Windows, but they don't know much more about computers than the people I described above.  It's the disadvantage of having an installer that is so incredibly easy to use.  They hear about how easy Ubuntu is to use and to install, so they do it, and then they ask questions.

I think many of the users here see the term "antivirus" and they think the user knows what they're talking about.  If you KNOW the poster is an expert then go ahead and rant about the futility of antivirus software on Linux.  But if you're talking to somebody who barely knows how to turn the computer on, they use the term 'antivirus' to mean a way to detect and get rid of malware, and also to protect their computer from those with malicious intent.

If you look at how "antivirus" is used on Windows, you'll realize that it's an umbrella for all software they don't want on their computer, AND a mechanism to prevent malware from being installed in the first place.

---

