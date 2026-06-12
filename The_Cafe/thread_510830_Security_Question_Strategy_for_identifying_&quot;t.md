---
title: "Security Question: Strategy for identifying &quot;trusted&quot; software?"
date: 2007-07-27
forum: The Cafe
---

### Post by aysiu on 2007-07-27
In some recent discussions about security, I've seen people talking about users guarding against social engineering and advising people to not be dumb. The advice is usually to not use random scripts or install binaries if you don't know what they do.

So my question to the security experts out there: What are some good tips for discerning what software can be trusted and what can't?

Personally, I just stick to the repositories, but I know I'm atypical in that respect.

If you're not a programmer (hence, looking at the source code wouldn't really be a practical security measure), what are good indicators of something being trustworthy to run?

---

### Post by moffatt666 on 2007-07-27
I either stick with the repos or, if a program isn't available, I'll look for recomendations on the forums.  The community is a powerful tool!

---

### Post by az on 2007-07-27
> **aysiu said:**
>  What are some good tips for discerning what software can be trusted and what can't?

Personally, I just stick to the repositories, but I know I'm atypical in that respect.

If you're not a programmer (hence, looking at the source code wouldn't really be a practical security measure), what are good indicators of something being trustworthy to run?

I'm not a security expert, but I think that's a great question.

No, looking at the source each time you want to consider running an application is not realistic even if you are a developper.  Nobody does this.  Just a base system without a GUI represents several million lines of code.

But a lot of people do look at the code as a normal part of development.  I figure that if there is a big, dynamic and diverse group of people who are actively looking at that code (and questioning it) that increases the chances of malware getting detected.

Three big criteria I use to estimate that are the licensing, the author and the community.

1.  If it's not GPLed or GPL-compatible, I worry.  Other factors would have to come into play which would mean that plenty of people are actively looking at this code for me to feel comfortable in using it.  Example:  Sun Java.

2.  Who is the author?  Why was this written?  Why are they maintaining it?  For example, Mambo forked into Joomla because the author was a company who didn't care what the developers were wanting to do with the program.  Joomla good, Mambo not so good.

3.  How big is the community?  How active?  How are new ideas handled?  It's normal (even good) for people to come in, have fun and leave - how easily can that happen here?  It's normal for a small project to have a small and relatively slow development process.  But if you visit the homepage and the last release was in 2002, I would not only start to think of security issues, but compatibility problems.

Basically, anything that makes it into the repositories gets a passing grade for the above criteria.  If the package is not directly supported in Ubuntu, it's maintained by a Debian Developer or package maintainer.  It's not easy to become a DD and you can't maintain a package for Debian (for long) if you are incompetent.

---

### Post by aysiu on 2007-07-27
Those are exactly the kinds of replies I'm looking for. Thanks especially to az for the detailed explanation.

Any other suggestions?

---

### Post by izanbardprince on 2007-07-28
Someone tried to backdoor the Linux kernel once, and it was just pure luck that anyone caught it in time.

---

### Post by koenn on 2007-07-28
> **aysiu said:**
> Those are exactly the kinds of replies I'm looking for. Thanks especially to az for the detailed explanation.
Any other suggestions?
I usually stick to the repo's, and for the few exceptions, I usually get the software at the site that made it. For VMware I went to the VMware site. For a more recent version of OpenOffice, I'd go to the OOo website. Problem is that if they don't have debs, there's some manual labour involved. 
Other than that, I'd trust (active projects) on SourceForge or so. Sites such as SourgeForce or debian-backports etc can't really afford to get a reputation for distributing infected software, so anything dodgy would be taking off the site, i assume. Hopefully before I get there and download it. 

If I'm not too sure about a package, I install it in a virtual machine first. Not that I have the skills or the tools to really check for viruses/trojans and other malware, but at least if the package ruins the system or misbahaves (like pull in so many dependencies that it causes conflicts with other packages), i'll spot it before I run it on a real computer.

---

### Post by 5-HT on 2007-07-28
For me it comes down to 1) trusting the author(s) and 2) trusting that what you are downloading is exactly what they have released.

For 1), az made some great points.
For 2) I always check the gpg signature and message digests.

---

