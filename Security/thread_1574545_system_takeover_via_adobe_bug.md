---
title: "system takeover via adobe bug??"
date: 2010-09-14
forum: Security
---

### Post by xzero1 on 2010-09-14
If this is true for Linux, which I doubt, what is the os mechanism that allows it? 
If it is not true why should Adobe be allowed to state such a claim?

[http://www.adobe.com/support/security/advisories/apsa10-03.html]("http://www.adobe.com/support/security/advisories/apsa10-03.html")

---

### Post by CharlesA on 2010-09-14
Flash would be running with the same privlages as the brower, which is run with same privlages as the user. Worst case is that it'll wipe out yer home directory.

Check out AppArmor.

You can check [here]("http://kb2.adobe.com/cps/155/tn_15507.html") to see what version of flash you are running.

---

### Post by xzero1 on 2010-09-14
> **CharlesA said:**
> Flash would be running with the same privlages as the brower, which is run with same privlages as the user. Worst case is that it'll wipe out yer home directory.

Check out AppArmor.

You can check [here]("http://kb2.adobe.com/cps/155/tn_15507.html") to see what version of flash you are running.

So why is adobe *allowed* to state what they do in the case of Linux. Linux *has* a better security model, but you would not know it from the bulletin.

---

### Post by endotherm on 2010-09-14
all they are saying, is that the linux version of adobe is vulnerable to this type of attack, and that that type of vulnerability lends itself to exploits that might be able to perform this kind of takeover. so far as I am aware, the only exploits that targets this vuln are windows based, but if someone was able to write a linux exploit, then we would be vulnerable.

there are at least 2 active 0-day exploits for acrobat in the wild, and at least this one  for flash, but all three focus on exploiting windows. for now...

---

### Post by bodhi.zazen on 2010-09-14
> **xzero1 said:**
> So why is adobe *allowed* to state what they do in the case of Linux. Linux *has* a better security model, but you would not know it from the bulletin.

I am not sure what you are asking. Adobe is telling you they are aware of this vulnerability and the vulnerability affects Linux.

Many people suggest you not use Flash until there is a fix to the vulnerability, you can choose what to do with the information.

There are opensource alternates to flash, gnash and lightspark.

[http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)

[https://launchpad.net/lightspark](https://launchpad.net/lightspark)

[https://launchpad.net/~sssup/+archive/sssup-ppa](https://launchpad.net/~sssup/+archive/sssup-ppa)

[https://launchpad.net/lightspark/+download](https://launchpad.net/lightspark/+download)

---

### Post by endotherm on 2010-09-14
remember, there is a differance between a vulnerability and an exploit. the vulnerability exists in the linux versions of the adobe software as it does in the windows version. the differance is that there is an exploit in the wild for the windows platform that uses this vulnerability, whereas there doesn't appear to be an exploit for the linux platform, despite the fact that the adobe software is vulnerable. to attack your system, the attacker must have both an vulnerability, and an exploit. either is worthless without the other.

---

### Post by jbrown96 on 2010-09-14
Adobe's response indicates that it could "potentially allow an attacker to take control of the affected system." That means that an attacker could bypass account controls and get root privileges. Hence, the whole "critical" part. 

xzero1,

While people love to say that Linux has a better security model than Linux, that hasn't been true since the Win 9x days. Especially, since Vista, Windows has some very effective protections. Base Linux, and particularly Ubuntu, do not have good account protections. The "octal" file permissions are about the only thing protecting users on Ubuntu. There are some profiles for AppArmor, but AppArmor is not secure by default since it does have mandatory access controls. Each application needs its own profile created, and Ubuntu doesn't have a way of distributing profiles.
The situation changes if you have SELinux+ACLs enabled, but I wouldn't even go so far as to say that it is better than Windows, per se.

Many of Linux's "advantages" are repeated memes from years ago, and they frequently don't hold any water.

---

### Post by bodhi.zazen on 2010-09-14
> **jbrown96 said:**
> Adobe's response indicates that it could "potentially allow an attacker to take control of the affected system." That means that an attacker could bypass account controls and get root privileges. Hence, the whole "critical" part. 

xzero1,

While people love to say that Linux has a better security model than Linux, that hasn't been true since the Win 9x days. Especially, since Vista, Windows has some very effective protections. Base Linux, and particularly Ubuntu, do not have good account protections. The "octal" file permissions are about the only thing protecting users on Ubuntu. There are some profiles for AppArmor, but AppArmor is not secure by default since it does have mandatory access controls. Each application needs its own profile created, and Ubuntu doesn't have a way of distributing profiles.
The situation changes if you have SELinux+ACLs enabled, but I wouldn't even go so far as to say that it is better than Windows, per se.

Many of Linux's "advantages" are repeated memes from years ago, and they frequently don't hold any water.

I respectfully disagree with most of this post.

Ubuntu can easily distribute apparmor profiles, see the package apparmor-profiles.

[http://packages.ubuntu.com/lucid/apparmor-profiles](http://packages.ubuntu.com/lucid/apparmor-profiles)

Also the survival time of Windows is poor

[http://news.cnet.com/2100-7349_3-5313402.html](http://news.cnet.com/2100-7349_3-5313402.html)

[http://itknowledgeexchange.techtarget.com/security-corner/whats-your-systems-survival-time/](http://itknowledgeexchange.techtarget.com/security-corner/whats-your-systems-survival-time/)

The second site lists the survival time as 78 minutes.

> August 7, 2010 (5 days after release of out-of-cycle patch for .lnk vulnerability) - 78 minutesAlthough both Windows and Ubuntu out of the box can be hardened, Ubuntu is much more secure, out of the box.

Linux has a number of security features beyond permissions on the file system, here is a discussion of some of the current considerations (the list is by no means complete)

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

See (search) pwn2own 2009 - Only Ubuntu was left (Windows and OSX were both cracked).

---

### Post by xzero1 on 2010-09-14
To clarify

From the bulletin:
 > This vulnerability (CVE-2010-2884) could cause a crash and potentially allow an attacker to take control of the affected system. 

But doesn't CharlesA have a point:
> Flash would be running with the same privlages as the brower, which is run with same privlages as the user. Worst case is that it'll wipe out yer home directory.

So the question is could this vulnerability cause a crash [the kernel] and potentially allow an attacker to take control of the system [without su privileges]? *How??* Wouldn't this be a kernel flaw and a hole in linux security
*in general* without regard to any flash problem.

---

### Post by JK3mp on 2010-09-14
If you havn't gotten your answer by now.... NO. It can't. =) And as stated it is very unlikely you'll see an exploit in the wild, the vulnerabilities still there for now, but with a limited time till its patched hackers won't waste time attacking(and building exploits for) linux machines when they can be attacking the more popular windows machines in the due time.

---

### Post by endotherm on 2010-09-14
> **xzero1 said:**
> To clarify

From the bulletin:
 

But doesn't CharlesA have a point:


So the question is could this vulnerability cause a crash [the kernel] and potentially allow an attacker to take control of the system [without su privileges]? *How??* Wouldn't this be a kernel flaw and a hole in linux security
*in general* without regard to any flash problem.
all code runs "through" the kernel (as it can't process on hardware without it), so theoretically any crash can have implications for the kernel. the kernel will attempt to isolate the crash, but more often than not, the crash itself is all the attacker needs. in fact, overflow attacks use the kernels methods for stacking executables against itself by definition.  at that point, they can execute arbitrary code as though it were associated with the crashed process. if that code contains escalation of privilege exploits, then it is possible that the attacker can do more, but until they do, the code is restricted to damaging the subsystems that the user can directly access.

linux attempts to protect itself with a series of tiny locks, that when put together build into one horkin big system of fences that an attacker must cut through in order to really execute nastiness.

---

### Post by bodhi.zazen on 2010-09-14
> **xzero1 said:**
> To clarify

From the bulletin:
 

But doesn't CharlesA have a point:


So the question is could this vulnerability cause a crash [the kernel] and potentially allow an attacker to take control of the system [without su privileges]? *How??* Wouldn't this be a kernel flaw and a hole in linux security
*in general* without regard to any flash problem.

I am not sure about the details of this particular security exploit.

As endotherm pointed out, there is a difference between a reported vulnerability and an actual exploit.

Most of the vulnerabilities are potential exploits and are generally termed "arbitrary code". Arbitrary code is exactly that, any code or command the cracker wishes to run, from bash to su to sudo.

See also :

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

From those vulnerabilities you can follow the links

[http://www.ubuntu.com/usn/usn-975-1](http://www.ubuntu.com/usn/usn-975-1)

You will need to track down the reports.

[http://en.wikipedia.org/wiki/Vulnerability_%28computing%29](http://en.wikipedia.org/wiki/Vulnerability_%28computing%29)

[http://www.cve.mitre.org/](http://www.cve.mitre.org/)

---

### Post by bodhi.zazen on 2010-09-14
> **JK3mp said:**
> If you havn't gotten your answer by now.... NO. It can't. =) And as stated it is very unlikely you'll see an exploit in the wild, the vulnerabilities still there for now, but with a limited time till its patched hackers won't waste time attacking(and building exploits for) linux machines when they can be attacking the more popular windows machines in the due time.

Depends on the cracker and the system to be exploited. What you say may be true of the so called "script kiddies" but this thinking does not apply to the big cheese.

Security through obscurity is no security at all and many of the big (financial) targets use *nix or a variant of BSD.

---

### Post by xzero1 on 2010-09-14
> **endotherm said:**
> all code runs "through" the kernel (as it can't process on hardware without it), so theoretically any crash can have implications for the kernel. the kernel will attempt to isolate the crash, but more often than not, the crash itself is all the attacker needs. in fact, overflow attacks use the kernels methods for stacking executables against itself by definition.  at that point, they can execute arbitrary code as though it were associated with the crashed process. if that code contains escalation of privilege exploits, then it is possible that the attacker can do more, but until they do, the code is restricted to damaging the subsystems that the user can directly access.

linux attempts to protect itself with a series of tiny locks, that when put together build into one horkin big system of fences that an attacker must cut through in order to really execute nastiness.

That explains it well.:)

---

### Post by OpSecShellshock on 2010-09-14
The vulnerability exists in Flash on all platforms because it's in the part of the application that isn't platform-specific. Given that, it is possible that a successful exploit could also affect all versions. Basically a successful exploit causes Flash to crash, which could then lead the the execution of additional code. It's the additional code that could be used to "potentially take control" of a system, but that code is very much platform-specific and could be anything from a download of further content to the installation of something or whatever.  It still has to be running in the context of a user with sufficient privileges to run the code, though (regardless of the OS).

---

### Post by bodhi.zazen on 2010-09-14
> **OpSecShellshock said:**
> The vulnerability exists in Flash on all platforms because it's in the part of the application that isn't platform-specific. Given that, it is possible that a successful exploit could also affect all versions. Basically a successful exploit causes Flash to crash, which could then lead the the execution of additional code. It's the additional code that could be used to "potentially take control" of a system, but that code is very much platform-specific and could be anything from a download of further content to the installation of something or whatever.  It still has to be running in the context of a user with sufficient privileges to run the code, though (regardless of the OS).

Very well put.

---

### Post by jbrown96 on 2010-09-14
> **bodhi.zazen said:**
> I respectfully disagree with most of this post.

Ubuntu can easily distribute apparmor profiles, see the package apparmor-profiles.

[http://packages.ubuntu.com/lucid/apparmor-profiles](http://packages.ubuntu.com/lucid/apparmor-profiles)

Also the survival time of Windows is poor

[http://news.cnet.com/2100-7349_3-5313402.html](http://news.cnet.com/2100-7349_3-5313402.html)

[http://itknowledgeexchange.techtarget.com/security-corner/whats-your-systems-survival-time/](http://itknowledgeexchange.techtarget.com/security-corner/whats-your-systems-survival-time/)

The second site lists the survival time as 78 minutes.

Although both Windows and Ubuntu out of the box can be hardened, Ubuntu is much more secure, out of the box.

Linux has a number of security features beyond permissions on the file system, here is a discussion of some of the current considerations (the list is by no means complete)

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

See (search) pwn2own 2009 - Only Ubuntu was left (Windows and OSX were both cracked).

I don't want to get into a long debate on the internet. It's not worth all the typing. 
The links about Windows are either very old (the first link) or use extremely outdated versions (Win XP SP2). 

Those Ubuntu security policies are mostly ("no ports open" is the exception) explanations on why security restrictions were relaxed. Things like world readable home directories is a terrible default security policy. 

The pwn2own contest is not a very good comparison of platform security. No OS was vulnerable (day one), and the vulnerability for Windows (Flash) would have worked equally well against Linux. However, the attacker wins the hardware that he "pwns," and the Windows hardware was better. Furthermore, an exploit can only be used once. It only seems logical that Ubuntu would last the longest because there was literally no interest in hacking the platform. Linux hasn't even been included in the contest for at least two years.  

Privilege escalation on Linux is one of the worst parts of the OS. Keyloggers are a very real threat in Linux because there's no secure way to enter a password; whereas, Windows' UAC protects against keyloggers. On many distros (not including Ubuntu), GUI apps that request additional privileges ask for the root password instead of a user's sudo password. It's stuff like this that is just asking to be exploited.

---

### Post by JK3mp on 2010-09-14
> **bodhi.zazen said:**
> Depends on the cracker and the system to be exploited. What you say may be true of the so called "script kiddies" but this thinking does not apply to the big cheese.

Security through obscurity is no security at all and many of the big (financial) targets use *nix or a variant of BSD.

Yeah but speaking of a vulnerability in an application that effects mostly desktop/client systems. Windows is the most targeted CLIENT system. And correct that *nix systems are highly set target for server based attacks. But this vulnerability is more targeted at the user end. And nahh script kiddies use other exploits don't write there own. So not really correct usage there(to me anywho). Since we are talking about those who are WRITING the exploit. And even researchers are more likely to write exploits for the windows based system over linux cause of its popularity and its slightly easier remote execution. (aside from like DEP and ASLR but theres bypass for that too). But i do agree that security  through obscurity is still no security. But still less people attacking the obscure. Lets see would i feel safer being beaten by 10 people.... or 10000?(i only have one sheild lol) Get me? Lol sorry long and confusing.... Im tired.

---

### Post by bodhi.zazen on 2010-09-14
@ [jbrown96]("http://ubuntuforums.org/member.php?u=304717") :

I think we shall have to agree to disagree.

The survival time of 78 minutes is from august 7, 2010. Do you have anything more recent to refute that ?

@[JK3mp]("http://ubuntuforums.org/member.php?u=762367") :

I think we are basically on the same page. Again it depends a bit on the target system and purpose of cracking it.

---

### Post by JK3mp on 2010-09-14
> **OpSecShellshock said:**
> The vulnerability exists in Flash on all platforms because it's in the part of the application that isn't platform-specific. Given that, it is possible that a successful exploit could also affect all versions. Basically a successful exploit causes Flash to crash, which could then lead the the execution of additional code. It's the additional code that could be used to "potentially take control" of a system, but that code is very much platform-specific and could be anything from a download of further content to the installation of something or whatever.  It still has to be running in the context of a user with sufficient privileges to run the code, though (regardless of the OS).

Just saw this lol. Same, very well put.

@bodhi.zazen:

I agree to agree. lol

---

### Post by jbrown96 on 2010-09-14
> **bodhi.zazen said:**
> @ [jbrown96]("http://ubuntuforums.org/member.php?u=304717") :

I think we shall have to agree to disagree.

The survival time of 78 minutes is from august 7, 2010. Do you have anything more recent to refute that ?


The problem is that link did not say which version(s) of Windows were used. Yes, I believe that a newly installed Windows XP SP2 machine might only last 78 minutes. 
I seriously doubt that a newly installed Windows 7 system would face such problems.

---

### Post by bodhi.zazen on 2010-09-14
> **jbrown96 said:**
> The problem is that link did not say which version(s) of Windows were used. Yes, I believe that a newly installed Windows XP SP2 machine might only last 78 minutes. 
I seriously doubt that a newly installed Windows 7 system would face such problems.

Linky ?

From the link I gave you, one line up :

> October 29, 2009 (1 week after release of Windows 7) - 74 minutes

---

### Post by movieman on 2010-09-14
> **jbrown96 said:**
> Those Ubuntu security policies are mostly ("no ports open" is the exception) explanations on why security restrictions were relaxed. Things like world readable home directories is a terrible default security policy.

Not unless you're expecting to be attacked. Yes, in principle you're safer if other users can't read your files, but for a home system it's a pain... and if you're serious about protecting your files you'll have encrypted them anyway.

Now, exporting all my files -- and writeable, not just readable -- to any computer on the network as Windows 7 does is a truly terrible default security policy. Frankly, I was appalled when I discovered it was doing that, my brain nearly melted at the insane stupidity it demonstrated.

> No OS was vulnerable (day one), and the vulnerability for Windows (Flash) would have worked equally well against Linux.

Not mine. Flash is wrapped in Apparmor and can hardly do anything other than read and write its own files.

> It only seems logical that Ubuntu would last the longest because there was literally no interest in hacking the platform. Linux hasn't even been included in the contest for at least two years.

LOL. Linux runs many of the most important servers on the planet... you really think 'there's literally no interest in hacking the platform'?

> Keyloggers are a very real threat in Linux because there's no secure way to enter a password; whereas, Windows' UAC protects against keyloggers.

Why would I need a keylogger for UAC? It puts up a box saying 'Do you want to allow Frobitz service to access your hard disk' and I think 'what the heck is Frobitz service, what parts of my disk is it trying to access and why would it want to do so?' and probably press 'Yes', because those questions are impossible for the average user to answer.

UAC isn't such a bad idea, but the implementation is appalling.

> On many distros (not including Ubuntu), GUI apps that request additional privileges ask for the root password instead of a user's sudo password.

If you can sudo to run arbitary programs there's absolutely no difference between a root password and a user password.

> It's stuff like this that is just asking to be exploited.

LOL. On my CentOS box there are two things that ask for my root password: the update manager and Wireshark. If a box appears any other time then it's clearly a fake.

On Windows I get UAC boxes several times a day, from completely random programs. Who needs to use a keylogger when you can just pop up a UAC box and half the Windows users will click 'OK'?

---

### Post by CharlesA on 2010-09-14
> **movieman said:**
> 
Now, exporting all my files -- and writeable, not just readable -- to any computer on the network as Windows 7 does is a truly terrible default security policy. Frankly, I was appalled when I discovered it was doing that, my brain nearly melted at the insane stupidity it demonstrated.

Are you talking about the homegroup thing?

> On Windows I get UAC boxes several times a day, from completely random programs. Who needs to use a keylogger when you can just pop up a UAC box and half the Windows users will click 'OK'?

I must be doing something wrong then. The only time I get UAC prompts is if/when I am installing programs or trying to run something in compatibility mode/as administrator. *shrug*

---

### Post by movieman on 2010-09-14
> **CharlesA said:**
> Are you talking about the homegroup thing?

No idea; after I got my new laptop I logged onto my old XP box to copy some files over and discovered that the XP box could write to any of my files on the laptop without Windows 7 ever asking me if I actually wanted to share every single file on the system.

On the old XP laptop I manually exported a couple of directories read-only and that was all anyone could access, this one has every single user directory exported writeable with no user intervention. I really don't know of a strong enough superlative to explain how insane that is.

---

### Post by CharlesA on 2010-09-14
> **movieman said:**
> No idea; after I got my new laptop I logged onto my old XP box to copy some files over and discovered that the XP box could write to any of my files on the laptop without Windows 7 ever asking me if I actually wanted to share every single file on the system.

On the old XP laptop I manually exported a couple of directories read-only and that was all anyone could access, this one has every single user directory exported writeable with no user intervention. I really don't know of a strong enough superlative to explain how insane that is.

Ah. How did you connect, and were the usernames/passwords the same? I'm curious now, since I haven't seen that sort of thing, outside of connecting to an administrative share (C$ D$ E$ etc).

---

### Post by movieman on 2010-09-14
> **CharlesA said:**
> Ah. How did you connect, and were the usernames/passwords the same?

Yeah, they're the same on both machines; I believe that's required for Windows file sharing?

---

### Post by CharlesA on 2010-09-14
> **movieman said:**
> Yeah, they're the same on both machines; I believe that's required for Windows file sharing?

Technically, they can be different usernames/passwords, but you'll be prompted for the username and password of a valid user on the machine you are trying to connect to.

---

### Post by rookcifer on 2010-09-14
> **jbrown96 said:**
> Adobe's response indicates that it could "potentially allow an attacker to take control of the affected system." That means that an attacker could bypass account controls and get root privileges. Hence, the whole "critical" part. 

Not really.  It depends on what privilege level adobe Flash is running at.  It doesn't run as root, so it's doubtful the attacker could get root.

> While people love to say that Linux has a better security model than Linux, that hasn't been true since the Win 9x days. 

I would add Win XP in there too.

> Especially, since Vista, Windows has some very effective protections.

Linux has those same protections (and more) and has had them before Vista ever came out.

> Base Linux, and particularly Ubuntu, do not have good account protections. 

Eh?  Define "account protections."

> The "octal" file permissions are about the only thing protecting users on Ubuntu.

That is the first line of defense but it's not the only defense (Linux has NX/ASLR/RELRO/stack smashing protections, etc.).

> There are some profiles for AppArmor, but AppArmor is not secure by default since it does have mandatory access controls.

Your quote doesn't really make sense.  Did you mean to say because it "*doesn't* have mandatory access controls?"  If so, you're wrong.  AppArmor ***is*** a MAC.

> Each application needs its own profile created, and Ubuntu doesn't have a way of distributing profiles.

Yes they do.  There are a number of profiles in the repos and each Ubuntu distro comes with a Firefox profile.

> The situation changes if you have SELinux+ACLs enabled, but I wouldn't even go so far as to say that it is better than Windows, per se.

Windows security is nothing compared to a system properly confined by SELinux or PaX with Grsecurity.  I would put Hardened Gentoo against Windows 7 any day.

> Many of Linux's "advantages" are repeated memes from years ago, and they frequently don't hold any water.

I think some exaggerate it, yes, and I think some think Linux is invulnerable.  But the truth is Linux (and other Unices) security is better.  The proof is in the havoc malware causes in the Windows world compared to Linux (it's unheard of even though there are millions of Linux desktops out there and even more servers).

---

### Post by JK3mp on 2010-09-16
> **CharlesA said:**
> 
I must be doing something wrong then. The only time I get UAC prompts is if/when I am installing programs or trying to run something in compatibility mode/as administrator. *shrug*


1st- lol +1

2nd- I think this threads going a little beyond and a little off topic.

3rd-No ones responded in ova a day. Wtf am i doing posting?? Ah well i've already started Im hitting post. =)

EDIT: 
@Rookcifer And yeah linux has had all those for quite a few years before windows. Then again ASLR is rather weak in general(on both systems) and so is NX. Along with DEP are becoming easily and commonly beaten.

---

