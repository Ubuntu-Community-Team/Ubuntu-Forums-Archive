---
title: "Ubuntu security - package review process"
date: 2010-07-27
forum: Security
---

### Post by Plus1Life on 2010-07-27
If this belongs in the Water Cooler section, I apologize. Please move if so.

Higher pay grades than myself have suggested a move to Ubuntu rather than Debian. I speak Engineer and not Managerialez ;) so I do not get far with them. I asked a few questions in the Installation and Upgrades forum. I dug up confirmation when I never got responses, but it lead me to question somethings.

They question Debian now because one person made a joke about where it is produced (made up, but they flocked on it). Funny part is that gentleman no longer works with us, talk about rolling a ball down hill. The move to Ubuntu would generally be easy enough, but nothing outside of main is security reviewed by Ubuntu Security Team. Hence another problem where Debian's main repository is bigger.

I think I have had a faulty assumption for years. I have believed all of main in Debian was under Debian Security Team review. No one else on our team knows if this statement is true. 

Dose anyone know if all of Debian main is Security Reviewed?

To move to Ubuntu would have us compiling a lot of software from source and Change Controlling it since it is in the universe. That is a lot of person-power that we are reviewing.

Any help, thoughts or ideas?

---

### Post by bodhi.zazen on 2010-07-27
You probably should have chosen a better title and probably posted in the security section.

I suggest you start here :

[https://wiki.ubuntu.com/SecurityTeam/FAQ](https://wiki.ubuntu.com/SecurityTeam/FAQ)

> 

[LIST]
[*]What does official security support mean?
[LIST]
[*]Members of the Ubuntu Security team are [Canonical]("http://www.canonical.com/") employees who provide [security updates]("https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase#Announcements")  for supported software in the Ubuntu distribution. Security updates are  in part prioritized based on severity of impact, exploitability and  number of affected users.
[/LIST]
 
[*]What software is officially supported by the Ubuntu Security team?
[LIST]
[*]Ubuntu is currently divided into four components: main, restricted, universe and multiverse. Packages in main and restricted are supported by the Ubuntu Security team for the [life of an Ubuntu release]("https://wiki.ubuntu.com/TimeBasedReleases"), while packages in universe and multiverse are supported by the Ubuntu community.
[/LIST]
 
[*]Who can receive official support?
[LIST]
[*]Official  support is provided free of charge to all users of Ubuntu during the  life of an Ubuntu release. You can see the release schedules in [Releases]("https://wiki.ubuntu.com/Releases").
[/LIST]
 
[/LIST]

[LIST]
[*]I would advise you contact the security team directly if you have additional questions.
[/LIST]
I would do the same with Debian.

---

### Post by Plus1Life on 2010-07-27
Thank you, greatly.

I am open to trying many communication pathways. We are pressed for time for the presentation, so I hoped there might be a security nut or two floating in the forums. :)

Perhaps the new title is more direct? Drat, we can't move our own threads.

---

### Post by Iowan on 2010-07-27
Use the "Report abuse" button (slightly misnamed ;)) to contact a moderator who can move, rename, etc.

---

### Post by Plus1Life on 2010-07-27
> **Iowan said:**
> Use the "Report abuse" button (slightly misnamed ;)) to contact a moderator who can move, rename, etc.

Thank you :p

---

### Post by bodhi.zazen on 2010-07-27
> **Plus1Life said:**
> Thank you :p

I moved and retitled the thread for you. I suggest you take a look at the sticky at the top of this forums as well.

---

### Post by Bachstelze on 2010-07-28
> **Plus1Life said:**
> 
Dose anyone know if all of Debian main is Security Reviewed?


"Security reviewed" means different things in the context of Debian and Ubuntu.  In Ubuntu, as the text copied by bodhi.zazen says, packages in main and restricted are reviewed (for security and otherwise) by paid employees of Canonical, and packages in universe and multiverse are reviewed by the community.  In Debian, there is no supporting company with paid employees to review any package, it is purely a community project.  What this means is that packages in Debian's main are reviewed in roughly the same way as packages in Ubuntu's universe/multiverse, and there is nothing like Ubuntu's main in Debian.

---

