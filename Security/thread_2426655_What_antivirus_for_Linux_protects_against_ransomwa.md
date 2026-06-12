---
title: "What antivirus for Linux protects against ransomware and infected web sites?"
date: 2019-09-11
forum: Security
---

### Post by dora5 on 2019-09-11
Linux servers are getting infected with ransomware like crazy, so it is not true that Linux machines don't get viruses.   

I find my usual vulnerability to viruses is downloading legitimate files from legitimate sites, such as Blue Mountain greeting cards, visiting legitimate sites taht are infected and in Windows Malwarebytes wouldn't let me at that web site, and, visiting a web page that runs ads, and they all do, ten million ads, only one of the ads will redirect to a malicious web site and download malware even on a Linux machine without my consent.   I don't know how they are doing that, but it's a major problem.   Here are some articles about it.   

[https://invenioit.com/security/linux-ransomware-attacks-rise/](https://invenioit.com/security/linux-ransomware-attacks-rise/)

I can't find any antivirus for Linux that even mentions ransomware, and in this day and age, that's fundamental to a minimally competent antivirus.   Clamav doesn't say it stops ransomware from installing or running, Comodo doesn't - none of them do.   

It's also critical to me that workstation/ PC antivirus software actually tell me if I'm on an infected web site and not let me on it, or not let infected files download.  Generally with Windows I found that if using antimalware like that I didn't get viruses, and if using antimalware that doesn't block bad web sites and doesn't block bad files from downloading, I do get malware.  It really doesn't matter what an antivirus does after the fact as the simplest and least threatening virus is a day's work to get off your system and I've never once seen the antivirus remove it for me.   I can't find a single Linux antivirus that does that.   

Can people please suggest software that actually blocks viruses on Linux systems including ransomware? 

If there is no such thing, that's a grave issue for expecting anyone to convert from using Windows.   Canonical needs to fix that!

---

### Post by uRock on 2019-09-12
> "While it may not be currently clear how the B0r0nt0K ransomware was able to establish a foothold on the affected Linux servers in question, typically it comes back to server misconfigurations or from running out-of-date versions of software with known remote code execution vulnerabilities," he told LinuxInsider. [https://www.linuxinsider.com/story/85870.html](https://www.linuxinsider.com/story/85870.html)

I also took a look at the link you posted which states the system they're talking about had a ten year old kernel on it. 

In short, run updates at least weekly, if not daily, and don't configure servers without following official documentation and doing research.

---

### Post by uRock on 2019-09-12
As for the anti-virus saying you're on an insecure website, there are browser plugins for that. What browser are you using?

---

### Post by The Cog on 2019-09-12
In general, the Linux kernel receives security patches for newly found vulnerabilities very quickly - probably quicker than any AV product could be updated to recognise any/all the different variants of malware that attack that vulnerability. So you are better off keeping the OS patched than you are trying to keep an AV product up to date. And one OS update/patch will protect against all malware that tries to use that patched vulnerability. 

An AV vendor will happily give a long list of names of malware variants it detects and will add to that list when new variants that attack the same vulnerability are found. Looks good on their web site. I don't think you will find any AV software that protects against un-patched vulnerabilities though. That's just not the order in which things happen. Plugging the hole is so much better than paying to keep the pumps running.

---

### Post by dora5 on 2019-09-12
You all seem to misunderstand.  I'm not looking for protection from vulnerabilities, I'm looking for protection from viruses.  Vulnerabilities are a fact of life and most are not going to be patched and known.   Honestly, the ways to deny the problem!

I specifically want an antivirus that specifically blocks ransomware, and specifically blocks viruses before they download.   Like many antivirus products do for Windows.

Come on, you all, the news media for the past two days is full of Linux servers infected with a specific kind of ransomware, and if it's infecting well secured government and corporate servers you KNOW it's affecting desktop users like me by the millions.  Quit denying the problem, if you want actual Linux users!

---

### Post by dora5 on 2019-09-12
Chrome.

Again, I am concerned about INFECTED web sites, not "insecure" ones.  Many Windows antivirus products such as malwarebytes block INFECTED web sites.   NOT "insecure" ones.

---

### Post by uRock on 2019-09-12
> **dora5 said:**
> Chrome.

Again, I am concerned about INFECTED web sites, not "insecure" ones.  Many Windows antivirus products such as malwarebytes block INFECTED web sites.   NOT "insecure" ones.
There are addons for Chrome to block infected sites, though Google Chrome already has you covered. [https://support.google.com/chrome/answer/99020?co=GENIE.Platform%3DDesktop&hl=en-GB](https://support.google.com/chrome/answer/99020?co=GENIE.Platform%3DDesktop&hl=en-GB) Those sites, whether blocked by a third party app or the browser, have to be reported and confirmed by the vendor before they start blocking. You're trying to treat Linux as if it were Windows. Linux is not Windows. Please take the time to read the Security sub-forum stickies to learn more about protecting yourself.

If you read up on anti-virus for Windows, then you'll find that they're usually a day late and dollar short on protection against malware.

---

### Post by uRock on 2019-09-12
> **dora5 said:**
> You all seem to misunderstand.  I'm not looking for protection from vulnerabilities, I'm looking for protection from viruses.  Vulnerabilities are a fact of life and most are not going to be patched and known.   Honestly, the ways to deny the problem!

I specifically want an antivirus that specifically blocks ransomware, and specifically blocks viruses before they download.   Like many antivirus products do for Windows.

Come on, you all, the news media for the past two days is full of Linux servers infected with a specific kind of ransomware, and if it's infecting well secured government and corporate servers you KNOW it's affecting desktop users like me by the millions.  Quit denying the problem, if you want actual Linux users!

Linux protects against malware by fixing vulnerabilities. Malwares usually require a vulnerability. The Linux SERVERs you are mentioning as being infected are usually outdated and misconfigured, as most of the articles I have read are mentioning. If you're seeing articles hinting that Linux desktop machines are being affected, then do share.

---

### Post by uRock on 2019-09-12
> **The Cog said:**
> An AV vendor will happily give a long list of names of malware variants it detects and will add to that list when new variants that attack the same vulnerability are found. Looks good on their web site. I don't think you will find any AV software that protects against un-patched vulnerabilities though. That's just not the order in which things happen. Plugging the hole is so much better than paying to keep the pumps running.

This! Malware vendors are expecting customers to have updated systems. If you were running Windows and hadn't run updates for ten years, like in the article you shared, then even the best anti-malware will likely not protect you.

---

### Post by SeijiSensei on 2019-09-12
From: [https://www.linuxinsider.com/story/85870.html](https://www.linuxinsider.com/story/85870.html)

> The most active way to prevent B0r0nt0K from entering your Linux server is to close the SSH (secure shell) and the FTP (file transfer protocol) ports, said Victor Congionti, CEO of Proven Data.
Anyone running an Internet-facing server that still supports plain-text FTP is an idiot. 

Also SSH to my remote servers only allows connections from a small list of known IPs.  Most of my communications between my office and the remote servers happens over OpenVPN connections. Again these are limited to a very small set of IPs.

> It is also possible that these attacks are being sent in through basic CMS (content management system) vulnerabilities.

I use WordPress and install new updates when they are released.  I also limit the permissions on the WP directories so that the web server "user" cannot write anything there except to the upload directory where objects like graphics are stored.  I run a simple script that changes the permissions before each update, then run another script that sets the permissions back when the update is finished.

It's not hard to protect yourself against these kinds of exploits if you invest some time and effort.  

I don't visit random websites, and I certainly wouldn't follow links in email to some site that I don't know.  I also run [MailScanner]("http://www.mailscanner.info/") on my mail server to scan all my mail for spam and viruses.  It will detect and "disarm" hidden links like 1x1 graphics that can be a source of "drive-by" infections.

Finally, all my servers are virtual machines, and I pay [Linode](https://www.linode.com) a few bucks extra a month to take daily snapshot backups of each server. If a server were ever to go south, I could replace it from its snapshot image.  At worst I'd lose a day or two of new content.

---

### Post by TheFu on 2019-09-12
The Linux servers infected were all running php webapps. They are not normal desktops. The files targeted were .html, js, and php files. 

Windows and Unix have completely different security models.  Hence, the solutions to potential problems are also different.  Trying to make Linux like Windows will only lead to frustration. They aren't the same OS and work very differently.

My 80 yr old mother never had any issues with malware or viruses on Linux.  She was hit with both on Windows, before she realized that changing to Linux was necessary.

Do a little research, please.
If you want to prevent any malware/virus/whatever harming your Linux system coming in over a web browser, then use the normal tools which prevent that, like **firejail** or a Linux container.  Linux containers have been around almost 15 yrs.  Light sandboxes have been around almost a decade making use of Linux namespaces.  These are used to limit access by processes not specifically allowed to certain kernel services and parts of the file system.  Canonical snaps are mini-containers for programs.

I would never use google-chrome on any of my systems. Their goals and my goals in a browser do not align.

Nothing can protect every user from every possible threat.  Not visiting untrustworthy websites is my primary way to avoid issues. To me, untrustworthy sites have more than 1 tracker included.  I don't allow javascript on most websites.  For email, only  7-bit ASCII is accepted.

Any AV/anti-malware is too late.  Be proactive.

And nothing can replace having daily, automatic, versioned, backups.  When you get hit with a problem, those backups will let you go back to before the attack happened and compare all the files, figure out what happened, before restoring.  As long as the backup storage isn't connected to the system while the malware is active, recovery is possible.  If it takes more than 45 minutes to restore a system to the way it was before the malware hit, then the backups aren't good enough. 


> Anyone running an Internet-facing server that still supports plain-text FTP is an idiot. 
+1000!
> 
"While it may not be currently clear how the B0r0nt0K ransomware was able to establish a foothold on the affected Linux servers in question, typically it comes back to server misconfigurations or from running out-of-date versions of software with known remote code execution vulnerabilities,"
Stay patched.  Have versioned backups.  If you run internet services, be paranoid.  Desktop users are not impacted.

Linux isn't Windows.  Think differently.

---

### Post by (kyT%0) on 2019-09-12
> **dora5 said:**
> [https://invenioit.com/security/linux-ransomware-attacks-rise/](https://invenioit.com/security/linux-ransomware-attacks-rise/)

i would not pay any heed to that article, a) it is outdated b) the  article seems like a promotional article for a certain company &  even suggests a free demo from the company (check the links in blue).

> **uRock said:**
> As for the anti-virus saying you're on an insecure  website, there are browser plugins for that. What browser are you  using?

i tried quite a few on firefox but they all seem  useless. all they seem to do is block trackers. even sites known for  doling out malicious jewels are given a green by these so called  security add-ons.  

> **TheFu said:**
> If you want to prevent any malware/virus/whatever  harming your Linux system coming in over a web browser, then use the  normal tools which prevent that, like **firejail** or a Linux container.

nice. kinda like default-deny. thank you for the firejail tip. 

> **TheFu said:**
> I  would never use google-chrome on any of my systems. Their goals and my  goals in a browser do not align.

ditto that.

---

### Post by uRock on 2019-09-12
> **u-n said:**
> <snip>
i tried quite a few on firefox but they all seem  useless. all they seem to do is block trackers. even sites known for  doling out malicious jewels are given a green by these so called  security add-ons.  
<snip>.
Yup. Like AV for Windows, they only make people feel more protected. I use Firefox. The only add-on I have enabled is Facebook Container, which has changed a lot about how FB offers ads. I don't see all of the ads for products I look at on other sites anymore.  I ran ClamAV after you posted about the malware in your cache and it found nothing on my system.  I attribute that to my running Bleachbit to clear cache and temp stuff several times a day and my not going to many websites aside from FB, local news, Amazon, UF, and gmail. Aside from those pages, I only visit pages that come up when doing research. 

@TheFu 
I had never taken a look at FireJail. I am going to start messing around with it. I wonder if the person in this Wordpress had to pay Metallica for royalties for his video. [https://firejail.wordpress.com/](https://firejail.wordpress.com/)

---

### Post by TheFu on 2019-09-12
There are about 10 other firejail-like tools.  "firejail vs" is a good search term to find some other options.

Some aliases that might be handy:
```
alias firechrome='firejail chromium-browser --mute-replay-warnings '
alias fireff='firejail firefox '
alias fire**p**chrome='firejail --private chromium-browser --mute-replay-warnings '
alias fire**p**ff='firejail --private firefox '
```

--private means nothing will be written to disk/storage. NOTHING.  Without that option, only the ~/Download/ and browser config directories can be written and specific parts of the file system support read.

For fun, do a **firejail --private bash** and see what you can see/do.  Try to sudo.  Put files in your HOME or ~/Downloads.  Knock yourself out.  Firejail has profiles for different programs - /etc/firejail/ ... most of the settings aren't hard to figure out.

---

### Post by QIII on 2019-09-12
> Canonical needs to fix that!

Just a note here dora5:

Canonical is just one of many distributors of a Linux-based OS.  Canonical produces Ubuntu, one of many Linux distributions.  Microsoft is entirely responsible for and in control of Windows.  Windows is Microsoft's product.  Canonical is not "in charge" of Linux.  Linux is not Canonical's product.  Canonical controls a small subset of the Linux world, a part called Ubuntu.

---

### Post by tomdkat on 2019-09-14
> **u-n said:**
> i tried quite a few on firefox but they all seem  useless. all they seem to do is block trackers. even sites known for  doling out malicious jewels are given a green by these so called  security add-ons.Which ones have you tried?  I'm currently in the process of evaluating some browser add-ons and so far, the two I'm using (Ad Blocker Ultimate and Malwarebytes browser extension) are working very well.

Thanks!

Peace...

---

### Post by ryansenn on 2019-09-15
What about brave browser? Don't they claim to do that stuff out of the box?

---

### Post by (kyT%0) on 2019-09-15
> **tomdkat said:**
> Which ones have you tried?

avast online security, avg online security, avira browser safety, bitdefender traffic light & norton safe web

> **tomdkat said:**
> I'm  using (Ad Blocker Ultimate and Malwarebytes browser extension) are  working very well.

i learnt of malwarebytes browser guard thanks to you. it did actually block access to some shady web sites but just a couple.

to be honest i think i am better of without the snake oil.

---

### Post by ecophobia on 2019-10-01
Ransomware needs a way in, usually by exploiting the user's misconfiguration or vulnerability. No need to install AV on Linux workstation really. All of this ransomware hype in the media refers to compromised Servers, not user (Linux) workstations. I often find these servers left with no updates and poorly configured. Usually this happens because of organisations HR problems (despite them running 6 step job interviews ):P). As to securing your web browser, there was a good post on this topic [https://www.linux.com/news/4-best-practices-web-browser-security-your-linux-workstation/](https://www.linux.com/news/4-best-practices-web-browser-security-your-linux-workstation/)

---

