---
title: "need suggestions for email server"
date: 2006-02-21
forum: Server Platforms
---

### Post by nephish on 2006-02-21
hello there,
i have apache installed and i am doing virtual hosting for 4 domains.
two of them would like an email service, nothing fancy, imap pop3 smtp.
what i need is the easiest to install and configure mail server that i can use with at least two different domain names 
like 
mail.firstdomain.com
mail.seconddomain.com

any one have a good suggestion ?

thanks

---

### Post by dbee on 2006-02-21
I'd be interested in hearing some views on this as well. I've heard that qmail is a good, clean, simple and secure mailserver... Anyone else have any thoughs ?

---

### Post by kmi on 2006-02-22
MySQL, Postfix, courier_imap and courier_pop seem to be the usual suspects (amongst others).

You might have look [there]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10").

Or [here]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier").

Is this the beginning of your answer ? I hope ! :)

---

### Post by nephish on 2006-02-22
these links are great, thanks !

---

### Post by Eternal Blade on 2006-02-23
Yeah, Postfix + MySQL + etc seem to be what the current standard is.  If you need links to help with the configuration I have a bunch, they just aren't on the computer I'm on now \\:D/

---

### Post by uopjohnson on 2006-02-23
To throw in my 2c:  I peraonlly use sendmail with about 5 domain and it works like a dream.  I imagine that the configuration would get out of hand however if I had moer than a few dozen users.  You can't beat sendmail though for rock solid configuration.  Once it is up it stays that way.

---

### Post by nephish on 2006-02-23
thanks for the tips, gents, looking into them

---

### Post by nephish on 2006-02-27
Eternal Blade, could you please post some of those links for me ?
thanks

---

### Post by Glut on 2006-02-28
[QUOTE=uopjohnson] I peraonlly use sendmail ... Once it is up it stays that way.[/QUOTE] I don't know whether to laugh or cry. If only this were the case, I could get rid of my stomach ulsers and work half the time.

---

