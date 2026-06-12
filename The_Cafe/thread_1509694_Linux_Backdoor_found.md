---
title: "Linux Backdoor found?"
date: 2010-06-14
forum: The Cafe
---

### Post by mr-woof on 2010-06-14
interesting reading:

[http://www.fewt.com/2010/06/linux-infected.html](http://www.fewt.com/2010/06/linux-infected.html)

Anyone use this unreal package?

---

### Post by Cushie on 2010-06-14
Linux infection proves Windows malware monopoly is over, see 

[http://www.zdnet.com/blog/bott/linux-infection-proves-windows-malware-monopoly-is-over/2206#comments](http://www.zdnet.com/blog/bott/linux-infection-proves-windows-malware-monopoly-is-over/2206#comments)

My comment:-
I think not Ed.
Ed, you probably know, but your readers might not, that Linux is NOT an operating system. This operating system is Ubuntu and  there are dozens of IRC clients to download from the official dedicated servers there was no sign of 'Unreal IRC' . So any Ubuntu user who ferrits out where this maverick server is, they must decide themselves that there is a risk. Every Ubuntu (and other Distros) soon find out that it is adviseed to stay with the official servers for the very reason you outlined.
So I believe it is still true to say my system is not vunerable to that trojan. (however I could download the file and pass the file onto someone else who might be stupid enough to run it. Were you?

---

### Post by anomie on 2010-06-14
Part 1: 

Signatures + one-way functions solved the problem of verifying software integrity long ago. (Unfortunately, this protocol is not followed as carefully as it could be.) 

It seems like end users need a brain-dead simple method for verifying sigs / file hashes. Think: push one button and "ding!". (GnuPG is perfect for geeks, but hard for many end users.) 

---

Part 2: 

Sysadmins need to be aware about what's running on their system, and what's actively listening for tcp/udp connections. Filter by default, and explicitly allow only needed connections, is a good policy.

---

### Post by ddrichardson on 2010-06-14
This is FUD. The backdoor is not in "Linux" it's a trojan. A trojan could be executed in any operating system. This story was being touted on [Computer World]("http://blogs.computerworld.com/16316/think_linux_is_free_from_malware_think_again_its_been_hacked") earlier too and then Tweets started appearing within a few minutes.

---

### Post by CharlesA on 2010-06-14
According to the article it was in the Gentoo repos (I think) but we all know how awesome zdnet is!

The file should have been checked, but that was the responsibility of the guys who released it to the mirrors.

---

### Post by anomie on 2010-06-14
The story has been misrepresented, twisted, and stupidly overblown, but it's still a good opportunity to review some common practices (and how they could be improved).

---

### Post by OpSecShellshock on 2010-06-14
It's also the responsibility of the users who installed it, of course. I haven't checked to see what all it was written to do. Frankly, when I first read about this on the SANS Internet Storm Center blog this morning, I was more amazed that people still play Unreal.

---

### Post by FuturePilot on 2010-06-14
> **OpSecShellshock said:**
> It's also the responsibility of the users who installed it, of course. I haven't checked to see what all it was written to do. Frankly, when I first read about this on the SANS Internet Storm Center blog this morning, I was more amazed that people still play Unreal.

It wasn't the game, it was the IRCD server.

---

### Post by bodhi.zazen on 2010-06-14
Moved to the cafe as I do not see a support question here.

---

### Post by bodhi.zazen on 2010-06-14
Threads merged.

---

### Post by linux-hack on 2010-06-14
On linux if you know what your doing and take care to not install and run everything will be fine and you'll not have any problems with this kind of things.

---

### Post by Frogs Hair on 2010-06-14
> **anomie said:**
> the story has been misrepresented, twisted, and stupidly overblown, but it's still a good opportunity to review some common practices (and how they could be improved).

+1

---

### Post by OpSecShellshock on 2010-06-14
OK, having read up on it a little, the package is for use as an IRC server to begin with, right? I only say this because servers get compromised all the time due to applications that are running on them. What makes this one such a big deal? Granted, the client accounts that connected to any server using the compromised version should be considered breached.

---

### Post by Linuxforall on 2010-06-14
Happy Happy Joy Joy time for MS, NOT.

[http://www.itworld.com/security/110942/linux-secure-ever](http://www.itworld.com/security/110942/linux-secure-ever)

---

### Post by bodhi.zazen on 2010-06-14
I think the "big deal" is that the gentoo repositories were compromised.

In giving security advice we always advise people not to install applications, including servers, from outside the repositories.

IMO, The event is mischaractarized as a fundamental security flaw in "Linux security" or some kind of a "back door". It is not a flaw in the underlying operating system or a back door in the core linux kernel / GNU applications we all run on a desktop.

I suggest you take the time to review apt security :

[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

None of that really applies if the repository is compromised and an application is replaced.

---

### Post by bodhi.zazen on 2010-06-14
> **Linuxforall said:**
> Happy Happy Joy Joy time for MS, NOT.

[http://www.itworld.com/security/110942/linux-secure-ever](http://www.itworld.com/security/110942/linux-secure-ever)

LOL, this ^^

---

### Post by manny43 on 2010-06-14
**How much more malware is lurking in Linux official  repositories?**


	                          The revelation that the open-source Unreal IRC server  download has been [infected  with malware]("http://forums.unrealircd.com/viewtopic.php?t=6562") for some eight months is pretty worrying. But the  added discovery that [this Trojan horse]("http://www.zdnet.com/blog/bott/linux-infection-proves-windows-malware-monopoly-is-over-gentoo-ships-backdoor-updated/2206") [made  its way into]("http://www.fewt.com/2010/06/linux-infected.html") the [Gentoo  distro]("https://bugs.gentoo.org/show_bug.cgi?id=323691") is real reason for the Linux community to re-examine how  trusted repositories are handled.
 It’s true that compared to Windows, Linux is pretty safe bet if you  want to remain protected from hackers. After all, the 1% or so usage  share that the OS enjoys (combined with the fact that many of its users  are pretty switched on) just doesn’t make it a worthwhile target to go  after.
 But there’s a big difference between the OS being a “pretty safe bet”  and it being invulnerable. No OS is invulnerable. If someone wants in  on your system, and they have the time and resources, they are likely to  find a way.
 But this is a major blunder. Allowing infected code to make its way  into an official distro demonstrates how complacent some in the Linux  community have become.
 Which leads to the biggest and most important question of all - how  can we, as Linux users, be sure that more malware hasn’t infiltrated  official channels?
 The idea that we can blindly trust official repositories of open  source code is slowly eroding. Earlier this year Mozilla discovered that  it had been [hosting a Firefox add-on that contained malware]("http://www.zdnet.com/blog/hardware/update-firefox-add-on-contained-toxic-trojan-code/7171").  This latest incident should underline the need to beef up security to  protect users.

---

### Post by bodhi.zazen on 2010-06-14
> **manny43 said:**
> **How much more malware is lurking in Linux official  repositories?**


                              The revelation that the open-source Unreal IRC server  download has been [infected  with malware]("http://forums.unrealircd.com/viewtopic.php?t=6562") for some eight months is pretty worrying. But the  added discovery that [this Trojan horse]("http://www.zdnet.com/blog/bott/linux-infection-proves-windows-malware-monopoly-is-over-gentoo-ships-backdoor-updated/2206") [made  its way into]("http://www.fewt.com/2010/06/linux-infected.html") the [Gentoo  distro]("https://bugs.gentoo.org/show_bug.cgi?id=323691") is real reason for the Linux community to re-examine how  trusted repositories are handled.
 It’s true that compared to Windows, Linux is pretty safe bet if you  want to remain protected from hackers. After all, the 1% or so usage  share that the OS enjoys (combined with the fact that many of its users  are pretty switched on) just doesn’t make it a worthwhile target to go  after.
 But there’s a big difference between the OS being a “pretty safe bet”  and it being invulnerable. No OS is invulnerable. If someone wants in  on your system, and they have the time and resources, they are likely to  find a way.
 But this is a major blunder. Allowing infected code to make its way  into an official distro demonstrates how complacent some in the Linux  community have become.
 Which leads to the biggest and most important question of all - how  can we, as Linux users, be sure that more malware hasn’t infiltrated  official channels?
 The idea that we can blindly trust official repositories of open  source code is slowly eroding. Earlier this year Mozilla discovered that  it had been [hosting a Firefox add-on that contained malware]("http://www.zdnet.com/blog/hardware/update-firefox-add-on-contained-toxic-trojan-code/7171").  This latest incident should underline the need to beef up security to  protect users.

Sigh ...

Threads merged again.

The event described in the referenced article is true, interpretation of events and their significance vary, mostly according to preconceived notions.

Read up ...

---

### Post by Shining Arcanine on 2010-06-14
> **mr-woof said:**
> interesting reading:

[http://www.fewt.com/2010/06/linux-infected.html](http://www.fewt.com/2010/06/linux-infected.html)

Anyone use this unreal package?

This issue is not Linux specific. I imagine that it affects Mac OS X and FreeBSD too.

---

### Post by cammin on 2010-06-15
> **Shining Arcanine said:**
> This issue is not Linux specific. I imagine that it affects Mac OS X and FreeBSD too.

FreeBSD's ports automatically checksum the downloaded files before compiling. The distinfo file with the checksum it uses for comparison hasn't been changed in 9 months, and included the proper checksum.

---

### Post by Legendary_Bibo on 2010-06-15
Does this have to do with Unreal Tournament? If not can someone help me install UT2004. I seems to be missing the linux-installer.sh and my attempts to find a mirror with the download have proven futile. :D

Well with Ubuntu, more users are becoming average users, so there's a slim chance that it would affect them.

---

### Post by Johnsie on 2010-06-15
If there was a backdoor on my system there would be nothing to detect and warn me of this. Linux currently has very few decent security tools and that is quite worrying.

Yes, repositories can be compromised... yes, your browser can be compromised... But sadly people are ignorant to the real security issues facing Linux.

LINUX IS NOT INVULNERABLE

LINUX DOES NOT HAVE A DECENT SET OF SECURITY WARNING TOOLS

---

### Post by ddrichardson on 2010-06-15
> **manny43 said:**
> The idea that we can blindly trust official repositories of open  source code is slowly eroding.
Such an idea has never existed, not in the sane at least. In distributions such as Gentoo that build from source and Arch where there is a pkgbuild file, users are told again and again not to compile them without reading them - Arch even warns you when you run the command!

---

### Post by mickie.kext on 2010-06-15
This is nothing but FUD. Some idiot installed a backdoor on Gentoo server. If you run Gentoo on production server and this stuff happens, then it is your fault.

If it was Ubuntu or RHEL, and if Trojan was distributed by Canonical or Red Hat with a valid GPG key, this story would have relevance. Otherwise, it is just stupid or malicious admin. It is even arguable that story was made on purpose so that haters can link it when they flame FLOSS for "insecurity".

---

### Post by Bachstelze on 2010-06-15
> **mickie.kext said:**
> It is even arguable that story was made on purpose so that haters can link it when they flame FLOSS for "insecurity".

Conspiracy theory much?

---

### Post by Johnsie on 2010-06-15
> This is nothing but FUD

Ubuntu repositories have been hacked before. Calling something 'FUD' doesn't take away the fact that this kind of thing actually can happen.

If you want to pretend that Linux is completely safe then go ahead, but anyone in IT security knows that ignorance is the worst form of security.

---

### Post by Linuxforall on 2010-06-15
WOW! I guess Google, Boeing, US Army all running Linux as well as IBM and other big names all got infected. This is nothing but FUD mongering, after all MS spends $421 million a year to counter Linux, those guys better deliver something substantial.

---

### Post by frodon on 2010-06-15
Social engineering works on any OS, nothing can be done to patch the user.

If you download your apps from trusted sources only or even better if you only use the ubuntu repository then this kind of threats isn't really a concern.

---

### Post by Johnsie on 2010-06-15
The guys running those big systems know and accept Linux has vulnerabilities. They are alot more careful than the average desktop user like yourself. It's called being proactive and sadly many Linux users just stupidly think they are somehow magically safe on their super safe Ubuntu machine.

Ignorance != Security

---

### Post by mickie.kext on 2010-06-15
> **Johnsie said:**
> Ubuntu repositories have been hacked before. 
When was Ubuntu repositories hacked? Any prof?

---

### Post by Shining Arcanine on 2010-06-15
> **cammin said:**
> FreeBSD's ports automatically checksum the downloaded files before compiling. The distinfo file with the checksum it uses for comparison hasn't been changed in 9 months, and included the proper checksum.

Sadly, the package maintainer might have used the checksum for the wrong package in ports. I just checked and while Gentoo Linux's portage does checksums as well, it was checking for the wrong checksum:

[http://bugs.gentoo.org/show_bug.cgi?id=323691](http://bugs.gentoo.org/show_bug.cgi?id=323691)

> **Johnsie said:**
> If there was a backdoor on my system there would be nothing to detect and warn me of this. Linux currently has very few decent security tools and that is quite worrying.

Yes, repositories can be compromised... yes, your browser can be compromised... But sadly people are ignorant to the real security issues facing Linux.

LINUX IS NOT INVULNERABLE

LINUX DOES NOT HAVE A DECENT SET OF SECURITY WARNING TOOLS

Linux was never immune to user stupidity or malicious upstream software.

---

### Post by iponeverything on 2010-06-15
> **Cushie said:**
> Linux infection proves Windows malware monopoly is over, see 

[http://www.zdnet.com/blog/bott/linux-infection-proves-windows-malware-monopoly-is-over/2206#comments](http://www.zdnet.com/blog/bott/linux-infection-proves-windows-malware-monopoly-is-over/2206#comments)

My comment:-
I think not Ed.
Ed, you probably know, but your readers might not, that Linux is NOT an operating system. This operating system is Ubuntu and  there are dozens of IRC clients to download from the official dedicated servers there was no sign of 'Unreal IRC' . So any Ubuntu user who ferrits out where this maverick server is, they must decide themselves that there is a risk. Every Ubuntu (and other Distros) soon find out that it is adviseed to stay with the official servers for the very reason you outlined.
So I believe it is still true to say my system is not vunerable to that trojan. (however I could download the file and pass the file onto someone else who might be stupid enough to run it. Were you?

and it also proves the moon is made of cheese.

---

### Post by 98cwitr on 2010-06-15
"The most interesting part of this discovery?  Windows isn't affected."

Not interesting at all, it was designed for Linux...wooptie-doo

Think about it...it would require you to download the file, untar it and install it. It would have to have major social engineering initiatives which is less probably with Linux users than Windows users on average.

---

### Post by corney91 on 2010-06-15
> **98cwitr said:**
> "The most interesting part of this discovery?  Windows isn't affected."

Not interesting at all, it was designed for Linux...wooptie-doo
Yeah, most interesting part of anything on Windows, to me, is that it's not on Windows - the person who said the quote tries turning it into a OS war and fails :p

---

### Post by ddrichardson on 2010-06-15
> **Johnsie said:**
> Ubuntu repositories have been hacked before. Calling something 'FUD' doesn't take away the fact that this kind of thing actually can happen.
I don't recall them being hacked but would be interested to read more - do you have a link?

I'm also unsure you understand what is meant by FUD - it doesn't mean it isn't based in truth or fact, it means reporting a story in such a way as to spread fear and uncertainty.

This could have occurred on any system, it's negligence on the part of the administrators - the post itself says it:
> We simply did not notice, but should have.
We did not check the files on all mirrors regularly, but should have.
We did not sign releases through PGP/GPG, but should have done so.

> **Johnsie said:**
> If you want to pretend that Linux is completely safe then go ahead, but anyone in IT security knows that ignorance is the worst form of security.
If you mean that overconfidence and complacency is a security risk then you are right. I don't think anyone disputes that but you must also see that for anyone who spends time working with and developing Linux systems, for such events to be explained in terms of "Linux failure" is unfair.

Actually, I would go further than that. To suggest it is a failing in the OS suggests that switching OS would solve the problem, which it wont.

---

### Post by Tristam Green on 2010-06-15
> **boogy9 said:**
> On linux if you know what your doing and take care to not install and run everything will be fine and you'll not have any problems with this kind of things.

Replace "Linux" with "Windows" and you and I have something in common with our attitudes about malware.




@all:  Can I say "in b4 $hills" now?

---

### Post by bodhi.zazen on 2010-06-15
> **Johnsie said:**
> If there was a backdoor on my system there would be nothing to detect and warn me of this. Linux currently has very few decent security tools and that is quite worrying.

Yes, repositories can be compromised... yes, your browser can be compromised... But sadly people are ignorant to the real security issues facing Linux.

LINUX IS NOT INVULNERABLE

LINUX DOES NOT HAVE A DECENT SET OF SECURITY WARNING TOOLS

That is not true, there are a number of outstanding security tools, everything from iptables to tcpwrappers to selinux to apparmor to snort to ossec. And that is the short list.

It sounds as if you are unaware of the tools at your disposal, see:

See :

[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")


[Host-based Intrusion Detection Systems (HIDS)]("http://ubuntuforums.org/showthread.php?t=1477662")

[Network Intrusion Detection Systems (Snort)]("http://ubuntuforums.org/showthread.php?t=1477696") 

Most computer users, in both linux and windows, feel they do not need to pay attention to security or they can not be bothered by it. Up to now Linux has been "secure enough" for all too many people. No one is claiming on this thread that Linux is invulnerable, you need to learn the vulnerabilities and monitor them.

---

### Post by Frak on 2010-06-15
What does this mean? Not that Linux is insecure, that's obvious. There's not such thing as a "secure" Operating System.

What this means is that package repositories are not as safe as they once were. If you infect the package at the source, little to nothing will be done to stop it. Here's the thing, if this got through, how many other packages are infected?

Central Package Management is just as bad as Central Economic Planning; it can be corrupted at the root.

---

### Post by Shining Arcanine on 2010-06-15
The issue here was that upstream did not provide checksums, so no one was verifying that the downloads were the same downloads that were released by upstream. Had upstream provided the correct checksums, this likely would not have happened.

---

### Post by Frak on 2010-06-15
> **Shining Arcanine said:**
> The issue here was that upstream did not provide checksums, so no one was verifying that the downloads were the same downloads that were released by upstream. Had upstream provided the correct checksums, this likely would not have happened.
But it *did* happen. That's a problem with trusting a single-party source. If they make a mistake, everyone who uses that is affected.

---

### Post by bodhi.zazen on 2010-06-15
> **Frak said:**
> What does this mean? Not that Linux is insecure, that's obvious. There's not such thing as a "secure" Operating System.

What this means is that package repositories are not as safe as they once were. If you infect the package at the source, little to nothing will be done to stop it. Here's the thing, if this got through, how many other packages are infected?

Central Package Management is just as bad as Central Economic Planning; it can be corrupted at the root.

That is partially true.

We rely on the sys admins to watch the repos and in this case, by their own admission, their diligence lapsed.

The lesson to be learned is not to take security for granted. I would tend to agree that the vast majority of computer users, both on Windows and Linux, take security for granted. for example even on this thread we have users who do not know what security tools exist for Linux.

---

### Post by McRat on 2010-06-15
This kind of malware pre-dates Linux and the widespread use of the internet.

Sometimes it was even the software developer doing it.  It has occurred in shrink-wrapped software, rarely though.

---

### Post by Frak on 2010-06-15
> **bodhi.zazen said:**
> That is partially true.

We rely on the sys admins to watch the repos and in this case, by their own admission, their diligence lapsed.

The lesson to be learned is not to take security for granted. I would tend to agree that the vast majority of computer users, both on Windows and Linux, take security for granted. for example even on this thread we have users who do not know what security tools exist for Linux.
This is no different than saying "Oh, Central Planning will provide food and goods for all people; Brezhnev apologizes for the shortage, it was due to a lack of diligence from the Planning Authority."

If people have to watch even a central repository for security risks, I see no reason why the means of distribution should not be actively opened up to third parties and recommended in such way.

---

### Post by Bachstelze on 2010-06-15
> **Frak said:**
> 
If people have to watch even a central repository for security risks, I see no reason why the means of distribution should not be actively opened up to third parties and recommended in such way.

They are. You are free to distribute any software you want (licensing questions put aside). Canonical (or any other company), on the other hand, is free to only recommend people download updates from its servers. You are not required to comply.

---

### Post by Frak on 2010-06-15
> **Bachstelze said:**
> They are. You are free to distribute any software you want (licensing questions put aside). Canonical (or any other company), on the other hand, is free to only recommend people download updates from its servers. You are not required to comply.
It goes a bit deeper than that. I'm advocating for a standalone package manager that doesn't tie into any other system. It doesn't provide updates or shared dependencies. That's going outside of what DPMS was designed for (not saying it can't do it, just wasn't designed for that).

---

### Post by Bachstelze on 2010-06-15
> **Frak said:**
> It goes a bit deeper than that. I'm advocating for a standalone package manager that doesn't tie into any other system. It doesn't provide updates or shared dependencies. That's going outside of what DPMS was designed for (not saying it can't do it, just wasn't designed for that).

This is not very relevant to the issue at hand, though. Why would a packaging system be more trustworthy than another?

---

### Post by Frak on 2010-06-15
> **Bachstelze said:**
> This is not very relevant to the issue at hand, though. Why would a packaging system be more trustworthy than another?
You stray away from the flaws that come with a central package authority. Besides that, it would advocate a mental steadfast determination advocating safety. Something that comes with a Central Authority is a sense of complacency that somebody above you is keeping you safe from all the dangers of malware, but these people are only human.

I'm talking about this for desktop systems, not servers. I think repos work great for server systems.

---

### Post by Bachstelze on 2010-06-15
> **Frak said:**
> You stray away from the flaws that come with a central package authority. Besides that, it would advocate a mental steadfast determination advocating safety. Something that comes with a Central Authority is a sense of complacency that somebody above you is keeping you safe from all the dangers of malware, but these people are only human.


That's a valid point, I'm the first to agree that people trust repositories too much (as demonstrated by the Debian OpenSSL fiasco: if it didn't come from Debian, people would probably have been more suspicious of the update that broke it). I don't think abandoning the repositories system would be a very popular idea, though, that's one of the most cited reason for Why Linux Is Better Than Windows™.

---

### Post by Frak on 2010-06-15
> **Bachstelze said:**
> That's a valid point, I'm the first to agree that people trust repositories too much (as demonstrated by the Debian OpenSSL fiasco: if it didn't come from Debian, people would probably have been more suspicious of the update that broke it). I don't think abandoning the repositories system would be a very popular idea, though, that's one of the most cited reason for Why Linux Is Better Than Windows&#8482;.
I guess that's something I like about Linux/UNIX: I can play with it all I want and nobody can tell me otherwise.

Also, I'd say repositories would be one of the things that makes LinuxIsBetterThanWindows&#8482; on the server, but it's far too limiting and assuring on the desktop end.

---

### Post by McRat on 2010-06-15
I believe they are putting the hay in the wrong end of the horse, and until they decide that A/V is not working (it's not), nothing will change.  Malware continues to increase almost as fast as new A/V companies are being formed.  Perhaps billions of dollars are now invested into putting out fires instead of hunting down arsonists.

The whole computing world needs to understand that crooks are a very small segment of society.  They are pretty easy to catch, as most are stupid, unlike what you see on TV.

That same billion dollars could be spent developing a system that will catch the crooks instead of catching their software hacks.

Very unpopular opinion, but I really don't believe anonymity is a "freedom".  If your computer is hooked to my computer and capable of malicious tasks, you shouldn't be guaranteed any privacy.  The minute you connected with others, you surrendered the concept of anonymity.

You would imagine that it would easy to catch whoever broke into Apache or Gentoo.

The two computers were hooked together, each having unique MAC addresses, and the payload had a defined target.

I'll venture a guess that this is not the only app affected, and that it is entirely possible to track down the crooks.  But instead of taking that approach, we'll do more checksums, more AV patches, etc.  We certainly wouldn't want them to Stop Doing It.

---

### Post by Bachstelze on 2010-06-15
> **McRat said:**
> I believe they are putting the hay in the wrong end of the horse, and until they decide that A/V is not working (it's not),

It does, when you use it for what it was designed for (i.e. detect "accidental" viruses, that you get randomly without any malicious intent). Obviously, an A/V alone will not make you secure, but nothing will. You have to combine different tools, that will help you maintain security in different contexts. AV can be one of them.


> The whole computing world needs to understand that crooks are a very small segment of society.  They are pretty easy to catch, as most are stupid, unlike what you see on TV.

The stupid ones, though, are not the ones that make the most damage. Also, those you see on TV *are* the stupid ones. The smart ones don't get caught.

> 
The two computers were hooked together,

No they weren't. There was a lot of routers in-between.

>  each having unique MAC addresses,

MAC addresses are by no means unique and can be very easily modified ([font=monospace]man ifconfig[/font]).

---

### Post by Ichido on 2010-06-20
[http://www.unrealircd.com/](http://www.unrealircd.com/)

Posted by Syzop on June 14, 2010, 3:36 pm EDT
After receiving many questions of what we are doing with regards to the hack incident, here's my reply:

First, we now PGP/GPG sign releases. Our GPG key is [email]releases@unrealircd.com[/email] (0x9FF03937). When downloading UnrealIRCd you will be given instructions on how to verify the integrity of the file.

Second, we're now isolating/shielding the main site from the rest, and making parts unmodifiable, to prevent catastrophes in case of a break-in.

Third, we added several methods of detection when files and other data is modified.

Fourth, we'll only serve the files from the main site for now. While the mirror admins did not have any blame in this, it does mean we only have to protect our own site(s).

And finally we did some other things which I won't mention here.

In short: we've really tightened security since the break-in to make sure this will never ever happen again. As you may understand, we really can't afford a repeat of this incident.

On an unrelated side note,** I find the claims in various media that this security incident indicates that Linux and Open Source cannot be trusted and that Microsoft and closed-software is better really silly. It lacks any foundation.** A hacker, once in, could just as easily have inserted the backdoor in Windows software. **In fact, it is *THANKS* to it being Open Source that this backdoor got noticed, though - I fully agree - much too late.**

NOTE: BOLD format, is mine, and Not the Authors.

---

### Post by yester64 on 2010-06-20
Wow, this article produced some stir really.
Well, the point is from my view, that any system can be breached. And it takes only one weak spot and it happend.
I am not in the camp to say, hey Linux is safe and nothing can happen.

Your biggest security whole is you webbrowser today. And its not just the browser.
If you update your system and something is not signed. What you do? Still update or pass?
What will a normal user do who doesn't really care?

I think if someone want to 'hack' a system, there is always a way to make that happen.
Once linux hits 10% marketshare, things will change.

---

### Post by Shining Arcanine on 2010-06-20
> **Frak said:**
> You stray away from the flaws that come with a central package authority. Besides that, it would advocate a mental steadfast determination advocating safety. Something that comes with a Central Authority is a sense of complacency that somebody above you is keeping you safe from all the dangers of malware, but these people are only human.

I'm talking about this for desktop systems, not servers. I think repos work great for server systems.

While you are right about the issues with a central package authority, you are wrong about two things.

One, this was caused by a communication issue between upstream and downstream, where upstream failed to provide proper hashes to downstream, so they generated them on their own, allowing for a man in the middle attack between the two.

Two, this exploit involves server software.

---

### Post by mickie.kext on 2010-06-20
> **yester64 said:**
> 
Once linux hits 10% marketshare, things will change.

I think this case should show that security has nothing to do with marketshare. Gentoo has very small marketshare compared to other distros. Why should someone attack Gentoo and not RHEL/CentOS or Ubuntu? 

Because Gentoo accept packages without checking first. Gentoo is distro for hobbyists, and by using Gentoo, you take some responsibility to yourself. You can't expect Gentoo developers who are very few and who are all volunteers to do checking of all packages. But Canonical and Red Hat developers must. Debian is also unlikely to let something like this happen because huge developer count and slower release cycle. 

Quick look at packagekit tells me that Fedora doesn't have the package in question: UnrealIRCd. I did not bother to check but I think Ubuntu does not either. If it had, all hell would break lose already.

---

### Post by McRat on 2010-06-20
Last news I have is that data packaged with executable code is the #1 threat:  #1 Adobe formats, #2 MS Office formats.

Trojans embedded in legit software are less common.  They used to be #1 a couple decades ago.

But any computer that can accept data with executables is at risk.  O/S does not come into play other than how much damage can be done.  Ditto for embedded Trojans.

Buffer overflow, hijacked ports, are less common, and those are O/S specific.

But I just know what I read, certainly not a security expert.  The only virus I've personally had came in a Excel spreadsheet about 15 years ago.  I also had the RPC port attack when XP? was first released, but that was just a PITA, and did not do any damage.

---

