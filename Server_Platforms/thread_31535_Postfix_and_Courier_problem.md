---
title: "Postfix and Courier problem"
date: 2005-05-03
forum: Server Platforms
---

### Post by dallypost on 2005-05-03
I am a first time server builder and am having trouble checking my email with Evolution from a remote system. I have installed postfix and courier-pop and courier-authdaemon. All three are up and running.

When I attempt to check my email with Evolution, I was getting a message that said something about "Maildir, no file or directory". I added a Maildir directory to my home directory and now I get this error message:

"Unable to connect to POP server mail.dallypost.com.
Error sending password: -ERR Maildir invalid (no 'cur' directory)

Please enter the POP password for lance on host mail.dallypost.com"

Thanks for any help that you may be able to offer.

Lance Earl

---

### Post by accuser on 2005-05-03
You need to create the Maildir properly:
```
$ cd ~
$ maildirmake Maildir

```

---

### Post by dallypost on 2005-05-04
Thanks for the help. Your post got me past the initial problem and led me to another one. With the Maildir in place I can now log in to the system. However, when I attempt to send an email I get:

"Welcome response error: Connection reset by peer"

I googled a bit for an answer and found others with the same problem but solutions.

Thanks,

Lance Earl

---

### Post by alastair on 2005-05-04
I'd go over the install again - this is a POP (Courier) problem, probably just misconfigured.

There should be Courier docs somewhere under /usr/share/doc (always first port of call). Go through Courier configuration docs, readme's etc. and make sure you installed/configured things correctly. I think the fact that making "Maildir" folders etc. was an afterthought means you've more to configure probably.

---

