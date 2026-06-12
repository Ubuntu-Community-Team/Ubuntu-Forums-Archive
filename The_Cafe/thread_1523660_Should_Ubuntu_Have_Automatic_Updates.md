---
title: "Should Ubuntu Have Automatic Updates?"
date: 2010-07-04
forum: The Cafe
---

### Post by chessnerd on 2010-07-04
Should it?

---

### Post by SmittyJensen on 2010-07-04
i know i wouldn't like it because if you update certain components and don't restart immediately it causes issues.

---

### Post by steveneddy on 2010-07-04
You can set that option in

System --> Administration --> Software Sources

Click the buttons for

**Install security updates without confirmation**

and

**Download all updates in the background**

---

### Post by khuttger on 2010-07-04
Heck no, I like manually doing it.

---

### Post by ssulaco on 2010-07-04
> **khuttger said:**
> Heck no, I like manually doing it.
Only notify about available updates ;)

---

### Post by chessnerd on 2010-07-04
I know that updates can be set up to install automatically, but it seems like it would be better for new users if they didn't need to even think about installing updates. While it may be annoying at times for Windows to nag about rebooting or for it to install updates before it shuts down/starts up it is rather nice that users don't even need to think about such things. They just happen.

The current default is just fine for most of us because we like working with computers, but might it be nicer if the default became the option and the option of "Install Security Updates Automatically" be the default so that new users are kept protected and up to date?

Plus, I think that option only does important and security updates, not recommended ones, similar to how the Windows automatic updates works.

> **khuttger said:**
> Heck no, I like manually doing it.

So do I. ;)

I would set it back to manual, but I think that for newbies it would be better to have it automatic.

---

### Post by NightwishFan on 2010-07-04
I like the few simple and decisive options they offer now. I set my friends computer to automatic updates weekly. I set mine to download in the background. Because I will probably want to install them but I have to review them and the change logs first.

---

### Post by undecim on 2010-07-04
I think the option should be available at install-time.

I think the ideal setup for new users would be to install important security updates automatically, and give dialog once per week (or another configurable frequency) to install other updates.

---

### Post by NightwishFan on 2010-07-04
> **undecim said:**
> I think the option should be available at install-time.

That is a good idea, though I bet if implemented it would be the target of criticism.

---

### Post by betrunkenaffe on 2010-07-04
No. While some might want it at install-time, there's already enough complaints about "too many questions".

yes, the option should be available and the default options work fine for myself, I never had issues figuring out how to install them or when I had them.

---

### Post by Elfy on 2010-07-04
> **NightwishFan said:**
> That is a good idea, though I bet if implemented it would be the target of criticism.

I installed opensuse the other day (at least I think it was opensuse that did it) that was part of the install procedure. 


Anything that ubuntu implements becomes a target for criticism, so much so that anything that could be a valid point becomes lost in the rest of it.

---

### Post by Lucifer The Dark on 2010-07-04
Perhaps the first time you boot up after installing it should give you the option to set updates to automatic or not, I prefer to just get the notification so I can see what it's going to update & decide whether I want to do it right then or leave it till later.

---

### Post by NightwishFan on 2010-07-04
> **forestpiskie said:**
> I installed opensuse the other day (at least I think it was opensuse that did it) that was part of the install procedure. 


Anything that ubuntu implements becomes a target for criticism, so much so that anything that could be a valid point becomes lost in the rest of it.

OpenSUSE installer is pretty cool.

*On topic*

I agree. Though I believe Canonical knows that the vocal minority is not always who should be listened to. The yahoo thing was blown out of proportion as well.

---

### Post by Dustin2128 on 2010-07-04
new users should be able to set a time, like 4 a.m., where updates automatically install. I, for one, prefer to have synaptic available at all times.

---

### Post by Troy Martin on 2010-07-04
I update stuff when I want stuff to be updated. Especially any kernel and/or system updates. I hate it when, on Windows, I'm working on something and I get a wonderful dialog telling me to reboot, let it reboot in 15 minutes, or postpone for a few hours. I like working without interruption, especially when I'm coding something in C or C++ under Ubuntu, my last safe haven from Windows' idiosyncracies.

--Troy

---

### Post by Khakilang on 2010-07-04
I prefer manual as I got limited bandwidth and update only when I need. I update it regularly like 2 to 3 time a week.

---

### Post by FuturePilot on 2010-07-04
> **chessnerd said:**
> 

Plus, I think that option only does important and security updates, not recommended ones, similar to how the Windows automatic updates works.


/etc/apt/apt.conf.d/50unattented-upgrades
```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu lucid-security";
//      "Ubuntu lucid-updates";

```

---

### Post by CharlesA on 2010-07-04
> **FuturePilot said:**
> /etc/apt/apt.conf.d/50unattented-upgrades
```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu lucid-security";
//      "Ubuntu lucid-updates";

```

Yup. You can set it to install security updates automatically during the install of Ubuntu Server. I've always had it set to do that and the worst that has happened is that it'll say *** reboot required*** when I log in via SSH. No big deal, since it does not reboot automatically.

---

### Post by Frogs Hair on 2010-07-04
Having had an issue with a kernel update with 9.10 , I check all updates prior to installation so I can remove the Nvidia driver before installing the new kernel  .  In general automatic updates are a good idea .

---

