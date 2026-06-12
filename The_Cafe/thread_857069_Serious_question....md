---
title: "Serious question..."
date: 2008-07-12
forum: The Cafe
---

### Post by Silpheed2K on 2008-07-12
I was wondering... I noticed some good replacements for Windows software..
but what I'm REALLY wondering is.. if GNU/Linux catches on... how would they prevent proprietary corporations from coming in and installing things in the startup or rootkits and protection schemes?

I'm just curious how this would even be dealt with?
cause GNU/Linux is known for its speed and I'm wondering if it became popular... how all the people, that make junk and install junk, would be handled? (cause this would slow the system down eventually making it act like Windows and such)

I'm really curious to know cause I noticed you need root access to install a LOT of things.
Anybody got any input?

---

### Post by Lord Xeb on 2008-07-12
That is a good question...

---

### Post by Barrucadu on 2008-07-12
I imagine it would be up to the user to not install anything like that.

---

### Post by shadylookin on 2008-07-12
There wouldn't be any protection. No one knows whats in proprietary software and if you give it root permission to run you're willfully letting it do whatever it wants. The nice thing though is that linux doesn't have a hidden registry so removing bad files wouldn't be as difficult 

Mostly people just have to learn that when you run something as root you're free reign over you're entire system and you shouldn't use programs you don't trust.

---

### Post by madjr on 2008-07-12
> **Silpheed2K said:**
> I was wondering... I noticed some good replacements for Windows software..
but what I'm REALLY wondering is.. if GNU/Linux catches on... how would they prevent proprietary corporations from coming in and installing things in the startup or rootkits and protection schemes?

I'm just curious how this would even be dealt with?
cause GNU/Linux is known for its speed and I'm wondering if it became popular... how all the people, that make junk and install junk, would be handled? (cause this would slow the system down eventually making it act like Windows and such)

I'm really curious to know cause I noticed you need root access to install a LOT of things.
Anybody got any input?

I think that looking at **macOS** is looking at linux in a few years.

We need to see what problem are arising in their platform and try to have barriers in place.

Every possible problem will hit their platform first and then pass on into linux (unless we do something)

**prevent before lament.**

a system like **Klik** or **[COLOR="RoyalBlue"]zeroinstall[/COLOR]** would help, software would not install system wide. Instead it would be stuck in the **user's home folder**

check this nice **comparison** of different systems for more details:

[http://0install.net/matrix.html](http://0install.net/matrix.html)


zeroinstall also has a few other handy security features and is cross distro

i would like to see more support given to the developer he works hard at it.

---

### Post by RudolfMDLT on 2008-07-12
At the moment you need a certain degree of intelligence and experience to install Ubuntu - and sudo annoys new users enough so that they go read up on it and discover that in reality it really is necessary.

But as Ubuntu is becoming more and more popular, it's creating a double edged problem. It is attracting more "stupid" users AND because of a wider user base, Ubuntu starts showing up on the radar of companies/people that specialize in getting malware installed on computers.

The good thing about Linux in general is that you can't really phone tech support! you need to search google or get involved on a forum. In the public space, people talk and if some company does include a root kit or malware, the news will spread much faster.

Also - Linux in general installs 90% of the app's from a controlled repo. If a good enough application comes along and people like it - it is usually included in the repo and so it stays within the closed loop of control. A malicious programmer/company will have a real hard time sneaking in some malware and keeping it there.

So even if Ubuntu becomes more popular than windows, it has a very good framework in place to keep most of its users safe from downloading crap.

---

### Post by Canis familiaris on 2008-07-12
I thought there was a way to fool those binary installers to think they are running in root environment when they are not.

---

### Post by scottuss on 2008-07-12
I think that systems like that only lets the installer think it's root for compatibility (sanity checks and such). I'm pretty sure it doesn't actually give it root permission i.e they can't do any real damage as they are not really root... AFAIK...

---

### Post by spupy on 2008-07-12
Two solutions come to mind:

1. As RudolfMDLT said, install only from repos. If the software library available becomes so bloated with crap software, maybe "private" repositories with quality selected software will appear.

2. Move to BSD. :P

---

