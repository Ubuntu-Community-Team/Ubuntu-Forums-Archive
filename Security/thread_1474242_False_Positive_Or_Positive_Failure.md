---
title: "False Positive? Or Positive Failure?"
date: 2010-05-05
forum: Security
---

### Post by munky99999 on 2010-05-05
Ok here's a hypothetical thought experiment. Lets go to virustotal. 

1st file uploaded is a game crack. Very commonly detected as a virus due to common packers and techniques; but often not actually a virus. For purpose of argument this is a known virus-free binary.

Virus Total reports 6/40 engines declare it as a virus. Among those, they are all small-time cheap products that nobody really has heard of.

Clearly this is a false positive. Understandable with heuristics and what have you. However this is a shame for those antivirus engines.

2nd file upload is a completely from scratch virus. It's specifically designed to defeat all antivirus, it's undetected, has never been released or have infected anyone. It will defeat all the bigname antivirus scanners.

Virus Total reports 6/40 engines declaring it as a virus. The exact same 6 noname cheap products nobody uses.

In this case it is an actual virus so it's not a false positive. However they are in a way not detecting it as a virus; so much as they detected the other as a virus.


What is it?

---

### Post by aysiu on 2010-05-05
It's antivirus being for all practical purposes useless as security.

I don't recommend antivirus to anyone, even Windows users. There is real security and then there is placebo. Antivirus is the ultimate computer placebo.

---

### Post by rookcifer on 2010-05-05
Who cares?  The AV industry is a sham -- it's about locking users into yearly payments whilst knowing full well that there's no end in sight to the virus threat.  It's a game of whack-a-mole and no one wins but the AV companies and the Eastern European cyber gangs.  And [studies]("http://en.wikipedia.org/wiki/Antivirus_software#Effectiveness") have shown AV software, even when fully updated, misses up to 70% of all threats.  I truly think history will show that AV software was one of the biggest scams in the modern age.  It's just that most non-computer people don't understand right now how big a sham it is (but they will as more and more people become computer adept).

The only way the virus problem will go away is if M$ stops making Windows users admins by default (Win7 does this finally, and it seems to already be having a positive effect).  Secondly, memory protections (DEP/ASLR) seem to be helping as they make exploits much more difficult (but not impossible as Pwn2Own showed).  Linux has had these protections for many years.  Thirdly, browsers should be sandboxed.  Google is setting the trend with Chrome in this regard (IE8 is sandboxed, even though it was bypassed at Pwn2Own.  Google's Chrome was not).  Firefox is falling behind here.

Again, the only true way to security is to stop giving people who have no idea what they're doing free reign of the entire system (root access).  This was M$'s fatal flaw from the start -- I understand *why* they did it, but they didn't think through the ramifications very well.  Now that they're trying to get away from it and join the *nix world, they are finding that many applications break since most third-party Windows developers still aren't accustomed to the user accounts.  This makes users turn UAC off and thus we're basically back to the bad old days.  *nix systems lock users down by default, but even still, *nix users are generally expert users and understand why it's being done and when to use root.  

I will call this Rookcifer's law: the amount of access a user has to a computer system should (in a perfect world) be directly proportional to his expertise and understanding of the system.

This is the problem with the "all users are superusers" mindset of Windows -- while it does make using the machine *easier*, it makes it much less secure.  It's like putting a 5 year old behind the wheel of an 18-wheeler.  This is why I keep my mother locked out of her own machine -- she is only given user access, no admin password and is only allowed to run a whitelisted set of apps (this is Windows 7, if it were Linux I probably wouldn't be so anal).  For her needs, this is perfect, as it would be for 80% of people out there.  Instead we give them admin access and the installing of cute screensavers and other knick knacks begins and massive botnets like Conficker emerge as a result.

---

### Post by SoFl W on 2010-05-05
> **rookcifer said:**
>  it's about locking users into yearly payments

Even the free anti-virus programs?

---

### Post by DZ* on 2010-05-05
> **munky99999 said:**
> In this case it is an actual virus so it's not a false positive. However they are in a way not detecting it as a virus; so much as they detected the other as a virus.
What is it?

Check this out --
[http://en.wikipedia.org/wiki/Positive_predictive_value](http://en.wikipedia.org/wiki/Positive_predictive_value)

---

### Post by OpSecShellshock on 2010-05-06
It's either luck or it's some of the smaller vendors seeing others identify the hash as malicious out on VT and then adding it to their own signatures (not exactly a good method of analysis, and something that VT is not supposed to be used for, but it happens).

On some systems, anti-virus software is at best one component of a larger strategy for securing data. It starts with the user understanding risks and how the system works. When that fails (as it tends to) you have permission restrictions. When those are circumvented you have anti-virus. I'm oversimplifying, but the point is that AV researchers work really hard, have a lot to do at any given time, and are not really meant to be leaned on as a first and last line of defense for anything.

---

### Post by wilee-nilee on 2010-05-06
> I will call this Rookcifer's law: the amount of access a user has to a computer system should (in a perfect world) be directly proportional to his expertise and understanding of the system.

Lol, self appointment, I'm kneeling before your majesty.

---

### Post by bodhi.zazen on 2010-05-06
> **munky99999 said:**
> Ok here's a hypothetical thought experiment. Lets go to virustotal. 

1st file uploaded is a game crack. Very commonly detected as a virus due to common packers and techniques; but often not actually a virus. For purpose of argument this is a known virus-free binary.

Virus Total reports 6/40 engines declare it as a virus. Among those, they are all small-time cheap products that nobody really has heard of.

Clearly this is a false positive. Understandable with heuristics and what have you. However this is a shame for those antivirus engines.

2nd file upload is a completely from scratch virus. It's specifically designed to defeat all antivirus, it's undetected, has never been released or have infected anyone. It will defeat all the bigname antivirus scanners.

Virus Total reports 6/40 engines declaring it as a virus. The exact same 6 noname cheap products nobody uses.

In this case it is an actual virus so it's not a false positive. However they are in a way not detecting it as a virus; so much as they detected the other as a virus.


What is it?

Those are the limitations of antivirus, or any rules based security system, such as rkhunter, chkrootkit, snort, etc, etc ...

They can alert you to potential known threats, but there will always be false positives (they err on the side of caution and expect the user to then investigate, this is true of all such systems, Linux or Windows).

These tools offer no protection against [Zero Day Exploits]("http://en.wikipedia.org/wiki/Zero-day_attack"), which is part of why aysiu calls it a placebo.

Last, Linux is not windows, and as you system was patched against known exploits long ago you will detect 99.999 % false positives.

Learn to use Linux security tools such as Apparmor, SELinux, OSSEC, etc for [HIDS]("http://en.wikipedia.org/wiki/Host-based_intrusion_detection_system").

There is no HIDS tool that can prevent the administrative user (root in Linux) from comprising a system, either by direct action or via Social Engineering.

---

### Post by rookcifer on 2010-05-06
> **bodhi.zazen said:**
> Learn to use Linux security tools such as Apparmor, SELinux, OSSEC, etc for [HIDS]("http://en.wikipedia.org/wiki/Host-based_intrusion_detection_system").

AppArmor and SELinux aren't really HIDS -- they are types of Mandatory Access Controls (Selinux more so than AppArmor as it's RBAC and MLS capable).  A HIDS would be Tripwire or AIDE.  Actually, AppArmor is sometimes called a HIPS since it's not a classical MAC and doesn't do MLS, etc.  IMO, both the terms HIDS and HIPS, are not very descriptive and have different definitions depending on who is asked.

> There is no HIDS tool that can prevent the administrative user (root in Linux) from comprising a system, either by direct action or via Social Engineering.

Actually AppArmor, SELinux (and other MAC systems) *can* confine root users, but I understand what you're saying.  I am just being a bit pedantic, I admit. :)

---

### Post by bodhi.zazen on 2010-05-06
> **rookcifer said:**
> Actually AppArmor, SELinux (and other MAC systems) *can* confine root users, but I understand what you're saying.  I am just being a bit pedantic, I admit. :)

You made excellent point and I do not disagree with your terminology.

I understand apparmor and selinux can restrict root, but, root can also disable both (or if you are using strict rather then targeted you need to log in as root the adminstrator not root the user).

---

### Post by munky99999 on 2010-05-06
> **DZ* said:**
> Check this out --
[http://en.wikipedia.org/wiki/Positive_predictive_value](http://en.wikipedia.org/wiki/Positive_predictive_value)

Perfect link for what I was looking for. Thanks.

<general thread response>
Also yes I was aware of all the other security topics as mentioned in the thread. Such as apparmor and the principal of least privilege.


> I will call this Rookcifer's law: the amount of access a user has to a computer system should (in a perfect world) be directly proportional to his expertise and understanding of the system. 

Gotta love appointing yourself to a half-century old principal.

> Who cares? The AV industry is a sham
I can get behind heuristics as a sham. I wouldnt say definition-based-antivirus scanners as a sham.

---

### Post by aysiu on 2010-05-06
> **munky99999 said:**
> 
I can get behind heuristics as a sham. I wouldnt say definition-based-antivirus scanners as a sham. Just of very limited practical use to secure a system.

---

### Post by rookcifer on 2010-05-07
> **munky99999 said:**
> I can get behind heuristics as a sham. I wouldnt say definition-based-antivirus scanners as a sham.

Definition based on-demand scanners can come in handy when using **Windows**, but they are worthless on any *nix system.  

And they are only helpful on Windows when one needs to install an untrusted binary they downloaded from some shady website.  Even then, the evidence shows they are ineffective at detecting malware 70% of the time (depending on the scanner).  So, if you use Windows, download untrusted apps, and want to be safe 30% of the time, then yes, AV is for you.  ):P

Otherwise, I stick by what I said before: It's a sham.

---

### Post by OpSecShellshock on 2010-05-07
A few years ago having a malware binary that was coded such that you couldn't tell what it would do until after it was done was kind of a novel and innovative concept. Now it's a baseline. Still, on a Windows system it's better to scan stuff than to not scan it, but only a little.

---

