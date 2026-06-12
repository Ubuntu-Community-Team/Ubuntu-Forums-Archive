---
title: "SSH pubkey for root, password for others"
date: 2006-08-04
forum: Server Platforms
---

### Post by el3ktro on 2006-08-04
Hello,

I'm running a virtual server with Debian, and I want to configure SSH access more secure. For backups I need root access to the machine with SSH, but usually I log in as a regular user and do things with sudo. Well allowing root access trough SSH is never a good idea, so I want to secure it a little bit more. What I want is that root can only login with pubkey authentication, so that my home server can login and make backups. But the regular user should be able to login with pubkey and with a password (if I ever need to log in from somewhere else). The problem is, SSH allows to only turn on/off password authentication for all users, but I'd like toturn it off for root only. Is that possible somehow? Or could I somehow restrict root access only to my machine etc.?

---

### Post by MJN on 2006-08-04
Check out the sshd_config manpage and, specifically, the **permitrootlogin** directive. This with the **without-password** argument should suit your needs.

Even better, investigate the use of the **forced-commands-only** argument - this allows root to only login with a key to execute a limited set of commands. I use this for my rsync backups i.e. only the rsync command is allowed to be executed. (the guide at [http://www.jdmz.net/ssh/](http://www.jdmz.net/ssh/) will give you some pointers)

Incidentally, I'm no expert but is there any security value in configuring key authentication for your normal users whilst still allowing password entry? Weakest link in the chain and all that?

Mathew

---

### Post by el3ktro on 2006-08-04
> **MJN said:**
> Check out the sshd_config manpage and, specifically, the **permitrootlogin** directive. This with the **without-password** argument should suit your needs.

Even better, investigate the use of the **forced-commands-only** argument - this allows root to only login with a key to execute a limited set of commands. I use this for my rsync backups i.e. only the rsync command is allowed to be executed. (the guide at [http://www.jdmz.net/ssh/](http://www.jdmz.net/ssh/) will give you some pointers)

Incidentally, I'm no expert but is there any security value in configuring key authentication for your normal users whilst still allowing password entry? Weakest link in the chain and all that?

Mathew

Thanks a lot, this will definitely help me. Well as I said, I need remote root login only to make backups of the server from my home machine, so it would be a good idea to reduce the root user to pubkey auth and to only execute the commands needed to create the backup. But, I want to be able to log in to my machine from basically anywhere. From my home machine, my laptop & my work I do this with pubkey too, but sometimes I'm at a friends house, in holidays or whatever, and I simply always want to be able to log in. So creating another (restricted) user for that is still better than allowing root to log in with password.

---

### Post by MJN on 2006-08-04
Sure, I'm just wondering what allowing key authentication is adding in terms of security given that you still allow password access. I suppose your regular use of key authentication limits your password 'exposure' as far as keyloggers etc are concerned (and that's just on your mate's PCs! ;))

Mathew

Edit: For clarity, when I say keyloggers I mean those that log keyboard keystrokes as opposed to those that might log your private key (assuming that possibility exists?). And I'm only talking about normal users (leaving root aside).

---

### Post by el3ktro on 2006-08-04
> **MJN said:**
> Sure, I'm just wondering what allowing key authentication is adding in terms of security given that you still allow password access. I suppose your regular use of key authentication limits your password 'exposure' as far as keyloggers etc are concerned (and that's just on your mate's PCs! ;))

Well I basically want additional pubkey access for my regular user simply because I use it pretty often and I'm lazy to type my (pretty long) password all the time :-) - at least when I'm @home.

---

### Post by MJN on 2006-08-04
As good a reason as any I suppose! ;)

---

