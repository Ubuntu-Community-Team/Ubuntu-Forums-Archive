---
title: "ssh sudo loophole?"
date: 2007-03-04
forum: Server Platforms
---

### Post by SanguineV on 2007-03-04
I recently came across a possible loophole in security which allows root access without requiring the root password. I have been able to repeat the process a couple of times on one box, but had trouble doing it on another. What I did was:

1. SSH into the box.
2. Enter a username, lets say "bob"
3. Enter the password, lets say "pass"
4. After/during the splash welcome ("Linux <server> ... i686 GNU/Linux ... Last Login ...") type "sudo -s" and hit enter.

This takes me immediately to root without requiring me to enter the root password!

I haven't tested this extensively and don't know if it has requirements regarding sudo access or not. What I have tested is doing it on another box with the same Ubuntu install but have been unable to replicate it (I suspect this is due to timing as the second server is much faster than the one I can break into).

Here is an edited transcript (removed all identifying details of boxes and user) if it is of interest (the parts in bold have been entered by me):

login as: **bob**
bob@<IP address>'s password:
Linux <stuff> i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: <more stuff>
**sudo -s**
bob@<server>:~$ sudo -s
root@<server>:~#


Any help with fixing this would be appreciated, while in this case it is only disturbing as opposed to a real security flaw (the box is isolated from everything for now), it would be nice not be able to circumvent root requiring a password!


**Update:** I have been able to replicate the process on the faster server as well now, it's just harder as the window to type in is smaller.

---

### Post by Mr. C. on 2007-03-04
This seems highly unlikely.

The process that spawns your shell changes userid's before your login shell is even spawned.

It is more likely that you sudo'd to root within timestamp_timeout minutes, and are able to sudo again w/out password.  Search for timestamp_timeout in:

$ man sudoers

Test this theory be setting it to 0 in /etc/sudoers.  For example:

Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=0

Now try your test as much as you'd like.

MrC

---

### Post by rbalfour on 2007-03-04
You logged in once with sudo. The password is cached.

I have run the above test and "sudo -s" doesn't bypass the password prompt.

From man

       -s  The -s (shell) option runs the shell specified by the SHELL envi&#8208;
           ronment variable if it is set or the shell as specified in
           passwd(5).

---

### Post by SanguineV on 2007-03-05
I'll try it again tomorrow and check the timestamp_timeout.

---

### Post by SanguineV on 2007-03-05
> **Mr. C. said:**
> This seems highly unlikely.

The process that spawns your shell changes userid's before your login shell is even spawned.

It is more likely that you sudo'd to root within timestamp_timeout minutes, and are able to sudo again w/out password.  Search for timestamp_timeout in:

$ man sudoers

Test this theory be setting it to 0 in /etc/sudoers.  For example:

Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=0

Now try your test as much as you'd like.

MrC

I updated the /etc/sudoers to contain "timestamp_timeout=0" and this appears to have fixed it.

Thanks!

---

### Post by Mr. C. on 2007-03-05
For your convenience, you can leave the timeout as is (default 15 minutes), and instead simply add a:

   sudo -K 

to your .logout file.  This will remove the cached timestamp, and invalidate the login. This way, you get the benefit of a 15 minute grace period, whilst having the security you desire upon logout 

MrC

---

