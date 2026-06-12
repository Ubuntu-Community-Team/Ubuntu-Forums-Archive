---
title: "Executed a command by mistake!"
date: 2009-01-14
forum: Security
---

### Post by smith02 on 2009-01-14
Hello Masters,

I was securing my HARDY LAMP and Joomla! installation
when I accidentaly execute this command 
" sudo find . -type f -exec chmod 644 {} \; "
on / directory, I should have execute it in 
/var/www where joomla resides. What's the effect
of the command to the entire server? 

Thanks in advance.

---

### Post by lswb on 2009-01-14
> **smith02 said:**
> Hello Masters,

I was securing my HARDY LAMP and Joomla! installation
when I accidentaly execute this command 
" sudo find . -type f -exec chmod 644 {} \; "
on / directory, I should have execute it in 
/var/www where joomla resides. What's the effect
of the command to the entire server? 

Thanks in advance.

You have given every regular file 644 permissions, or rw-r--r--
Is this system still running at all?

---

### Post by amauk on 2009-01-14
chances are you're screwed

you've disabled the execution of all programs on your system

---

### Post by Dr Small on 2009-01-14
It doesn't look pleasant.

---

### Post by smith02 on 2009-01-15
Actually the system's still fine, i just installed bastille.
It actually print an error message that it can't find
" {}\ ", something like that after exec.

---

### Post by amauk on 2009-01-15
guess there's safeguards against doing things like that (AppArmor, maybe?)

---

### Post by smith02 on 2009-01-15
apparmor is not installed as i'm trying to be minimalistic.
I guess the switch "{} \" that coused hardy to not execute
the command at all, It doesn't hurt the system, after bastille
I installed mod-security and it goes well.

thanks for the reply.

---

