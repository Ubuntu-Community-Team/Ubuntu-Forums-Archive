---
title: "dekko mail provider configuration"
date: 2015-09-06
forum: Ubuntu Phone and Tablet
---

### Post by jopub on 2015-09-06
I use a bq Aquaris E5 and have installed the dekko mail program with the recent release.
I followed the guided account setup and I was astonished, the mail program asked only for
an incoming server configuration.
I tried to fetch mails and that worked. Sending did not work, dekko crashed.
Could be the program reaction on a missed outgoing server configuration?
I found no possibilty to add the outgoing server in that account.
So I added a new account and configured a smtp-server. At saving - or better
finalizing - the configuration, dekko chrashed.
I have reinstalled the mail client, but the behaviour is unchanged.
Any ideas, what I do wrong?

---

### Post by w2vy on 2015-09-06
Your best bet is to go to IRC channel #dekko to look for help

tom

---

### Post by howefield on 2015-09-07
> **jopub said:**
> I have reinstalled the mail client, but the behaviour is unchanged.

Did you also remove the configuration files ?

As I understand it, removing....

```
~/.config/dekko.dekkoproject/
~/.cache/dekko.dekkoproject/
```

should get you back to a "clean slate" allowing you to cleanly recreate your account.

Note that this will also delete all accounts configured, so if you have more than one account set up, bear that in mind.

---

### Post by jopub on 2015-09-07
During the reinstallation of dekko, I didn't remove .config and .cache. Now I have removed the both folders (without reinstalling dekko).
In result, I'm able to configure smtp and imap server without crash. Receiving does work, sending ends with crash.
Hmm, I have seen ~/.local/share/dekko.dekkoproject. I suppose, it's the location of the mail database.
Is it?
I would delete that folder also, because I have no data to loose.
Is that a bad idea?

---

