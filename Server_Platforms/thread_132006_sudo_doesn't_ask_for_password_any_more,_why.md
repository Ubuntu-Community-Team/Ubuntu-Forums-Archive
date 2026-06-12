---
title: "sudo doesn't ask for password any more, why?"
date: 2006-02-17
forum: Server Platforms
---

### Post by jlist on 2006-02-17
I installed ubuntu server as user "admin" and every time I do sudo or "sudo -s" the server prompts for password. So I assumed this was the correct behavior.

Today I changed admin's password to a longer one, and changed root's password. Then I logged out, and logged back in as admin. When I do sudo or "sudo -s", the system doesn't ask for admin's password any more. Any idea why the behavior changed?

BTW, is root's password always the same as the first user? What if I log in as root and run passwd? I can not verify this because the system doesn't ask for a password any more.

---

### Post by localzuk on 2006-02-17
Ordinarily root doesn't have a password in Ubuntu. Take a look at '/etc/sudoers' and see if there are any options set for your 'admin' user as you call it.

You normally would not be able to log into root.

---

### Post by jlist on 2006-02-21
This is strange. On all the ubuntu/kubuntu installations I have, sudo always asks for password, except for the recent incident, on one of the boxes. What are others' experience?

---

### Post by mdmarmer on 2006-02-21
Not sure.

If you want a separate password for "root" (not the default in Ubuntu) you can key

sudo passwd root

This will give "root" a password (key your password first, then "root" password)

This is best security practice IMHO ...

Mike

sudo should ask for a password, though only the first time you key sudo in a teminal session -- repeated sudo statements don't ask for password ...

---

### Post by LordHunter317 on 2006-02-21
[QUOTE=mdmarmer]Not sure.

If you want a separate password for "root" (not the default in Ubuntu) you can key

sudo passwd root

This will give "root" a password (key your password first, then "root" password)

This is best security practice IMHO ...[/quote]No it isn't.

---

### Post by jlist on 2006-02-21
[QUOTE=LordHunter317]No it isn't.[/QUOTE]
Can you explain why?

---

### Post by LordHunter317 on 2006-02-21
Sure: having two passwords doesn't net you anything in a social engineering attack.  If I can get your user password, I can likely get root.

Most compromises aren't by password anyway, they're by software.

It just makes thigns more complicated for the regular user, without any clear gain.  If they manage to learn one of your passwords, the odds of them not being able to learn them all is pretty low.

---

### Post by newUBuser on 2006-02-27
this may be related....

I spent few hours installing ubuntu on my vmware and the user I created doesn't successfully log in....

I am guessing there is no default root password.....  so what can I do??

I tried to reboot and type init 1...  bu t there doen't seem be a way to force a boot to single user mode.   Or is there???

---

