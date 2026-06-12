---
title: "How often should I update my server?"
date: 2010-07-08
forum: Server Platforms
---

### Post by Saorex on 2010-07-08
Hi guys. I'd like your thoughts on when should I apply updates (apt-get upgrade) on my Ubuntu Server 10.04 machine. It is used as an intranet server which mostly runs Flex 3 and 4 applications.

Should I do all upgrades right away but keep away from dist-upgrades? Should always do both? Or should I let the server as it is and let it run?

I'm aware there is no black or white answer to this question, but any thought you might have on the subject is welcome.

Thanks!

---

### Post by Lucky. on 2010-07-08
Just my opinion only - if it's not exposed to the world and your clients are trustworthy or too ignorant to attempt a hack, leave it be and only update when you absolutely need to.

If it's got a port exposed to the net - update as often as possible.

---

### Post by sh1ny on 2010-07-08
First things first :

Use "do-release-upgrade" instead of "apt-get upgrade" and/or "apt-get dist-upgrade". Why ? Well if someone took their time to write the tool and if ubuntu folks put it in their instructions, it must be for a reason :D

Then :

When installing ubuntu server choose "Install security updates automatically". I've been using this option for 2 years and it never screwed anything. If you had already skipped this, you can do "dpkg-reconfigure unattended-upgrades". I'd check updates once a week and see if there's anything worth installing and if there is, i'd schedule a possible downtime ( if there's a new kernel or such ) and then upgrade when the time comes.

On the distro to distro upgrade :

With 10.04 out, my suggestion is to stick to it for the next 2 years, *unless* a new feature comes to 10.10 - 11.10 that you *really* need. Less headache - better service ! :)

---

### Post by subba9000 on 2010-07-08
upgrade you server ok

---

### Post by Drenriza on 2010-07-08
A good advice.

Security updates, a good idea. But dont make major changes unless YOU RLY NEED TO.

---

### Post by CharlesA on 2010-07-08
> **sh1ny said:**
> First things first :

Use "do-release-upgrade" instead of "apt-get upgrade" and/or "apt-get dist-upgrade". Why ? Well if someone took their time to write the tool and if ubuntu folks put it in their instructions, it must be for a reason :D

That would be used when you upgrade to a different release (8.04 to 10.04), not normal updates.

> When installing ubuntu server choose "Install security updates automatically". I've been using this option for 2 years and it never screwed anything. If you had already skipped this, you can do "dpkg-reconfigure unattended-upgrades". I'd check updates once a week and see if there's anything worth installing and if there is, i'd schedule a possible downtime ( if there's a new kernel or such ) and then upgrade when the time comes.

I've got mine set to install security update automatically and it doesn't reboot by itself or anything. The only thing it does is notify you that a reboot is required when you log in.

You can always upgrade everything, including the kernel, but wait to reboot until the off hours, so you can ensure that everything is working as intended.

---

### Post by sh1ny on 2010-07-08
> **CharlesA said:**
> That would be used when you upgrade to a different release (8.04 to 10.04), not normal updates.



I've got mine set to install security update automatically and it doesn't reboot by itself or anything. The only thing it does is notify you that a reboot is required when you log in.

You can always upgrade everything, including the kernel, but wait to reboot until the off hours, so you can ensure that everything is working as intended.

Isn't that what i said ?

---

### Post by Saorex on 2010-07-08
Thanks for you opinions guys. I'll have a look at "do-release-upgrade", I wasn't aware of its existence.

I might go with "do all updates" on every 2-3 weeks early in the morning so it doesn't affect too much people.

... and yes, I'll stick with 10.04.

---

### Post by QIII on 2010-07-08
As stated above "do-release-upgrade" is used to upgrade to the next  version of Ubuntu when it is released.  Do not use it for any other  purpose.

---

### Post by ptn107 on 2010-07-08
I just modify /etc/apt/apt.conf.d/50unattended-upgrades and change:
```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu lucid-security";
//	"Ubuntu lucid-updates";
};
```
to
```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu lucid-security";
	"Ubuntu lucid-updates";
};
```
and forget about it.
The server will update itself (both bug fix and security updates).  You'll be notified on login if it needs a restart.

---

### Post by CharlesA on 2010-07-08
Interesting. I didn't think you could do that.

---

### Post by Vegan on 2010-07-08
I update my server regularly, this way security is at its best.

---

### Post by Saorex on 2010-07-09
> **ptn107 said:**
> I just modify /etc/apt/apt.conf.d/50unattended-upgrades:
```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu lucid-security";
	"Ubuntu lucid-updates";
};
```
and forget about it.
The server will update itself (both bug fix and security updates).  You'll be notified on login if it needs a restart.

Interesting. I'll try it out as soon as I have a minute. Thanks a lot.

---

### Post by Saorex on 2010-09-30
Well, it took me a while, but I implemented ptn107's solution and I can't make it work.

Is there anything special I have to do other than create and modify "/etc/apt/apt.conf.d/50unattended-upgrades" ?

On Monday I installed like 50 updates and had to restart the server after that. I thought the "unattended upgrades" would start working after that, but they don't. I logged into the server this morning and got that message:

> 3 packages can be updated.
3 updates are security updates.

Any help would be greatly appreciated. Thanks!

---

