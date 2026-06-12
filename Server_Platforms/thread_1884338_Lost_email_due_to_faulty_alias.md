---
title: "Lost email due to faulty alias"
date: 2011-11-21
forum: Server Platforms
---

### Post by Dougga on 2011-11-21
I have a fairly standard email server running on Ubuntu

Postfix/Dovecot

I setup an alias I believe incorrectly by manually altering the alias file.  The server has been accepting email for this alias address but i can't figure out where they're being stored.  The users under which the alias was created is definitely not receiving the emails.

Can someone assist?

---

### Post by Jonathan L on 2011-11-21
> **Dougga said:**
> I have a fairly standard email server running on Ubuntu

Postfix/Dovecot

I setup an alias I believe incorrectly by manually altering the alias file.  The server has been accepting email for this alias address but i can't figure out where they're being stored.  The users under which the alias was created is definitely not receiving the emails.

Can someone assist?

Hi Dougga

Well one way is just to brute force search for a unique string: make up a random string
[INDENT]859933b2382cf8c00305df8caaf1632a
[/INDENT]Put it in an mail message to the alias. Then look for it:
```
sudo find / -exec fgrep -h 859933b2382cf8c00305df8caaf1632a '{}' ';'

```

Once you know where it's actually landing, you can debug it a lot easier.

Any use?

Kind regards,
Jonathan.

---

### Post by SeijiSensei on 2011-11-21
What do you see in /var/log/mail.log?

---

### Post by Dougga on 2011-11-21
I see no references to the aliased email address.

I have an smtp proxy and I do see the email getting forwarded to this email machine.

---

