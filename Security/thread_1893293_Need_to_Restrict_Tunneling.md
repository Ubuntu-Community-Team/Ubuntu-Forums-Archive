---
title: "Need to Restrict Tunneling"
date: 2011-12-09
forum: Security
---

### Post by coolguy918 on 2011-12-09
Hi,

I run a server (Ubuntu 10.04 server edition) and have a small problem... I have a few users that need access to the system for business purposes, but I don't trust them with the ability to tunnel as there are a few that are highly immature and very likely to use it as a proxy for cyberbullying/other cybercrimes and I don't want to be held liable for that. I installed [lshell]("http://lshell.ghantoos.org") and created a "restricted" group (and set lshell as the shell for the restricted users). While I could find a way to disable SCP, I couldn't find a way to use lshell to keep users in the restricted group (and *only* the users in the restricted group) from tunneling. Is there something I'm overlooking? Is there a better way to go about this?

---

### Post by Lars Noodén on 2011-12-10
Please clarify a little more about what kind of access you need to provide and what kind you wish to block.

---

### Post by coolguy918 on 2011-12-10
> **Lars Noodén said:**
> Please clarify a little more about what kind of access you need to provide and what kind you wish to block.
They need to be able to access all other functions on the Linux system (SCP, certain command-line programs installed on the system, etc.), but I don't want to allow them to use SSH Tunnels (like the ones described in [this tutorial]("http://www.revsys.com/writings/quicktips/ssh-tunnel.html")). And I only want to block this for the "restricted" group because I use it heavily and removing it from the system completely is not an option. I've already been able to prevent them from using [Usermin]("http://www.webmin.com/usermin.html")'s HTTP tunnel but can't seem to block them from doing it directly through OpenSSH.

---

### Post by Lars Noodén on 2011-12-11
You could try something like this in /etc/ssh/[sshd_config](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html):
```

Subsystem sftp internal-sftp

Match Group restricted
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

If you want to let them have shell access then take out the [font=Courier New]ForceCommand[/font] directive.  Then you probably should have them using [rbash](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rbash.1.html) for their shell and provide a special $PATH with only a subset of programs available.

---

