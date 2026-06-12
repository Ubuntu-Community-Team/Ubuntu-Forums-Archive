---
title: "Apparmor Linux Security"
date: 2006-01-13
forum: Server Platforms
---

### Post by hod139 on 2006-01-13
Just an FYI.  I was reading Arstechnica today, and saw that Novell is opening up and releasing [AppArmor]("http://www.opensuse.org/Apparmor").  From their website, "AppArmor is an application security tool designed to provide a highly secure yet easy to use security framework for your applications. AppArmor proactively protects the operating system and applications from external or internal threats, even zero-day attacks, by enforcing good behavior and preventing even unknown application flaws from being exploited."

All that I know is that AppArmor was originally written by Immunix, has a performance overhead of 0-2 percent, and claims to be easier to maintain than Redhat's SElinux.

Has anyone used this before?  Is it overkill for "normal" desktop users?  Any other thoughts?

---

### Post by tcwitte on 2006-01-17
I have no experience with it, but it looks very promising -- I really like the approach of indicating e.g. what files a program may read or write. If overhead turns out not to be prohibitive it would be nice if AppArmor profiles would be packaged with programs to make it easy to enable it. And possibly to enable it by default.

---

### Post by arthur on 2006-05-12
Can it be installed for Ubuntu?
Anybody using it?

---

### Post by arthur on 2006-05-12
Can it be installed for Ubuntu?
Anybody using it?

---

### Post by nocturn on 2006-05-18
I don't think it works very well on Ubuntu yet, it's even disabled by default on SuSE.

---

### Post by Glut on 2006-05-19
There's been a fair amount of discussion on the ubuntu-hardened mailing list about apparmor, start in february: [https://lists.ubuntu.com/archives/ubuntu-hardened/](https://lists.ubuntu.com/archives/ubuntu-hardened/)
 A port probably will be available for edgy: [https://lists.ubuntu.com/archives/ubuntu-hardened/2006-May/000145.html](https://lists.ubuntu.com/archives/ubuntu-hardened/2006-May/000145.html)  Because I can get my 2c in: Personally I would prefer the effort be put into making SELinux accessible.

---

### Post by kwilliam on 2006-11-29
Any news on AppArmor? I just learned about it and was reading the wiki ([https://wiki.ubuntu.com/AppArmor]("https://wiki.ubuntu.com/AppArmor")).  Did AppArmor make it into Edgy, or is it slated for Feisty?

I find the project fascinating, because it's exactly the concept I thought was needed: a kernel feature that would prevent any old application or shell script from running "rm -r /*.*" (I think I got that right... it's not a command you use often. ;))  Also, since the One Laptop Per Child group announced that their applications will run in "walled gardens", I think application containment is an exciting topic that is finally getting addressed.

---

