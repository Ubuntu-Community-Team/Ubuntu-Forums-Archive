---
title: "I tried to update to the latest Ubuntu 23.04 &quot;Lunar Lobster&quot;"
date: 2023-07-26
forum: Ubuntu, Linux and OS Chat
---

### Post by retiredat44 on 2023-07-26
I tried to update to the latest Ubuntu 23.04 "Lunar Lobster" , and it messed up bad. I had to wipe the drive and start over, and put the last version back in, 22.04 LTS. It froze on install from the USB. I had no problems with the hardware with previous versions. Asus P8Z68 Pro, which I had replaced with newer faster computers

This is an FYI< and anyone else had install issues?

btw, I really don't post here much, as my main computers are not Linux. I could not find how to put my computer info into my profile or signature, if any.

---

### Post by guiverc on 2023-07-26
Ubuntu 22.04 LTS was the 2022-April release, and the end of the two year *development* cycle that started at the end of April 2020 (*after release of the prior 20.04 LTS*).

Ubuntu's full LTS development cycle occurs over two years, with the current *development* cycle starting in April 2022, and complete with the release of Ubuntu 24.04 LTS in 2024-April.

During that*two year* cycle, three *interim* (non-LTS) releases are provided that show the progress in the work; in effect the two year cycle is split into 4 smaller six monthly cycles.  Those releases being 22.10, 23.04 & 23.10.

Your initial post has you upgrading from 22.04 and *skipping* the 22.10 release which receives more QA testing, and the expectation is users will upgrade through all releases, or jump from one LTS to the next LTS (ie. 22.04 will upgrade to 24.04 **after** 24.04.1's release).

The upgrade from 22.04 to 23.04 did receive CI testing yes; is supported; but if you want a reliable upgrade path, I'd recommend sticking to the intended & QA tested upgrade paths, which is use every release (*no skips*) OR go from one LTS to the next LTS when it opens (ie. **after** release of the .1)

Maybe I'm missing something; you don't mention 22.10 & mention 22.04 near "*last version*" where 22.04 was two releases before 23.04 & not the *last* version.

FYI:  One of the things I *love* about Ubuntu is the ability to non-destructively re-install a Desktop system (inc. *flavors* that are actually easier), and whilst I don't know if you're talking about a Server or Desktop system; this non-destructive re-install is my backup for a *problematic* *release-upgrade*, though if I'm lacking time I often use it instead (*as its so fast*). Of course you may not be using Desktop systems, and may use other/different 3rd party apps thus may have different results to me.

---

### Post by DuckHook on 2023-07-26
Your MOBO is quite old. Therefore, running a standard release on it with their hamster wheel 6 month release cycles is not recommended. If I were you, I would stick with LTS releases only.

Frozen installs on old HW are all too common. Often this is caused by failing HW: bad RAM, bad HDD, bad MOBO, bad PSU&#8230;

These possible problems need to be eliminated as much as the OS, which rarely is the problem.

My ex&#8209;main box, now used only as fallback machine, is about the same age, a P9X79. I've had no problems installing any of the new LTS versions on it. I haven't tried any standard versions because I have no desire to invite trouble (or the running on the hamster wheel trying to keep up every 6 months).

Does the machine successfully get to a LiveUSB session? If so, then it obviously will run the OS, in which case, a stalled install might indicate a bad HDD. You do not mention other HW specs. How much RAM do you have? What GPU? Resource limitation is another reason for failed installs. So is corrupted install media. Be sure to check the integrity of your install media.

You do not need to post your computer info in your sig or profile. Just add it to the body of your post.

If you wish to turn this post from a FYI into a request for help, please self&#8209;report it and a staff member will move it to a proper technical help subforum.

---

### Post by coffeecat on 2023-07-27
> **retiredat44 said:**
> btw, I really don't post here much

Hardly surprising, as you created your account only 7 minutes before posting, but welcome to the forum anyway! :wink:

> **retiredat44 said:**
> I could not find how to put my computer info into my profile or signature

See: [https://ubuntuforums.org/showthread.php?t=2034393](https://ubuntuforums.org/showthread.php?t=2034393)

---

### Post by grahammechanical on 2023-07-27
> It froze on install from the USB.

Did you manage to get Ubuntu 22.04.2 installed and working? Depending on the options we choose the installer might require user input. Failure to tick a require box will cause the installer to stall until the user makes the choice needed.

Regards.

---

