---
title: "Virus, spyware in Ubuntu???"
date: 2008-04-06
forum: Security Discussions
---

### Post by songuke on 2008-04-06
I dunno any of you encountered strange behaviours like me in Ubuntu 7.10. My problem  is that when I leave it idle, the terminal and browser are popped up automatically, opening some websites related to Naruto. In the terminal, I saw the command like "Naruto remix video's" executed itself. 

I thought I got some malwares. At the moment, I cannot find a way to get rid of them. Could you please help? :(

Thanks in advance.

---

### Post by insineratehymn on 2008-04-06
I can't say I've ever seen it, I've heard of linux viruses/malware, but never had/ nor see anyone who has/ one. 

What have you done to try to find the root of this problem?

---

### Post by bodhi.zazen on 2008-04-06
Thread moved to Security section.

---

### Post by x3roconf on 2008-04-06
> **songuke said:**
> I dunno any of you encountered strange behaviours like me in Ubuntu 7.10. My problem  is that when I leave it idle, the terminal and browser are popped up automatically, opening some websites related to Naruto. In the terminal, I saw the command like "Naruto remix video's" executed itself. 

I thought I got some malwares. At the moment, I cannot find a way to get rid of them. Could you please help? :(

Thanks in advance.

i dont believe your story :lolflag:

---

### Post by netlogic on 2008-04-06
> **songuke said:**
> I dunno any of you encountered strange behaviours like me in Ubuntu 7.10. My problem  is that when I leave it idle, the terminal and browser are popped up automatically, opening some websites related to Naruto. In the terminal, I saw the command like "Naruto remix video's" executed itself. 

I thought I got some malwares. At the moment, I cannot find a way to get rid of them. Could you please help? :(

Thanks in advance.

I am sorry. Do you work for Microsoft? Curious... I know in the golden age of Microsoft, Steve Balmer sent his goons to nuke OS/2 machines in certain stores.
I have to assume you must have installed a warez application. Too many people downloaded the warez version of Nero CD burner off the net. Buy commercial apps. If you don't want to buy apps, use open source apps.

---

### Post by Chayak on 2008-04-06
I find it a bit difficult to believe myself though working in malware research if you do find the root of this so called problem please message me and I'll provide you with an email address and my gpg public key that you can send it to in .tar.gz format encrypted so no one will accidently open it

If you don't know how to find it you can send my office a forensic dd image (I'll provide instructions on how to make it) and I'll examine it for malware.

I find it difficult to believe that someone would spend the time to write linux specific malware to make you go to naruto sites rather than simply botting your machine and using it as a relay.  Have you installed any untrusted third party executables with sudo? If so why?

If this is a genuine problem I do want to help you but until I see something that I can reproduce in a lab with a binary or an image I'm chalking it up as vaporware.

If you don't wish to provide me with anything then I suggest you back up your data (no executables) and reinstall your system as it's better to be safe than sorry.

---

### Post by songuke on 2008-04-07
Thank you, Chayak. I will try to reproduce the situation and post it here for you. I installed some packages like epiphany, msttcorefonts, wine recently. Some of them required to verify before installing since they do not have certificates. Badly, I cannot remember which package. In summary, my strange situation is as follow:
- Automatically open terminal and enter some commands like "Naruto" there.
- Open Nautilus.
- Open browser and open Naruto website. 

Please understand that this is a real issue occurred to me. My post is after April Fools' Day, guys. :(

---

### Post by netlogic on 2008-04-07
I am sorry. It sounded really odd that your terminal wants to watch an Japanese anime.  Also, it sounded odd that he also happened to be a ninja. I never seen the show, but that is all I know.

---

### Post by DexterLB on 2008-04-07
> **songuke said:**
> I dunno any of you encountered strange behaviours like me in Ubuntu 7.10. My problem  is that when I leave it idle, the terminal and browser are popped up automatically, opening some websites related to Naruto. In the terminal, I saw the command like "Naruto remix video's" executed itself. 

I thought I got some malwares. At the moment, I cannot find a way to get rid of them. Could you please help? :(

Thanks in advance.

No viruses under linux.

---

### Post by atomkarinca on 2008-04-07
> **netlogic said:**
> I am sorry. It sounded really odd that your terminal wants to watch an Japanese anime.  Also, it sounded odd that he also happened to be a ninja. I never seen the show, but that is all I know.

He's not a ninja, he's a shinigami representative :)

---

### Post by Crafty Kisses on 2008-04-07
> **songuke said:**
> I dunno any of you encountered strange behaviours like me in Ubuntu 7.10. My problem  is that when I leave it idle, the terminal and browser are popped up automatically, opening some websites related to Naruto. In the terminal, I saw the command like "Naruto remix video's" executed itself. 

I thought I got some malwares. At the moment, I cannot find a way to get rid of them. Could you please help? :(

Thanks in advance.
Honestly, I don't see how this could of happened. Usually in order for something like this to happen, you'd either had to activate the virus or script, or whatever is causing the issue, yourself.

---

### Post by dmizer on 2008-04-07
have remote desktop enabled and open to the web maybe?

---

### Post by cdenley on 2008-04-07
> **dmizer said:**
> have remote desktop enabled and open to the web maybe?

That's what it sounds like to me. Can you see the mouse move when the computer automatically did something? Post the output for
```

netstat -tln

```

---

### Post by cdenley on 2008-04-07
> **Chiko2008 said:**
> how that can actually be done?
System>Preferences>Remote Desktop

It can also be done through the terminal, but not remotely by someone else unless your computer was already compromised.

---

### Post by insineratehymn on 2008-04-07
> No viruses under linux.

[Yes]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/") [there]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses") [is]("http://www.securityfocus.com/columnists/188").

**Nothing** is safe.

---

### Post by netlogic on 2008-04-07
malware isn't virus. yes, malware is bad, but it doesn't work like virus.
maybe, this is the reason people go back to Debian.

---

### Post by brian_p on 2008-04-07
> **insineratehymn said:**
> > No viruses under linux. 

[Yes]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/") [there]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses") [is]("http://www.securityfocus.com/columnists/188").

**Nothing** is safe.

Take the list of so-called viruses at the wikipedia link. Name one of them which spreads to the system and to other machines when activated by a user.

I'll start you off with diesel. This is from [www.viruslist.com:](www.viruslist.com:)

'It searches for Linux executable files in system directories and subdirectories, then writes itself to the middle of the file.'

Writes to system directories? Really?

---

### Post by netlogic on 2008-04-07
also, on the certain file server, your binaries should be read-only on a separate partition. want to upgrade? umount and mount as a writable, install new apps, umount and mount as a read-only. in my entire life, i never heard a Linux server suffered from a virus breakout. other people might have different experiences.

---

### Post by Chayak on 2008-04-07
> **netlogic said:**
> malware isn't virus. yes, malware is bad, but it doesn't work like virus.
maybe, this is the reason people go back to Debian.

Malware is a combo of Malicous and Software and by definition includes any code that executes with a malicous intent so yes, a virus falls under the term "Malware" as do worms, trojans, etc.

---

### Post by Chayak on 2008-04-07
> **songuke said:**
> Thank you, Chayak. I will try to reproduce the situation and post it here for you. I installed some packages like epiphany, msttcorefonts, wine recently. Some of them required to verify before installing since they do not have certificates. Badly, I cannot remember which package. In summary, my strange situation is as follow:
- Automatically open terminal and enter some commands like "Naruto" there.
- Open Nautilus.
- Open browser and open Naruto website. 

Please understand that this is a real issue occurred to me. My post is after April Fools' Day, guys. :(

Can you provide screenshots of the command line and the results when it happens?  I'd still like to see some binaries or code.

---

### Post by netlogic on 2008-04-07
> **Chayak said:**
> Malware is a combo of Malicous and Software and by definition includes any code that executes with a malicous intent so yes, a virus falls under the term "Malware" as do worms, trojans, etc.

I can't agree with everything you said. Virus and Malware/Trojans are different variants of infection on the computer. Maybe, we should have stated the difference between Trojans/Spyware/Rootkit vs Virus/worms. How is it possible for virus to infect the filesystem in Linux? You need administrative privilege to get infected. You are saying there is a virus that can create a root privilege escalation? How is that possible?

---

### Post by netlogic on 2008-04-07
Where can you download a Linux Virus? I want to install it in a VM? I am starting to get very curious.

Only way Linux virus binaries can infect other binaries, those binaries must be writable by that user to activate them. The default vanilla permission is read-only. I am really curious how virus can spread in a Linux system. Even a mystery way, the user randomly execute any random compiled binaries people sent them, application has to be owned by the user and spread will be very limited to that users environment.  I am constantly hearing Linux virus crashed my system on this forum and it is really hard to believe that is the truth. Also, in order to spread to other machines,  the virus must have a root privilege on the both machines.

---

### Post by insineratehymn on 2008-04-08
Viruses can start as rootkits, replacing a simple command that requires common sudo access, like chmod or rm. A malicious code writer can put his code inside of it and when the command is executed (silently during the normal program execution)it is done so at root level, it can then download its own program with root permissions.

---

### Post by hyper_ch on 2008-04-08
> **netlogic said:**
> How is it possible for virus to infect the filesystem in Linux?
Don't underestimate the power of social engineering...

Make a .deb, give it to people for downloading... as it will require root access it can infect other stuff...

---

### Post by brian_p on 2008-04-08
> **insineratehymn said:**
> Viruses can start as rootkits, replacing a simple command that requires common sudo access, like chmod or rm. A malicious code writer can put his code inside of it and when the command is executed (silently during the normal program execution)it is done so at root level, it can then download its own program with root permissions.

A rootkit comes into play after the system is compromised. So how does that happen in the first place?

Possible though it may be, the exploit you describe sounds more like a trojan than a virus. It does not spread, just like the list of so-called viruses at wikipedia.

---

### Post by brian_p on 2008-04-08
> **hyper_ch said:**
> Don't underestimate the power of social engineering...

Make a .deb, give it to people for downloading... as it will require root access it can infect other stuff...

There is nothing technical which can be done to protect against people being persuaded to install unknown or unverified software as root. That they do so does not reflect on the inherent security of Linux.

---

### Post by roderick on 2008-04-08
Given the open nature of Linux, fixing holes in the kernel, libraries and applications is pretty easy and usually happens fairly quickly.

Given this, there are relatively less problem areas for a virus, rootkit, or other malware to gain entrance.

Given that there is a much smaller install base of Linux compared to windows, this makes the threat even less for the desktop user.

However, the threat still exists (though there is a lower probability if getting hit using Linux than there is when using Windows).

Ultimately, the user is to blame for 99.999% of infections on their system. By following some simple rules (you decide how far you need to go) outlined below, you can reduce your chances for getting hit.

A hackers best friend is the end users trusting nature. If you are 100% trusting of everyone and everything, you increase the odds greatly that you will be a victim. Read the fine print when installing programs. Examine the files being installed. Learn to recognize suspicious behaviour. Ask questions to fellow users and see if they know anything about the application or trust it.

Here are some words of advice:

1) Install only from the main repo or sites you really trust (never use a random .deb from a forum)
2) Do not install hacked/cracked software - instead support the OSS equivalent
3) Always keep your system up to date (make sure you enabled security updates)
4) Do not connect directly to the Internet (always connect behind a NAT/Firewall)
5) Configure a firewall on your system (ufw, guarddog, etc)
6) Install some peace of mind programs like chkrootkit, rkhunter, logcheck to help look for possible intruders
7) If you have windows, mount any windows shares or share files with windows users, then install a virus scanner (like ClamAv, AVG, or Avast - no need spreading windows virii to other users)

Hope this helps someone.

---

### Post by JemW on 2008-04-08
> **DexterLB said:**
> No viruses under linux.

Rootkits though...

---

### Post by netlogic on 2008-04-08
> **insineratehymn said:**
> Viruses can start as rootkits, replacing a simple command that requires common sudo access, like chmod or rm. A malicious code writer can put his code inside of it and when the command is executed (silently during the normal program execution)it is done so at root level, it can then download its own program with root permissions.

Somebody has to install a rootkit on your system. Rootkit doesn't spread in LINUX or you have to be really drunk and install it yourself. Rootkit doesn't spread in Linux. Unix isn't Windows. People think too much through Windows terminology.

---

### Post by netlogic on 2008-04-08
> **hyper_ch said:**
> Don't underestimate the power of social engineering...

Make a .deb, give it to people for downloading... as it will require root access it can infect other stuff...

Right.  Like I have been saying to many newbies. Install only from Ubuntu. I don't even install stuff from Getdeb. If it is not in Ubuntu, compile it yourself. The main reason 8% of Windows infected with crap is they randomly install stolen software from the net. Trojans, rootkits, and virus scanners are mostly definition driven. They will save them or fully protect them.

---

### Post by netlogic on 2008-04-08
> **roderick said:**
> 

Here are some words of advice:

1) Install only from the main repo or sites you really trust (never use a random .deb from a forum)
2) Do not install hacked/cracked software - instead support the OSS equivalent
3) Always keep your system up to date (make sure you enabled security updates)
4) Do not connect directly to the Internet (always connect behind a NAT/Firewall)
5) Configure a firewall on your system (ufw, guarddog, etc)
6) Install some peace of mind programs like chkrootkit, rkhunter, logcheck to help look for possible intruders
7) If you have windows, mount any windows shares or share files with windows users, then install a virus scanner (like ClamAv, AVG, or Avast - no need spreading windows virii to other users)

Hope this helps someone.

These suggestions make a great final note to this thread.

---

### Post by brian_p on 2008-04-08
> **netlogic said:**
> These suggestions make a great final note to this thread.

Following the advice in 3) makes it unnecessary to do either of 4) and 5).

---

### Post by roderick on 2008-04-08
> **brian_p said:**
> Following the advice in 3) makes it unnecessary to do either of 4) and 5).

Not entirely.

Just because you have the latest updates, doesn't mean you have "all" the holes plugged. There are the as of yet unknown holes which still need fixing. As well, what if you installed software which opened ports unknowingly and this exposed a possible exploit. A firewall/NAT box will protect against those unknowns. Arguably, if you do 4, you can omit 5, however if you have a wireless network or connect to a public area or other network where you cannot guarantee security, 5 is important.

Updates are extremely important, but it's not a bulletproof solution on its own (in reality the only bulletproof solution is to unplug the thing and turn it off - haha).

---

### Post by brian_p on 2008-04-08
> **roderick said:**
> Not entirely.

Just because you have the latest updates, doesn't mean you have "all" the holes plugged.

It does. That is why the maintainers and/or the distribution provide the updates.

>  There are the as of yet unknown holes which still need fixing.

How do you fix or protect against something about which you have no knowledge?

> As well, what if you installed software which opened ports unknowingly and this exposed a possible exploit.

If you install a service you presumably want it to be used. That involves it listening on a port (opening a port). In any case the daemon will be safe because it is provided that way to you.

>  A firewall/NAT box will protect against those unknowns.

The firewall offers no protection because you cannot close off a port you are offering a service on and it cannot know what to protect against (the potential exploit is unknown).

>  Arguably, if you do 4, you can omit 5, however if you have a wireless network or connect to a public area or other network where you cannot guarantee security, 5 is important.

If it is safe at home it is safe anywhere. Remember, there are no known exploits the software is vulnerable to. Your updates ensure that.

> Updates are extremely important, but it's not a bulletproof solution on its own (in reality the only bulletproof solution is to unplug the thing and turn it off - haha).

Updates guarantee security.

---

### Post by Chayak on 2008-04-08
> **netlogic said:**
> I can't agree with everything you said. Virus and Malware/Trojans are different variants of infection on the computer. Maybe, we should have stated the difference between Trojans/Spyware/Rootkit vs Virus/worms. How is it possible for virus to infect the filesystem in Linux? You need administrative privilege to get infected. You are saying there is a virus that can create a root privilege escalation? How is that possible?

Malware is any malicious code by industry definition.  It is possible to use an exploit to gain root privileges so it's also possible to write that exploit into malware.

Personally I've never seen a Linux virus.  Though that's not to say it can't exist.  I work with windows VMs in Linux using debuggers, procmon, procexp, OLLYDBG, Wireshark, IDA pro, and whatever else I need at the time.

I'm not saying I blindly believe it, just that if it does exist I'm curious enough to want to see it for myself.

Security is a process and it reaches a point where costs escalate for small returns.  There's no such thing as perfect security so don't fool yourself in thinking that Linux is totally immune.  It's just a much harder target and part of security is being that hard target that's passed over for easier prey.

---

### Post by netlogic on 2008-04-08
All great suggestions. Maybe, we can finally put this VIRUS related threads to rest. It seems like there are least 500 of these threads floating around.

---

### Post by Chayak on 2008-04-08
> **brian_p said:**
> 
Updates guarantee security.

Only for exploits that are known.  Do you seriously think every person who finds a hole spreads the word about it? The open nature of the code allows bugs to be squashed fairly quickly due to peer review though it doesn't 100% guarantee that the exploit won't be used before it's patched.  That's exactly how the rare Apache worm is spread though as soon as they do surface they're quickly patched.

Take a trip to Blackhat or Defcon you'll find it an eye opening experience. (reformat and reload any laptops you take as soon as it's over, especially if you use the wireless access that's available.)

Then there is always the problems of users... AKA the dancing bunny theory. [http://www.codinghorror.com/blog/archives/000347.html]("http://www.codinghorror.com/blog/archives/000347.html")

---

### Post by netlogic on 2008-04-08
> **Chayak said:**
> Only for exploits that are known.  Do you seriously think every person who finds a hole spreads the word about it? The open nature of the code allows bugs to be squashed fairly quickly due to peer review though it doesn't 100% guarantee that they exploit won't be used before it's patched.  That's exactly how the rare Apache worm is spread though as soon as they do surface they're quickly patched.


That is why system architects spend tons of  time designing the network. The security isn't only codes. How servers interact with each other play a big role in a security design concept. Most of the security related things are how to out wit your opponent when they are tired and stop being paranoid. The magic codes are rare. Security automations are some times pointless. Yes, there is a huge money to be made in selling vulnerability codes in the  black market. In case some of you don't know. Sometimes, many security firms 
buy black market codes to protect their applications for Windows and OSX.
Linux software engineers are too poor to buy since they are barely breaking even or losing money on their software.

> 
Take a trip to Blackhat or Defcon you'll find it an eye opening experience. (reformat and reload any laptops you take as soon as it's over, especially if you use the wireless access that's available.)

RIGHT, because they purposely don't give anyone a secure connection. Everyone sniffs the network. It would defeat the whole experience if they gave people a secure environment. There will be nothing interesting to write back home. The situation like this, I just boot off a SD card and yank out my ide interface. First thing people look is user's home directory that contains scripts with passwords. 

I have been there. They are mostly pen testers or IT professionals. There are very few Blackhats. If they were there, they probably wouldn't admit to it. Just like if you are part of the press or FBI, you would hide your identity.

---

### Post by roderick on 2008-04-08
> **brian_p said:**
> Updates guarantee security.

I have to really disagree with much of what you have said. 

I work in telecommunications and have seen first hand where having a firewall prevented an attack from succeeding against a machine which was regularly updated. Exploits can exist and happen before any update occurs. 

A firewall (if properly configured) will protect your system. The problem is that most people do not know how to configure or lock down a system with a firewall.  Remember, a firewall can have multiple facings (internal, external, local, etc). Each can have policies on the type of traffic, etc. 

Anyway, I won't debate my 15 years experience in this field :)

Cheerio.

---

### Post by netlogic on 2008-04-08
> **roderick said:**
> 

Cheerio.

I prefer the Raisin Bran, but that is totally a different topic.

Anyway, we all have different views. It is a good idea to share different perspectives.

---

### Post by netlogic on 2008-04-08
> **Chayak said:**
> 
Then there is always the problems of users... AKA the dancing bunny theory. [http://www.codinghorror.com/blog/archives/000347.html]("http://www.codinghorror.com/blog/archives/000347.html")

Hmm... I read the article, but VM doesn't make things more secure. Sandboxing an application does. I don't know why many browsers don't come with a sandboxing technology. It isn't very hard to take over a VM and make it attack each other.
Most likely, they have no configurations not to trust each other.

Oh, Virtual PC is a pure garbage code. Maybe, that is why MS is a bit scare to promote it.

---

### Post by mimada on 2008-04-08
This may be something triggered through Wine. Is the Visual Basic or VBA DLL installed? Do you have ActiveX installed/enabled?

---

### Post by netlogic on 2008-04-08
> **mimada said:**
> This may be something triggered through Wine. Is the Visual Basic or VBA DLL installed? Do you have ActiveX installed/enabled?

Yes, it can, but wine should have been installed as an user.

---

### Post by brian_p on 2008-04-08
> **Chayak said:**
> Only for exploits that are known.  Do you seriously think every person who finds a hole spreads the word about it? The open nature of the code allows bugs to be squashed fairly quickly due to peer review though it doesn't 100% guarantee that the exploit won't be used before it's patched.  That's exactly how the rare Apache worm is spread though as soon as they do surface they're quickly patched.

Of course updates can only address security issues which are known. That's a matter of logic. As for your question, the answer is 'no' and I didn't claim that. However, an exploit which is not exploited is not a threat and when it is used and noticed it is, as you yourself say, quickly defended against. The updates bring us back to safeness.

On the other hand, packet filtering gives no protection. My sshd accepts connections from anywhere and an exploited vulnerability in the ssh protocol could not be countered by a firewall. If I keep the service up and I'm hit before the updated sshd gets to me it's tough luck or bad judgement, depending on how much sympathy you want to extend to me. I'd give you a quizzical look if you told me a firewall would have saved me. I could be persuaded otherwise by the outline of an iptables rule which protected the service from an unknown exploit.

The concept of firewalls in Windows is different from that in Linux. They are presented as all-in-one package solution to security rather than a packet filtering mechanism. A PC on every desktop and a firewall on every PC appears to be the slogan now. The Linux solution is easy - find out which services you are running and switch off the ones you do want to offer.

---

### Post by netlogic on 2008-04-08
> **brian_p said:**
> The Linux solution is easy - find out which services you are running and switch off the ones you do want to offer.

I disagree with this statement. Trusting every source destinations and relying on software protection will fail you if you are running any server based services. i always believed firewall is a must. If you aren't running any services, there is no need for a firewall in Linux. There are insane programmers who take advantage of 24hr windows before fixes get out. MS has an entire freaking month. Security is a policy. Network management and education will play a huge role.

---

### Post by insineratehymn on 2008-04-08
> **netlogic said:**
> Somebody has to install a rootkit on your system. Rootkit doesn't spread in LINUX or you have to be really drunk and install it yourself. Rootkit doesn't spread in Linux. Unix isn't Windows. People think too much through Windows terminology.

I am very aware that Unix isn't windows. If you are saying that a rootkit is only a rootkit after the system has been compromised, then you are simply arguing semantics. Unfortunately, semantics won't stop the problem; even though the problem is not a conducive investment of a malicious code writers time (writing malware/viruses for *ux). A rootkit can (theoretically) spread towards other workgroup computers. As someone said above; do **not** underestimate the power of social engineering.

---

### Post by netlogic on 2008-04-08
> **insineratehymn said:**
> I am very aware that Unix isn't windows. If you are saying that a rootkit is only a rootkit after the system has been compromised, then you are simply arguing semantics. Unfortunately, semantics won't stop the problem; even though the problem is not a conducive investment of a malicious code writers time (writing malware/viruses for *ux). A rootkit can (theoretically) spread towards other workgroup computers. As someone said above; do **not** underestimate the power of social engineering.

I am not following the trend of your statements. You clearly said, virus exists and "no one is safe." The nuclear bomb exists and no one is also safe. However, there are preventions and other operating systems are better at preventing certain things from occurring. Based on your theory, how would you spread the rootkit like a virus? Rootkit by design is a way to hide the processor from the operating system. The behavior pattern isn't like a virus. In Windows world, anyone can call the dll to the memory, because dll can be trigger with proper executables. Once that happens, dll can be ran in an administrative mode even an user is logged in as an user.  Windows by design doesn't maintain the execution of the permission. Do you believe there is something similar can be done in a Linux environment? Also, the concept social engineering isn't necessary technology.  It wouldn't be hard to convince an average user to just give away their password over the phone. Also, it wouldn't be hard to figure out the name of syadmin and his lunch schedules from his/her administrative assistance. Social engineering isn't necessary hacking. 
I think we are starting to drift apart from it. Linux operating system by design has a prevention from virus like behaviors. Just like you cannot prevent people from breaking their machines if they have the administrative rights. In most companies, I am pretty definitive that they aren't give administrative right to their users. The privilege escalation without the admin password is pretty difficult in Linux. If someone does invent AI level virus, it would be such a big of size of attachment, I doubt it would be ran.

---

### Post by frankos44 on 2008-04-09
Lets face it, you have to work hard to suffer from malicious attack on any Linux distro.  In fact the more novice you are the safer Linux is. Problems like this are normally induced by tinkering with settings or installing dodgy software. 

My kids could break a windows PC within 2 weeks consistently. They now been using Linux for best part of 2 years and their PC's are running perfectly without any issues whatsoever.

---

### Post by kenweill on 2008-04-14
> **songuke said:**
> I dunno any of you encountered strange behaviours like me in Ubuntu 7.10. My problem  is that when I leave it idle, the terminal and browser are popped up automatically, opening some websites related to Naruto. In the terminal, I saw the command like "Naruto remix video's" executed itself. 

I thought I got some malwares. At the moment, I cannot find a way to get rid of them. Could you please help? :(

Thanks in advance.

That's possible. I have tried that myself.
That will happen IF you have installed VNC SERVER in  your linux box and someone is accessing your PC through VNC.

---

