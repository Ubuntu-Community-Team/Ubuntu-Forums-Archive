---
title: "SELinux on Ubuntu"
date: 2010-05-07
forum: Security
---

### Post by km0r3 on 2010-05-07
Hey Forum,

I'm reading quite positive stuff about SELinux, but also negative things like sophisticated configuration.

Would you recommend SELinux on Ubuntu?

---

### Post by Bachstelze on 2010-05-07
> **km0r3 said:**
> Hey Forum,

I'm reading quite positive stuff about SELinux, but also negative things like sophisticated configuration.

Would you recommend SELinux on Ubuntu?

If you have to ask, I'd say SELinux is not for you. What do you want to do with it, exactly?

---

### Post by Jive Turkey on 2010-05-07
I advise agianst it unless you are already an expert in all of the most common scripting languages.  For Ubuntu, apparmor is the way to go.  Both SELinux and Apparmor act to restrict what various applications can do. Apparmor is significantly easier to configure IME.  In playing with SELinux on CentOS I found that I needed to learn some pretty hardcore regular expression and something else I forget now.  Its overkill for most people, but the sticky in Security Discussions here does a pretty good job of making understandable.

---

### Post by bodhi.zazen on 2010-05-08
If you want to try SELinux, I suggest Fedora.

Installing SELinux on Ubuntu has never been easy and often fails.

The tools to manage selinux policy are much easier then in the past as are the graphical tools.

[http://docs.fedoraproject.org/selinux-user-guide/f12/en-US/](http://docs.fedoraproject.org/selinux-user-guide/f12/en-US/)

Selinux is much more mature then apparmor and although selinux is more complex, you are unlikely to need to modify the selinux policies. If you do need to adjust the policies there are a numer of tools, both graphical and on the command line to assist you.

See Setroubleshoot for example.

Ubuntu uses Apparmor, see the sticky at the top of these forums. Apparmor is not as mature as selinux and most people suggest using a profile for all network aware applications.

There are no graphical tools to manage Apparmor profiles in Ubuntu, apparmor-notify will give you (graphical) alerts.

---

