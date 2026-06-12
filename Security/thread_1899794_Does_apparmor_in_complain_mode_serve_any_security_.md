---
title: "Does apparmor in complain mode serve any security purpose?"
date: 2011-12-24
forum: Security
---

### Post by arroy_0209 on 2011-12-24
If I understand correctly, apparmor profile in complain mode only reports instances of violations of rules by the corresponding application but it does not deny the application of doing the action. Is apparmor profile in complain mode really a security tool? It seems to me that an OS remains unprotected if an apparmor profile is in complain mode. Is that correct?

---

### Post by Larkspur on 2011-12-24
That is correct, as far as I know.  The complain mode is only really useful when testing Apparmor profiles that you have written or amended to see the impact of the changes made to the policy without the new restrictions affecting the program as it is running.  If an overly restrictive policy (e.g. one that stops non-risky actions) were enforced, some features would appear broken without feedback that apparmor is the cause (you would have to check the logs to find out).  

If you want to avoid using complain mode, you could try apparmor-notify from the Software Centre.  With this package, you can run your policies in enforce mode and, when the apparmor stops an action, you are told through notifyOSD (though only if you're running the program in an admin account, as far as I know).

---

### Post by aeronutt on 2011-12-24
> **arroy_0209 said:**
> If I understand correctly, apparmor profile in complain mode only reports instances of violations of rules by the corresponding application but it does not deny the application of doing the action. Is apparmor profile in complain mode really a security tool? It seems to me that an OS remains unprotected if an apparmor profile is in complain mode. Is that correct?

FYI, many distro's don't ship with apparmor installed. I've not found a compelling reason to use it on a home computer.

---

### Post by uRock on 2011-12-24
> **aeronutt said:**
> FYI, many distro's don't ship with apparmor installed. I've not found a compelling reason to use it on a home computer.

They usually have AppArmor or SELinux. I recommend its use on the home PC, because it protects against many attacks. 

Complain mode i great for making custom configurations. It allows you to debug a new rule without your system being crippled by it. You can have multiple rules for one application. A default rule can be implemented, while the customized rule can be in complain mode. Once debugging is complete, the default rule can be removed/disabled and the new one set to enforce.

---

### Post by aeronutt on 2011-12-24
> **uRock said:**
> They usually have AppArmor or SELinux. I recommend its use on the home PC, because it protects against many attacks. 

Complain mode i great for making custom configurations. It allows you to debug a new rule without your system being crippled by it. You can have multiple rules for one application. A default rule can be implemented, while the customized rule can be in complain mode. Once debugging is complete, the default rule can be removed/disabled and the new one set to enforce.

Well...I guess I need to learn how apparmor works, and how to use it. But, not to be controversial, what does it protect against that's a risk with a standard home linux load, with iptables, etc. Most of the stuff I read on apparmor seems to apply to enterprise installations of linux.

---

### Post by uRock on 2011-12-24
> **aeronutt said:**
> Well...I guess I need to learn how apparmor works, and how to use it. But, not to be controversial, what does it protect against that's a risk with a standard home linux load, with iptables, etc. Most of the stuff I read on apparmor seems to apply to enterprise installations of linux.

I would expect enterprise systems to need AppArmor less, unless there is an improperly locked down network involved. 

AppArmor's use is explained [here]("http://ubuntuforums.org/showthread.php?t=1008906").

---

### Post by Gentoo64 on 2011-12-26
Complain mode is just "pretending" it's working purely to get the logs, to see what needs editing in the config, most security stuff like selinux and grsec (rbac) use testing modes too.
If you just set something like selinux to enforce without testing first, it wouldn't allow you to boot. Apparmor is a lot more lightweight, so you could get away with no "complain mode" but it'd take longer.
Basically you just want to get the bulk of the false errors away using complain mode, then tweak it in proper enforced mode.

---

### Post by aeronutt on 2011-12-26
If using linux needs this (apparmor) in order to be secure, and apparmor is this difficult to get right, then I'd argue linux isn't secure.

---

### Post by Gentoo64 on 2011-12-26
You don't need apparmor... the average user shouldn't need to touch it. But as it's there, built into Ubuntu, no harm in learning it if you're interested in security.

Things like apparmor, grsec, selinux are mostly for server type systems, but nothing stopping anyone using any of them on a desktop. They're certainly not pointless, but as a normal desktop user shouldn't be doing much, they shouldn't be needed either.

If someone exploits a program, apparmor just limits what they can then access, but security updates usually fix exploits anyway. So the main one basically is just to stay up to date. But even running very out of date software, I doubt the average joe would be at much risk anyway.

---

### Post by uRock on 2011-12-26
> **aeronutt said:**
> If using linux needs this (apparmor) in order to be secure, and apparmor is this difficult to get right, then I'd argue linux isn't secure.
What makes you think it is hard to use? One command is all it takes to start enforcing AppArmor.```
sudo /etc/init.d/apparmor start
```
> **Gentoo64 said:**
> You don't need apparmor... the average user shouldn't need to touch it. But as it's there, built into Ubuntu, no harm in learning it if you're interested in security.

Things like apparmor, grsec, selinux are mostly for server type systems, but nothing stopping anyone using any of them on a desktop. They're certainly not pointless, but as a normal desktop user shouldn't be doing much, they shouldn't be needed either.

If someone exploits a program, apparmor just limits what they can then access, but security updates usually fix exploits anyway. So the main one basically is just to stay up to date. But even running very out of date software, I doubt the average joe would be at much risk anyway.
The average Joe probably clicks  lot of links while surfing the net. All it takes is one with a bad script to hijack/compromise a system when not using AppArmor.

---

### Post by Telengard C64 on 2011-12-26
> **uRock said:**
> The average Joe probably clicks  lot of links while surfing the net. All it takes is one with a bad script to hijack/compromise a system when not using AppArmor.

Average Joe probably thinks he is safe because he is careful not to run programs from untrusted sources. Average Joe probably also runs Firefox with Javascript enabled because the web works better that way. Average Joe probably has Flashplayer, Java, PDF viewer, and other plug-ins installed in to enable streaming videos web games, and document viewing in Firefox.

Does Average Joe ever consider that programs written in Javascript, Flash, and Java are still programs? Does Average Joe even know that those programs are not subject to review by Canonical or the Ubuntu community? Does Average Joe realize that any program executing within Firefox or one of its plug-ins can potentially gain full access to everything Average Joe himself has access to?

[https://www.google.com/search?q=+firefox%20+execution%20+%22privilege%20escalation%22%20+linux](https://www.google.com/search?q=+firefox%20+execution%20+%22privilege%20escalation%22%20+linux)

---

### Post by uRock on 2011-12-26
> **Telengard C64 said:**
> Average Joe probably thinks he is safe because he is careful not to run programs from untrusted sources. Average Joe probably also runs Firefox with Javascript enabled because the web works better that way. Average Joe probably has Flashplayer, Java, PDF viewer, and other plug-ins installed in to enable streaming videos web games, and document viewing in Firefox.

Does Average Joe ever consider that programs written in Javascript, Flash, and Java are still programs? Does Average Joe even know that those programs are not subject to review by Canonical or the Ubuntu community? Does Average Joe realize that any program executing within Firefox or one of its plug-ins can potentially gain full access to everything Average Joe himself has access to?

[https://www.google.com/search?q=+firefox%20+execution%20+%22privilege%20escalation%22%20+linux](https://www.google.com/search?q=+firefox%20+execution%20+%22privilege%20escalation%22%20+linux)Probably not. :P

---

### Post by lovinglinux on 2011-12-27
I suggested the complain mode to see if the problem described in your other thread is in fact caused by AppArmor. It is not supposed to leave it in complain mode forever, if you like to use AppArmor.

---

