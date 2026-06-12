---
title: "gksudo - can anyone reassure me?"
date: 2006-03-12
forum: Server Platforms
---

### Post by essexman on 2006-03-12
I have become concerned about gksudo and sudo - the problem is more noticable on Dapper testing as I start privileged programs such as syaptic with higher frequency.

My concern is that after starting a privileged program (such as synaptic or a root nautilus)  the password remains for any other program and thereby the time limit is extended by starting the new program.

Of course I can reduce the time, even make it zero; but this defeats the ease of use of sudo as a root tool.

My sudoers is pretty basic:
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults    !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin    ALL=(ALL) ALL
ralph ALL= NOPASSWD: /usr/sbin/firestarter
jenny ALL= NOPASSWD: /usr/sbin/firestarter
The documentation for sudoers is pretty complex for me (I have read it) but I wondered if there was a way to limit sudo creating root access within a single program session?

for example:  I start a terminal session, and sudo is confined to that session.
Or: I start synaptic then close it it may or may not keep the sudo, but if I add printers I have to enter my password again.

This way sudo is limited by visual control, and a person present at the computer, keying in (or swiping a pass card) a password.

I am happy with the time limit of 15 minutes, but I am concerned that a root session can be started whilst I am using sudo, without my knowledge.

Can someone tell me how do do this?

---

### Post by knalle on 2006-03-12
[QUOTE=essexman]My concern is that after starting a privileged program (such as synaptic or a root nautilus)  the password remains for any other program and thereby the time limit is extended by starting the new program.
[/QUOTE]

running nautilus and stuff as root isn't a good practice but it isn't dangerous, a exploit attack on your computer can gain root and change your password, but it cannot that easily get your password because its not stored on your computer, only the [hash]("http://en.wikipedia.org/wiki/Hash_algorithm") is.

so even if your computer isn't safe, your password has pretty good privacy

---

### Post by essexman on 2006-03-12
[quote=knalle]running nautilus and stuff as root isn't a good practice but it isn't dangerous, a exploit attack on your computer can gain root and change your password, but it cannot that easily get your password because its not stored on your computer, only the [hash]("http://en.wikipedia.org/wiki/Hash_algorithm") is.

so even if your computer isn't safe, your password has pretty good privacy[/quote]

but if i can run sudo without entering my password because I am in the time slot, can anyone?

That is the crux of my question.

---

### Post by knalle on 2006-03-12
[QUOTE=essexman]but if i can run sudo without entering my password because I am in the time slot, can anyone?

That is the crux of my question.[/QUOTE]

technically yes, but sudo is very mature and have been around for such a long time so no seriouse exploits is know afik.

---

