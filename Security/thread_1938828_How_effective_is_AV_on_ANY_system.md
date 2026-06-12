---
title: "How effective is AV on ANY system?"
date: 2012-03-10
forum: Security
---

### Post by 0011235813 on 2012-03-10
Hi,
now I am sure similar posts might have been posted before, but I just want to ask you guys something; Is running antivirus programs on **any** platform an effective security measure? Now I've seen this interesting link; [http://skeptics.stackexchange.com/questions/2167/is-anti-malware-software-effective](http://skeptics.stackexchange.com/questions/2167/is-anti-malware-software-effective)
but I would be curious for more details. How likely is it that a system with a "reputable" anti-virus program is going to stop a threat?

My experience has been quite negative with these types of programs, I have often seen AV programs spew up nonsense warnings on non-malicious software, but completely ignore real malware. I have seen malware programs taken down by malware, thus leaving the system unprotected. Additionally, they consume large amounts of resources and are filled with ads to buy their "premium" subscriptions. 

Oh and when I ask this, I mean for ALL platforms, not just Linux. I am talking especially in regards to Windows powered PCs ;)

---

### Post by synaptix on 2012-03-10
No AV is 100%, but most of the major suites usually score in the high 90% range for detections and most major suites now include 0day protection which typically helps stop the ones that disable the program.

And false-positives are generally remedied quite quickly if/when reported. I use Comodo IS Premium on my Windows 7 install and it does a fantastic job.

---

### Post by hakermania on 2012-03-10
An antivirus can be very effective. It can help you get rid of viruses but they also slow down your system. They are more needed for windows rather than for linux.

Also note that no antivirus can detect easily new viruses, until they are reported. If a hacker builds an virus especially for you, then your AV will not easily detect it, unless it does something obviously evil, and so you will have to be generally careful.

PS. Always remember that no AV can help a user, if he is not careful enough to protect his system himself. You won't click on a link blinking that you are the 10^6 visitor of the page, lolz :P

---

### Post by 0011235813 on 2012-03-10
> **synaptix said:**
> No AV is 100%, but most of the major suites usually score in the high 90% range for detections and most major suites now include 0day protection which typically helps stop the ones that disable the program.

And false-positives are generally remedied quite quickly if/when reported. I use Comodo IS Premium on my Windows 7 install and it does a fantastic job.
From the statistics I've seen, the number tends to be about 30% detection rate.

I've still seen AV programs a plenty get terminated by malicious agents. Their defence seems pretty basic in comparison to the advanced rootkits I've seen. I can say this from personal experience. 
> **hakermania said:**
> An antivirus can be very effective. It can help you get rid of viruses but they also slow down your system. They are more needed for windows rather than for linux.

Also note that no antivirus can detect easily new viruses, until they are reported. If a hacker builds an virus especially for you, then your AV will not easily detect it, unless it does something obviously evil, and so you will have to be generally careful.

PS. Always remember that no AV can help a user, if he is not careful enough to protect his system himself. You won't click on a link blinking that you are the 10^6 visitor of the page, lolz :P
I've actually heard that many of these AV suites can't get rid of threats very easily. 

In any case, I think AV can be useful for scanning scripts, .deb and any .exe you might want to run in wine, but I've never gotten "realtime" protection from them. In my experience, running an AV program doesn't magically make your system secure. Please tell me if you had cases were the AV genuinely stopped a threat before it continued. In any case, AV programs heavily mislead the user and I think harm their security more than they help it, as users are often lulled into a false sense of security by them. 

Just my two pennyworth. I wish OS manufacturers could be bothered to put some basic tutorials on their systems when the user first installs it. It would help security more than anything. I also think add-ons like WOT and adblock should be pre-installed, as they greatly help security without compromising on usability.

---

### Post by Dangertux on 2012-03-10
> **0011235813 said:**
> From the statistics I've seen, the number tends to be about 30% detection rate.

I've still seen AV programs a plenty get terminated by malicious agents. Their defence seems pretty basic in comparison to the advanced rootkits I've seen. I can say this from personal experience. 

I've actually heard that many of these AV suites can't get rid of threats very easily. 

In any case, I think AV can be useful for scanning scripts, .deb and any .exe you might want to run in wine, but I've never gotten "realtime" protection from them. In my experience, running an AV program doesn't magically make your system secure. Please tell me if you had cases were the AV genuinely stopped a threat before it continued. In any case, AV programs heavily mislead the user and I think harm their security more than they help it, as users are often lulled into a false sense of security by them. 

Just my two pennyworth. I wish OS manufacturers could be bothered to put some basic tutorials on their systems when the user first installs it. It would help security more than anything. I also think add-ons like WOT and adblock should be pre-installed, as they greatly help security without compromising on usability.

Real time scanning of .debs? What AV are you using for Linux that offers on access functionality. I'm not aware of any free AV that does this.

---

### Post by 0011235813 on 2012-03-10
> **Dangertux said:**
> Real time scanning of .debs? What AV are you using for Linux that offers on access functionality. I'm not aware of any free AV that does this.

I wasn't talking of real time of .debs sorry if I confused you. I meant that the so-called "realtime" scanning features of some Windows programs doesn't really work that well. You can scan .debs with Clamscan but I doubt you'd find much since there really aren't that many Linux viruses out there.

---

### Post by Dangertux on 2012-03-10
> **0011235813 said:**
> I wasn't talking of real time of .debs sorry if I confused you. I meant that the so-called "realtime" scanning features of some Windows programs doesn't really work that well. You can scan .debs with Clamscan but I doubt you'd find much since there really aren't that many Linux viruses out there.

Ah gotcha...

So like here is the thing about av's effectiveness or lack thereof. AV definitions particularly those that are designed to match "suspicious behavior" are carefullly crafted. If the definition is too broad it will generate false positives. Too narrow and it wont do its job. It isnt easy to build software that attempts to pass judgement on other software's intentions. Thus it is relatively easy to bypass AV in most environments.

---

### Post by Ms. Daisy on 2012-03-10
> **0011235813 said:**
> Hi,
Is running antivirus programs on **any** platform an effective security measure? 
I'll focus my answer on this particular question.  IMO running antivirus can be part of an effective security strategy. . But it can't be THE answer to security.  A quote from [this article]("http://www.techrepublic.com/blog/security/understanding-layered-security-and-defense-in-depth/703"):
> 
no single security application is capable (nor should we expect a single  application to be capable), of providing adequate computer system  protection.

It's not terribly difficult to defeat all the commercial AV programs. That's why it's important to fill in the gaps with other layers like mandatory access controls, firewall, updating your OS, good passwords, auditing logs, confining applications, harden the browser, etc.

---

### Post by lisati on 2012-03-10
My $0.02:

As long as people are people, I don't think there will be a software-based AV solution that will 100% protect your system. Sure, you might get lucky and find one that does a good job of recognising the kinds of problems that your surfing habits bring your way, but it will have trouble identifying threats that its database, rules and heuristics haven't been crafted to recognise. How well it is able to help you do repairs and otherwise clean up should the unthinkable happen is another story.

---

### Post by 0011235813 on 2012-03-10
> **Ms. Daisy said:**
> I'll focus my answer on this particular question.  IMO running antivirus can be part of an effective security strategy. . But it can't be THE answer to security.  A quote from [this article]("http://www.techrepublic.com/blog/security/understanding-layered-security-and-defense-in-depth/703"):


It's not terribly difficult to defeat all the commercial AV programs. That's why it's important to fill in the gaps with other layers like mandatory access controls, firewall, updating your OS, good passwords, auditing logs, confining applications, harden the browser, etc.
I agree! To be honest, I think AV software is a  big myth companies spread to get money from their customers. For once, Mr Gibson actually got something right;
> Any form of "protection" in the form of an executable is quite frankly idiotic {IMO}

A little off-topic, but have you heard that updates that fix old security flaws can cause new ones?... I've heard some system admins deliberately refuse to install updates unless they know **exactly** what it does, and there is no other way to achieve it than via the update.

---

### Post by Ms. Daisy on 2012-03-10
> **0011235813 said:**
> A little off-topic, but have you heard that updates that fix old security flaws can cause new ones?... I've heard some system admins deliberately refuse to install updates unless they know **exactly** what it does, and there is no other way to achieve it than via the update.
Hmm.  I think you're talking about large corporations with sensitive information on their systems. They won't install an update (or anything else for that matter) without first knowing exactly how it will interact with everything else already running.  So they install the updates/software/whatever in sandboxed systems to make sure nothing breaks first.

---

### Post by Thewhistlingwind on 2012-03-11
Once you're rooted the game is over. So even an effective AV can only tell you that your rooted or that the package you are about to install is malware. Short of offsite backups with a checksum to match against your root directory to prove what has and hasn't been tampered with a reinstall will be involved. An AV is a security tool, but it's not something that will really help you in a lot of situations. You should focus more on whitelist based security applications like noscript and apparmor.

---

### Post by jerome1232 on 2012-03-11
> **0011235813 said:**
> 
A little off-topic, but have you heard that updates that fix old security flaws can cause new ones?... I've heard some system admins deliberately refuse to install updates unless they know **exactly** what it does, and there is no other way to achieve it than via the update.

Leaving yourself open to a known old vulnerability for fear of the fix possibly opening a new unknown vulnerability sounds idiotic to me...

---

### Post by 0011235813 on 2012-03-12
> **Thewhistlingwind said:**
> Once you're rooted the game is over. So even an effective AV can only tell you that your rooted or that the package you are about to install is malware. Short of offsite backups with a checksum to match against your root directory to prove what has and hasn't been tampered with a reinstall will be involved. An AV is a security tool, but it's not something that will really help you in a lot of situations. You should focus more on whitelist based security applications like noscript and apparmor.
Yes, I agree. Hardening the browser with NoScript, Adblock and WOT is far more effective than installing the magical malware protector...
> **jerome1232 said:**
> Leaving yourself open to a known old vulnerability for fear of the fix possibly opening a new unknown vulnerability sounds idiotic to me...
Yes I was just saying that not all updates are "fixes" and that some sysadmins will have figured out how to protect against that threat anyway... But I do agree.

---

### Post by CharlesA on 2012-03-12
> **jerome1232 said:**
> Leaving yourself open to a known old vulnerability for fear of the fix possibly opening a new unknown vulnerability sounds idiotic to me...

Perhaps. I've seen sysadmins install a *nix box, harden it and just leave it. I think their thing is that if it works, don't break it.

---

### Post by OpSecShellshock on 2012-03-13
As far as a lot of shops are concerned (from the admin or management perspective that is) down time is down time regardless of whether it's due to being owned or due to patches being applied. As a security guy it kind of makes my skin crawl, but I understand where they're coming from.

---

### Post by jerome1232 on 2012-03-13
Oh I understand there are valid reasons for waiting to update (Like thoroughly testing the updates with your configurations etc...) I just can't wrap my head around the particular one reason I quoted earlier.

---

