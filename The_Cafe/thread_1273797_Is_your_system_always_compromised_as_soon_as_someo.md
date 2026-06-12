---
title: "Is your system always compromised as soon as someone gets the root password?"
date: 2009-09-23
forum: The Cafe
---

### Post by hoppipolla on 2009-09-23
This one keeps coming up and it's getting on my nerves lol xD

Especially as now I have this friend who is VERY pro Windows and always seems rather anti-Linux, who has a theory Windows is much more secure because as soon as a threat gets the root pass in Linux you're screwed and somehow Windows has some magical veil built into it's core that makes it impervious to all threats! lol xD

What is the actual truth about this? How secure can you make a Linux system, how secure is it by default, and is the root password really our ONLY level of defense? Does Windows or does Mac OSX somehow have more? Surely not...

Thanks guys and it will be great to see this niggle finally answered! I do know a bit about optional things you can do in Linux to make it more secure but not loads, and it would just be great to have a fuller picture!

Hoppi :)

---

### Post by Firestem4 on 2009-09-23
Sudo is a good example of limited elevated permissions. You can modify sudo-access to not be a "full-root". IE: You can only perform these "root actions" while using sudo, otherwise you have to be root. you can (i believe) have different passwords set for each. 

However, if a malicious person has root access then your system is as good as gone, because they KNOW how to destroy a machine in those instances.

---

### Post by dragos240 on 2009-09-23
Well. Once you get the root password, you can do ANYTHING with your system. This can be very good, and very bad.

---

### Post by schauerlich on 2009-09-23
Look into SELinux. Someone has a box running SELinux which gives everyone root access, but no one has been able to compromise the box's security.

---

### Post by #11u-max on 2009-09-23
oops, double post... :)

---

### Post by #11u-max on 2009-09-23
my little brother got by my weak [saddening weak!] password and into root, my mom caught him before he did any real damage... thank goodness he doesn't know about rm -rf...

---

### Post by t0p on 2009-09-23
> **EDavidBurg said:**
> Look into SELinux. Someone has a box running SELinux which gives everyone root access, but no one has been able to compromise the box's security.

Do you have a link to something that explains this a little better?  It sounds... curious.  What's so "special" about SELinux that makes the root password useless?

As for the OP's friend's idea that Windows is somehow more secure than Linux: I dunno about Vista or Win7, but I know it's possible to compromise XP without any passwords at all.  Sometimes you just need to *stare hard* at a Windows box and it'll crack... :p

---

### Post by hoppipolla on 2009-09-23
> **t0p said:**
> Do you have a link to something that explains this a little better?  It sounds... curious.  What's so "special" about SELinux that makes the root password useless?

As for the OP's friend's idea that Windows is somehow more secure than Linux: I dunno about Vista or Win7, but I know it's possible to compromise XP without any passwords at all.  Sometimes you just need to *stare hard* at a Windows box and it'll crack... :p

Rofl! Yeah XP was notoriously unbelievably easy to get into!

I wonder how much of an improvement Vista and 7 are.

---

### Post by p_quarles on 2009-09-23
> **EDavidBurg said:**
> Look into SELinux. Someone has a box running SELinux which gives everyone root access, but no one has been able to compromise the box's security.
Sure, but that works by completely redefining what root access *means*. I mean, yes, it's a fantastic way of limiting privileges in a more fine-grained way than the unpatched kernel allows for, but it's also essentially removing "root" privileges from UID 0 and granting them only to the GRUB command line parameters.

---

### Post by t0p on 2009-09-23
> **p_quarles said:**
> Sure, but that works by completely redefining what root access *means*. I mean, yes, it's a fantastic way of limiting privileges in a more fine-grained way than the unpatched kernel allows for, but it's also essentially removing "root" privileges from UID 0 and granting them only to the GRUB command line parameters.

Hmm I don't like the sound of that.  In a *nix, root should be able to override everything else if s/he so wishes.  And I really don't see that as a vulnerability.  If you set a good strong password and observe proper on-site hardware security, no one's gonna crack the box. The administrator of a computer should be allowed to *administer* the computer.  And that means having full, unfettered access when you want it.  If you set yourself *too* many hoops to jump through, you're just making your task needlessly difficult.

---

### Post by p_quarles on 2009-09-23
> **t0p said:**
> Hmm I don't like the sound of that.  In a *nix, root should be able to override everything else if s/he so wishes.  And I really don't see that as a vulnerability.  If you set a good strong password and observe proper on-site hardware security, no one's gonna crack the box. The administrator of a computer should be allowed to *administer* the computer.  And that means having full, unfettered access when you want it.  If you set yourself *too* many hoops to jump through, you're just making your task needlessly difficult.
I mean no disrespect, but from your comment it sounds like you don't understand what SELinux is or does. It doesn't disable root access from within a TTY, it *enables* you to disable it, if you like. It's fine-grained control that the standard kernel doesn't have. If you are administering computers in any professional capacity, I'm sure you can see the benefit of having that kind of control.

---

### Post by hoppipolla on 2009-09-23
> **p_quarles said:**
> I mean no disrespect, but from your comment it sounds like you don't understand what SELinux is or does. It doesn't disable root access from within a TTY, it *enables* you to disable it, if you like. It's fine-grained control that the standard kernel doesn't have. If you are administering computers in any professional capacity, I'm sure you can see the benefit of having that kind of control.

That's very clever, I think more Linux set-ups should have more degrees of control and administration than just root shouldn't they?

I mean to be fair I don't understand much about this which is why I started this thread, but anyway... :)

---

### Post by JDShu on 2009-09-23
I heard that physical access to a system will always render it insecure, no matter the operating system.

---

### Post by renkinjutsu on 2009-09-23
Even Vista doesn't need a password for it's UAC system.

all the user needs to do is click a button and a process can do whatever it wants to a system.. I'm no hacker, but that can probably be compromised easily (plus it can be disabled by the user)

---

### Post by hoppipolla on 2009-09-24
> **JDShu said:**
> I heard that physical access to a system will always render it insecure, no matter the operating system.

I dunno I reckon that an encrypted filesystem is a pretty good barrier... isn't it?

---

