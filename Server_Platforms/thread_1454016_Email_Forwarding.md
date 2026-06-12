---
title: "Email Forwarding"
date: 2010-04-14
forum: Server Platforms
---

### Post by fortune2008 on 2010-04-14
I have like 40 email accounts fro all 10 of my domains and i'd like to know how can i forward say like all the [email]admin@mywebsite.com[/email] and like [email]admin@site2.com[/email] to one email so i can read them from one email

---

### Post by volkswagner on 2010-04-14
You should include some information on your current setup.

Sounds like you can use the alias directive.

---

### Post by HermanAB on 2010-04-14
fetchmail and nullmailer?

---

### Post by fortune2008 on 2010-04-14
The setup i used is 
**[How to set up a mail server on a GNU / Linux system]("http://flurdy.com/docs/postfix/")**

---

### Post by volkswagner on 2010-04-14
So you can use the alias directive from the how to.

[http://flurdy.com/docs/postfix/#data_add](http://flurdy.com/docs/postfix/#data_add)

---

### Post by ruuden on 2010-04-14
I use postfix and cyrus imap and in /etc/postfix/main.cf I have this line for alias for the mail accounts in imap: 

```
virtual_alias_maps = hash:/etc/postfix/virtual_alias
```The virtual alias file should look something like this:

```
info@example.com     ruuden@example.com
postmaster@example.com     ruuden@example.com
webmaster@example.com     ruuden@example.com

info@example.net     ruuden@example.net
postmaster@example.net     ruuden@example.net
webadmin@example.net     ruuden@example.net
```

---

### Post by ruuden on 2010-04-14
If you have several domains that need many aliases it might make sense to create one lookup table for each domain, you can just separate the tables with a comma like this in /etc/postfix/main.cf

```
virtual_alias_maps = hash:/etc/postfix/virtual_alias_example.net,hash:/etc/postfix/virtual_alias_example.com
```

---

