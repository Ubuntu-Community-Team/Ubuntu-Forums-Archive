---
title: "Jailkit passwd etc."
date: 2008-03-06
forum: Security Discussions
---

### Post by NicklauZ on 2008-03-06
So is it possible for a jailkit user to somehow change his own password? I've tried to copy the passwd script to /jail, but seems like it's not so simple.

And I also have a few another questions: Is it possible to determine which programs and commands a non-root-user can use in a system? I mean is jailkit the easiest way for this or are there any other ways?? Also is it possible to prevent users from seeing all system files etc.

Somehow I just don't like the idea all shell users reading system files and using all possible commands/programs available. That's why I use jailkit now, but I'm considering to remove it if there are any other convenient ways.. 

Thanks for help!!

---

### Post by moonpup on 2008-03-06
Hi,

I've recently tried getting jailkit to work but have been unsuccessful in similar endeavors. On a bright note, the openssh team recently announced a new chroot feature that was just committed into the cvs tree.

The next openssh version should make it really easy to do a chroot, see here...

[http://undeadly.org/cgi?action=article&sid=20080220110039](http://undeadly.org/cgi?action=article&sid=20080220110039)

---

### Post by NicklauZ on 2008-03-06
> **moonpup said:**
> Hi,

I've recently tried getting jailkit to work but have been unsuccessful in similar endeavors. On a bright note, the openssh team recently announced a new chroot feature that was just committed into the cvs tree.

The next openssh version should make it really easy to do a chroot, see here...

[http://undeadly.org/cgi?action=article&sid=20080220110039](http://undeadly.org/cgi?action=article&sid=20080220110039)
Yeah, I've been hosting some shell accounts for my friends for irc (irssi) /fileserver etc. But the passwd thing is quite annoying since I have to set the passwords for the users myself.

---

### Post by moonpup on 2008-03-06
I see your point, but like I said in my other post email the developer as he is responsive and may be able to point you in the right direction. Good luck!

---

