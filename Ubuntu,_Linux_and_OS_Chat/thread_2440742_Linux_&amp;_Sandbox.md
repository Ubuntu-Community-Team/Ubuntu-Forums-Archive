---
title: "Linux &amp; Sandbox"
date: 2020-04-14
forum: Ubuntu, Linux and OS Chat
---

### Post by bionic3epl on 2020-04-14
So basically Linux OS & Company (All other Linux OSs) is a Giant Sandbox Application OS where apps/snaps can run w/ limited or restricted access to main resources?

---

### Post by DuckHook on 2020-04-14
It is invariably a mistake to try boxing highly complex systems with multiple goals into one-line overly simplistic summaries, and so it is with Linux.

Linux runs everything from Desktops to smartphones to supercomputers to cars to spacestations to refigerators to stock exchanges to doorbells. How can something so vast, varied and amorphous be shoehorned into such a small definition?

---

### Post by CatKiller on 2020-04-15
> **bionic3epl said:**
> So basically Linux OS & Company (All other Linux OSs) is a Giant Sandbox Application OS where apps/snaps can run w/ limited or restricted access to main resources?

No.

---

### Post by DuckHook on 2020-04-15
Not a help request.

*Thread moved to **Ubuntu, Linux and OS Chat** as the more appropriate forum.*

---

### Post by TheFu on 2020-04-15
> **bionic3epl said:**
> So basically Linux OS & Company (All other Linux OSs) is a Giant Sandbox Application OS where apps/snaps can run w/ limited or restricted access to main resources?

It can be, but doesn't have to be. It isn't commonly used in that way today, since relatively few software packages are actually being deployed in the constrained snap packages.  There are flaws with the attempted forced constraint solutions that don't allow local choice control. Trying to control an open desktop OS like it is a cell phone is a flawed strategy, especially on systems with low RAM, small storage and limited CPU.  The snap team has forgotten there are plenty of people using single core, 2G RAM, and 16G storage systems today.

If you want a constrained container for each app, you can set that up outside snap packages, but you don't have to.  There are a few (perhaps 10) different tools to make that a little easier.  It is also easy with some of them to create a useless system due to being over constrained.

---

### Post by grahammechanical on 2020-04-16
How do we know that an application does not contain code that will do nasty things to our OS. If the application is Free Open Source Software (FOSS) we can download the source code and browse through it looking for malicious code. I imagine it would be vary time consuming.

Another way is to have a program called AppArmor installed. Ubuntu has this by default.

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

Ubuntu's Snap package format tries a different approach. The developer of the application has to fill in something called a manifest that lists the actions and access that the application wants. Once the application is packaged as a snap and installed if it tries to do something not in the manifest it is blocked from carrying out that action. This is my understanding of the way snap applications are contained. 

I do not agree that Linux distributions are a giant sandboxed application OS. They are still far from that. Not only do we need applications that are contained but the OS itself has to be shielded much better than it at present is. As the Windows OS is more numerous it is the main target of malicious hackers. So, we fortunate few using Linux are protected because scamming Linux users is not so profitable as scamming Windows users. 

So, until we are only allowed to install applications that are packaged in one of the packaging formats that contain the application we will be dependent on the trustworthiness of Linux application developers.

Regards

---

### Post by DuckHook on 2020-04-17
> **grahammechanical said:**
> …As the Windows OS is more numerous it is the main target of malicious hackers. So, we fortunate few using Linux are protected because scamming Linux users is not so profitable as scamming Windows users.
This was the old theory and it is still circulated today as the reason that Linux is targeted less often. But this old paradigm has been rendered obsolete by the explosive growth of Linux into all walks of life. These days, compromising the Linux ecosystem is much more lucrative to bad actors than compromising Windows. A bad actor can extort at most a couple of hundred bucks holding individual Windows users to ransom, more if they can successfully encrypt an entire Windows network, but not by a massively higher amount.

The really valuable data now resides on Linux foundations, whether it's banks, stock exchanges, mid to large corporations, intellectual property or the cloud. These are almost all Linux-based. Therefore, the most lucrative payoff involves compromising Linux systems.

And it's happening. Blackberry just reported a severe coordinated espionage campaign that has been active for the last decade:
[https://www.techrepublic.com/article/blackberry-chinese-cybercriminals-target-high-value-linux-servers-with-weak-defenses/](https://www.techrepublic.com/article/blackberry-chinese-cybercriminals-target-high-value-linux-servers-with-weak-defenses/)
[https://www.blackberry.com/us/en/forms/enterprise/decade-of-the-rats](https://www.blackberry.com/us/en/forms/enterprise/decade-of-the-rats)

The sorts of IT "crime" that most users are focused on are really the equivalent of street muggings and break-&-enters: the petty crimes of the IT world. They are painful to the individuals who are victimized, but as crimes, they remain of the petty sort. In contrast, the sorts of crime that affect us collectively are like those exposed by Blackberry. They are far larger and their pain is shared by all. In my opinion, they are also far more damaging to our society, though perversely ignored by common folks.

As for those petty crimes that are the IT equivalent of street muggings? I don't think the old theory is correct here either. It is almost as easy to infect a Linux installation as it is a Windows one. And, as I've already stated, on the whole, it would be more lucrative because Linux installations are more heavily representative of enterprise-critical uses including those where just one infection would cripple a whole network.

The reason that fewer Linux users are infected is because Linux users are more informed and geeky than Windows users. If we were as uninformed and security delinquent as the average Windows user, we would be just as infected. Equally, if Windows users were to magically become as informed and security conscious as the average Linux user, Windows infections would drop to a tiny fraction of their current rate.

---

