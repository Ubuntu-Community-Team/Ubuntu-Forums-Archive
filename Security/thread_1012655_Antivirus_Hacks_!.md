---
title: "Antivirus Hacks !"
date: 2008-12-16
forum: Security
---

### Post by 3dmatrix on 2008-12-16
Kindly read the article at the following links.

[http://timesofindia.indiatimes.com/articleshow/msid-3843100,prtpage-1.cms](http://timesofindia.indiatimes.com/articleshow/msid-3843100,prtpage-1.cms)
[http://www.ivizsecurity.com/Antivirus-page1.html](http://www.ivizsecurity.com/Antivirus-page1.html)

Can this security hole create any problem for Linux users esp. because ClamAV is also mentioned in the list.

---

### Post by hyper_ch on 2008-12-16
don't run antivirus on linux :)

---

### Post by gtdaqua on 2008-12-16
> **3dmatrix said:**
> Kindly read the article at the following links.

[http://timesofindia.indiatimes.com/articleshow/msid-3843100,prtpage-1.cms](http://timesofindia.indiatimes.com/articleshow/msid-3843100,prtpage-1.cms)
[http://www.ivizsecurity.com/Antivirus-page1.html](http://www.ivizsecurity.com/Antivirus-page1.html)

Can this security hole create any problem for Linux users esp. because ClamAV is also mentioned in the list.

The times of india article you got above quotes: "When the email is scanned by the vulnerable antivirus software it either crashes the antivirus software or executes arbitrary code". We have already seen this and as usual these kind of old stuff comes as new in our country.

We have already witnessed several viruses/worms that will crash the AV engine, block access to AV sites and MS updates. 

In one case, MS had to rename their server so customers could download the patch for the virus which was preventing access to that specific site. In fact, MS had to rely on Linux servers for this temporary but very important change.

Linq: [Microsoft Using Linux-Based Network]("http://www.newsfactor.com/perl/story/22171.html")

M$ changed this on Aug 15! Hope you know what I know!

So all in all, it is totally unrelated to Linux users. Only windows users/administrators got to worry about such problems.

---

### Post by 3dmatrix on 2008-12-16
Thanx gtdaqua hope this brings more people in the Linux safezone, esp in our country.

---

### Post by The Cog on 2008-12-16
I think it is relevant to Linux users. The articles don't appear to say what operating system is being attacked with these techniques, and at least some of those AV products have variants that can run on Linux. So there is a potential issue. 

Although I think it is most likely that the attacks target Windows machines, Linux users shouldn't get too complacent.

---

### Post by 3dmatrix on 2008-12-16
Dont you think the email attachments get automatically executed only by foolish email clients like outlook express.
Moreover, what about file executable permission ? The attachments in order to execute the code has to be in some text mime type dont you think Linux is smart enough to read the file headers and not decide by the file extension.

If at all one needs to take precaution about this then what should one prepare for ?

---

### Post by bodhi.zazen on 2008-12-16
I think the mistake that is made in these threads is to use the term "virus" interchangeably with "malware".

For the most part , Linux is not windows and viruses are not yet a part of linux malware.

To understand why, take a look at this article : 

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

Linux is not windows and, unlike windows, will not execute code based on an extension.

For an attachment to execute code you would first have to mark it as executable. Then you would have to run it as root to affect the system files.

In addition antivirus can do nothing to protect you from zero day exploits (the next virus to be developed = zero day exploit). It can only protect you against known viruses. If you are running an up-to-date system, then your system is already patched for known viruses, so again antivirus is irrelevant.

I suggest you check your windows antivirus technology at the door and learn Linux Security.

Start with the stickies and look into Apparmor, HIDS (OSSEC or similar), and NIDS (snort or similar). Most people that push Linux Antivirus software aer trying to sell you a product and many people blindly follow their advice without understanding what they are doing or looking at open source options, which are more effective then Linux antivirus anyways (I will take SELinux /Snort / OSSEC over any antivirus).

Now, as time passed, the situation may change and someone may develop some kind of linux virus that can not be easily patched. In that event I would consider antivirus, but not before.

---

### Post by gtdaqua on 2008-12-16
> **The Cog said:**
> I think it is relevant to Linux users. The articles don't appear to say what operating system is being attacked with these techniques, and at least some of those AV products have variants that can run on Linux. So there is a potential issue. 

Although I think it is most likely that the attacks target Windows machines, Linux users shouldn't get too complacent.

You are wrong, i am afraid! Linux doesn't need anitvirus. Along that line, if there is a virus that crashes anti-virus engines, then it becomes totally irrelevant to linux users because they don't need anti-virus. 

There are no known viruses for Linux that can automatically execute and crash the system. The article specifies nothing in particular so theoretically they may not even be talking abt Windoze! 

Vulnerability exploits are the only concerns of Linux Community.  They could be much more devastating than a virus for Linux users.

---

### Post by The Cog on 2008-12-17
I disagree. 

If you read the articles, it says that the attacks are targeting defects in antivirus scanner software. When the AV software scans a suitably malformed email, it crashes and can execute arbitrary code in the process. 

Now the article doesn't say whether the AV software targeted is a windows, mac or a linux version, and I guess they are probably targetting windows-based AV, but I don't see a technical reason why AV scanners in Linux should be immune. Such weaknesses have already been found and fixed in wireshark protocol dissectors, and I think I remember reading about fixes to similar weaknesses in snort. Such weaknesses have certainly been addressed in image rendering libraries in Linux, so although image rendering is not normally something that happens autonomously, it shows that such defects can exist in Linux systems.

Of course, on Linux there are things like user permissions restrictions, so to do much damage the malware code also has to find a local exploit to gain root, but the AV scanner software may at least provide a bridgehead for an attacker.

You argue that AV software isn't needed for Linux, but that doesn't mean it's never run on Linux. I have already pointed out that some of the named AV packages have Linux variants. Not only do recent Windows refugees feel a need to run AV software, but smart people also run AV scanners on Linux to cleanse email passing through between their users and the outside world. It is entirely possible that such corporate email cleaners may be targeted. In fact, owning a corporate email scanner could prove very valuable for competitors, and reading all a competitors email this way wouldn't even require a root exploit. Just send one email to the company and start reading everything their email server copies you on.

I think that weaknesses in email scanners like this could be very relevant to Linux users.

---

### Post by rasti121 on 2008-12-17
> **gtdaqua said:**
> You are wrong, i am afraid! Linux doesn't need anitvirus. Along that line, if there is a virus that crashes anti-virus engines, then it becomes totally irrelevant to linux users because they don't need anti-virus. 

There are no known viruses for Linux that can automatically execute and crash the system. The article specifies nothing in particular so theoretically they may not even be talking abt Windoze! 

Vulnerability exploits are the only concerns of Linux Community.  They could be much more devastating than a virus for Linux users.
Not exactly true. If you run a Linux server and your clients are using Windows, you have to scan the messages for them with an antivirus.

---

