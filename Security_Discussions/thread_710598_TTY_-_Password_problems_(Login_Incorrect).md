---
title: "TTY - Password problems (Login Incorrect)"
date: 2008-02-28
forum: Security Discussions
---

### Post by chriswyatt on 2008-02-28
I'm using Ubuntu 7.10 (Gutsy) with an NVidia GeForce 4 MX440:

Hi, I'm having trouble with TTY consoles, I can never seem to use them.  Whenever I type a command it prompts for a password but never accepts it, I'm definitely typing the correct password and root and my account both use it, is this disabled for security reasons?  I've tried searching the internet for a solution and it seems that others can use TTY successfully, what gives :'( .

Oh, and looking at /etc/securetty they all seem to be enabled.

P.S. I noticed in Users & Groups all the permissions for root were disabled, I enabled them all to see if this would help (which I doubted very much), should I disable them again, is this a security risk?

---

### Post by Mr. C. on 2008-02-29
Can you clarify somethings?
[LIST]
[*]It sounds like you are able to login to the TTY correctly?
[*]You get to the shell?
[*]Every command after that prompts for a password?
[*]What user are you logging in as?
[*]From another TTY, show the output of all processes running on the first TTY (hint: ps -ux -t *ttynam*e, where *ttyname* is the last component of what is returned from the **tty** command)
[/LIST]

This sounds like there is some command that is running alongside your shell attached to STDIN, and which is also grabbing STDIN, and therefore it appears to you that each command is asking for a password.

Or, there's a trojan horse, but let's not worry yet.

MrC

---

