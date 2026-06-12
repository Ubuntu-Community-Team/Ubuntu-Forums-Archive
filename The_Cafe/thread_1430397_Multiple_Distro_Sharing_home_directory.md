---
title: "Multiple Distro Sharing /home directory"
date: 2010-03-15
forum: The Cafe
---

### Post by thetaLord on 2010-03-15
I wanted to triple boot Ubuntu, Fedora, and openSUSE.
Each distro has it's own / directory. Separate partitions. But all of them should share the same /home directory.

Is that possible? All 3 distros sharing the same /home directory?
What will be the possible problems that will occur doing this kind of setup?
And, which one should I install first, then 2nd, then third? and why?

---

### Post by snowpine on 2010-03-15
You can't share a single /home *directory*, but if you create a separate /home *partition*, yes, you can share it. You will need a separate username for each distro so your settings don't conflict.

Here is a tutorial on installing Ubuntu with a separate /home partition: [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Or if you've already installed it and forgot to make a separate /home: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

HOWEVER, my personal preference in this case is to *not* create a separate /home for any of the distros. Instead, I install each distro to a single partition and create a separate *data* partition for my documents, music, etc., which I share by mounting it to /media/data in all 3 distros. This also means I can use the same username in all distros without any danger of conflicting settings.

It is matter of preference and an argument could be made for/against either method.

---

### Post by oldfred on 2010-03-15
Having a separate /home is only for upgrading from the same version to a newer version. System settings and program configurations may be based on different versions and not be compatible. Having different users may eliminate the conflict but has no advantage.

I agree with snowpine and have separate data partition(s) that I mount and linking into home so home looks the same but the data is elsewhere. I am converting my set up to a bash file that I can run for each new install, by listing and saving history of my commands.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of blog
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by thetaLord on 2010-03-16
> **oldfred said:**
> Having a separate /home is only for upgrading from the same version to a newer version. System settings and program configurations may be based on different versions and not be compatible. Having different users may eliminate the conflict but has no advantage.
[]("http://ubuntuforums.org/showthread.php?t=1405490")

Im confused. Does that mean, some distro specific system settings and program configurations are stored in /home directory? When I press CTRL+H in nautilus, there are other files hidden other than those i truly use and created myself. I don't know what those files are for. Are they system settings and program configurations? So, if that's the case, what will happen if i do a fresh install, or upgrade to latest version formatting "/boot" , and "/" partitions, leaving /home partition at is. What will happen to the system settings and program configurations stored in /home partition? Will they be upgraded also?

---

### Post by earthpigg on 2010-03-16
> [QUOTE]Having a separate /home is only for upgrading from the same version to a newer version. System settings and program configurations may be based on different versions and not be compatible. Having different users may eliminate the conflict but has no advantage.
Im confused. Does that mean, some distro specific system settings and program configurations are stored in /home directory? When I press CTRL+H in nautilus, there are other files hidden other than those i truly use and created myself. I don't know what those files are for. Are they system settings and program configurations?[/QUOTE]

no, he is talking about different versions of the same program on different distros.

ie: is firefox's ~/.mozilla from 3.0 compatible with 3.5? can ff 3.0 accurately read the data from ~/.mozilla after 3.5 has changed it?

i have no idea, maybe.

and that same "maybe" will apply to every single program you have.

---

### Post by madjr on 2010-03-16
this will come in handy :D

---

