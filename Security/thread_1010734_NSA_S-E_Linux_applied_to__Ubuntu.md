---
title: "NSA S-E Linux applied to  Ubuntu??"
date: 2008-12-14
forum: Security
---

### Post by american.swan on 2008-12-14
I need some help.  I'd like to know if SELinux is already a part of Ubuntu.  Will be a part of Ubuntu.  Should I add it to my desktop?  How?  Viable?  Too restrictive?  Server only?  Step by step guide?  Will I find it in the repositories?  Hard to install, not for a novice?  Easy to install?  Opinions?  Not worth the effort? 

Sorry for my ignorance...doing forum search after posting this. 

Thanks for any and all feedback.

---

### Post by american.swan on 2008-12-14
[http://packages.ubuntu.com/intrepid/selinux-utils](http://packages.ubuntu.com/intrepid/selinux-utils)

Found this.  I'm looking now for some detailed information on desktop implementation of it.  I hope I can turn on the "strictest" settings.  Unsure how that would affect my computer.

---

### Post by bodhi.zazen on 2008-12-14
SELinux can be installed on Ubuntu, but AppArmor is installed by default.

I suggest you :

1. Consider looking into apparmor first (see my sticky).

2. If you want to take SELinux for a spin, try Fedora 10 (SELinux is installed and configured).

3. If you want to try strict, install Engarde Linux.

Note: Strict SELinux has a steep learning curve and restricts even the root user. I think you will be quickly frustrated unless you understand the basics first :

[http://linuxtopia.org/online_books/centos_linux_guides/centos_selinux_guide/index.html](http://linuxtopia.org/online_books/centos_linux_guides/centos_selinux_guide/index.html)

Engarde , Fedora, and Redhat (Centos) all have guides for SELinux.

Basically converting Ubuntu is easy, but you might wish to read up first.

---

### Post by HermanAB on 2008-12-14
The main purpose of SELinux is to provide mandatory access control that guarantees separation between data sets and streams of different classification levels.  Using SELinux, a machine can be configured such that it can process both Secret and Confidential data for example, without the Confidential data becoming automatically reclassified as Secret.

This is a problem peculiar to government and military systems and is not of much use to ordinary mortals.

Hope that helps!

Herman

---

