---
title: "Installing servers without knowledge?"
date: 2009-11-27
forum: Security
---

### Post by Irihapeti on 2009-11-27
We are told regularly that if you are going to install a server, you should be aware of the security implications.

However, some programs install a mail server as a dependency. Rkhunter installs exim4, so does darcs (version control software) and I think that there may be others.

There's no warning during installation that this is happening. I'm wondering if this also is an accident waiting to happen. On the other hand, I've not seen any reports of problems with exim4.

Can someone with more knowledge tell me if I'm missing something here?

---

### Post by QLee on 2009-11-28
[QUOTE=Irihapeti]However, some programs install a mail server as a dependency. Rkhunter installs exim4, so does darcs (version control software) and I think that there may be others.
[/QUOTE]

Rkhunter also sets a cron tab to run daily, doesn't it? So, it has to have some way of communicating with root after it has run, thus a mail transport of some kind has to be available. It doesn't need to be Exim, I think any mail transport agent you have installed and configured on your system would satisfy the dependency.

---

### Post by Irihapeti on 2009-11-28
I can understand why rkhunter would have a mail server: to alert a remote sysadmin. BUT, does an ordinary user who installs rkhunter "just to be sure" know about this?

More importantly, once they've done that, are they more vulnerable to being hacked? That's my concern.

---

### Post by rookcifer on 2009-11-28
> **Irihapeti said:**
> I can understand why rkhunter would have a mail server: to alert a remote sysadmin. BUT, does an ordinary user who installs rkhunter "just to be sure" know about this?

More importantly, once they've done that, are they more vulnerable to being hacked? That's my concern.

I don't use rkhunter but I would assume that the mail server it installs is bound locally and not to the Internet at large (unless the user changes this).

---

### Post by koenn on 2009-11-29
> **Irihapeti said:**
> I can understand why rkhunter would have a mail server: to alert a remote sysadmin. BUT, does an ordinary user who installs rkhunter "just to be sure" know about this?

More importantly, once they've done that, are they more vulnerable to being hacked? That's my concern.

A Lot of programs require an MTA (Mail Transfer Agent, 'mail server') to deliver messages (alerts and other feedback) to the sysadmin. E.g. any cron job might fail if cron doesn't have a way to report results (redirecting output to a file sometimes helps to work around this if you don't have an MTA). Debian installs Exim4 by default to cover this - it's considered a part of a debian 'base' install. 

If you're installing something like rootkithunter without paying attention to basic stuff such as dependencies, you're just going through the motions. If you're really concerned about security, you'll pay attention to what you're installing, including dependencies, default configs you might want to change, etc. 

the first thing to learn about security is always : it's not about installing tools, it's about knowing your system, and knowing what you are doing.

---

