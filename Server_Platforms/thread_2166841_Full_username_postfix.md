---
title: "Full username postfix"
date: 2013-08-11
forum: Server Platforms
---

### Post by Bondar_Mircea on 2013-08-11
Hy
When login on my e-mail account with thunderbird my username is mircea. How to user full username  (mircea@domain.com). I use postfix+dovecot with mysql virtual user.

---

### Post by SeijiSensei on 2013-08-12
Set your Default Identity in Thunderbird to [email]mircea@domain.com[/email] using Edit > Account Settings.  Then pick Server Settings in the left-hand menu and make sure that your User Name is still mircea.

---

### Post by Bondar_Mircea on 2013-08-12
> **SeijiSensei said:**
> Set your Default Identity in Thunderbird to [EMAIL="mircea@domain.com"]mircea@domain.com[/EMAIL] using Edit > Account Settings.  Then pick Server Settings in the left-hand menu and make sure that your User Name is still mircea.
I set this but when add new email account thunderbird use t6he name without domainame. Dovecot/postfix check username (mircea) where this user not exist in database, and then check [email]mircea@andortipo.ro[/email]. I want to use [email]mircea@andortipo.ro[/email] username format first to fast login...Sorry for bad english

---

