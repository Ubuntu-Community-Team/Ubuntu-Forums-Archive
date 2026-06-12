---
title: "Set varying admin levels?"
date: 2022-07-01
forum: Security
---

### Post by supercar55uk on 2022-07-01
Is it possible to have varying levels of admin rights?

Such as:

Root - Full admin access
2nd Admin - Cant change root password but can do other things like install apps etc?
Normal users - Possible to restrict certain things like viewing the app store, viewing the sda etc?

Guess Im after some sort of group policy that I can define who does what etc?

Any help appriciated.

---

### Post by DuckHook on 2022-07-01
The answer is: absolutely yes. Security finesse is one of Linux's (and Ubuntu's) most important strengths.

Unfortunately, my own admin use case is pretty basic and I've never explored how to do what you've requested. You will have to wait for more knowledgeable members to chime in with details on how to actually do that.

In the meantime, you may want to have a look at the link in my sig: *Resources for Newcomers*

Pay especial attention to resources under "Free books for advanced GNU/Linux system administrators"

---

### Post by TheFu on 2022-07-02
> **supercar55uk said:**
> Is it possible to have varying levels of admin rights?

Such as:

Root - Full admin access
2nd Admin - Cant change root password but can do other things like install apps etc?
Normal users - Possible to restrict certain things like viewing the app store, viewing the sda etc?

Guess Im after some sort of group policy that I can define who does what etc?

Any help appriciated.

There are distros where this is easier than on Ubuntu.  But, ubuntu doesn't use a 'root' account, so there is little need to do anything more than limit which users have full sudo access.  All other levels can be restricted using the settings available in the sudoers file(s) which can be as relaxed or strict as you like. There are multiple examples in the sudoers manpage. userids, groupids, hostnames, netgroups, can all be used to limit which users, groups and system can run which commands as different, specific, accounts (not just the root userid).

I have no idea what a group policy is besides something made up by some other OS, but if you place Unix users into a group, that can generally be used to control access to anything.  There is a core concept in all Unix systems.  "Everything is a file", which means everything has an owner, group, ACLs, xattrs, and simple permissions.  By limiting which group can read or write or create specific files, we have amazing control over the system.  Like with MSFT, Canonical is most interested in making things work easily together. They often make reasonable security choices in doing that.  These forums are full of complaints about the difficulty getting a CIFS mount working, for example.

So, all of these things have been part of Unix over 25 yrs, some over 50 yrs, but getting them properly setup isn't something that 95% of the world does. It is usually just enterprise installations where this happens and they would use enterprise identify management solutions and custom built scripts to ensure the systems remain as configured.  That's where devops tools come in.

BTW, the normal term on Unix for what I think you are describing is called "role based administration".  Web search for that.  I suspect that SELinux makes configuration less hassle (with other hassles elsewhere), but since Ubuntu isn't an SELinux-based OS, if you really want that level of control, it would be best to choose a different distro.  

It is very possible to setup these role-based administration in such a way as to kick your userid out and prevent any access, so be very careful.  A broken sudoer config is bad for all sudoers.

---

### Post by supercar55uk on 2022-07-04
So what distro would you recommend to be best for role based administration?

---

### Post by #&amp;thj^% on 2022-07-04
Completly subjective, for what you ask of us.
My choice is Arch, why? >>>This is *my* choice for over 5 years now, I can hear others already moaning and griping and I don't care. :P
Arch Linux is a lightweight, flexible Linux distro. It offers excellent customization out of the box.**_ However, Arch Linux is not for beginners,_** and it should only be used by advanced users who already know the Linux operating system.

It is best suited for programmers or advanced Unix users. At the core, it is designed to follow a strict design principle, and this makes it hard to work with. So, if you are someone with an understanding of the system’s core operation, then the distro is for you.
It's built by you for you.
Fedora Silverblue is also a good one, but again the more exprience the better your results will be. (This is just good sense right?)
Another would be Rocky Linux
Rocky Linux is a fork of CentOS, intended as a “bug for bug compatible” drop-in replacement for CentOS. Its name is a tribute to late CentOS project co-founder Rocky McGaugh who has worked in high-performance computing for a long time.

---

### Post by TheFu on 2022-07-04
> **supercar55uk said:**
> So what distro would you recommend to be best for role based administration?

Solaris using NIS+.  I doubt that's the answer you seek.
[https://docs.oracle.com/cd/E18752_01/html/816-4557/rbactask-42.html](https://docs.oracle.com/cd/E18752_01/html/816-4557/rbactask-42.html)

Anyone looking for role-based administration is likely in an enterprise, that will leave about 3 possible Linux distros left for consideration.  Only those with formal, enterprise, support.  For servers, I think you are down to RHEL or SuSE and for desktops, only SuSE, but I don't think **any** Linux is up to the task of roles like Solaris is and has been for 15+ yrs.

---

### Post by #&amp;thj^% on 2022-07-04
> **TheFu said:**
>  I don't think **any** Linux is up to the task of roles like Solaris is and has been for 15+ yrs.

Completely absent in my mind when I posted ^^^^+1
I would also agree here as well, as long as we are talking in terms of Enterprise Only. ;)

---

