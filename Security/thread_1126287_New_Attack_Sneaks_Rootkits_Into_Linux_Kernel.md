---
title: "New Attack Sneaks Rootkits Into Linux Kernel"
date: 2009-04-15
forum: Security
---

### Post by Dragonbite on 2009-04-15
From[INDENT][[COLOR=Blue]http://www.darkreading.com/security/vulnerabilities/showArticle.jhtml?articleID=216500687[/COLOR]]("http://www.darkreading.com/security/vulnerabilities/showArticle.jhtml?articleID=216500687")[/INDENT]
>  New Attack Sneaks Rootkits Into Linux Kernel
A researcher at Black Hat Europe this week will demonstrate a new, more stealthy way to hack Linux

Apr 14, 2009 | 04:21 PM
By Kelly Jackson Higgins
DarkReading

Kernel rootkits are tough enough to detect, but now a researcher has demonstrated an even sneakier method of hacking Linux.

The attack attack exploits an oft-forgotten function in Linux versions 2.4 and above in order to quietly insert a rootkit into the operating system kernel as a way to hide malware processes, hijack system calls, and open remote backdoors into the machine, for instance. At Black Hat Europe this week in Amsterdam, Anthony Lineberry, senior software engineer for Flexilis, will demonstrate how to hack the Linux kernel by exploiting the driver interface to physically addressable memory in Linux, called /dev/mem.

---

### Post by gnomeuser on 2009-04-15
I am pretty sure that copy pasting the entire article doesn't qualify as fair use and is in fact copyright violation that may legally endanger the forums.

Aside that, it sounds like a very nifty piece of work. I assume this depends on there first being an attack vector that will have priviliages to write to /dev/mem which in these SELinux days might hard. Never the less it is interesting as an approach.

---

### Post by aaaantoine on 2009-04-15
So... What do we do about it?  Other than not run every little thing as root?

---

### Post by gnomeuser on 2009-04-15
> **aaaantoine said:**
> So... What do we do about it?  Other than not run every little thing as root?

SELinux is what we do. If your program has no reasonable grounds to access /dev/mem it should be confined and barred from doing so.

---

### Post by Johnsie on 2009-04-15
Who needs root? Malware can easisily cause alot of trouble without root. Sure it's harder to break the system, but you can pretty much do anything with the current users account. TCP/IP, email, adding things to the users startup etc.

---

### Post by bobmatino17 on 2009-04-15
> **Johnsie said:**
> Who needs root? Malware can easisily cause alot of trouble without root. Sure it's harder to break the system, but you can pretty much do anything with the current users account. TCP/IP, email, adding things to the users startup etc.

you have to be root to update your system, install packages, install drivers, modify config files so they work right, plus being root is just pwnage. 
I say let them hack my machine, i have nothing to lose, i will in a few years, but not yet.

---

### Post by gnomeuser on 2009-04-15
> **bobmatino17 said:**
> you have to be root to update your system, install packages, install drivers, modify config files so they work right, plus being root is just pwnage. 
I say let them hack my machine, i have nothing to lose, i will in a few years, but not yet.

No no, you do not need to be root. You need your privilliages raised, you do not need full no holds bar access to everything to do any of those tasks. You look should look at PolicyKit, it is already being used to elevate specific tasks you mentioned such as installing packages and updating the system using PackageKit.

You should never need to be root.

---

### Post by ssam on 2009-04-15
i think there is already some protection in ubuntu
[http://thread.gmane.org/gmane.linux.ubuntu.user/176419](http://thread.gmane.org/gmane.linux.ubuntu.user/176419)

---

### Post by Johnsie on 2009-04-15
You can install software in a user account without root and you can run all kinds of shell scripts without root. It's just a matter of copying the files into the users home folder and adding an entry to the users "session" so it starts every time the user logs in. All of that can be done without root.

---

### Post by Dragonbite on 2009-04-15
> **Johnsie said:**
> Who needs root? Malware can easisily cause alot of trouble without root. Sure it's harder to break the system, but you can pretty much do anything with the current users account. TCP/IP, email, adding things to the users startup etc.

Isn't every time you type in your password for sudo you are technically as root?

---

### Post by Johnsie on 2009-04-15
When you type your password in you can pretty much do anything if your account has alot of privileges. By default an admin user on Ubuntu has almost limited privileges at this point. However the misconception is that you need to be Sudo to do anything significant. There are a lot of significant things that can be done by non sudo users. Email, TCP/IP, reading the users files, adding stuff the users startup etc,

---

### Post by Dragonbite on 2009-04-15
> **gnomeuser said:**
> SELinux is what we do. If your program has no reasonable grounds to access /dev/mem it should be confined and barred from doing so.

Is this a case where SELinux works at protecting it because it is worked into the kernel while AppArmor does not because it is a layer on top of it?

I've been interested in SELinux but I hear so many negative things about it keeping one from doing things and I am not that deeply technical (I skim the top a little) that I wouldn't know how/where to start fixing things to bother trying it.

---

### Post by Sef on 2009-04-15
Locked.  Under review.  For post #2 reasons.

---

### Post by Dragonbite on 2009-04-15
Reopened.

Thank you Sef for your understanding.

~Drew

---

### Post by jdong on 2009-04-15
Note that Ubuntu and many other distributions do have /dev/mem protection that prevents key regions of the system memory from being written or read:

```

$ sudo dd if=/dev/mem of=/dev/null
dd: reading `/dev/mem': Operation not permitted
2056+0 records in
2056+0 records out
1052672 bytes (1.1 MB) copied, 0.0286411 s, 36.8 MB/s

```

This will make these "new attacks" pretty difficult to pull off. This feature has been around since Dapper.


In a situation where /dev/kmem and /dev/mem access is indeed necessary, SELinux type enforcement can be an extremely powerful mitigation strategy. Executing these kinds of rootkit deployments requires malware to be on your system AND have gained root access, by which time you are pretty screwed anyway in terms of what else an attacker can do.

---

### Post by geoken on 2009-04-15
> **Johnsie said:**
> Who needs root? Malware can easisily cause alot of trouble without root. Sure it's harder to break the system, but you can pretty much do anything with the current users account. TCP/IP, email, adding things to the users startup etc.

Agreed. I install/test/try new OSes and distros at least once a month. Re-installing a fubar'd system is completely trivial. It's the stuff in my /home directory that I really care about.

---

### Post by gnomeuser on 2009-04-15
> **Dragonbite said:**
> Is this a case where SELinux works at protecting it because it is worked into the kernel while AppArmor does not because it is a layer on top of it?

I've been interested in SELinux but I hear so many negative things about it keeping one from doing things and I am not that deeply technical (I skim the top a little) that I wouldn't know how/where to start fixing things to bother trying it.

Not this case specifically. The SELinux is largely untrue, it does keep you from doing things you shouldn't do and if it prevents real legitimate work then it is a policy bug and will be fixed if filed - normally within hours if you use Fedora (since Dan Walsh never sleeps.. I am convinced of this).

I will agree that the SETroubleshooter tool could definitely be easier to use, something like apport would be great here. In a stable release you should never see it and most often you do not.

The reason why SELinux is seen as more invasive than AppArmor is largely that the policy is stricter by default. Each cycle of Fedora adds more policy to increase containment. 

Another place where SELinux has good things going for it is the integration with existing applications. You can label windows in metacity with security labels, there is also an option to label packages in the network stack.

I believe that eventually AppArmor will run out of steam, it has made several failed attempts at getting into the kernel. The development team was let go by Novell and they started their own company. I haven't seen a submission for review in at least a year on LKML. Novell have started offering SELinux as a option and from what I hear unless AppArmor manages to get into the kernel soon the additional work and vendor insecurity about using out of kernel code for security will make them drop AppArmor. I think if Novell does that, Ubuntu will follow.

In the end I believe everyone will win from this, we can push towards a collective upstream policy that works well for everyone with a few modifications to address distributions specific concerns. This would give good reliable security across distributions that support SELinux. We do need better tools, things to help us catch policy mistakes in the development cycle and make it easy to report them so it can be sorted out of it is a policy problem or an application that does something it is not supposed to. I think an proper upstream effort here with lots of backers would greatly help getting a very complete security system going for everyone.

---

### Post by jdong on 2009-04-15
> **gnomeuser said:**
> Not this case specifically. The SELinux is largely untrue, it does keep you from doing things you shouldn't do and if it prevents real legitimate work then it is a policy bug and will be fixed if filed - normally within hours if you use Fedora (since Dan Walsh never sleeps.. I am convinced of this).

I will agree that the SETroubleshooter tool could definitely be easier to use, something like apport would be great here. In a stable release you should never see it and most often you do not.


SELinux works quite well these days 99.99% of the times, has way more default confinement domains defined by reference policy, and the SETroubleshooter and audit2allow systems make it fairly simple to patch your own policy exceptions. The modular policy architecture is a lot more flexible for patch-and-fixes than before.

Ubuntu/Debian has decent SELinux support too; one of my shell servers uses SELinux RBAC and I don't have an issue with it (it runs Debian Lenny; used to run Ubuntu Hardy as well)


> 

The reason why SELinux is seen as more invasive than AppArmor is largely that the policy is stricter by default. Each cycle of Fedora adds more policy to increase containment. 


Now there I disagree. One reason SELinux is seen more invasive is that it is! There's no such thing as "targeted profiles" -- it's really a misnomer. All it means is "untargeted" apps are labeled as an "unconfined" type. In Apparmor, any app you do not define a confinement profile for are untouched 100% by the AA subsystem. This is not true with SELinux; the unconfined domain is just a normal SELinux domain with a lot more allowed liberties.

Furthermore, you have to have correctly labeled filesystems when SELinux is enabled with a policy (even targeted policy), otherwise you're going to run into AVC denials and weird behavior.

Is this a necessarily bad thing? Nah, I don't think so; this model is much better for serious full-system MAC, but IMO AppArmor is still far more convenient for Average Joe Sysadmin who just wants to jail crappyserverd.


> 
Another place where SELinux has good things going for it is the integration with existing applications. You can label windows in metacity with security labels, there is also an option to label packages in the network stack.


Absolutely; the SELinux userland/kernelspace system makes it very power in terms of extensibility -- virtually extendable to apply "labels" to anything. There's a lot of work already in labeling elements in X, now there's ongoing work to make it possible to label network traffic too. Is it possible to extend to labeling Firefox tabs? I bet with a bit of hacking it probably is.

Apparmor cannot compete on this; its profile language is highly specific to restricting filesystem access permissions, and apart from a simple language to limit POSIX capabilities, it's really really difficult to express much more in the language without it becoming cluttered.

> 
I believe that eventually AppArmor will run out of steam, it has made several failed attempts at getting into the kernel. The development team was let go by Novell and they started their own company. I haven't seen a submission for review in at least a year on LKML. Novell have started offering SELinux as a option and from what I hear unless AppArmor manages to get into the kernel soon the additional work and vendor insecurity about using out of kernel code for security will make them drop AppArmor. I think if Novell does that, Ubuntu will follow.


Now come on, let's not play the-sky-is-falling on this.... AA is still being maintained fine by the community, and does bring a simple unintrusive MAC to the table. I like both technologies for different reasons, and personally I'd like to see both survive. I see no reason why Novell's "offering SELinux" implies that it will stop caring about Apparmor altogether (Ubuntu's "offering SELinux", Novell used to be KDE and has started offering GNOME, ...), nor am I convinced why Ubuntu follows Novell in distro architectures.


> 
In the end I believe everyone will win from this, we can push towards a collective upstream policy that works well for everyone with a few modifications to address distributions specific concerns. This would give good reliable security across distributions that support SELinux. We do need better tools, things to help us catch policy mistakes in the development cycle and make it easy to report them so it can be sorted out of it is a policy problem or an application that does something it is not supposed to. I think an proper upstream effort here with lots of backers would greatly help getting a very complete security system going for everyone.

The chances of getting THAT good cross-distro consensus on SELinux policy is probably difficult; tresys does a good deal of work on Ubuntu refpolicy, and I see no reason why more knowledgeable people cannot contribute more to the SELinux Ubuntu effort; Debian's got some good work on SELinux too.

SELinux can and does spread and prosper; it does not have to be at the expense of AppArmor.

---

### Post by Paqman on 2009-04-15
> **aaaantoine said:**
> So... What do we do about it?  Other than not run every little thing as root?

We keep our kernel patched up to date.

---

### Post by MaxIBoy on 2009-04-15
The article says that there has already been a kernel patch issued to lock down /dev/mem at the kernel level. I assume the patch will show up in the latest kernel release, so I'll have the patch soon!

Guess I'll just have to ruin my server's uptime...

---

### Post by zekopeko on 2009-04-15
> **MaxIBoy said:**
> The article says that there has already been a kernel patch issued to lock down /dev/mem at the kernel level. I assume the patch will show up in the latest kernel release, so I'll have the patch soon!

Guess I'll just have to ruin my server's uptime...

i was wondering what happened to the hotfixing of kernel vulnerabilities (is hotfixing the correct term) without restarting the system?

---

### Post by MaxIBoy on 2009-04-15
You mean it's possible to do that?

---

### Post by jdong on 2009-04-15
> **MaxIBoy said:**
> The article says that there has already been a kernel patch issued to lock down /dev/mem at the kernel level. I assume the patch will show up in the latest kernel release, so I'll have the patch soon!

Guess I'll just have to ruin my server's uptime...


The patch has already been "applied" in Ubuntu for a LONG time now. We do not permit read/write of kernel memory using /dev/*mem.

---

### Post by BGFG on 2009-04-15
> **jdong said:**
> The patch has already been "applied" in Ubuntu for a LONG time now. We do not permit read/write of kernel memory using /dev/*mem.

So who exactly is running this out of date kernel that is vulnerable ? what is the point of this new hack if no one up to date is susceptible ?

---

### Post by gnomeuser on 2009-04-15
> **BGFG said:**
> So who exactly is running this out of date kernel that is vulnerable ? what is the point of this new hack if no one up to date is susceptible ?

People who compile their own kernel yet do not know how to configure it. 

I don't think any of the major distros ship a kernel which doesn't have protection enabled for this attack vector. I think this is pretty much a non-issue, we knew about the problem and we had a workaround - several in fact you can lock it down both using SELinux/AppArmor techniques and there is the kernel strict access functionality.

Unless this researcher has a way to defeat these protections, he ain't bringing anything to the table. I would like to reserve judgement till after the presentation.

---

### Post by Xoanan on 2009-04-15
Hi All 

I saw this article from Linux today; have a look.

Do you think we're ready?

[http://www.darkreading.com/security/vulnerabilities/showArticle.jhtml?articleID=216500687]("http://www.darkreading.com/security/vulnerabilities/showArticle.jhtml?articleID=216500687")

---

### Post by bodhi.zazen on 2009-04-15
Two comments :

1. This is a "[zero day exploit](http://en.wikipedia.org/wiki/Zero-Day_Attack)"

The only way to protect yourself against zero day exploits at this time is AppArmor in Ubuntu and SElinux in other OS (Fedora).

As you can imagine, Apparmor and SELinux are NOT foolproof.

2. At the very end of the article :

> And there's now a way to defend against such an attack, too: the Linux development community recently issued a patch to locks down /dev/mem, limiting read and write access from the outside, he says.

So it appears it has already been patched. This is what I love about the Open Source community, it does not take years for patches to be released.

---

### Post by Therion on 2009-04-15
Being discussed here:  [http://ubuntuforums.org/showthread.php?t=1126287](http://ubuntuforums.org/showthread.php?t=1126287)

---

### Post by Xoanan on 2009-04-15
Thanx!

---

### Post by Xoanan on 2009-04-15
Ah; got it! Thanx

---

### Post by bodhi.zazen on 2009-04-15
Threads merged and moved to the security section.

---

