---
title: "User accounts for security and viruses"
date: 2010-02-12
forum: Security
---

### Post by e24ohm on 2010-02-12
Folks:
I understand that Linux is a little better off when windows when it comes to viruses, but what about scripts or other items on webpages?

Would it be safe to say that if I build a restricted user: "Desktop" or "unprivileged" user I will be ok? From what I understand - most scripts or applications can not install with out the 'sudo' prompt then and user input.

Can anyone offer any suggestions?

---

### Post by cariboo on 2010-02-12
If you are worried about malware, use the noscript add-on for Firefox, otherwise just use your desktop the way you normally do.

There is no need to go to great lengths create other users tobe safe. The big thing to remember is to think before you click that link.

---

### Post by rookcifer on 2010-02-12
> **e24ohm said:**
> Folks:
I understand that Linux is a little better off when windows when it comes to viruses, but what about scripts or other items on webpages?

Would it be safe to say that if I build a restricted user: "Desktop" or "unprivileged" user I will be ok? From what I understand - most scripts or applications can not install with out the 'sudo' prompt then and user input.

Can anyone offer any suggestions?

A script is just a type of computer code, and all computer code's job is to tell your computer what to do.  

All browsers are essentially the same on all OS's -- that is, they contain much of the same code.  This is evidenced by the fact that when you see a vulnerability for Firefox or Chrome, it is usually released as an advisory for both Unix and Windows.  This means Linux's browsers are just as prone to attack as Windows (since they are basically the same).

Now a virus is simply code that is programmed to replicate itself.  What you are talking about here are scripts which just give instructions and are done (no replicating).  Either way, both can be done on Linux.

So what you see happen on Windows with scripts automatically installing themselves *can* happen on Linux, but usually don't because of the file permissions and the fact most users run from a user account.  Actually, running from a user account doesn't stop any script, all it does is *mitigate* what damage a script can do.  If something malicious happens to your browser while surfing, it will be limited to affecting only those files/processes that run with the same permission level as the browser, but that *doesn't mean* it will be harmless or incapable of doing anything.  The difference is that on Windows the browser is usually running with full admin privileges, which means the box is totally owned by one bad script.

Bottom line: there is nothing special about Linux that magically makes it immune to malicious code.  Since Linux is an OS and an OS is merely a layer that interacts with the hardware, then it follows that the OS only does what it is told to do.  The difference is that Linux has much more sane default security measures that help stop malicious code from ever taking hold in the first place.  And a user can make those default protections *almost* bullet-proof by turning on all data/stack/heap hardening features and utilizing the numerous Mandatory Access Control options.

Keep in mind that all code is vulnerable at some point.  So even if the OS tells some code "no you cannot do this because you don't have permission" that doesn't mean the code can't override that denial if it can find a flaw in the kernel itself.  Basically, if one can find the right *kernel level* exploit, one can do anything one pleases, *even if you are running SELinux or AppArmor.*
The truth is, however, since there typically are no kernel level processes accessing the network directly on a desktop machine, there typically are no kernel level exploits that can be done against the box.  So, yes, this means one is typically rather safe when running from a user account since any exploit would not be able to get a code path to the kernel.

---

### Post by e24ohm on 2010-02-15
> **rookcifer said:**
> 
The truth is, however, since there typically are no kernel level processes accessing the network directly on a desktop machine, there typically are no kernel level exploits that can be done against the box.  So, yes, this means one is typically rather safe when running from a user account since any exploit would not be able to get a code path to the kernel.

Do you recommend running with a user account that is restrictred then? I do not understand.

---

### Post by e24ohm on 2010-02-15
> **cariboo907 said:**
> If you are worried about malware, use the noscript add-on for Firefox, otherwise just use your desktop the way you normally do.

There is no need to go to great lengths create other users tobe safe. The big thing to remember is to think before you click that link.
The "noscript add-on for Firefox", do I download that from Firefox?

---

### Post by adam814 on 2010-02-15
Your normal user account you create during install is by default "unprivileged."  You wouldn't get any benefit from trying to make a more "locked down" user, most likely all you'd gain is headaches.

Just don't run anything as root you don't have to.  Especially not a web browser.  You might also want to look at the security "stickies" at the top of this forum.

---

### Post by cariboo on 2010-02-15
> **e24ohm said:**
> The "noscript add-on for Firefox", do I download that from Firefox?

Open Firefox and go to Tools->Addons, and search for noscript

---

### Post by teward on 2010-02-15
Actually, if you are afraid of scripts, you should be very careful then.  I use Linux primarily, and I've hit a few nasties that have nuked my Wine config, required manual purge of the configs in all users, and wiped out Wine completely.  The NoScript addon in firefox helps, but its not the best thing in the world...

---

### Post by e24ohm on 2010-02-19
> **TrekCaptainUSA said:**
> Actually, if you are afraid of scripts, you should be very careful then.  I use Linux primarily, and I've hit a few nasties that have nuked my Wine config, required manual purge of the configs in all users, and wiped out Wine completely.  The NoScript addon in firefox helps, but its not the best thing in the world...
Do you think locking down the user account would have helped with this or not?

---

