---
title: "samsung knowingly installed keylogger on their laptops!"
date: 2011-03-30
forum: The Cafe
---

### Post by szymon_g on 2011-03-30
"(...)Mohamed Hassan, MSIA, CISSP, CISA graduated from the Master of Science in Information Assurance (MSIA) program from Norwich University in 2009. As usual, it is a pleasure to collaborate with an alumnus on interesting articles – and in this case, his research is startling. Everything that follows is Mr Hassan's own work with minor edits.

* * *

In the fall of 2005, the security and computer world was abuzz with what was at the time dubbed as the "Sony BMG rootkit Fiasco." Sony BMG used a rootkit, computer program that performs a specific function and hides its files from the regular user, to monitor computer user behavior and limit how music CDs were copied and played on one's computer.

The issue was not about the extent Sony BMG had gone to protect its music CD, but more about the manner in which it accomplished its business objective. Following the wide publication of this security incident, there was torrent of bad press for Sony BMG; its earlier denial of the presence of the rootkit on its music CDs did not help. There were class-action lawsuits as well as state and federal investigations, one of which was spearheaded by the United States Federal Trade commission (FTC).  (...)"

link1 : [http://www.networkworld.com/newsletters/sec/2011/032811sec2.html](http://www.networkworld.com/newsletters/sec/2011/032811sec2.html)

link2 : [http://www.networkworld.com/newsletters/sec/2011/040411sec1.html](http://www.networkworld.com/newsletters/sec/2011/040411sec1.html)

This keylogger was detected by AV software- i wonder, how quick rootkit like that would be detected on computers with linux preinstalled...

---

### Post by itguy1985 on 2011-03-30
> **szymon_g said:**
> "(...)Mohamed Hassan, MSIA, CISSP, CISA graduated from the Master of Science in Information Assurance (MSIA) program from Norwich University in 2009. As usual, it is a pleasure to collaborate with an alumnus on interesting articles – and in this case, his research is startling. Everything that follows is Mr Hassan's own work with minor edits.

* * *

In the fall of 2005, the security and computer world was abuzz with what was at the time dubbed as the "Sony BMG rootkit Fiasco." Sony BMG used a rootkit, computer program that performs a specific function and hides its files from the regular user, to monitor computer user behavior and limit how music CDs were copied and played on one's computer.

The issue was not about the extent Sony BMG had gone to protect its music CD, but more about the manner in which it accomplished its business objective. Following the wide publication of this security incident, there was torrent of bad press for Sony BMG; its earlier denial of the presence of the rootkit on its music CDs did not help. There were class-action lawsuits as well as state and federal investigations, one of which was spearheaded by the United States Federal Trade commission (FTC).  (...)"

link1 : [http://www.networkworld.com/newsletters/sec/2011/032811sec2.html](http://www.networkworld.com/newsletters/sec/2011/032811sec2.html)

link2 : [http://www.networkworld.com/newsletters/sec/2011/040411sec1.html](http://www.networkworld.com/newsletters/sec/2011/040411sec1.html)

This keylogger was detected by AV software- i wonder, how quick rootkit like that would be detected on computers with linux preinstalled...

This is just an assumption, but from what I've learned, I would believe this same kit wouldn't run on a Linux based machine. Correct?

---

### Post by Welly Wu on 2011-03-30
Based on the same information up to this point, the key logger program will only run on the Microsoft Windows 7 operating system for those two specific Samsung notebook PCs. I am not sure if the new Samsung Series 9 made from Duraluminum also has a key logger program built in as well.

It will not run on GNU/Linux.

Suffice it to say, it is very difficult to install a key logger into any of the major GNU/Linux distributions especially within the officially supported repositories without escaping detection from any of the popular anti-virus, rkhunter, or chkrootkit security programs when the user initiates a scan of his or her computer.

I am studying Principles of Operating Systems, CompTIA Security+, and I am pursuing a Masters of Science in IT Administration and Security at New Jersey Institute of Technology. I am also studying for my CISSP exam as well.

It should be well known that Microsoft Windows is the most popular operating system used by people worldwide and it is filled with vulnerabilities, exploits, and unpatched bugs. I decided to migrate away from it to Ubuntu 10.10 64 bit based on my growing knowledge of computer security. As a graduate student, cost was an important factor in choosing an alternative operating system and Ubuntu meets most of my other needs for stability, reliability, ease of use, popularity, support, and security.

---

### Post by Welly Wu on 2011-03-30
For those that did purchase a new Samsung R525 or R540 notebook PC, here are some instructions to detect and remove the StarLogger key logging program:

[http://download.cnet.com/8301-2007_4-20048963-12.html?tag=cnetRiver](http://download.cnet.com/8301-2007_4-20048963-12.html?tag=cnetRiver) .

As for myself, my next notebook PC will be a System76 Serval Professional with all of the latest and best upgrade options. System76 does not install key logger programs on their products.

---

### Post by disabledaccount on 2011-03-30
> **szymon_g said:**
> This keylogger was detected by AV software- i wonder, how quick rootkit like that would be detected on computers with linux preinstalled...
...and Your point is?
Are You trying to say that thanks to wonderfull AV software windows is more secure, even with rootkit pre-installed? Do You know that there are viruses that can turn-off AV?

Linux: such software can be detected very quickly, unless that preinstaled distro would come with patched, closed source kernel, with no possibility of external updates and without community/developers support. Nearly impossible :)

Nevertheless conlusion is simple: When You buy laptop with pre-installed Windows then:
- You have OEM version of system
- no original cd
- less disk space (hidden recovery partition)
- no possibility to change partitions (because this will render recovery software unusable or You will lose data during recovery or You will lose recovery partition)
- tons of bundled, crappy, mostly trial versions of software -> side effect is slower booting, lower overall performance.
- rootkit for free - the only extra software in full version, not just trial :)

I'm allways suggesting to buy normal version of Windows - if someone don't want to use linux...

---

### Post by Copper Bezel on 2011-03-31
Oh, unquestionably, but I think all serious Windows users know that. My Windows friends' factory installs tend to survive an average of three months.

That doesn't make Samsung any less evil, and I won't be buying any of their products any time soon (but I'm an Asus fanboy, anyway.)

---

### Post by dgw on 2011-03-31
The Samsung keylogger story sounds like a hoax, or possibly like the guy who found it was actually infecting himself (maybe with an infected USB stick, or with pirated antivirus software that came with a keylogger, for example). Has anyone besides that guy actually found the keylogger on their Samsung yet?

I remember when I heard about the Sony rootkit, I performed the uncloaking instructions and saw the rootkit in my Task Manager. I developed a hatred of DRM with that incident. :P

---

### Post by piquat on 2011-03-31
If it's a hoax, perpetrated by the guy that says he found it, he's putting a lot on the line.  His full name and credentials are all out there for everyone to see.

At one point he says a CS manager of some sort seems to have confirmed the fact that Samsung put it there on purpose to see how people were using their laptops.

No, I think the most innocuous possibility here is that Samsung loaded up some infected bloatware from upstream.  That in itself is even MORE worrisome.  If that's the case, *who knows where those logs have been sent!*

---

### Post by gnomeuser on 2011-03-31
Today I am ashamed of having furthered Samsung's business by having bought a Galaxy S.

---

### Post by dgw on 2011-03-31
> **piquat said:**
> If it's a hoax, perpetrated by the guy that says he found it, he's putting a lot on the line.  His full name and credentials are all out there for everyone to see.
And as long as it's not proven to be a hoax, he may have a lot to gain in the way of publicity for himself and the security consulting company he's trying to start. It's possible though that it's not a hoax, but that he installed the keylogger unknowingly after buying the computers. It's also possible it really did come installed on the computers.
> At one point he says a CS manager of some sort seems to have confirmed the fact that Samsung put it there on purpose to see how people were using their laptops.If this story is true, it's unlikely that Samsung would have told the people they hire to do tech support about the keylogger. I can imagine that if he convinced the person he was on the phone with that the computers had definitely come with keyloggers preinstalled, that person might have made up a reason for it that seemed plausible to them.
> No, I think the most innocuous possibility here is that Samsung loaded up some infected bloatware from upstream.  That in itself is even MORE worrisome.  If that's the case, *who knows where those logs have been sent!*It would be nice to know what IP addresses the infected computers are sending the logs to, actually.

---

### Post by eentonig on 2011-03-31
Hoax or not, I won't be using his security consulting company.

If he were any good in it's security consulting business, he would have investigated this a bit further and come up with the details as to:

1: When and where does this software attempts to upload it's collected information. Could be easily discovered by putting a packet sniffer between the host and the internet.

2. Is the software already installed when doing a factory restore without any connection to the network or adding other devices, to make sure it's not self infected by a USB he used on both systems. 

...

---

### Post by piquat on 2011-03-31
> **eentonig said:**
> Hoax or not, I won't be using his security consulting company.

If he were any good in it's security consulting business, he would have investigated this a bit further and come up with the details as to:

1: When and where does this software attempts to upload it's collected information. Could be easily discovered by putting a packet sniffer between the host and the internet.

2. Is the software already installed when doing a factory restore without any connection to the network or adding other devices, to make sure it's not self infected by a USB he used on both systems. 

...

Both good points.  Especially #1.  Does seem kind of fishy now that you put it that way.

---

### Post by szymon_g on 2011-03-31
> **Welly Wu said:**
> Suffice it to say, it is very difficult to install a key logger into any of the major GNU/Linux distributions especially within the officially supported repositories without escaping detection from any of the popular anti-virus, rkhunter, or chkrootkit security programs when the user initiates a scan of his or her computer.

you forgot: that kl was installed /apparently/ by manufacturer, it wasn't "installed by accident" or "by itself". in that case- all repositories, signed packages- related security would be useless. and, as far i'm concerned- neither rkhunter or chrootkit will detect Xorg- level keylogger.
how many people run those programs on desktop computers? and how will you comment it [http://www.zdnet.com/blog/bott/linux-infection-proves-windows-malware-monopoly-is-over-gentoo-ships-backdoor-updated/2206](http://www.zdnet.com/blog/bott/linux-infection-proves-windows-malware-monopoly-is-over-gentoo-ships-backdoor-updated/2206) - sure, it was detected. but similar stuff in windows's program would be detected much faster.

> **Welly Wu said:**
> It should be well known that Microsoft Windows is the most popular operating system used by people worldwide and it is filled with vulnerabilities, exploits, and unpatched bugs. I decided to migrate away from it to Ubuntu 10.10 64 bit based on my growing knowledge of computer security. As a graduate student, cost was an important factor in choosing an alternative operating system and Ubuntu meets most of my other needs for stability, reliability, ease of use, popularity, support, and security.

hm... i can trade a bit of security for better hardware and software support, and easy management. cost? my time isn't free

ps. tbh- i found fedora/rhel/centos better security-wise.

[QUOTE=Tomazzi]
Linux: such software can be detected very quickly, unless that preinstaled distro would come with patched, closed source kernel, with no possibility of external updates and without community/developers support. Nearly impossible [/quote]

... unless it would be just a bit of firmware loaded by a kernel; or xorg modified to log keystrokes..

/// edit///
btw, don't forget that security whole in openssl was detected after 2 years. it was created by package maintainer's patch.

---

### Post by Welly Wu on 2011-03-31
The officially supported repositories are open source and they are freely available for others to read and analyze the code. Too many people have access to the code and there is a tremendous amount of scrutiny that the code undergoes before it is released to the official repositories. It is a fact that a key logger has never entered an official Ubuntu repository and it has never infected and spread across the world.

The key logger program was installed by Samsung, but it only effects Microsoft Windows 7 and it does not work for Ubuntu or any GNU/Linux distribution.

I understand that this is an open community for Ubuntu users, but I am beginning to question the logic behind some of the members that have posted false information about this topic.

This was not a hoax. It is an isolated case to be sure, but it is also real. Samsung is investigating this matter now. So too are the major computer magazine writers at PC Magazine, PC World, and Laptop Magazine along with CNet.

Part of the requirement for CISSP and CISA along with a Masters of Science in Information Assurance is to report security breaches directly to the software and hardware vendor upon detection and try to get the source to resolve the matter. If not, then go public. He was simply following through on his training. I would have done the same thing too.

---

### Post by CharlesA on 2011-03-31
Don't forget to don yer tinfoil hats!

[http://www.digitaltrends.com/computing/samsung-keylogger-accusations-prove-false/](http://www.digitaltrends.com/computing/samsung-keylogger-accusations-prove-false/)

---

### Post by Tristam Green on 2011-03-31
> **CharlesA said:**
> Don't forget to don yer tinfoil hats!

[http://www.digitaltrends.com/computing/samsung-keylogger-accusations-prove-false/](http://www.digitaltrends.com/computing/samsung-keylogger-accusations-prove-false/)

<3  I was just about to post the Engadget article about this.


Those poor, poor Slovenians.

---

### Post by SeijiSensei on 2011-03-31
I recommend bold text to make sure everyone sees this:

**This was a [false positive]("https://threatpost.com/en_us/blogs/samsung-keylogger-case-turns-out-be-false-positive-033111"); Samsung did not ship a keylogger.**

Didn't anyone else think it was unlikely that something designed to be surreptitious like a keylogger would be stored in plain view in a directory called C:\Windows\SL?  What kind of anti-virus program looks only at directory names to identify malware rather than scanning the binaries themselves?  A stupid one, it appears.

---

### Post by Quadunit404 on 2011-03-31
Good thing I use ESET rather than Vipre it seems :wink:

---

### Post by sdowney717 on 2011-03-31
An antivirus false positive
or so they want you to think

[http://www.cio.com/article/678696/Samsung_Cleared_of_Laptop_Keylogger_Accusation?source=rss_all&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+cio%2Ffeed%2Farticles+%28CIO.com+Feed+-+Articles%29](http://www.cio.com/article/678696/Samsung_Cleared_of_Laptop_Keylogger_Accusation?source=rss_all&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+cio%2Ffeed%2Farticles+%28CIO.com+Feed+-+Articles%29)

---

### Post by Quadunit404 on 2011-03-31
I do not really understand that, as the article you linked to basically confirms it was indeed a false positive :confused:

---

