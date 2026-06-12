---
title: "Root switches users passwordless. Problem?"
date: 2006-11-10
forum: Server Platforms
---

### Post by ridgerunner7 on 2006-11-10
It's possible to "su -" and then as root "su <any user>" without a pw prompt. To which I said "so what." I already have access to every user's files as root anyway. If the goal is to su to another user to let them get blamed for your "risky ventures" it won't work because the logs track su.

Thinking briefly, I can think of one instance right away where this would need consideration, compartmentalized root tasks. I'm sure there are other instances.

I find no discussion of this anywhere on the forums or googling. I don't know if this behavior is similar on other distros or not. 

Is  this is a problem and in what instances?

---

### Post by lloyd_b on 2006-11-10
As far as I know, this behavior is standard for every Unix variant.  Once you're root, you can switch to anyone without needing to know the password for that account.  I believe this is quite intentional - with things set this way, if an administrator needs to switch to a user account to debug an issue, he doesn't need to know the user's password.

As for compartmentalizing root tasks, "sudo" provides for such.

Lloyd B.

---

### Post by ridgerunner7 on 2006-11-10
Ya, I was guessing that to be the case. Just wanted to check. I'm not worried about it in the default config.

What I'm wondering about is other instances. For example, as part of the admin group I can "sudo su <any user>" and switch users. Fine. But if I want to prevent that how do I compartmentalize it so that an sudoer (or ultimately root itself in the extreme paranoid case) cannot switch to another user?

---

### Post by seuaniu on 2006-11-10
Sudo is a very powerful tool.  Ubuntu has it set up by default to let the first regular user use sudo to do anything as root.

In larger installations, its very helpful to be able to give certain users privileged access to certain parts of the system without having to give them the root password, or get the root user involved (calling the admin when you fsck up your httpd.conf and bring down the webserver).  This is what sudo was born from.  It also helps keep an audit trail so you know who has been screwing around with what when there's been a problem.

check out the documentation on sudo.  You can set up different permissions for each user, or restrict them to certain commands, i.e. if you have a web admin on your server, he doesn't need root access, but can 'sudo apache2ctl reload' if he needs to.  Its very flexible!

---

### Post by ridgerunner7 on 2006-11-10
Thanks for the hint. I did read su man page but wasn't thinking of sudo at the time.

For those who care:
1) I add this (red highlight) to my default /etc/sudoers:
 ```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults
Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
[COLOR=Red] <some user>    ALL=/usr/bin/su ""[/COLOR]

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```Of course <some user> would be a real user!

2) Now if <some user> tries to sudo su <any other user> a (very polite, I might add) error throws:
Sorry, user <some user> is not allowed to execute '/bin/su <any other user>' as root on <your hostname>.

---

