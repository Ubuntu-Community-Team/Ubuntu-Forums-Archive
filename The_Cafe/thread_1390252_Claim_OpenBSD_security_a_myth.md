---
title: "Claim: OpenBSD security a myth"
date: 2010-01-25
forum: The Cafe
---

### Post by Sporkman on 2010-01-25
> An argument often made by proponents of OpenBSD is the extensive code auditing performed on the base system to make sure no vulnerabilities are present. The goal is to produce quality code as most vulnerabilities are caused by errors in the source code. This a noble approach, and it has worked well for the OpenBSD project, with the base system having considerably less vulnerabilities than many other operating systems.

Used as an indicator to gauge the security of OpenBSD however, it is worthless. The reason being is that as soon as a service is enabled or software from the ports tree installed, it is no longer the default install and the possibility of introduced vulnerabilities is equal to any other platform. Much like software certified against the common criteria, as soon as an external variable is introduced the certification, or in this case the claim can no longer be considered relevant...

[http://allthatiswrong.wordpress.com/2010/01/20/the-insecurity-of-openbsd/](http://allthatiswrong.wordpress.com/2010/01/20/the-insecurity-of-openbsd/)

---

### Post by foldingstock on 2010-01-25
This article is primarily a rant over OpenBSD not implementing a standard security / access control framework. 

In theory, these frameworks work well. SELinux and AppArmor, for example, can protect against a range of things including code running with root privileges. This method allows the ability to sandbox processes and severely reduce the risk of compromise.

The problem with these frameworks is that if an attacker manages to get control over what code is executed in kernel mode, they are useless. It is literally impossible for an in-kernel security framework to "lock down" code running at kernel level. 

Because of this, one cannot look at security frameworks as the be-all solution, it is merely another layer. OpenBSD would benefit from a security framework, as another layer of security, but for the projects primary goal this is not required.

---

### Post by Xbehave on 2010-01-25
IN kernel vulnerabilities FTL, however openBSDs claims to security are vastly overstated, having a secure default install by providing few services is all good and well but as soon as you start using any apps the lack of security framework makes it far less safe then a linux install.

---

### Post by juancarlospaco on 2010-01-25
I know that is secure, but i never believed their *"security"*, 
they say only 2 errors on coding becomes a security hole, its coded by humans,
and is not possible on so many lines of code dont get errors.
[I]
"Only two remote holes in the default install, in a heck of a long time!"[/I] say openbsd.org

I want something like USN or TechNet.

---

### Post by Daisuke_Aramaki on 2010-01-25
Plain bull****. The guy is obviously a moron, and he has been ranting his a** off even on openbsd mailing lists. and most people know that. 

So stop spreading the moron's BS for God's sake.

---

### Post by Daisuke_Aramaki on 2010-01-25
Have a look at daemonforums to get an idea.

---

### Post by foldingstock on 2010-01-25
> **juancarlospaco said:**
> I know that is secure, but i never believed their *"security"*, 
they say only 2 errors on coding becomes a security hole, its coded by humans,
and is not possible on so many lines of code dont get errors.
[I]
"Only two remote holes in the default install, in a heck of a long time!"[/I] say openbsd.org

I want something like USN or TechNet.

No one has ever claimed that OpenBSD code is 100% error-free. Such a statement would be uneducated at best. 

"Only two remote holes in the default install.." is a statement about remote exploits in the OS, not errors in the code. Since the OpenBSD default install is fairly locked down, it is quite believable that they have only experienced two remote holes in the past 10+ years.

---

### Post by juancarlospaco on 2010-01-25
IP stack/DNS got security holes/bugs how can they dont have it, 
its a fixed problem on IPv6 but i dont think that they are using IPv6, and no IPv4 by default.

---

### Post by Xbehave on 2010-01-25
> **juancarlospaco said:**
> IP stack/DNS got security holes/bugs how can they dont have it, 
its a fixed problem on IPv6 but i dont think that they are using IPv6, and no IPv4 by default.
THe vulnerabilities in DNS are not remote code execution vulnerabilities and i'd guess that by default they arn't running a DNS server.

---

### Post by DeadSuperHero on 2010-01-25
Most people don't realize that many libraries and applications available for OpenBSD are often heavily patched/forked from their main projects to align with OpenBSD's own security designs. It is harder to exploit, say, OpenBSD's implementation of Ruby than it is to exploit Ubuntu's.

---

### Post by Xbehave on 2010-01-25
> **Mr. Psychopath said:**
> Most people don't realize that many libraries and applications available for OpenBSD are often heavily patched/forked from their main projects to align with OpenBSD's own security designs. It is harder to exploit, say, OpenBSD's implementation of Ruby than it is to exploit Ubuntu's.
Don't these patches get upstreamed?
I'd say that Fedoras ruby implementation would be harder to exploit than BSDs because if it does anything suspicious in memory selinux will take action, for ubuntu if the ruby app has an apparmor profile it will also be safer than the same app in ruby, so while openBSD may have the most secure ruby stack in practice your better of in linux.

---

### Post by juancarlospaco on 2010-01-25
[I]But BSD dont have something like SELinux, SELinux its independent of Kernel Holes.

**I think the point its any properly configured Unix is rock solid...**[/I]

---

### Post by juancarlospaco on 2010-01-25
*[SIZE="1"]dejavu[/SIZE]*

---

### Post by maple on 2010-01-31
wow. just ignorance at its finest. people that know absolutely nothing about security throwing around buzzwords like they have a clue. great job.

do a little research.

---

### Post by Xbehave on 2010-01-31
> **maple said:**
> wow. just ignorance at its finest. people that know absolutely nothing about security throwing around buzzwords like they have a clue. great job.

do a little research.
Perhaps instead of attacking everybody you could actually explain who is wrong and justify that point in some way. I'm by no means a security expert but I do have a basic idea of what is going on.

---

### Post by juancarlospaco on 2010-01-31
**+1 ^^^^**

---

### Post by Sporkman on 2010-01-31
I must say, I'm all about the AppArmor - great concept & easy to deploy. I'd think OpenBSD would want to support something along those lines (does it? I recall the article implying not).

---

### Post by phrostbyte on 2010-01-31
Security is very subjective, you can not really quantify what OS is more secure. Though I think a mandatory access framework like AppArmor or SELinux is very helpful.

---

### Post by kevin01123 on 2010-01-31
Fud

---

