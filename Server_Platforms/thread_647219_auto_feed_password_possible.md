---
title: "auto feed password possible?"
date: 2007-12-22
forum: Server Platforms
---

### Post by davidcopper on 2007-12-22
Hi. When I type su or sudo in terminal, it will ask you for a password. Is it possible to write a program that will feed password to su or sudo. So when I run the program, I will become root instantly rather than entering password every time.


Many thanks for any suggestions.

---

### Post by wormser on 2007-12-22
Why would you want to do that.  It defeats the whole purpose of having passwords.  It would be a big security risk.

---

### Post by davidcopper on 2007-12-22
Hi. I just want to try this out on my computer. Obviously I am not going to do this on a public computer. 

Every coin has two sides. This leaves the computer at the state as if there was no password, but brings convenience for me in which I don't need to type my password every time I use sudo. I can say, no one can use my computer physically. :p

---

### Post by p_quarles on 2007-12-22
It's easy to set up a passwordless sudo user, but based on your reply to wormser's point, I suspect you may be unaware of the risk of remote exploits on such a system. Essentially, what you would be doing is creating a situation where any security vulnerability (even a minor Firefox bug) could get you a rootkit on your system. 

The passwordless sudo user configuration, imho, is only useful for sudoers with extremely limited abilities (and not member of the admin group), and for computers that are completely non-networked.

---

### Post by rsw686 on 2007-12-22
Well for a personal desktop it is not worse than Vista's hey this program needs elevated resources click okay to proceed message. The users just click without thinking.

You need to add NOPASSWD to the /etc/sudoers file. For your username change

ALL = (ALL) ALL

to 

ALL = NOPASSWD: ALL

---

### Post by p_quarles on 2007-12-22
> **rsw686 said:**
> Well for a personal desktop it is not worse than Vista's hey this program needs elevated resources click okay to proceed message. The users just click without thinking.

You need to add NOPASSWD to the /etc/sudoers file. For your username change

ALL = (ALL) ALL

to 

ALL = NOPASSWD: ALL
Not really true. At least UAC has the potential to catch remote exploits in the act, and if the user clicks through, they obviously weren't paying attention. Running a passwordless sudoer makes it possible to exploit remote vulnerabilities without any kind of warning to the user. 

Besides, last time I checked, "no worse than Windows" wasn't exactly the benchmark for good security practices.

---

### Post by rsw686 on 2007-12-22
> **p_quarles said:**
> Not really true. At least UAC has the potential to catch remote exploits in the act, and if the user clicks through, they obviously weren't paying attention. Running a passwordless sudoer makes it possible to exploit remote vulnerabilities without any kind of warning to the user. 

Besides, last time I checked, "no worse than Windows" wasn't exactly the benchmark for good security practices.

I haven't tried it but I'm fairly sure you could make a program that just clicks through for them.

This is a personal machine not a business server. At least the OP is using linux, which in itself is much better off than Windows. Most boxes that are targeted for exploits are Windows based, except for unix daemons like ssh, apache, etc. So if the OP is just browsing the internet with a decent browser like Firefox than I don't see the harm.

---

### Post by jken146 on 2007-12-22
Yes, that is a better solution.  You'll need to do ```
sudo visudo
``` to edit /etc/sudoers.

---

### Post by p_quarles on 2007-12-22
> **rsw686 said:**
> I haven't tried it but I'm fairly sure you could make a program that just clicks through for them.

This is a personal machine not a business server. At least the OP is using linux, which in itself is much better off than Windows. Most boxes that are targeted for exploits are Windows based, except for unix daemons like ssh, apache, etc. So if the OP is just browsing the internet with a decent browser like Firefox than I don't see the harm.
Yes, and one of the main reasons *nix boxes are fundamentally more secure than Windows boxes is the privilege separation. Enabling passwordless sudo effectively negates that altogether. 

Moreover, browser exploits don't target operating systems *per se*, they target scripting languages that are built-in to the browser. Firefox -- while it does get patched more quickly than Explorer -- has been known to have many exploits, even as recently as 2.0.0.9. Basically, anything that interacts with unknown networks -- no matter how well its designed -- is a potential security risk. 

Anyway, I'm not trying to tell anyone what to do or not to do, but I do think it's important to understand the very real risks of running a system in this mode before doing it.

---

### Post by anemptygun on 2007-12-22
just log in as root.

---

### Post by bacante on 2008-04-08
Hi,

We're deploying some mini PCs (with no mouse, keyboard or screen) in some unaccesible areas. I really need to use "sudo" without the need of entering any password as I have no keyboard.

The aim to do so is to get the WiFi connected automatically (imagine power going down).

My user's "josue" and this is my /etc/sudoers file:

```
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL
josue ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
josue   ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

Although "josue" is member of admin and sudo groups, this is not working for me. It still asks me for a password.

Any clue?

Thank you in advance.

---

### Post by hyper_ch on 2008-04-08
add a script to the runlevels that runs the according command for starting the wifi...

btw, you will be ready to use passwordless accounts when you will know yourself how to do that and at that point you will realize that you don't need to have that anyway.

---

### Post by koenn on 2008-04-08
> **hyper_ch said:**
> add a script to the runlevels that runs the according command for starting the wifi...

btw, you will be ready to use passwordless accounts when you will know yourself how to do that and at that point you will realize that you don't need to have that anyway.
good point

---

