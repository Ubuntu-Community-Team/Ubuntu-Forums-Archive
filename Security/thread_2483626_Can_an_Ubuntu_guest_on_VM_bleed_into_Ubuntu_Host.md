---
title: "Can an Ubuntu guest on VM bleed into Ubuntu Host?"
date: 2023-02-04
forum: Security
---

### Post by Heeter on 2023-02-04
Hi All,

If I install ubuntu desktop guest in a VM environment (eg virtualbox or gnomes box), then I open firefox in guest OS, and website has malware, can the malware leak into the host ubuntu desktop?

Conflicting answers on my internet searches on this topic

Regards

---

### Post by TheFu on 2023-02-05
Nothing is 100%.  In theory, no, they wouldn't be able to cross, but in practice, humans make mistakes and software has bugs.

VM security is also extremely specific to the user, applications, configurations and how they are being used.  For example, lots of VM users will connect storage between the guest and host.  If you do that, you've take down part of the security.
If a VM is placed onto a bridge connection that is shared with the host, some network traffic could leak if promiscuous modes are used with the network driver(s).

See how this isn't a yes or no answer?  It depends.

However, I have a strong belief that VM hypervisor makers do try to keep the desired separation, to the best of their ability.  They've all failed to accomplish that at least 20 times previously, so I have belief there are more bugs and new code, especially drivers, that will break this veil.

This applies to PVM, HVM, Containers, sandboxes ... all have issues.  Hardware has issues too.  That's the nature of computing and networking.  We can only use the best methods that are available, strive to avoid misuse and dumb mistakes, based on the actual threats.  If you are running a VM in a multi-tenant setup, like any commercial VPS, I'd have much higher worries than running a VM on a laptop in my home, provided that home system is properly maintained, patched, gets versioned backups, etc.  All standard stuff we all know to do, but perhaps we don't.

---

### Post by DuckHook on 2023-02-05
You couldn't get a more complete summary than what TheFu posted.

I would only add this:

In most real world scenarios, a VM is a very good sandbox. I have no doubt that three&#8209;letter nation state agencies have many ways to penetrate even the most well constructed VM, but if we are going to get that paranoid, then we may as well give up computing.

I personally don't even go as far as VMs to feel reasonably safe. I use containers, which give me all the comfort that I need. If I use a VM, then I feel even more secure, but it's rarely needed, and I am known as one of the more paranoid among forum members here.

The most important thing I've found about security is that the platform and tools (things like VMs) are at most only 10% of the solution, so focusing on them is more often than not misdirected attention. 90% of security problems is a result of user behaviour. We can implement as many security tools as exists out there and, in the process, turn our computing experience into an ordeal, but unless we practice good computing habits, all of those technical measures become only so much spitting into the wind. There are long time forum members who don't sandbox at all, but never run into security problems because they practice excellent personal security hygiene. It's more important to understand their practices and to emulate them than it is to load your system up with sandboxes.

If you apply what TheFu has written to my above warnings, then a nasty real world security compromise might look like this:

[LIST=1]
[*]You implement your proposed solution.
[*]You visit a bad site.
[*]The site surreptitiously loads a keylogger.
[*]Due to the false sense of security from your sandbox, you use your VM browser to do your banking.
[*]The bad guys now have your banking login and password.
[/LIST]
See the problem? Your VM did not fail you. No malicious software infected your base system. But the results are just as bad—perhaps even worse—than having your system ransomed.

---

### Post by Heeter on 2023-02-08
Thank you Guys for your input!!! Appreciate it

---

