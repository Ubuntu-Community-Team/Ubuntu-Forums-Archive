---
title: "Can any one Hack Ubuntu ?"
date: 2012-09-08
forum: Security
---

### Post by sachinvaidya9999 on 2012-09-08
Can any one Hack Ubuntu ?  If no then can you please tell me the reasons>:popcorn:

---

### Post by hakermania on 2012-09-08
Hi there :)

There is an excellent answer for this over here: [http://askubuntu.com/questions/1069/why-is-ubuntu-more-secure-than-windows-or-mac-os-x](http://askubuntu.com/questions/1069/why-is-ubuntu-more-secure-than-windows-or-mac-os-x)

---

### Post by Frogs Hair on 2012-09-08
[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

---

### Post by SeijiSensei on 2012-09-08
Before we get a rash of comments along the lines of "OMG, look at all those vulnerabilities" you need to read the blurbs very carefully.

First, most of them do not expose machines, even ones connected directly to the Internet like servers, to remote exploitation.  There are a couple that have that problem, but the software involved is obscure.

Second, instead most of them can be exploited by a local user on the machine to gain privileges he or she should not have or simply to crash the machine entirely.  If you are the only user of your machine, then those will not affect you.  If you share your machine with other users, say family members, how many of them are sophisticated enough to craft the kinds of attacks required to exploit these vulnerabilities?

Third, some of them concern things like specially-crafted files that can crash the machine or, in some cases, gain root privileges if the file is opened.  Since everyone here knows better than to open random file attachments or follow random links that appear in email, you should not be damaged.  You all do know not to do those sorts of dumb things, right?  Right?

Finally, most serious vulnerabilities are patched quickly by the project's maintainers and the patches distributed via updates to Ubuntu users.  Always install security patches when your system tells you about them.

---

### Post by The Cog on 2012-09-08
Moved to security discussions

---

### Post by wacky_sung on 2012-09-08
In short, all OS is hackable but it is just the intent of how the user run it or uses it services such as running for a server.

---

### Post by Frogs Hair on 2012-09-08
> Before we get a rash of comments along the lines of "OMG, look at all those vulnerabilities" you need to read the blurbs very carefully.

Agreed , simply keeping your system updated eliminates the possibility of being affected by many vulnerabilities. OS security is most dependent on the practices of the user.

---

### Post by mr-woof on 2012-09-10
I agree with the comments above, any os can be hacked if left open on the internet. Update your machine, activate your firewall, configure ssh properly (if needed) and don't use vnc and upnp on your router and you should be ok with a Linux based distro.

---

### Post by Stonecold1995 on 2012-09-11
**Long I know but I put most of what I remember into it.  You can find far more complete/detailed explanations elsewhere.**

Technically yes, but it's difficult to do.  Also remember that most Linux computers that are hacked are servers.  Assuming you have a desktop, you should be very secure.  Because your computer isn't going to be controlled remotely, it by default denies incoming connections like SSH.  This means that no one, even if they know your password, can remotely control your computer.  So you are relatively safe from online attacks.  Note that it is possible for a script on a website to break out of your browser's sandbox, use a privilege escalation exploit, gain root access, and plant a rootkit, (basically pwn you completely), but this is VERY difficult and the average exploit for Linux is patched in two hours (or that's what I heard at least), so it'd take a really, really excellent hacker to do that, and a hacker at that level wouldn't be interested in your computer.

The other way a hacker could get into your computer is through malicious code that they trick you into downloading (aka malware).  Linux is very safe from malware and hackers for many reasons:

1) All programs are by default not run as root, which means they can't change system files.  You'd have to be a fool to run all your programs as root.  ONLY run a program as root if you trust that it won't stab you in the back...

2) Ubuntu's AppArmor can protect a process from changing files it shouldn't (for example, Firefox should never be changing your kernel, or modifying the configuration files of another program, so AppArmor would block that, while allowing Firefox to save files to the downloads directory and edit its own configuration files, etc).

3) The kernel is small and not attached to "userland" applications (applications run by you, like Gedit), so if someone manages to compromise Gedit the worst they could do would be mess up your text files!  On Windows, on the other hand, if someone compromises IE they've essentially compromised the whole system.

4) Windows was designed originally to be single-user, so all programs are given the same permissions by default.  Linux is multi-user, so most programs are run under a user that doesn't have the privileges to do much damage.  This also means you have to enter that user's password to run a program as a different user (like root), instead of simply clicking "yes" or "no" like on Windows.

5) By default Linux has no open ports, except the ones it absolutely needs.  Any extra ports are a sign that something extra is communicating with the outside world, which may be bad.

6) Because Linux is open source, it has thousands of eyes watching it.  Some might say it's insecure because anyone can easily find a vulnerability, and that's true, except for the fact that it's GOOD for someone to find a vulnerability because the average Linux user is more likely to report that vuln and get it patched then they are to use it black-hat style and hack maybe a few computers before someone else notices it, and fixes it.  Windows is entirely closed source, so you just have to hope that those Microsoft employees work faster then the black hat hackers our there.  Without many people monitoring it, Windows bugs become stale, and sometimes Microsoft openly states that they'll *never* fix a certain patch.  Always remember, *bugs come through open Windows.*

7) Linux only runs necessary services, whereas Windows will even run the remote desktop service by default if I'm not mistaken.  Because Linux doesn't run any services it doesn't need, it's both easier to spot rouge services, plus less running services means less methods to break into your computer (and less CPU usage goes to useless services).

8) Linux employs "chroots", which essentially lock a process to a certain directory, and preventing the process from changing files OUTSIDE that directory.  While it is possible to break out of a chroot, it is very hard, and there are methods to harden chroots.

9) Windows has crappy programs installed by default (IE, Notepad, Paint, etc) which means Windows users will have to wade through all the fake/malicious programs on the web till they find a good alternative (e.g. Paint.NET instead of Paint).  Ubuntu on the other hand comes with what it believes to be the best programs at the time (Firefox instead of IE, Gedit/Kate instead of Notepad, Gimp instead of Paint, etc).  Any other programs are all primed to install with "sudo apt-get install packagename" (this lets me install Chromium instantly if I don't like Firefox without having to look for it online).

10) Linux doesn't make things so easy that users lower their guard.  It forces you to think, and get smart with computers.  That will help prevent foolish mistakes like logging in as root and running any program you might come across.  Windows on the other hand does everything for you and you become lazy, making it easier for hackers to control a computer without you noticing.  Of course, Linux doesn't make it too hard either.  If you want hard, install Gentoo.

11) Most Linux programs are installed through the repository, which is basically a long list of URLs for Linux programs and their source code.  It's very hard to get malware approved and put into the repository.  It's hard to trick someone into downloading, compiling, and running malicious script when most users are use to simply running "sudo apt-get install packagename".  See [here]("http://www.gnu.org/fun/jokes/evilmalware.html") for a funny example.

12) Linux was written with the UNIX philosophy in mind, where everything is kept to the minimum to be useful, but not *too* simplistic.  This reduces the number of potential exploits a hacker can use to get in, while simultaneously maximizing system stability and speed.  And even though it's minimalist(ish, each distro is different), it's possible to install nearly anything you want quickly, so no functionality is lost.  Plus, Linux's simplicity makes it easy to spot mistakes and fix them before a hacker gets hold of it.

13) Because there are some many versions of Linux (this is because Linux isn't technically an operating system, it's just a kernel.  Whereas Windows is the Windows NT kernel with Microsoft utilities, Linux distros are the Linux distros with GNU utilities), it's hard to make already compiled, ready to execute binary code that works on every system.  However making the source code available DOES allow it to work on (almost) every Linux system.  This forces programmers to release the source code if they want it to work on more than one distro.  Because of this, any malicious programmer would also have to make their malware open source, and it's VERY hard for malware to hide in plain site (even if you can't understand the source code, SOMEONE will and will quickly alert people to the problem).

14) Updates and security updates are released rapidly, so make sure you keep all your programs up to date.  For every security update that rolls out, that's (generally) one less exploit a hacker can use against you.  In fact, the average time for an exploit to be patched under Linux is about two hours (compared to months/years/never for Windows).

15) Ubuntu (and many other distros) has the option to encrypt your passwords, which means you have to enter a master encryption key to get at it.  So any malware that is able to install itself will have a hard time getting at your PayPal passwords, etc.  Windows on the other hand stores passwords in plaintext, which is dangerous.  Just for an experiment, I infected my own computer with the trojan Darkness (aka Destination Darkness Outcast System, aka Optima bot), and was shocked to see that it was instantly able to grab all my internet passwords, even without Administrator privileges.  And that's with a bot dedicated to denial of service attacks, not stealing passwords!  Imagine how easy it would be to steal someone's passwords with a dedicated password-theft bot like Zeus or SpyEye!  One of the reasons those kinds of trojans aren't made for Linux is that your passwords are encrypted, and inaccessible to a malicious program even if it were to infect you.

16) There are a huge number of security tools available for Linux, from the ultra secure tin-foil hat kinds like the grsecurity kernel patch, to simpler ones like rkhunter and SELinux, and of course Ubuntu's built-in AppArmor.  Windows on the other hand is plagued with fake, useless, scam, or just really bad security software (*cough* Norton *cough*).  And Windows users always expect a program to make their computers invincible and do all the work for them, and so think it's safe to download "hot_pr0n.wmv.exe". ;)

17) Linux hashes your passwords with SHA512, which is a very, very secure hash algorithm.  Even better the hash is salted (that protects it from rainbow tables, which are massive databases of pre-computed hashes that speed up cracking billions of times... or something)  While it does little to protect you if you have a very short password, it is uncrackable if you use a longer password.

18) Linux won't let a user make foolish security decisions easily.  For example, it warns you harshly if you try to set automatic login, or use a short root password.  Windows on the other hand can be made completely insecure without it saying anything to you.

19) The kernel is simply secure.  It was built with simplicity, speed, stability, and security in mind, and it blocks as many exploits as it can, because access to the kernel means instant game over.  Plus, the kernel can be made even more secure with patches, like the *immensely* secure grsecurity patch to specific vulnerability-targeting patches like TRESOR (TRESOR Runs Encryption Securely Outside RAM, a wonderful patch that stores AES states in the CPU registers instead of the RAM, completely mitigation cold-boot attacks against encrypted drives while even increasing performance, although it only works on CPUs that support the AES-NI instruction set).

20) Ubuntu does not use Internet Explorer.

tl;dr
There are many ways Ubuntu (and Linux in general) can be hacked, but there are far more obstacles to this than their are exploits.  Unless you go willy nilly downloading everything you find and *purposefully* reducing security level, you'll be fine.  I've never been hacked or gotten malware, and I don't know anyone who's gotten their Linux desktops infected/hacked.

You are safe.  Just avoid foolish choices and Ubuntu will do the rest.

---

### Post by dodo3773 on 2012-09-11
@Stonecold1995

Please throw a couple of carriage returns in there if you don't mind (preferably between the new items "-"). My eyes can't handle that. Love your sig by the way. Man I miss demonoid. 

@sachinvaidya9999

It really depends what you mean. Your question is very vague. If you mean hack as in edit the source code for your system then yes you are free to do so. If you actually mean s/hack/crack/ then the answer again would be it depends. Don't run internet facing services / daemons, use pax, use selinux, etc..etc.. There are a lot of things you can do if you are really worried about it. My current understanding of what systems are most secure is this (this is subject to chance and based solely of my opinion (from most secure to least (mobile devices not included))):

BSD -> GNU/Linux -> Mac -> Windows

The assumption is that you are running a default mainstream distro for GNU/Linux (not a hardened self made source distro).

---

### Post by Stonecold1995 on 2012-09-11
> **dodo3773 said:**
> Please throw a couple of carriage returns in there if you don't mind (preferably between the new items "-"). My eyes can't handle that.
Done.

> **dodo3773 said:**
> BSD -> GNU/Linux -> Mac -> Windows

The assumption is that you are running a default mainstream distro for GNU/Linux (not a hardened self made source distro).
Exactly.  BSD (particularly OpenBSD) is the most secure system out of the box, but Hardened Gentoo (or really any distro with a grsecurity-patched kernel) is far more secure than BSD, but only because BSD doesn't have equivalent patches.  BSD is also more server-oriented so naturally has less pre-installed features, and that naturally makes it more secure.

---

### Post by dodo3773 on 2012-09-11
> **Stonecold1995 said:**
> Done.


Exactly.  BSD (particularly OpenBSD) is the most secure system out of the box, but Hardened Gentoo (or really any distro with a grsecurity-patched kernel) is far more secure than BSD, but only because BSD doesn't have equivalent patches.  BSD is also more server-oriented so naturally has less pre-installed features, but that makes it more secure.

Thanks. I agree with what you had to say. I almost fell over laughing when I read this:

> 
Ubuntu does not use Internet Explorer


hahaha. Yep. Even if that was the only thing it did different it would still win hahahahaha. You should add that to your sig. Classic.

---

### Post by mike acker on 2012-09-11
Suggested reading [http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

the essay is a little dated but very insightful .

the thing that concerns me most at the moment is java-script. i have to find out what functions are available to the java-script programmer . i'm thinking i ain't going to be happy

---

### Post by Hungry Man on 2012-09-11
Ubuntu isn't very security focused. 64bit binaries are still shipping sans PIE and, while NX is used by default for shipped binaries, there's nothing like execshield. It also ships with a lot of software/ services installed. 

It's not *insecure* or anything. It's still Linux - you can secure it with a bit of work. But it's nothing compared to hardened gentoo and other distros are shipping with 64bit PIE now.

---

### Post by rookcifer on 2012-09-11
> **Hungry Man said:**
> Ubuntu isn't very security focused. 64bit binaries are still shipping sans PIE and, while NX is used by default for shipped binaries, there's nothing like execshield. It also ships with a lot of software/ services installed. 

Execshield accomplishes nothing NX doesn't.  It was written to emulate NX on 32 bit platforms that didn't have it built into the hardware.  This is all native in the kernel now, thus making Execshield unneeded in most cases.

> It's not *insecure* or anything. It's still Linux - you can secure it with a bit of work. But it's nothing compared to hardened gentoo and other distros are shipping with 64bit PIE now.

As for PIE's, Ubuntu ships with the most vulnerable services compiled with PIE support (and on 64 bit systems as well). Things like CUPS, udev, dhclient, ntpd, sshd, as well as the browsers.  I think this is fine for a desktop box.  

I think Ubuntu is among the best of all binary mainstream distros when it comes to security.

---

### Post by VishnuNJ on 2012-09-11
Yes.. But linux is safer than Windows and Macs.. 

In fact 99.99% of windows virus can be viewed and deleted using linux

---

### Post by orange2k on 2012-09-11
I am concerned with the ease you can reset the login password on ubuntu. There are quite a few tutorials on the internet on how to reset the login password and thus accessing everything on a users hard drive including the encrypted home folder. 

Just take a look here: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

How do I protect my Ubuntu system from something like this?

---

### Post by rookcifer on 2012-09-11
> **orange2k said:**
> I am concerned with the ease you can reset the login password on ubuntu. There are quite a few tutorials on the internet on how to reset the login password and thus accessing everything on a users hard drive including the encrypted home folder. 

Just take a look here: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

How do I protect my Ubuntu system from something like this?

I prefer to use full disk encryption.  To do that you need to use the alternate installer CD.  It doesn't have any problems with password resets.

---

### Post by CharlesA on 2012-09-11
> **VishnuNJ said:**
> Yes.. But linux is safer than Windows and Macs.. 

In fact 99.99% of windows virus can be viewed and deleted using linux

Any OS is as secure as you make it.

> **rookcifer said:**
> I prefer to use full disk encryption.  To do that you need to use the alternate installer CD.  It doesn't have any problems with password resets.

That would be the best way to protect your data imo. I believe you would just be prompted for the encryption key before the partition/drive is mounted.

---

### Post by orange2k on 2012-09-11
> **rookcifer said:**
> I prefer to use full disk encryption.  To do that you need to use the alternate installer CD.  It doesn't have any problems with password resets.

Nice to know that...
But then whats the point of having a normal installation with a encrypted home folder (thats the option you can choose whe installing Ubuntu) if you are not warned that it doesn't actually protect the data in the home folder from someone who knows how to reset the login password...

And I thaught that my encrypted home folder was safe...:mad:

---

### Post by CharlesA on 2012-09-11
> **orange2k said:**
> Nice to know that...
But then whats the point of having a normal installation with a encrypted home folder (thats the option you can choose whe installing Ubuntu) if you are not warned that it doesn't actually protect the data in the home folder from someone who knows how to reset the login password...

And I thaught that my encrypted home folder was safe...:mad:
Cuz it is still encrypted and couldn't be read from a livecd?

Don't you still need the encryption key you created during install?

---

### Post by orange2k on 2012-09-11
> **CharlesA said:**
> Cuz it is still encrypted and couldn't be read from a livecd?

Don't you still need the encryption key you created during install?

I'm not sure, but doesn't the ability to change the users login password give you access to the encrypted home folder even without the encryption key?

---

### Post by orange2k on 2012-09-11
Oh I see, now that I've read this I feel a little safer now...
[http://askubuntu.com/questions/120206/encrypted-home-forgotten-password-but-no-passphrase](http://askubuntu.com/questions/120206/encrypted-home-forgotten-password-but-no-passphrase)

---

### Post by Hungry Man on 2012-09-11
> **rookcifer said:**
> Execshield accomplishes nothing NX doesn't.  It was written to emulate NX on 32 bit platforms that didn't have it built into the hardware.  This is all native in the kernel now, thus making Execshield unneeded in most cases.



As for PIE's, Ubuntu ships with the most vulnerable services compiled with PIE support (and on 64 bit systems as well). Things like CUPS, udev, dhclient, ntpd, sshd, as well as the browsers.  I think this is fine for a desktop box.  

I think Ubuntu is among the best of all binary mainstream distros when it comes to security.
Hence why I said that execshield isn't a big deal as Ubuntu ships with all NX enabled binaries by default. Where execshield is nice is for forcing binaries that don't use it. This is rarer these days.

As for PIE, all services are vulnerable. There's really no excuse for not at least having a test build for it - there shouldn't be any performance hit on 64bit and tons of services (pulseaudio for example, other root services like rsyslogd) aren't running PIE. While they have it enabled in really critical services like dhclient it's still important for it to be used in others.

---

### Post by rookcifer on 2012-09-12
> **Hungry Man said:**
> Hence why I said that execshield isn't a big deal as Ubuntu ships with all NX enabled binaries by default. Where execshield is nice is for forcing binaries that don't use it. This is rarer these days.

According to checksec, every running process on my system has NX enabled, so I think we're good there.

> As for PIE, all services are vulnerable. There's really no excuse for not at least having a test build for it - there shouldn't be any performance hit on 64bit and tons of services (pulseaudio for example, other root services like rsyslogd) aren't running PIE. While they have it enabled in really critical services like dhclient it's still important for it to be used in others.

It's a lot of work for some services.  Pulseaudio is a monster blob of complicated code.  According to checksec, PA has everything enabled but PIE (it has Full RELRO, NX and a canary).

I am sure the Ubuntu security team would like to have everything compiled with full PIE at some point (I think this is their goal), but it will take a little time.

IIRC, some of the PaX code is going to be merged to the mainlaine kernel one of these days (or at least it has been talked about).  That should help strengthen the ASLR of the vanilla kernel a bit.  Right now, the default ASLR built into the vanilla kernel is already a bit stronger than what Windows offers.

---

### Post by Hungry Man on 2012-09-12
> IIRC, some of the PaX code is going to be merged to the mainlaine kernel one of these days (or at least it has been talked about). That should help strengthen the ASLR of the vanilla kernel a bit. Right now, the default ASLR built into the vanilla kernel is already a bit stronger than what Windows offers.

It's been talked about for a long long time. Pretty much everything starts off in PaX though and ends up mainline under another name (and often a faulty implementation...).

Windows ASLR has a big weakness in that VirtualAllocEx() is not randomized whereas all mmap() is randomized on Linux. In terms of entropy Windows would probably be ahead but if you use PaX/Grsecurity you can up the entropy and also enable some other features that prevent ASLR bruteforcing.

But only the randomized mmap is there by default.

> It's a lot of work for some services. Pulseaudio is a monster blob of complicated code. According to checksec, PA has everything enabled but PIE (it has Full RELRO, NX and a canary).

Pretty sure other distros like Fedora have it enabled. Can't be sure/ haven't checked but after Spender showed that fun exploit a while back there was some buzz for a bit that probably spurred it.

It's been "talked about" for a long time. It would be nice if they actually had test builds out. I haven't been tracking the progress, for all I know they're working on it, but what I do know is that it's not mainline yet.

---

