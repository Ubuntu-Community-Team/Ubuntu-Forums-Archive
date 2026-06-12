---
title: "Question to those of you who know something about OS security"
date: 2010-06-03
forum: Security
---

### Post by V for Vincent on 2010-06-03
Okay, so it's impossible to give any program the exact privileges it needs. But why are there no major OSes that demand a rough list of (unsafe) operations a program is expected to perform? That is, a broad enumeration of system calls a program will execute? Say you grouped those into a limited number of transparent categories and then showed them to a user upon installation of software from a non-trusted source.

For example: 

This program could:
- "silently monitor input"
- "communicate with other systems"
- "communicate with other programs"
- ...

Any hazardous operation not on the list would then throw an exception.

I'm sure there must be some technical objection, but I can't see what it would be. It's not entirely foolproof, but I'd know something was up if I had something like sticky notes applet silently gathering info and then sending it across the internet.

---

### Post by philinux on 2010-06-03
Moved to Security Discussions.

---

### Post by bodhi.zazen on 2010-06-03
> **V for Vincent said:**
> Okay, so it's impossible to give any program the exact privileges it needs. But why are there no major OSes that demand a rough list of (unsafe) operations a program is expected to perform? That is, a broad enumeration of system calls a program will execute? Say you grouped those into a limited number of transparent categories and then showed them to a user upon installation of software from a non-trusted source.
 
For example: 
 
This program could:
- "silently monitor input"
- "communicate with other systems"
- "communicate with other programs"
- ...
 
Any hazardous operation not on the list would then throw an exception.
 
I'm sure there must be some technical objection, but I can't see what it would be. It's not entirely foolproof, but I'd know something was up if I had something like sticky notes applet silently gathering info and then sending it across the internet.
 
Sounds like you are looking for tools such as Apparmor (Ubuntu) or SELinux (Fedora).

---

### Post by Velnias on 2010-06-03
Well, not exactly what asked:

[Less-known-Solaris-features-RBAC-and-Privileges-Part-1]("http://www.c0t0d0s0.org/archives/4073-Less-known-Solaris-features-RBAC-and-Privileges-Part-1-Introduction.html")

---

### Post by rookcifer on 2010-06-03
Sounds like OP is asking about something like [capability based security]("http://en.wikipedia.org/wiki/Capability-based_security").  Linux can do this sort of thing (via POSIX capabilities), even though the POSIX capability system probably isn't as fine-grained as it needs to be.  A more robust option right now is SELinux or Grsecurity which both can do RBAC.  You also have AppArmor and TOMOYO which, although not as robust as SELinux, can help protect individual applications.

---

### Post by V for Vincent on 2010-06-04
Thanks for the info. I'm a bit surprised, though, that the mechanism is never really made visible to the user by default.

---

### Post by Sporkman on 2010-06-08
If somebody really wanted to design a secure OS, they'd require the user to register a capability spec for an executable before that executable is given execute privileges - that would include system executables as well. No capability spec = no execute.

---

