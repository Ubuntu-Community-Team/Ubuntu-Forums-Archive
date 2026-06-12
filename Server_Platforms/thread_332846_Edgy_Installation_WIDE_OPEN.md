---
title: "Edgy Installation WIDE OPEN"
date: 2007-01-06
forum: Server Platforms
---

### Post by zackr on 2007-01-06
I'm having some real problems with security on my Linux PCs.

Problem 1: Users have managed to figure out that 'HIbernate' means that when they turn the computer on again it will bypass ALL login prompts and take them straight to the desktop.

Solution to Problem: Must not involve merely removing the hibernate button. Since this applies to both Xubuntu and Ubuntu, I want an easy way to fix this on a fundamental level.

Problem 2: There are apparently other ways of getting in, either by finding out the password via system logs, or using Switch User when locked and the screen saver is playing, etc. It may not even be these ways (I'm unsure), but there are apparently 'other ways'. Yes, users have been boasting :evil: 

Solution to Problem: Suggest ways to minimize these problems, and a way to figure out how users are bypassing security points. Maybe a key logger? Setting up a surveillance system isn't practical, though it would help to maybe be made aware of any possible ways to intrude into a default X/Ubuntu installation with an auto-generated root password.

---

### Post by riven0 on 2007-01-07
Not sure about problem 2, but for hibernation; have you tried setting a BIOS password? When coming from hibernation it will always prompt you first for the BIOS password.

---

### Post by Akita on 2007-01-07
For hibernation, configure the box to lock the desktop when it hibernates. It'll come back up with the screen locked asking for the users password. I've only done this for individual accounts, but there should be a way to make it a system default.

---

### Post by KaeseEs on 2007-01-07
The beginnings of a solution to problem #2:


1)  Check /var/log/auth.log to see when your lusers are logging in, from where, and under which accounts.  This should give you a good picture of where your security hole is.

2)  Reconsider your current privelege scheme.  Do you have a root login, and to whom have you given either the root password or access via sudo?

3)  Reset all priveleged account passwords, and enforce a strong password policy for them hereafter.

    I'm assuming that your problem with user access in #2 is that lusers are gaining priveleges that they shouldn't have.  It's very, very unlikely that they've taken a technological route - this would encompass either code injection through a known security hole (which would mean you are employing script kiddies), or brute-force cracking /etc/shadow (which would entail the execution of a hash cracking program, hours of 100% CPU utilization per password to crack, and mean you are employing a moderately knowledgeable cracker who is comfortable on the UNIX command line).  

    Given this, your problem is most likely that 'social engineering' was used to gain access - somebody either guessed a password, saw where someone wrote it down, overheard it, or was told/given the pasword.  Solution #3 should solve this.  Solution #1 will help you track down and punish the guilty.  If they are evasive, use psychological warfare - I would suggest googling 'BOFH' for a primer.

---

