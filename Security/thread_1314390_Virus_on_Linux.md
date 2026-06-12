---
title: "Virus on Linux?"
date: 2009-11-04
forum: Security
---

### Post by Jean-Danjou on 2009-11-04
Bonjour,
I was browsing the web when I found this page:
[http://nuclear-imaging.info/site_content/2009/02/17/linux-aint-virus-free-no-more/](http://nuclear-imaging.info/site_content/2009/02/17/linux-aint-virus-free-no-more/)
And I was wondering, as I am new to Linux, how accurate and true is this post?
Thanks for the reply.

---

### Post by duanedesign on 2009-11-04
I have never had any problems with viruses, and i dont know anyone who has while using Ubuntu. Not saying it doesnt/cant happen. Given the right set of circumstances anything can happen. A nice set of AppArmor profiles and a correctly configured browser...I know someone who can explain it better than me.

[Ubuntu Security ]("http://ubuntuforums.org/showthread.php?t=510812")

[Firefox Security]("http://ubuntuforums.org/showthread.php?t=671604")

---

### Post by m4tic on 2009-11-04
That is not true, it will take a supercomputer many years to kill Linux. What that guy pointed out is similar to you going to a folder and clicking delete, only this time you were blind folded. and even if there was a virus, every time it needed to change something in the system it will ask for your password, how embarrassing would that be for you.

---

### Post by cariboo on 2009-11-04
That article has been discussed here many times. There is a lot of misinformation in the blog post. The exploit depends on social engineering to work. In other words, you personally have to install the exploit yourself, and it can't spread it self to other systems on it's own like a real virus can.

Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1120670&highlight=linux+virus").

I'll leave this thread here for a day or two, then move it to recurring, because this subject comes up so often.

---

### Post by Jean-Danjou on 2009-11-04
Thanks for the kind reply, and please excuse my paranoia as I come from a Mickeysoft Background!

Merci.

---

### Post by cdenley on 2009-11-04
I believe ubuntu now requires launchers to be executable, as I had suggested they do when this was discussed here previously. You can't simply double-click attachments or downloaded files to execute anything malicious. You would have to be dumb enough to extract then run malicious software from an archive, install a malicious package after entering your password in the package installer, change the permissions on your malicious software in order to allow it to execute, or do a "sh ./malware.sh".

There is no reason a malicous piece of software can't be written for Linux or any OS, but it requires social engineering to trick the user into executing it, which means it isn't a virus.

---

### Post by rookcifer on 2009-11-04
> **Jean-Danjou said:**
> Bonjour,
I was browsing the web when I found this page:
[http://nuclear-imaging.info/site_content/2009/02/17/linux-aint-virus-free-no-more/](http://nuclear-imaging.info/site_content/2009/02/17/linux-aint-virus-free-no-more/)
And I was wondering, as I am new to Linux, how accurate and true is this post?
Thanks for the reply.

Old news.  And the KDE team has already taken steps to fix this issue with 4.3.2.  Whenever you create a "desktop" file, it will not execute without first providing a warning that displays the exact command to be executed.

---

### Post by P4man on 2009-11-04
> **Jean-Danjou said:**
> Bonjour,
I was browsing the web when I found this page:
[http://nuclear-imaging.info/site_content/2009/02/17/linux-aint-virus-free-no-more/](http://nuclear-imaging.info/site_content/2009/02/17/linux-aint-virus-free-no-more/)
And I was wondering, as I am new to Linux, how accurate and true is this post?
Thanks for the reply.

An effective (propagating) virus for linux is something like the monster of lochness. Perhaps it exists or it is theoretically possible, but no one ever saw it, or at least the ones that claim to have seen it cant prove they saw it and tend to be unreliable witnesses with an agenda or looking for attention ;)

Thats not to say malware is impossible on linux, but by using signed repositories to download your apps and updates from, and security mechanisms inherent to the OS, the chance of ever getting one seems  theoretical at best.

Of course nothing will protect against user stupidity so enabling ssh or remote desktop with a 3 letter password will get you hacked.

---

