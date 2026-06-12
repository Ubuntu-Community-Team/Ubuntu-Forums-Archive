---
title: "/etc/postfix/aliases doesn't exist"
date: 2007-03-09
forum: Server Platforms
---

### Post by caffeinated.chimp on 2007-03-09
hi all- i'm setting up an email server using 6.10.  i'm using a book on postfix (and a few online tutorials) as my guide.  

while trying to map email addresses to usernames, i've been instructed to edit the /etc/postfix/aliases file, but no such file exists.  should i create it?  and if so, what should go in it?

thanks mucho.

---

### Post by jtc on 2007-03-09
Actually, the default usually is /etc/aliases

If there is another path set, you should be able to find it by looking in /etc/postfix/main.cf

The syntax of aliases is as fallow

```
alias:  destination
```

(where destination can be a username as well as an email address)

---

### Post by Mr. C. on 2007-03-10
The /etc/aliases file is an old standard Sendmail location, and later /etc/mail/aliases.  You can move your aliases file into /etc/postfix/aliases; just change your /etc/postfix/main.cf setting:

alias_database = hash:/etc/postfix/aliases

MrC

---

